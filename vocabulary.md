# Vocabulary

These are the words this pack uses with specific meanings. Each definition is plain and short; it describes what the word means in context, not a rule it enforces. The rules live in [roles/](roles/) and [rituals.md](rituals.md).

## The project's pieces

**Goal / goals file.** The project's intent in the user's own words. One file (by convention `GOALS.md`), written only by the user. Nothing in the pack paraphrases it as rules elsewhere; other documents point to it when they need its words. The goals file is a document you may read and cite; it is not a document you may edit.

**Design.** The accepted design of the thing being built — what it must do, what is shared across its parts, what is outside its current scope. Owned by the user; changed only with the user's permission. Sections are referred to by number so other documents can cite them precisely.

**Plan in force.** The plan under which the current work runs: a list of jobs in order, saying what each gives the user and how its result is judged. One plan at a time. Earlier plans move to `docs/history/` as record; they do not bind.

**Job.** A unit of work a builder does. Each job has:
- a **level** — where in the hierarchy it sits;
- what it serves — which part of the design;
- a **standard** — how the result is judged;
- a definition of **done**.

**Level.** The depth at which a piece of work sits. Naming a level matters because a builder may decide anything at or below its job's level, but nothing above. "Level" is not seniority; it is scope.

**Standard.** The criterion a job's result is judged by. Set by the coordinator from what the design says the job serves, before the builder starts. A builder may challenge the standard (with reason) before measuring, or after measuring when the data gives it a reason. The coordinator decides; the user is told.

## The documents

**Record.** A dated document under `docs/history/` that says what a session did and found. One per discrete piece of work. A record is permanent reference; it binds nothing. Later sessions may contradict a record if the design or new evidence says so.

**Handoff.** A dated document under `docs/history/` that gives the next session everything it needs: reading list, the user's standing instructions that bind the work, memory files that bear on it, the job, the files involved, the branch, done criteria, the outgoing session's id. A handoff is written when a session is passing specific work on, not at every session's end.

**State file.** A short (about a page) document that lets a cold session take over. It carries: current plan and where the work stands in it, open work with who owns each thread, waiting-on-user list (short by design — a long one is itself a sign of trouble), known problems, and next action. Overwritten, not appended to. A closed item leaves; its life continues in its record.

**Findings ledger.** A running log of audit findings, if the project uses auditors. Each finding is named, dated, sourced, and stays in the "Open" table until the user settles it (applied, decided, or dropped).

**Inventory.** A list of what exists on disk, by full path, with a line each of what the file is for. Optional; useful on projects with many files whose purpose a fresh session can't guess from names.

## The roles

**Coordinator.** Holds the conversation with the user and the plan across sessions. Turns the plan into jobs. Writes handoffs. Answers builders' questions from the design. Confirms every builder's result against the job before it reaches the user. Keeps the state file, the findings ledger, and the inventory current. Does not build.

**Builder.** Does one piece of work: builds it, measures it, shows it does its job. Has judgment over everything at or below its job's level; nothing above. Never addresses the user — its questions go to the coordinator. Writes a record at the end of its work.

**Auditor.** Activated by the user, at their discretion, for a scope the user names. Independent of the coordinator and builders. Reads the user's documents (goal, design, roles) and the primary evidence (code, records, check outputs), and finds mismatches between what the project says it is doing and what it is actually doing. Reports; does not fix.

## The rituals

**Paragraphs.** A short piece of writing — a few paragraphs of plain prose — that a builder (or any session about to do non-trivial work) writes *before* starting. It says what the session understands the job to be, what it will build, what done looks like, and what it is unsure of. Read against the design and the handoff before building begins. The cheapest drift test in the pack.

**Where are we.** A plain-prose review of where the project stands, what is next and why, what is outstanding from earlier sessions, and what problems or undecided questions remain. The drift canary (see [rituals.md](rituals.md)).

**Check before agreeing.** Standing rule, built into every role. Before agreeing with the user's or another session's proposal, look for what is wrong or risky in it against the goal, the design, and the evidence. Raise that first. Agreement after a check is worth something; a bare yes is not.

**Record every session.** At the end of a session's piece of work, write a dated record under `docs/history/`. Even a short one. A session without a record didn't happen, for the next session's purposes.

**Go.** The user's word for *proceed*. No session starts a long-running job, a sub-session, or a large piece of work without a plain "go" from the user. Short of that, it may propose, draft, measure small things, and wait. This is a cost rule as much as a direction rule: unauthorised fan-outs and long runs waste tokens and attention.

## The approach

**History as reference, not binding.** Anything under `docs/history/` is a record of what a session did or found. It is reference. No number, no name, no requirement is taken from it unless the design or a current document (plan in force, state file, handoff) says so. A new session treats it as useful background, not as law.

**CLAUDE.md holds current state only.** The project's `CLAUDE.md` (or equivalent) describes the code as it stands today and how to run and test it. It does not hold decisions, rules, interpretations, or methods — those live in the design, in [roles/](roles/), in [rituals.md](rituals.md), and in records. A fact in `CLAUDE.md` is a current value, not a limit; a description there is what the code does today, not a definition of what the project is.

**No shadow design.** The design is one document. Decisions of the user's that change the design are held in the state file's "Pending design updates" only until the design is updated (with the user's permission); they are not scattered across records or rules in `CLAUDE.md`.

**Full paths, always.** Every file named to the user carries its full path or a link. Every command given to the user is given in full and in the user's actual shell. Relative paths and half-commands waste the user's time.
