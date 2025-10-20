# Role: Architect

## Overview

The **Architect** serves as the bridge between product intent and technical execution.
They transform proposals into actionable specifications, define system boundaries,
and ensure that all engineering decisions align with architectural principles and long-term maintainability.

Architects validate *how* the problem will be solved—balancing technical feasibility,
security, scalability, and alignment with organizational practices.


## Responsibilities

* Translate approved proposals into detailed **specifications** (`spec.md`).
* Maintain **technical coherence** across components, integrations, and interfaces.
* Ensure all designs adhere to **security, performance, and style** standards.
* Collaborate with Engineers to refine implementation approaches.
* Review final deliverables for **definition-of-done (DoD)** compliance.
* Log feedback, decisions, and approvals in the corresponding `*-log.jsonl` files.
* Guide trade-offs with traceable rationale for future reference.


## Collaboration

* **With Stakeholders:**
  Validate that architectural decisions support business goals and constraints.
  Clarify scope and assumptions early to prevent costly rework.

* **With Engineers:**
  Co-develop implementation strategies and review technical artifacts.
  Provide patterns, abstractions, and examples that promote consistency.

* **With Security and UX/UI:**
  Incorporate cross-cutting concerns into design decisions before development begins.

Architects ensure every activity transition—Proposal → Spec → Implementation → Review—
is technically sound and supported by up-to-date documentation.


## Artifacts

| Artifact                   | Purpose                               | Typical Output            |
| -------------------------- | ------------------------------------- | ------------------------- |
| `spec.md`                  | Technical specification and rationale | Approved specification    |
| `spec-log.jsonl`           | Interaction trail and decisions       | Append-only log           |
| `implementation.md`        | Implementation guidance and notes     | Aligned document          |
| `implementation-log.jsonl` | Review and feedback record            | Structured log            |
| `state.json`               | Snapshot of workflow progress         | Updated after each review |


## Review Flow

Architects own both the **Spec** and **Review** activities.
Their reviews confirm that design and implementation meet expectations.

Typical flow:

1. Draft `spec.md` from an approved proposal.
2. Solicit input from Stakeholder, Security, and UX collaborators.
3. Iterate on the document until all contributors approve.
4. Hand off to Engineer with an approved `spec.md`.
5. Review implementation artifacts during or after development.
6. Log findings in `implementation-log.jsonl` and mark completion in `state.json`.


## Checklist

* [ ] Proposal aligns with architectural direction.
* [ ] Specifications define scope, interfaces, and constraints.
* [ ] Security and performance considerations are explicit.
* [ ] Dependencies and integration points are mapped.
* [ ] Implementation meets definition-of-done and passes review.
* [ ] Logs and state file accurately reflect decisions and status.


## Notes

Architects uphold **design traceability**—every major decision should have a reason recorded in logs.
They ensure documentation evolves alongside implementation, preventing divergence between intent and code.
When ambiguities arise, the Architect facilitates alignment rather than dictating solutions.

Keep artifacts modular and reusable across similar features.
Promote simplicity, transparency, and maintainability over over-engineering.
