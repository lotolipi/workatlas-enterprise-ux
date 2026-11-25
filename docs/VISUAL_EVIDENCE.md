# WorkAtlas — Visual evidence atlas

Independent portfolio prototype · Synthetic scenarios · Manual results, not production validation

## 01 / One task, four perspectives

```mermaid
flowchart TB
  T["Shared task collection"]
  T --> M["My Day · current assignee"]
  T --> W["Work Board · shared status"]
  T --> P["Projects · project context"]
  T --> A["Activity · change history"]
```

Design intent: a reassignment changes ownership, not project association or status by itself. Activity represents the actor separately from the assignee. This is conceptual information architecture, not a verified backend schema.

## 02 / From blocker to intervention

```mermaid
flowchart TD
  A["Contributor reports blocker"] --> B["Task becomes Blocked"]
  B --> C["Lead reviews context"]
  C --> D{"Intervention"}
  D --> E["Respond / record next action"]
  D --> F["Reassign ownership"]
  D --> G["Deliberately change status"]
  E --> H["Shared views and Activity"]
  F --> H
  G --> H
```

Sprint 03: five user-reported manual workflow checks passed. The branches illustrate possible actions, not a required sequence or exhaustive test coverage.

## 03 / Ownership changes; history stays

```mermaid
flowchart TD
  A["Before · Contributor A owns task"] --> B["Lead reassigns to Contributor B"]
  B --> C["After · Contributor B owns task"]
  C --> D["Former assignee attempts status edit"]
  C --> E["Current assignee edits status"]
  D --> F["Rejected · no new Activity event"]
  E --> G["Saved · shared views and Activity update"]
  classDef denied fill:#fce8e8,stroke:#a33,color:#451515
  classDef allowed fill:#e4f3e9,stroke:#28734a,color:#143d29
  class F denied
  class G allowed
```

Sprint 04 exposed a former-assignee status-edit defect. A focused correction restricted editing and saving. Sprint 05 recorded user-reported passes for the two illustrated regression paths, including the checked refresh scenarios. Contributor A/B are illustrative labels, not research participants.

## 04 / Evidence, not impact

| Sprint | Recorded manual checks | Initial result |
| --- | ---: | --- |
| 02 | 3 | 3 passed |
| 03 | 5 | 5 passed |
| 04 | 5 | 4 passed, 1 failed |
| 05 | 2 | 2 passed |

```mermaid
flowchart LR
  A["Sprint 04 · defect observed"] --> B["Focused UI correction"]
  B --> C["Save rejection confirmed"]
  C --> D["Sprint 05 · two reported passes"]
```

Counts describe recorded checks, not participants, success rates, adoption or business impact. The Sprint 04 follow-up is intentionally not added to the counts. No new testing was performed for this visual atlas.

**Still unverified:** production authorization, concurrency, cross-device persistence, exhaustive role coverage, formal usability and business impact.

Source: [README](../README.md) and [Sprint 03–05 verification log](SPRINT_03_BLOCKER_RESOLUTION.md). All diagrams are explanatory design artifacts derived from those records.
