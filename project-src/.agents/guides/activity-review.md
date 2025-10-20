# Activity: Review

## Overview

The **Review** activity validates that the delivered implementation meets all functional, technical, and quality expectations.
It serves as the formal checkpoint between development completion and feature acceptance.

This activity ensures that the **definition of done (DoD)** criteria have been met and that the resulting system
matches the approved specification, implementation plan, and stakeholder goals.

Review provides a traceable audit of approvals, issues, and resolutions before final sign-off.


## Purpose

* Verify that the implemented feature aligns with `spec.md` and `implementation.md`.
* Assess completeness, correctness, and maintainability of the resulting code.
* Capture structured review feedback and final approvals in logs.
* Confirm that tests, documentation, and compliance requirements are satisfied.
* Ensure all deviations from prior artifacts are explicitly acknowledged and accepted.


## Participants

| Role                         | Responsibility                                                     |
| ---------------------------- | ------------------------------------------------------------------ |
| **Architect**                | Owns the activity; performs technical and design reviews.          |
| **Engineer**                 | Addresses feedback, fixes issues, and updates artifacts as needed. |
| **Stakeholder**              | Confirms alignment with product intent and success criteria.       |
| **Reviewer / QA (optional)** | Conducts quality and regression testing.                           |


## Artifacts

| Artifact                       | Purpose                                                   | Example Output                          |
| ------------------------------ | --------------------------------------------------------- | --------------------------------------- |
| `implementation.md`            | Updated document reflecting final code and revisions.     | Approved implementation record.         |
| `implementation-log.jsonl`     | Feedback, revisions, and approvals from the review cycle. | Append-only log.                        |
| `state.json`                   | Tracks activity status and approval outcome.              | `"Review": { "status": "in_progress" }` |
| Source code (`src/`, `tests/`) | Validated implementation under review.                    | Final reviewed commits.                 |


## Workflow

Typical flow of the Review activity:

1. **Initialization**
   The Architect begins review after the Development activity marks `ready_for_review` in `state.json`.
   The code, tests, and documentation are reviewed for compliance with the specification and DoD criteria.

2. **Evaluation**
   The Architect verifies code quality, maintainability, and design adherence.
   The Stakeholder evaluates outcomes against functional and product goals.
   Reviewers log feedback as `comment`, `request_changes`, or `approve` events in `implementation-log.jsonl`.

3. **Iteration**
   The Engineer addresses requested changes, updating code and documents as necessary.
   Each revision and re-submission is logged to maintain an auditable trail.

4. **Approval**
   Once all feedback has been resolved, the Architect and Stakeholder record final `approve` entries.
   The CLI or workflow tool updates `state.json` to mark the activity as **approved** and closes the task.

5. **Completion**
   The final approved implementation and logs serve as the permanent record of the feature’s completion.


## Checklist

* [ ] Development activity is marked `ready_for_review`.
* [ ] Implementation aligns with the approved specification.
* [ ] Code passes linting, tests, and security checks.
* [ ] Documentation is complete and synchronized.
* [ ] All feedback has been logged and addressed.
* [ ] Approvals are recorded in `implementation-log.jsonl`.
* [ ] `state.json` reflects final approved status.


## Guidelines for Conducting Reviews

* Use the log as the single channel for structured review communication.
  Avoid side discussions that bypass traceability.

* Prefer specific, actionable feedback over general remarks.
  Example: “Clarify exception handling in `auth/service.py:45`” instead of “Improve error handling.”

* Log all decisions explicitly, including rationale for any accepted trade-offs.
  Each log entry should contain timestamps and actor identity.

* Maintain clarity between roles:

  * The Architect focuses on system integrity and maintainability.
  * The Stakeholder focuses on alignment with business intent.
  * The Engineer executes and documents corrective actions.

* Update the `implementation.md` file to reflect any accepted design deviations
  or refinements discovered during review.

* When changes are significant, append a brief “post-review summary” section
  documenting lessons learned or recommendations for future work.


## Example Log Entries

```jsonl
{"ts": "2025-10-11T10:05:43Z", "actor": "Architect", "type": "comment", "targets": ["#api-endpoints"], "message": "Add timeout parameter for long-running requests."}
{"ts": "2025-10-11T12:21:00Z", "actor": "Engineer", "type": "doc_update", "message": "Added timeout handling and updated spec section 3.2."}
{"ts": "2025-10-11T13:30:15Z", "actor": "Stakeholder", "type": "approve", "scope": "Implementation", "notes": "Meets defined success metrics."}
{"ts": "2025-10-11T13:42:09Z", "actor": "Architect", "type": "approve", "scope": "Review", "message": "All criteria satisfied; marking complete."}
```


## Notes

The Review activity closes the workflow loop between intent, design, and delivery.
It confirms that what was built truly reflects what was planned and agreed upon.

All review discussions, approvals, and outcomes must be visible in `implementation-log.jsonl`
and mirrored in `state.json` to preserve full auditability.

When disagreements arise, the Architect facilitates resolution by referencing prior artifacts
(`proposal.md`, `spec.md`, `implementation.md`) and recorded decisions.

A thorough review process ensures confidence in the release quality
and strengthens institutional memory for future projects.
