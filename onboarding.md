# Onboarding

This document is for the day you decide to adopt this pack on a project. The rest of the pack describes how to work once the structure is in place; this one says how to get the structure in place.

Keep this light. The pack is additive. Set up only the pieces you need now, add more later. At any step, if setup is slowing you down more than the work itself, stop setting up and go write code.

## What you need before you begin

- A project with a git repository.
- A capable AI assistant you work with (Claude, in the author's case) and a way to point it at a folder of instructions.
- A sense of whether the project is big enough that keeping intent intact across sessions matters. If your head holds the whole project, you do not need this. Come back when it doesn't.

## The moves, in order

### 1. The goals file (do this first, by hand)

Create `docs/GOALS.md` at the project root. Write in your own words what this project is and why you are building it. As long or as short as you want — one paragraph is enough. No format required; it does not have to be a list or a plan or a spec.

This file is yours. Never paraphrased elsewhere; never rewritten by a session. It is the thing the whole project answers to. The [vocabulary entry for Goal / goals file](vocabulary.md) and [shapes/goals.md](shapes/goals.md) say more; both deliberately short, because the file is yours.

### 2. The current-state document

Make sure your project has a root-level document that says what the code is and how to run it. In Claude Code the convention is `CLAUDE.md`; other assistants have their own. If there is no such document yet, create a short one.

**What goes in it:** the code as it stands today, where things are, how to run the tests, any environment the project needs. Current state.

**What does not go in it:** decisions, rules, interpretations, the project's own rituals, lessons from past mistakes. Those live elsewhere — in the design, in the role docs, in `docs/history/`.

This separation is load-bearing. The [vocabulary entry](vocabulary.md) under "The approach" says why.

### 3. A design document (when the project is big enough)

When the project is big enough that you need to say what the thing *must do* apart from how you are currently building it, write a design document at `docs/design/<name>.md`. Numbered sections, so other documents can cite them. Numbered sections also make the design stable to reorganise: a cited section number can survive many rewrites.

The design is yours. It changes only on your deliberate decision, never on a session's. If a session proposes a design change, that proposal goes to a draft (not to the design) until you say otherwise. See [roles/coordinator.md](roles/coordinator.md) "What it never does" for the rule.

Small projects can skip the design. The project's goal is enough.

### 4. A plan in force (when you have more than a few jobs ahead)

Write a plan at `docs/plan/plan-<date>-<short-name>.md`, following [shapes/plan.md](shapes/plan.md). Numbered jobs, in the order they will be done, each with what it gives you and how it is judged. One plan at a time; when it is superseded, move it to `docs/history/` and write a new one.

### 5. Records (as soon as you want history)

Create `docs/history/`. Every substantive session's work ends in a dated record. See [shapes/record.md](shapes/record.md) and [examples/record.md](examples/record.md). Even a short record is better than none: a session without a record is invisible to the next.

Records bind nothing. They are reference, not law. See the [vocabulary entry](vocabulary.md) for "History as reference, not binding."

### 6. Roles (when work needs parallelism, or runs beyond one session)

Copy `roles/coordinator.md`, `roles/builder.md`, and (if you want it) `roles/auditor.md` from this pack into your project's `docs/roles/`.

Then — before you point any session at them — read them in full and edit them in your own terms where any of their rules do not fit your project. This is not optional. The role docs are the user's; the pack's versions are examples, not rules. A role doc that reads as the pack's wording unchanged is a role doc no one has thought about yet.

Common edits: your tooling's specific message tool (where the pack says "the tooling's message tool"), the specific ports or runners your project uses, your project's conventions for commits and merges, any constraints on when a run can go unattended. The structural content — what each role is for, what it decides, what it never does — usually transfers unchanged.

### 7. A state file (when you add roles)

Create `docs/coordination/state.md`, following [shapes/state.md](shapes/state.md) and [examples/state.md](examples/state.md). One page. Overwritten, not appended.

The state file starts short — just the mode, the plan, and an empty open-work table. It grows texture as work actually happens. If after a week it is still empty, you probably did not need it yet.

### 8. A findings ledger (only if you will use auditors)

Create `docs/coordination/findings.md` with just an empty "Open" table. The auditor writes findings here; the coordinator tracks them. If you are not running audits, skip this file entirely — an empty ledger is not a ritual.

### 9. Pointing a session at the pack

Once the above is in place, you can start a Claude session and say something like:

> Read the method pack: `<path to this pack>`. Start with its `START.md`. Then read this project's goals file (`docs/GOALS.md`), its design (`docs/design/...`), the plan in force (`docs/plan/...`) and the state file (`docs/coordination/state.md`). You are taking the coordinator role (`docs/roles/coordinator.md`).

The session has what it needs.

## A first check, after setup

Start a cold session, point it at your project with the pack loaded, and ask: "Run a where-are-we review." If what comes back reads as a plain summary of the project's current state against the goal, with specific items and specific uncertainties, the structure is in place.

If it reads as evasive, generic, or vaguely upbeat, something is missing — most often the goal is too abstract, the state file is empty, or the plan is not yet in force.

## When you do not need any of this

- One-session work, or work you can hold in your head between sittings. Skip the pack. A short record at the end if you want one.
- A short-lived experiment. Pack adoption costs time you would rather spend on the work.
- You have looked at the pack and its role docs do not fit the way you actually work. Change them, or drop them. A pack that gets in the way is not helping.

## What to watch for in the first few sessions

Three patterns, each a sign the pack is not earning its weight and needs attention:

- **The state file keeps going out of date.** Either you are not committing it after changes, or the coordinator is not writing to it. Both are fixable.
- **The waiting-on-user list grows long.** The pack is designed so that most things can be settled by the coordinator from the design. A long waiting list means either the design is thin, or the coordinator is deferring decisions it should make itself.
- **Handoffs read like templates.** If the session that writes a handoff fills the shape without engaging with the specific job, the handoff teaches nothing to whoever takes it over. The fix is the handoff review itself: the user or coordinator reads the draft and pushes back on the empty parts before the next builder gets it.

None of these mean the pack is wrong. They mean one piece of the method needs attention in your project's specific context. The pack is a frame; the work fills it.
