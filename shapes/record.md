# Record — template

A record is a dated document under `docs/history/` that says what a session did, found, and left. It is permanent reference. It binds nothing: a later session may contradict a record if the design or new evidence says so.

Short-form by default. A long investigation gets its own document; a record points to it.

---

# <job code or short name> — <YYYY-MM-DD>

Session: <title, id>
Branch: <branch name> (merged into <base> at <commit>, where applicable)

## What this record covers

<One line: the scope. If it is a job, name the job.>

## What was done

(In project terms, not function names. What the user cares about.)

## What was measured

(For each measurement: how it was taken, against what, and the result. Point at output files by full path.)

## What remains

(What is not done or not tested in this record's scope. Open questions the user or the next session may need to settle.)

## Files touched

- `<full path>` — <role in this record>
- …

## Decisions recorded here

(Choices made at the responsible session's level, with the reason. Numbers chosen, inputs chosen, standards applied.)

## References

(Papers, prior records, external sources. Each with its citation.)
