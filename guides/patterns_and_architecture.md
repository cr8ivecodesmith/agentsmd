Patterns and Architecture
===

## Principles

- Reduce cognitive load with organization
- Prefer composition over inheritance
- Use inheritance when modeling stateful polymorphism
- Functions should be stateless and idempotent
- Classes represent stateful, mutable data
- Classes can namespace stateless functions
- Avoid nesting beyond 4 levels

### Reduce cognitive load with organization

#### Why
- Readers should grasp intent quickly without tracing every line.
- Clear boundaries and names shorten the “what is this?” loop.

#### How
- Separate concerns into small modules/functions with single responsibilities.
- Name things by responsibility and outcome, not by implementation detail.
- Keep entrypoints thin; push detail into helpers.

#### Python example
```python
def process_order(order):
    """Thin orchestration reads like a checklist."""
    validated = validate_order(order)
    priced = price_order(validated)
    payment_result = charge(priced)
    return summarize(payment_result)

def validate_order(order):
    if not order.items:
        raise ValueError("empty order")
    return order

def price_order(order):
    order.total = sum(i.qty * i.price for i in order.items)
    return order

def charge(order):
    # Hidden complexity lives behind a simple name.
    return {"ok": True, "amount": order.total}

def summarize(result):
    return "paid" if result["ok"] else "failed"
```

#### Pitfalls
- Catch-all utils modules; prefer feature-oriented modules.
- Over-abstracting early; extract only when duplication or complexity appears.

### Prefer composition over inheritance

#### Why
- Composition keeps types small, testable, and flexible to change.
- Inheritance couples you to a parent’s lifecycle and surface area.

#### Python example (composition)
```python
class Logger:
    def info(self, msg: str) -> None:
        print(f"INFO: {msg}")

class PaymentGateway:
    def charge(self, amount: float) -> bool:
        return amount >= 0

class Checkout:
    def __init__(self, gateway: PaymentGateway, logger: Logger) -> None:
        self.gateway = gateway
        self.logger = logger

    def pay(self, amount: float) -> bool:
        self.logger.info(f"Charging {amount}")
        ok = self.gateway.charge(amount)
        if not ok:
            self.logger.info("Charge failed")
        return ok

# Swap collaborators in tests without subclassing Checkout.
```

#### Counterexample (inheritance used poorly)
```python
class CheckoutLogger(PaymentGateway):
    # Inherits unrelated API; violates LSP and mixes roles.
    def __init__(self, logger: Logger) -> None:
        self.logger = logger
```

### Use inheritance when modeling stateful polymorphism

#### Why
- A stable interface with multiple stateful implementations benefits from inheritance or ABCs.
- Good fit for domain variants that share a contract.

#### Python example (ABC-based stateful variants)
```python
from abc import ABC, abstractmethod

class PriceRule(ABC):
    @abstractmethod
    def apply(self, total: float) -> float: ...

class NoDiscount(PriceRule):
    def apply(self, total: float) -> float:
        return total

class PercentageOff(PriceRule):
    def __init__(self, pct: float) -> None:
        self.pct = pct
    def apply(self, total: float) -> float:
        return total * (1 - self.pct)

def checkout(total: float, rule: PriceRule) -> float:
    return rule.apply(total)
```

#### Notes
- Prefer ABCs/protocols for contracts; avoid deep hierarchies.
- Consider `collections.UserDict`/`UserList` when extending container behavior.

### Functions should be stateless and idempotent

#### Why
- Stateless, idempotent functions are easy to test, compose, and cache.

#### Python example
```python
def normalize_email(email: str) -> str:
    """Pure: same input => same output; no side effects."""
    return email.strip().lower()

def upsert_keys(existing: set[str], new: list[str]) -> set[str]:
    """Idempotent: applying twice yields same result as once."""
    return existing | set(new)

# Idempotency check
e1 = upsert_keys({"a"}, ["b", "b"])     # {"a","b"}
e2 = upsert_keys(e1, ["b"])               # still {"a","b"}
```

#### Pitfalls
- Hidden global mutation, time, randomness, or I/O inside “utility” functions.

### Classes represent stateful, mutable data

#### Why
- Encapsulate invariants and lifecycle around changing state.

#### Python example
```python
class RateLimiter:
    def __init__(self, limit: int) -> None:
        self.limit = limit
        self.count = 0

    def allow(self) -> bool:
        if self.count < self.limit:
            self.count += 1
            return True
        return False

    def reset(self) -> None:
        self.count = 0
```

#### Notes
- Use `@dataclass` for simple data holders; add methods when rules emerge.

### Classes can namespace stateless functions

#### Why
- Group related pure operations with shared configuration or naming.

#### Python example
```python
import hashlib

class Password:
    ALGO = "sha256"

    @staticmethod
    def hash(plain: str, salt: str) -> str:
        return hashlib.new(Password.ALGO, f"{salt}:{plain}".encode()).hexdigest()

    @staticmethod
    def verify(plain: str, salt: str, digest: str) -> bool:
        return Password.hash(plain, salt) == digest
```

#### Notes
- Prefer modules or functions unless namespacing adds clarity (config, domain grouping).

### Avoid nesting beyond 4 levels

#### Why
- Deep nesting harms readability and increases cognitive load.

#### How
- Use guard clauses, extract helpers, or dispatch tables/polymorphism.

#### Python example (refactor deep nesting)
```python
# Before
def handle(event):
    if event:
        if event.get("type") == "CREATE":
            if event.get("active"):
                do_create(event)

# After
def handle(event):
    if not event or event.get("type") != "CREATE":
        return
    if not event.get("active"):
        return
    do_create(event)
```

#### Alternative: dispatch
```python
def on_create(e): ...
def on_delete(e): ...

DISPATCH = {
    "CREATE": on_create,
    "DELETE": on_delete,
}

def handle(event):
    fn = DISPATCH.get(event.get("type"))
    if fn:
        fn(event)
```


## Testing


## Security Practices


## Optimization and Trade-offs


## Logging and Error Handling


## Module and Package Layout


## Anti-patterns and Micro-patterns


