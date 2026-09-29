---
key: ABC-123
summary: Short title as in the tracker
from: mine            # mine / <login> / unassigned — where it came from
priority: P2          # P0 on fire / P1 / P2 / P3 — our own priority, not the tracker's
tracker_status: In Progress
tracker_assignee: dev
sprint: S12
real_state: in progress   # not started · analysis · in progress · in review (MR open) · merged to dev ·
                          # merged to main/prod, awaiting verification · confirmed by customer · waiting on external · not relevant
proposed_status: keep
next_step: Finish the migration and open an MR to dev
next_owner: us        # us / product / customer:<who> / colleague
merge_candidate: —
plan: "S12: doing"    # S12: doing / S12: if time permits / waiting / close / S13 / not ours
size: M               # S / M / L
plan_note: —
confidence: medium    # low / medium / high
checked: 2026-01-15
---

# ABC-123 — Short title

## What is asked
In your own words, 2–5 lines. Link to the issue in the tracker.

## History
Where it came from, what was discussed (with links to reference/ and journal/).

## What is done
- `service-api@a1b2c3d` — model and endpoint
- `group/web-frontend!42` — screen, open

## Where it is now
One or two lines: branch, environment, what has been verified.

## What remains
- [ ] …

## Questions
- 2026-01-15 🤖: do we need CSV export? → shared/questions.md

## Links
ABC-100 (parent), architecture/billing.md

## Tracker comment draft
(accumulates here while writing to the tracker is off)

## Log
- 2026-01-15 🤖 reconciliation: MR open, waiting for review.
