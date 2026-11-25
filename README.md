# WorkAtlas
### Making shared work visible, actionable, and accountable

**Independent enterprise product-design case study · Interactive responsive prototype · Synthetic data**

WorkAtlas explores a role-aware task workspace that connects **My Day**, **Work Board**, **Projects**, and **Activity** around a shared task collection. The design question is not simply whether work is visible, but whether responsibility, intervention, and changes remain understandable as tasks move between people.

> **Evidence boundary:** WorkAtlas is an independent portfolio exploration using fictional people, tasks, and scenarios. It is not an employer product, production deployment, or validated business outcome. No confidential employer materials are included.

## Case study at a glance

WorkAtlas explores how individual contributors and team leads can move beyond tracking work to resolving blockers, understanding ownership, and maintaining accountability.

I designed a connected enterprise workspace built around one shared task collection, with personal work, team coordination, projects, and activity history offering different perspectives on the same system. My design process spans problem framing, information architecture, role-based interactions, responsive prototyping, and manual scenario testing.

A critical ownership defect emerged when a former assignee could still change a reassigned task's status. A focused interaction correction restricted editing and rejected unauthorized saving in the tested prototype scenario. Subsequent user-reported manual regression checks supported activity integrity and current-assignee editing.

The project demonstrates an evidence-grounded approach to designing complex operational workflows. It uses synthetic data; formal usability outcomes, production authorization, and business impact remain unverified.

[Explore the case-study presentation](#case-study-presentation) · [Review the design and verification evidence](docs/SPRINT_03_BLOCKER_RESOLUTION.md)

## The problem

A shared board can show progress without clarifying what happens when a task is blocked, reassigned, or updated by a team lead. WorkAtlas frames four design concerns: **visibility, ownership, intervention, and accountability**. This framing is a design hypothesis, **not a finding from formal user research**.

## What I designed

- **Connected information architecture:** One shared task collection presented through My Day, Work Board, Projects, and Activity.
- **Role-aware interactions:** Contributors can report blockers and update their own assigned task status; team leads can intervene, update statuses, and reassign work in the tested prototype scenarios.
- **Blocker-to-intervention journey:** Report a blocker → review context → intervene/reassign → synchronize views → trace changes in Activity.
- **Edge-case iteration:** A former assignee was initially able to change task status after reassignment. A focused prototype correction restricted the edit and rejected saving in the tested scenario.

## Visual evidence atlas

[Explore the four visual evidence plates](docs/VISUAL_EVIDENCE.md): connected information architecture, blocker-to-intervention workflow, ownership transitions, and recorded manual validation results. The diagrams explain design intent and bounded prototype evidence, not production behavior.

## Evidence from manual prototype checks

| Sprint | Recorded results | Scope |
| --- | --- | --- |
| 02 | 3 manual checks passed | Earlier task visibility and synchronization checks |
| 03 | 5 manual checks passed | Blocker reporting, lead review, reassignment, shared state, activity trail |
| 04 | 4 checks initially passed; 1 initially failed | Former assignee could save a status change after reassignment |
| 04 follow-up | Tested former-assignee save restriction corrected; lead reassignment retested successfully | Scenario-specific user-reported manual checks |
| 05 | 2 user-reported regression checks passed | Rejected former-assignee edit left Activity unchanged; current assignee could update task status |

These counts are **not** participant counts, automated test results, usability metrics, or business impact. See [Sprint 03 blocker resolution and Sprint 04 verification](docs/SPRINT_03_BLOCKER_RESOLUTION.md) for the underlying decision log, observations, corrections, and unverified cases.

## What remains unverified

Formal usability research, real-world adoption, business impact, production authentication and authorization, comprehensive security testing, concurrent editing, cross-device persistence, and exhaustive regression coverage. Sprint 05 separately reports passing prototype-level checks for post-fix Activity integrity after a rejected edit and current-assignee status editing. Other roles, paths and environments remain unverified.

## Case-study presentation

A six-frame visual case study was prepared:

1. **Overview** — concept and connected workspace
2. **Problem framing** — visibility versus actionability
3. **System architecture** — shared data, different perspectives, roles
4. **Primary workflow** — blocker-to-intervention journey
5. **Defect resolution** — ownership boundary and correction
6. **Evidence and reflection** — manual checks, capabilities, limitations

**Presentation exports:** [View the final case-study PDF](https://drive.google.com/file/d/1hbOIAZaUfbbNq1OZzaKGkB7WqoYDD5S7/view) · [View/download the six-frame PNG export ZIP](https://drive.google.com/file/d/1ZQUW4DRGkSy2FIiUbKQWMeeOwhLmPy0M/view). These files are hosted in Google Drive, not yet committed as binary assets to GitHub. Access depends on the Drive files' sharing permissions.

## Project status

**Interactive prototype and case-study presentation completed for the documented scenarios; further validation remains open.** This is a portfolio prototype, not a shipped product.

## Design approach

Problem framing → information architecture → role and workflow modeling → interactive prototyping → manual scenario checks → defect correction → evidence-grounded reflection.

**Created by Shilpi Mishra (Lotolipi).**
