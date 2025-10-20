# Activity: Proposal

## Overview

The **Proposal** activity establishes the foundation for any new feature, improvement, or initiative.
It captures the *problem definition*, *motivation*, and *intended value* before any technical work begins.
This activity aligns all collaborators—Stakeholders, Architects, and Engineers—on *why* the work exists
and *what success looks like* from a product or user perspective.

The Proposal serves as the primary input for the **Spec** activity.
Once approved, it becomes a stable reference point for all subsequent decisions.


## Purpose

* Define the **problem** and desired **outcomes** in clear, measurable terms.
* Build shared understanding between roles before design or implementation.
* Establish **scope, constraints, and assumptions** early.
* Reduce rework by clarifying expectations and dependencies.
* Provide a transparent record of discussions and rationale through logs.


## Participants

| Role                | Responsibility                                        |
| ------------------- | ----------------------------------------------------- |
| **Stakeholder**     | Owns the Proposal, defines value and priorities.      |
| **Architect**       | Validates feasibility and technical framing.          |
| **Engineer**        | Offers implementation perspective and early feedback. |
| **User (optional)** | Contributes practical insights or problem context.    |


## Artifacts

| Artifact             | Purpose                                                     | Example Output                            |
| -------------------- | ----------------------------------------------------------- | ----------------------------------------- |
| `proposal.md`        | Main document outlining goals, scope, and success criteria. | Approved proposal file.                   |
| `proposal-log.jsonl` | Append-only log of feedback, comments, and approvals.       | Structured review history.                |
| `state.json`         | Snapshot of current activity and approval status.           | `"Proposal": { "status": "in_progress" }` |


## Workflow

Typical flow of the Proposal activity:

1. **Drafting**
   The Stakeholder creates an initial `proposal.md` using the project template.
   It should define the *problem statement*, *goals*, and *success metrics*.

2. **Collaboration**
   Architects and Engineers review the proposal for feasibility and clarity.
   Feedback is logged in `proposal-log.jsonl` using structured entries.

3. **Iteration**
   The Stakeholder revises the proposal based on feedback until alignment is reached.

4. **Approval**
   Once all collaborators agree, an `approve` entry is logged, and
   `state.json` updates to mark the activity as **approved**.

5. **Handoff**
   The approved proposal becomes the input for the **Spec** activity.


## Checklist

* [ ] Problem and motivation are clearly defined.
* [ ] Success criteria and measurable outcomes are included.
* [ ] Scope and assumptions are explicitly documented.
* [ ] Dependencies and risks are acknowledged.
* [ ] All relevant roles have reviewed and logged feedback.
* [ ] Approval event is recorded in `proposal-log.jsonl`.
* [ ] `state.json` reflects the approved status.


## Guidelines for Writing Proposals

* Write from the user or business perspective first, not from an implementation angle.
* Keep the **problem statement** separate from the **solution outline**.
* Use clear, outcome-oriented language—avoid vague terms like “improve performance” without context.
* Include references or supporting materials in `.include/` or external docs if necessary.
* Maintain semantic clarity and readability—follow line length and indentation rules from `styleguides.md`.


## Example Structure

```md
# Feature Proposal: Improved Authentication Flow

## Problem
Current login flow causes user drop-offs due to multiple redirects.

## Goal
Simplify authentication while preserving security and compatibility.

## Success Metrics
- Reduce login completion time by 40%.
- Maintain 100% MFA coverage for enterprise users.

## Scope
Affects login, session handling, and SSO integrations.
Does not modify user database schema.

## Dependencies
Requires API v2 readiness and frontend update to new OAuth flow.

## Risks
Breaking changes to existing clients if tokens are not migrated correctly.

## Next Steps
Draft the specification with technical design and rollout plan.
```


## Notes

The Proposal phase defines *intent*.
Avoid prematurely defining implementation details—that’s reserved for the **Spec** activity.

Every feedback cycle should produce structured log entries (`comment`, `request_changes`, `approve`)
to maintain a clear history of reasoning and decisions.

Keep the final document concise and easy to review—target one feature or initiative per proposal file.
