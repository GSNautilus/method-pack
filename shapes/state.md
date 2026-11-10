# State file — template

The state file lets a cold session catch up. It is a page, not an archive. Overwritten, not appended to. Closed items leave; they live in their records.

See [roles/coordinator.md](../roles/coordinator.md) "Context, the state file, and handing over" for the full discipline. The short form:

- **Facts only, each one checkable.** Session ids against the session list; branches against git; user decisions quoted verbatim with their date and where they are recorded. No summaries of what the user prefers, no reasoning, no rules.
- **Current, not cumulative.** Overwritten. Closed items leave.
- **Visible when stale.** It opens with when it was written, at which commit, and by which session. A coordinator taking over checks it against git and the session list before acting.
- **No shadow design.** User decisions that change the design are held here only until the design is updated.
- **Every open thread names who moves next.** A long waiting-on-user list is itself a sign that something is going wrong.

---

# Coordinator state

Written: <date, time> at commit <hash> by <session title, id>
Mode: per batch | continuous  (the user's words, date)
Plan: <full path to the plan in force>; where the work stands in it

## The user's standing instructions

(Each a directive of the user's, verbatim and dated. Approvals of changes and reactions to events live in their records, not here.)

## Open work

| thread | owner (session, role) | branch | status | next action | whose |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |

## Waiting on the user

(Each item says why it can't be settled from the design.)

## Branches

| branch | head | merged into |
| --- | --- | --- |
|  |  |  |

## Pending design updates

(The user's decisions, verbatim, dated, where recorded, which design section they change. Held here only until the design is updated with the user's permission.)

## Known problems

(Facts, each with where the evidence is.)

## Next

(One short paragraph: what the coordinator does next.)
