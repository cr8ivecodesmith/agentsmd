Patterns and Architecture
===

## Principles

- much like documentation, code should be organized in such a way that it reduces cognitive load
- prefer composition over inheritance
- although managing state can benefit from inheritance
- generally functions should be stateless idempotent operations
- generally classes should be representations of stateful mutable data
- although classes can be great for namespacing stateless functions too
- never nest code beyond 4 levels--rethink your solution otherwise!

