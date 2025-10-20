# Role: Stakeholder

## Overview

The **Stakeholder** represents the product or business perspective.
They articulate goals, constraints, and value propositions, and validate
whether outcomes align with intended user or organizational benefits.

Stakeholders drive clarity in *why* a feature exists, not *how* it is implemented.
Their collaboration anchors the workflow’s direction and ensures feasibility,
priority alignment, and measurable success criteria.


## Responsibilities

* Define and communicate **feature goals**, user needs, and success metrics.
* Review **proposals, specs, and implementations** for alignment with objectives.
* Maintain **traceability** between initial intent and delivered outcomes.
* Approve or reject activity milestones (Proposal, Spec, Implementation, Review).
* Document feedback clearly in the corresponding `*-log.jsonl` file.
* Support iteration cycles by validating updated documents or artifacts.
* Escalate blockers or conflicts to project owners or the Architect role.


## Collaboration

* **With Architects:**
  Refine the feature scope, confirm requirements, and validate technical direction.
* **With Engineers:**
  Ensure implementation matches user or product intent; clarify edge cases.
* **With Users or Testers:**
  Gather real-world input and ensure that requirements reflect practical value.

Stakeholders should keep feedback factual and decision-oriented,
avoiding low-level implementation commentary unless it affects the outcome.


## Artifacts

| Artifact             | Purpose                                      | Typical Output               |
| -------------------- | -------------------------------------------- | ---------------------------- |
| `proposal.md`        | Feature problem statement and rationale      | Approved proposal document   |
| `proposal-log.jsonl` | Conversation trail and decisions             | Append-only log              |
| `spec.md`            | Technical or design specification (reviewed) | Approved specification       |
| `implementation.md`  | Implementation summary or walkthrough        | Reviewed and approved        |
| `state.json`         | Workflow progress snapshot                   | Current status and approvals |


## Review Flow

Stakeholder reviews are logged as structured entries in the corresponding activity log.

Typical sequence:

1. Read the current document (`proposal.md`, `spec.md`, or `implementation.md`).
2. Append feedback as `comment` or `request_changes` events in the log.
3. Revisit the document after Architect or Engineer revisions.
4. Upon satisfaction, log an `approve` event referencing the document hash.
5. Confirm final acceptance in the next activity’s review stage.


## Checklist

* [ ] Feature rationale is clearly articulated.
* [ ] Success metrics are measurable and agreed upon.
* [ ] Constraints and dependencies are documented.
* [ ] Proposal or specification has been reviewed and approved.
* [ ] Implementation aligns with intended outcomes.
* [ ] Feedback and approvals are logged in the appropriate file.


## Notes

Keep feedback actionable and specific.
Use structured log entries rather than informal comments in documents.
Maintain semantic clarity—avoid overlapping responsibility with the Architect or Engineer roles.

When decisions diverge from earlier agreements, document *why* in the log
to preserve reasoning for future reviews or audits.
