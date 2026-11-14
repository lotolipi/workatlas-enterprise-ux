# Sprint 03 — Blocker Resolution and Task Ownership

**Status:** Product requirements confirmed; UX specification proposed; implementation unverified  
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

## Proposed role permissions (not implemented or tested)
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

## Primary proposed journey
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

## Edge cases to design before implementation
1. Team lead reassigns a Blocked task without resolving the blocker.
2. Team lead changes both assignee and status in one edit.
3. A contributor opens a task that has been reassigned away from them.
4. A team lead attempts to reassign to an inactive or unavailable member (eligibility rules not yet defined).
5. Two people edit the same task concurrently (not supported by the current demo; do not imply conflict resolution exists).
6. An empty or missing blocker explanation (validation rule to decide).

## Acceptance criteria for a future prototype
- Team lead can change another contributor's task status.
- Team lead can reassign a task to a different contributor.
- Reassignment moves the task between the relevant My Day views without duplicating it.
- Work Board and project association remain consistent.
- Status and assignee changes are separately attributable in Activity.
- Blocker explanation remains accessible after resolution or reassignment.
- Contributor cannot perform unauthorized reassignment in the proposed role-based UI.
- Existing Sprint 02 filtering and status synchronization continue to work.

## Evidence boundaries
**Verified in Sprint 02 (manual user checks):** blocked-task reason display in Needs attention; Assigned to me filter; status updates synchronized to Work Board and Activity; mobile layout usable.

**Not verified:** role-based permissions, reassignment, blocker-response workflow, audit-field completeness, notifications, concurrency, security, production multi-user synchronization, formal usability outcomes.

## Next milestone
Create a low-fidelity, end-to-end interaction specification for **Blocked task → lead review → reassign or update → contributor sees change → Activity records actor**, then test one synthetic scenario before spending Figma Make credits on broader UI work.

No confidential employer data, designs, screenshots, or source code should be included.
