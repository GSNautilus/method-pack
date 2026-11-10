# Handoff — template

A handoff is a dated document under `docs/history/` that gives the next session (usually a builder) everything it needs to pick up the work. Written before the session starts; the user sees it first.

For the content a handoff must carry, see [roles/coordinator.md](../roles/coordinator.md) "Handoffs to builders". For who reads it and in what order, see [roles/builder.md](../roles/builder.md) §2. A builder working in its own worktree does not hold the project's memory folder, so the handoff names the files it needs by full path.

---

# Handoff — <job code or short name> — <YYYY-MM-DD>

From: <outgoing session title, id>
For: <builder session, or "the next builder of this job">

## Reading list

Read, in this order, before touching code:

1. `<full path to goals file>` — the project's goal, in the user's words.
2. `<full path to design>` (§<sections relevant to this job>) — the accepted design.
3. `<full path to roles/builder.md>` — how to work.
4. Persistent memory / notes that bear on this job, by full path:
   - `<path>` — <one line on why>
   - …
5. `<full path to plan>` — specifically the <section> for this job.
6. This handoff.

Everything under `docs/history/` is record. Reference, never binding.

## The user's standing instructions that bind this builder

(Verbatim, from the state file. Examples: runs under thirty minutes without asking; which browsers to use; what cannot be committed without the user; where sessions working in a worktree lose access to the main project's memory.)

## The job

- **Level:** <where in the hierarchy this job sits>
- **Parts it serves:** design §<X>, §<Y>
- **What they need from this job:** <in the design's terms>
- **Standard:** <how the result is judged, derived from what the design says the job serves>
- **Done means:**
  - <criterion 1, specific to this job>
  - <criterion 2>
  - record under `docs/history/` with every file by full path;
  - committed on `<branch>` and merged into `<base>`.

## Files

- `<full path>` — <role in this job>
- …

## Where to work

- **Branch:** `<branch name>`
- **Base:** `<base branch or commit>`
- **Worktree:** `<path>` (where the project uses worktrees)

## Coordinator's session id

`<id>` (for the tooling's message tool)

## Notes

(Anything else that doesn't fit above. Keep short.)
