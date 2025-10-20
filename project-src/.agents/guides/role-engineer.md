# Role: Engineer

## Overview

The **Engineer** is responsible for transforming approved specifications into working software.
They implement, test, and document features while ensuring code quality, maintainability,
and adherence to the established architectural and style guidelines.

Engineers embody the *how* of delivery—translating design intent into reliable, testable, and observable systems.
They collaborate closely with Architects and Stakeholders to maintain clarity, efficiency, and alignment throughout the workflow.


## Responsibilities

* Translate approved specifications (`spec.md`) into concrete implementations.
* Write clean, maintainable, and tested code following project **style guides** and **best practices**.
* Maintain synchronization between **implementation docs** and actual code.
* Record progress and reasoning in the relevant `*-log.jsonl` files.
* Participate in **development** and **review** activities with transparency and traceability.
* Communicate blockers, trade-offs, and technical constraints early.
* Propose refinements to specifications when implementation realities diverge.


## Collaboration

* **With Architects:**
  Validate design feasibility and request clarifications early.
  Report deviations or risks discovered during implementation.

* **With Stakeholders:**
  Demonstrate progress against goals and ensure functional alignment.
  Gather feedback on feature usability or performance where relevant.

* **With Other Engineers:**
  Share implementation patterns, enforce conventions, and perform code reviews.
  Ensure consistent test coverage and dependency hygiene across modules.

Effective collaboration depends on logging all key discussions and decisions.
Every substantial change or concern should result in a new log entry with context and rationale.


## Artifacts

| Artifact                       | Purpose                                               | Typical Output              |
| ------------------------------ | ----------------------------------------------------- | --------------------------- |
| `implementation.md`            | Implementation notes, rationale, and design decisions | Updated document            |
| `implementation-log.jsonl`     | Structured log of development actions and reviews     | Append-only file            |
| `changelog.jsonl`              | Sequential record of progress during development      | Event log                   |
| `state.json`                   | Snapshot of current workflow and activity status      | Updated per milestone       |
| Source code (`src/`, `tests/`) | Actual implementation deliverables                    | Reviewed and merged commits |


## Development Flow

Engineers own the **Implementation** and **Development** activities.
They ensure the transition from specification to working code is smooth, traceable, and validated.

Typical flow:

1. Read and understand the approved `spec.md`.
2. Plan implementation steps and outline the approach in `implementation.md`.
3. Begin coding and track progress in `changelog.jsonl`.
4. Update logs regularly to reflect discussion, commits, and test outcomes.
5. Submit artifacts for Architect review once the implementation meets the DoD criteria.
6. Address feedback iteratively until approval is logged and recorded in `state.json`.


## Checklist

* [ ] Specification is approved and fully understood.
* [ ] Implementation plan is documented.
* [ ] Code adheres to language and project style guides.
* [ ] Unit and integration tests meet coverage targets.
* [ ] Logs and changelog entries reflect current progress.
* [ ] All blockers and trade-offs are documented.
* [ ] Implementation passes review and is marked complete in `state.json`.


## Notes

Engineers should prioritize **clarity, traceability, and maintainability** in all deliverables.
Logs and documentation are part of the product, not side artifacts.
Prefer small, reviewable changes over large untracked updates.

Follow the repository’s established style and testing conventions.
Reference `styleguides.md`, `patterns-and-architecture.md`, and `workflow.md`
for details on design patterns, formatting, and collaboration expectations.

When the specification changes during development,
record the rationale in both the `implementation-log.jsonl` and the updated document.
Every significant deviation should leave an auditable trace.
