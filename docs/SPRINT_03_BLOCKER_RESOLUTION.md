# Sprint 03 — Blocker Resolution and Task Ownership

**Status:** Low-fidelity interactive prototype; five user-reported manual workflow checks passed; broader behavior unverified  
**Project:** WorkAtlas (independent portfolio prototype)  
**Date:** 14 November 2026

## Problem and goal
WorkAtlas Sprint 02 makes blocked work visible. Sprint 03 explores how a team can coordinate resolution without losing ownership or auditability.

**Design hypothesis:** Enabling team leads to respond to blockers, update task statuses, and reassign work within a single shared task system may improve coordination. This is not a research finding or measured outcome.

## Confirmed product decisions
- Team leads may change the status of tasks assigned to contributors.
- Team leads may reassign tasks to other contributors.
- WorkAtlas retains one shared task collection; My Day is filtered by assignee.
- The Activity view should make changes attributable to the person who performed them.

## Proposed role permissions (not comprehensively tested)
| Action | Contributor | Team lead |
| --- | --- | --- |
| View shared tasks | Yes | Yes |
| Change status of own assigned task | Yes | Yes |
| Change status of another contributor's task | No | Yes |
| Reassign tasks | No | Yes |
| Report a blocker on own task | Yes | Yes |
| Respond to a blocker | To be defined | Yes |
| View task activity | Yes | Yes |

Actual role identities, authentication, and authorization enforcement remain unspecified.

## Primary journey (manually checked in Sprint 03)
1. Contributor opens an assigned task, records a blocker explanation, and sets status to Blocked.
2. Team lead identifies the blocked task in Work Board.
3. Team lead reviews its context and records a response or next action.
4. Team lead may update status and/or reassign ownership, depending on what is needed.
5. My Day for the affected contributors reflects the current assignee; Work Board reflects the current status.
6. Activity records each change, including actor, timestamp, and before/after values.

## Proposed interaction rules
- **Reassignment does not automatically change status.** A blocked task remains Blocked unless its status is deliberately changed.
- **Status change does not automatically reassign ownership.**
- **A task appears in only the current assignee's My Day.** It remains in the same shared task collection and project.
- **History is append-only in the UX concept.** Reassignment or status changes must not erase the earlier blocker explanation.
- **Actor and assignee are distinct.** A lead's update must not appear as an action performed by the assignee.
- **Confirmation and feedback:** Show the new assignee and updated status after save; avoid silently changing other fields.
- **No invented notification behavior:** Notifications are outside the confirmed scope.

## Suggested event fields for prototype design
- Task identifier
- Event type (status_changed, assignee_changed, blocker_reported, blocker_response)
- Actor identifier and display name
- Timestamp
- Previous and new status or assignee where relevant
- Optional blocker explanation/response

These are proposed fields, not a claim about the current data schema.

## Edge cases requiring additional verification
1. Team lead reassigns a Blocked task without resolving the blocker.
2. Team lead changes both assignee and status in one edit.
3. A contributor opens a task that has been reassigned away from them.
4. A team lead attempts to reassign to an inactive or unavailable member (eligibility rules not yet defined).
5. Two people edit the same task concurrently (not supported by the current demo; do not imply conflict resolution exists).
6. An empty or missing blocker explanation (validation rule to decide).

## Acceptance criteria and remaining coverage
- Team lead can change another contributor's task status.
- Team lead can reassign a task to a different contributor.
- Reassignment moves the task between the relevant My Day views without duplicating it.
- Work Board and project association remain consistent.
- Status and assignee changes are separately attributable in Activity.
- Blocker explanation remains accessible after resolution or reassignment.
- Contributor cannot perform unauthorized reassignment in the proposed role-based UI.
- Existing Sprint 02 filtering and status synchronization continue to work.

## Sprint 03 manual verification — user report
The user reported **Passed** for all five test assignments in the existing Figma Make prototype:

| Assignment | Reported result | Scope |
| --- | --- | --- |
| 01 — Report a blocker | Passed | Contributor reports blocker on assigned task |
| 02 — Review the blocker | Passed | Team lead reviews blocker context |
| 03 — Reassign ownership | Passed | Team lead reassigns task |
| 04 — Verify shared state | Passed | Ownership reflected in relevant shared task views |
| 05 — Verify audit trail | Passed | Changes and prior blocker context reflected in activity history |

Screenshots supplied during the review show a Blocked task, blocker explanation, lead response, reassignment history, distinct contributor/lead identities, and the same existing WorkAtlas app shell. The complete before/after state for each test was not independently inspected in code; the five pass results are user-reported manual checks, not automated test results.

**Verified in Sprint 02 (manual user checks):** blocked-task reason display in Needs attention; Assigned to me filter; status updates synchronized to Work Board and Activity; mobile layout usable.

**Not yet verified:** comprehensive role restrictions beyond the tested contributor reassignment scenario, combined status-and-assignee edits, validation of empty blocker explanations, persistence after reload, all audit-event fields in every case, concurrent editing, security, notifications, production multi-user synchronization, formal usability outcomes, or business impact.

## Sprint 04 — Permission boundary verification
**Assignment 01: Passed (user-reported manual check, 14 November 2026).** In the existing Figma Make prototype, the user tested the Individual Contributor role and reported that reassignment was unavailable and no reassignment was saved. This supports the intended UI-level restriction for the tested scenario only. It does **not** verify backend authorization, bypass resistance, other role restrictions, or security controls. No new Figma Make generation was needed.

**Next untested case:** Team Lead changes both status and assignee in a single save; verify shared views and actor-attributed Activity entries.

## Next milestone
Document a concise **interaction and state-transition map** for the tested blocker-to-reassignment journey, then perform targeted edge-case checks (especially simultaneous status-and-assignee edits and reload persistence). Preserve the existing Figma Make project and avoid further generation until a specific failure or design gap warrants a narrowly scoped change.

No confidential employer data, designs, screenshots, or source code should be included.
