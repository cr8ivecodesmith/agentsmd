# Activity: Implementation

## Overview

The **Implementation** activity translates an approved specification into a concrete execution plan.
It bridges design and development by defining *how* the feature will be built, tested, and validated.

This activity ensures that every technical decision—structure, dependency, or integration—remains consistent
with the approved specification and overall architectural direction.
It documents the engineering approach before active coding begins in the **Development** phase.


## Purpose

* Convert the specification into actionable engineering tasks or modules.
* Outline technical steps, resource requirements, and success conditions.
* Record reasoning behind design adjustments or implementation trade-offs.
* Define testing strategy, deployment plan, and validation approach.
* Provide an auditable, pre-development reference for collaborators.


## Participants

| Role                         | Responsibility                                                    |
| ---------------------------- | ----------------------------------------------------------------- |
| **Engineer**                 | Owns the activity; authors and maintains the implementation plan. |
| **Architect**                | Reviews technical soundness and adherence to the specification.   |
| **Stakeholder**              | Confirms that the plan still meets user or business objectives.   |
| **Reviewer / QA (optional)** | Prepares validation criteria for later testing.                   |


## Artifacts

| Artifact                   | Purpose                                                 | Example Output                                  |
| -------------------------- | ------------------------------------------------------- | ----------------------------------------------- |
| `implementation.md`        | Main document describing technical plan and rationale.  | Approved implementation plan.                   |
| `implementation-log.jsonl` | Structured record of progress, feedback, and approvals. | Append-only log.                                |
| `state.json`               | Snapshot of activity status and progression.            | `"Implementation": { "status": "in_progress" }` |


## Workflow

Typical flow of the Implementation activity:

1. **Initialization**
   The Engineer creates `implementation.md` from the approved `spec.md`.
   It should outline how the design will be executed in practice,
   including module structure, data models, interfaces, and testing plans.

2. **Collaboration**
   The Architect reviews feasibility, and the Stakeholder validates scope alignment.
   All feedback is appended to `implementation-log.jsonl` using structured entries.

3. **Iteration**
   The Engineer updates the plan based on feedback and logs changes or decisions.
   Each revision should maintain traceability back to the `spec.md` and `proposal.md`.

4. **Approval**
   Once all collaborators are satisfied, an `approve` event is logged.
   The CLI or orchestrator updates `state.json` to mark the activity as **approved**.

5. **Handoff**
   The approved `implementation.md` becomes the foundation for the **Development** activity,
   where coding, testing, and integration take place.


## Checklist

* [ ] Specification has been approved and linked.
* [ ] Implementation plan references all key design elements.
* [ ] Major components and data models are clearly described.
* [ ] Testing and validation strategy are defined.
* [ ] Dependencies, environment setup, and tooling are documented.
* [ ] All feedback has been reviewed and logged.
* [ ] Final approval is recorded in `implementation-log.jsonl` and reflected in `state.json`.


## Guidelines for Writing Implementation Plans

* Write for future maintainers—describe intent, not just steps.
* Keep the plan synchronized with `spec.md`; note any deviations explicitly.
* Use Markdown headings consistently (H2–H4) per the style guide.
* Record justifications for changes in the log instead of embedding long commentary in the document.
* Maintain semantic line breaks for readable diffs in version control.
* Link to supporting documents or assets under `.include/` where appropriate.
* Document setup commands, code structure, and key function responsibilities concisely.


## Example Structure

```md
# Implementation: Improved Authentication Flow

## Overview
Defines the implementation approach for the approved authentication redesign.

## Goals
- Align code with `spec.md` architecture and interface definitions.
- Maintain backward compatibility for existing OAuth clients.

## Code Structure
\`\`\`

project/
├─ auth/
│   ├─ service.py
│   ├─ routes.py
│   └─ models.py
├─ tests/
│   ├─ test_auth_flow.py
│   └─ test_token_refresh.py

\`\`\`

## Key Steps
1. Implement new `/auth/login` route and session handling.
2. Migrate legacy token checks to unified verification layer.
3. Add Redis caching for session tokens.
4. Update tests and validation scripts.

## Testing Strategy
- Unit: `pytest` coverage ≥ 90%.
- Integration: Validate cross-service token exchange.
- Security: Verify MFA enforcement and session expiration.

## Risks
- Legacy SSO clients may fail if JWT claims differ.
- Session cache warm-up may temporarily impact performance.

## Validation
- CI pipeline passes linting, tests, and security scans.
- Architect review confirms DoD alignment.
```


## Notes

The Implementation document forms the *contract between design and development*.
Once approved, it defines the baseline scope and quality expectations for the feature.

All implementation feedback—especially deviations from the specification—
must be recorded in `implementation-log.jsonl` with sufficient context and timestamps.

Avoid jumping straight into code without a reviewed plan;
clear documentation upfront reduces rework, improves visibility,
and keeps the system architecture aligned with long-term maintainability.
