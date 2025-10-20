# Activity: Spec

## Overview

The **Spec** activity transforms an approved proposal into a concrete, actionable technical design.
It defines *how* the proposed feature will be realized, including architecture, interfaces, data flow, and dependencies.
The specification becomes the single reference document for the **Implementation** activity that follows.

This activity ensures that the team shares a complete understanding of the design before any development begins.
All collaborators—Architects, Engineers, and Stakeholders—contribute to refining and approving the document.


## Purpose

* Translate the proposal’s intent into a **technical plan** with clear structure and rationale.
* Identify **components, boundaries, and interactions** between systems.
* Capture design decisions, trade-offs, and assumptions.
* Provide sufficient detail for Engineers to implement without ambiguity.
* Establish the baseline for architectural review and later validation.


## Participants

| Role                         | Responsibility                                                                 |
| ---------------------------- | ------------------------------------------------------------------------------ |
| **Architect**                | Owns the activity; drafts and maintains the specification.                     |
| **Engineer**                 | Reviews feasibility, raises implementation concerns, and proposes refinements. |
| **Stakeholder**              | Validates that the design fulfills the proposal’s goals and constraints.       |
| **Security / UX (optional)** | Provides focused feedback on compliance and usability.                         |


## Artifacts

| Artifact         | Purpose                                                      | Example Output                        |
| ---------------- | ------------------------------------------------------------ | ------------------------------------- |
| `spec.md`        | Core document describing architecture, components, and flow. | Approved specification file.          |
| `spec-log.jsonl` | Structured record of comments, revisions, and approvals.     | Append-only log.                      |
| `state.json`     | Snapshot of activity status and approvals.                   | `"Spec": { "status": "in_progress" }` |


## Workflow

Typical flow of the Spec activity:

1. **Initialization**
   The Architect drafts `spec.md` based on the approved `proposal.md`.
   It should outline architecture, interfaces, and design constraints.

2. **Collaboration**
   Engineers and Stakeholders review for feasibility, clarity, and goal alignment.
   Feedback is appended to `spec-log.jsonl` as structured `comment` or `request_changes` events.

3. **Iteration**
   The Architect integrates feedback, revising the document until all collaborators are aligned.

4. **Approval**
   Once consensus is reached, participants log `approve` events referencing the final document hash.
   The CLI or workflow tool updates `state.json` to mark the activity as **approved**.

5. **Handoff**
   The approved `spec.md` becomes the input artifact for the **Implementation** activity.


## Checklist

* [ ] The proposal has been approved and linked.
* [ ] All major design components are documented.
* [ ] Data flow, dependencies, and interfaces are defined.
* [ ] Security, performance, and UX considerations are addressed.
* [ ] Trade-offs and assumptions are recorded.
* [ ] All relevant roles have reviewed and logged feedback.
* [ ] Approval is logged in `spec-log.jsonl` and reflected in `state.json`.


## Guidelines for Writing Specifications

* Start from the **problem statement** and work downward into solution design.
* Keep architecture diagrams and data flow references lightweight and link external diagrams as needed.
* Follow consistent structure:

  * Overview
  * Architecture / Design Summary
  * Components and Interfaces
  * Dependencies and Risks
  * Implementation Notes
  * Acceptance Criteria
* Use Markdown headings consistently (H2–H4) as outlined in `styleguides.md`.
* Favor declarative over imperative tone—describe the system, not the process of building it.
* Use semantic line breaks to make diffs readable in version control.


## Example Structure

```md
# Specification: Improved Authentication Flow

## Overview
Defines the technical approach for simplifying the login process
while maintaining MFA compliance.

## Architecture
- Use centralized OAuth2 service for all client apps.
- Replace legacy redirects with direct token exchange.
- Cache session metadata in Redis for performance.

## Components
- `auth-service`: manages tokens and sessions.
- `ui-login`: new SPA component integrating the flow.
- `audit`: logs events to the monitoring pipeline.

## Interfaces

| Endpoint       | Method | Description                           |
| -------------- | ------ | ------------------------------------- |
| `/auth/login`  | POST   | Initiates OAuth login                 |
| `/auth/verify` | POST   | Verifies MFA and issues session token |

## Security Considerations
- Enforce token TTLs.
- Require HTTPS across all interactions.
- Validate JWT signatures against internal keys.

## Risks
- Incompatibility with legacy SSO clients.
- Temporary login latency during rollout.

## Acceptance Criteria
- MFA success rate ≥ 99%.
- Login completion time reduced by 40%.
```


## Notes

Specifications should remain living documents until approval.
Once approved, they are treated as *contract artifacts*—only modified through logged change requests.

All design feedback and decisions must be reflected in `spec-log.jsonl` for traceability.
Do not approve a spec until it clearly defines scope, interfaces, and responsibilities.

A well-formed specification should allow any qualified Engineer to implement the feature
without requiring additional clarification sessions.
