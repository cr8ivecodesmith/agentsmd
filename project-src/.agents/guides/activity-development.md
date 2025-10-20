# Activity: Development

## Overview

The **Development** activity turns the approved implementation plan into working, testable code.
It covers the full build–test–refine cycle while maintaining alignment with the design and documentation artifacts.
This activity is both iterative and traceable—each engineering action, decision, or change is logged for visibility and accountability.

The Development activity culminates in a validated, review-ready feature that satisfies the **definition of done (DoD)** criteria.


## Purpose

* Implement the feature or change as defined in `implementation.md` and `spec.md`.
* Ensure code meets the project’s **style, testing, and quality** standards.
* Record progress, updates, and design adjustments in structured logs.
* Maintain synchronization between documentation, code, and workflow state.
* Deliver a complete, review-ready artifact for the **Review** activity.


## Participants

| Role                         | Responsibility                                                       |
| ---------------------------- | -------------------------------------------------------------------- |
| **Engineer**                 | Owns the activity; writes, tests, and validates the implementation.  |
| **Architect**                | Monitors alignment with specification and reviews key milestones.    |
| **Stakeholder**              | Verifies that development progress aligns with goals and priorities. |
| **Reviewer / QA (optional)** | Conducts early validation or test execution.                         |


## Artifacts

| Artifact                       | Purpose                                                     | Example Output                               |
| ------------------------------ | ----------------------------------------------------------- | -------------------------------------------- |
| Source code (`src/`, `tests/`) | Actual implementation deliverables.                         | New or modified modules and tests.           |
| `changelog.jsonl`              | Incremental record of development progress and milestones.  | Append-only log.                             |
| `implementation-log.jsonl`     | Structured feedback and decisions from prior activity.      | Updated during handoff or review.            |
| `state.json`                   | Tracks current activity status, DoD progress, and blockers. | `"Development": { "status": "in_progress" }` |


## Workflow

Typical flow of the Development activity:

1. **Initialization**
   Engineer reviews the approved `implementation.md` and sets up the development environment.
   Tasks are broken down into manageable work units for traceability.

2. **Execution**
   Code is written, tested, and committed incrementally.
   Each milestone or decision is appended to `changelog.jsonl` using structured log entries.

3. **Continuous Validation**
   Run automated tests, linters, and CI pipelines regularly.
   Address feedback from Architects or Reviewers as part of iterative refinement.

4. **Documentation Sync**
   Update `implementation.md` and logs if the code diverges meaningfully from the original plan.
   Maintain a verifiable connection between artifacts and code.

5. **Completion**
   Once the feature meets DoD requirements and passes all tests,
   log an `implementation_complete` event in `changelog.jsonl` and update `state.json` to **ready_for_review**.


## Checklist

* [ ] All implementation steps from `implementation.md` are complete.
* [ ] Code conforms to project and language style guides.
* [ ] Unit and integration tests pass locally and in CI.
* [ ] Security, performance, and documentation criteria are verified.
* [ ] Logs accurately capture commits, progress, and blockers.
* [ ] Any deviations from the spec are documented and approved.
* [ ] `state.json` marks activity as `ready_for_review`.


## Guidelines for Development

* **Follow style and tooling conventions.**
  Adhere to linting, formatting, and testing standards described in `styleguides.md`.

* **Commit small and often.**
  Prefer frequent, atomic commits to large, unreviewable changes.

* **Keep logs factual and structured.**
  Each `changelog.jsonl` entry should record timestamp, summary, and related document references.

* **Maintain test discipline.**
  Add or update tests with every new module or feature path.
  Ensure coverage remains at or above project-defined thresholds.

* **Sync documents continuously.**
  Update relevant sections in `implementation.md` when scope, dependencies, or methods change.

* **Surface blockers early.**
  Log them explicitly in `state.json` and communicate with Architects or Stakeholders.


## Example Log Entries

```jsonl
{"ts": "2025-10-10T09:12:34Z", "actor": "Engineer", "type": "commit", "message": "Implement OAuth token validation"}
{"ts": "2025-10-10T11:05:22Z", "actor": "Engineer", "type": "test_passed", "scope": "integration"}
{"ts": "2025-10-10T13:48:57Z", "actor": "Engineer", "type": "blocker_reported", "details": "Redis cache latency in staging"}
{"ts": "2025-10-10T15:12:00Z", "actor": "Engineer", "type": "implementation_complete"}
```


## Notes

The Development phase is where **intent becomes reality**.
Every meaningful change—whether code, test, or documentation—should have a corresponding trace in the logs.
Avoid silent modifications; reproducibility and visibility are as important as correctness.

Use `state.json` as the system of record for status,
and ensure it always reflects the true state of development:
`in_progress`, `blocked`, `ready_for_review`, or `completed`.

A disciplined development process reduces friction in the **Review** activity
and builds confidence that artifacts faithfully represent the system being delivered.
