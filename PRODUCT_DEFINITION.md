# WorkAtlas — Product Definition v1.1

**Status:** Independent interactive prototype; limited manual checks completed  
**Product type:** Connected Team Work OS (Hybrid Work OS exploration)  
**Author:** Shilpi Mishra (Lotolipi)  
**Updated:** 14 November 2026

## Product vision
From individual work to collective clarity.

WorkAtlas explores whether one connected task system can help individual contributors understand priorities while giving teams a consistent view of work and progress.

## Problem statement and hypothesis
Individual contributors need clarity about assigned work, priorities, deadlines, and blockers. Team leads need visibility into ownership, project progress, and work requiring attention.

**Hypothesis:** A shared task system with contextual personal and team views may reduce coordination friction and improve clarity. This hypothesis has not been validated through formal WorkAtlas user research.

## Proposed users
- **Primary — Individual contributor:** A designer, analyst, or knowledge worker managing assigned tasks and reporting progress.
- **Secondary — Team lead:** A person coordinating assignments, deadlines, blockers, and project visibility.

These are provisional user roles, not research-validated personas. Production permissions and authorization are not defined.

## Product model — one connected task system
WorkAtlas uses one shared task collection rather than separate private and team task systems.

- **My Day:** Personalized view of tasks assigned to the active demo user.
- **Work Board:** Team-wide tasks grouped by To Do, In Progress, Blocked, and Done.
- **Projects:** Project-level grouping and progress representation.
- **Activity:** Task update history.

This is a new WorkAtlas design decision, not a verified implementation pattern of the earlier internal application. The demo does not claim secure multi-user access.

## Primary journey
1. Open My Day and review assigned work.
2. Select a task and open Task Detail.
3. Change its status and save.
4. See the updated task on Work Board.
5. Review the corresponding Activity event.

**Manual prototype evidence:** A status change for the fictional task “Finalize launch readiness brief” from To Do to In Progress was confirmed to appear on Work Board and in Activity. After a UI refinement, the status synchronization was retested and reported working. This verifies a limited demo scenario, not production reliability.

## Sprint 02 — Prioritization and team filtering
**Proposed rationale:** My Day should communicate why a task requires attention rather than leaving urgency implicit. Work Board should support a personal lens without creating a second task collection.

The proposed My Day classification gives each assigned task exactly one section:
1. Done → Completed.
2. Blocked → Needs attention (Blocked).
3. Incomplete and overdue → Needs attention (Overdue).
4. Incomplete and due today → Needs attention (Due today).
5. Incomplete, high priority and due within three calendar days → Needs attention (High priority).
6. Remaining In Progress → In progress.
7. Other incomplete tasks → Upcoming.

The Work Board offers **All team tasks** and **Assigned to me** views, filtering the same task collection without modifying task status.

**Reported manual verification:** The user confirmed three checks passed: a blocked task appeared in Needs attention with a reason; Assigned to me filtered the Work Board without changing task data; and a status change still updated Work Board and Activity. These checks do not establish exhaustive edge-case coverage.

## MVP scope
- My Day with reason-based prioritization
- Shared Work Board with status columns and assignee filter
- Task creation, detail, and status editing
- Basic project associations and project views
- Shared activity history
- Responsive desktop and mobile layouts

## Out of scope
- Private personal tasks (removed from the selected MVP model)
- Team availability, recognition, and sessions
- AI recommendations
- Advanced permissions and enterprise authentication
- External integrations
- Production multi-user synchronization

## Evidence and limitations
WorkAtlas is an independent portfolio concept informed by experience designing an internal enterprise work-management application. That earlier application remains partially functional; its access model and some editing behavior are unverified.

WorkAtlas uses fictional people, projects, and synthetic data. No confidential employer materials, source code, screenshots, or proprietary assets are reproduced.

The Figma Make prototype has undergone limited manual interaction checks. Mobile usability was reported as acceptable. There has been no formal user research, usability study, measured business impact, or production deployment.

## Next product-design milestone
Design and evaluate **blocked-task resolution**: how an individual contributor communicates what is preventing progress, and how a team lead identifies and responds to the blocker. First document the workflow, states, and permissions as proposals; then prototype and manually verify one scenario before claiming implementation.
