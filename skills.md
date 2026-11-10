# Skills

The slash-commands the author uses alongside these methods, and what each does. Skills are optional: the methods work without them; the commands only save keystrokes and keep the rituals from being skipped.

This file is a map, not an installer. In Claude Code, skills live in each user's own configuration (user-level, under `~/.claude/skills/`) or in a project's `.claude/skills/` folder (project-level). The pack doesn't install any of them.

## In active use

**/where-are-we** — Runs the where-are-we review (see [rituals.md](rituals.md)). The session reads the goals file, the design, the plan in force, the state file, the findings ledger's Open table, and the git log, then writes the four-section review in plain prose. The author keeps this as a project-level skill so its reading list points at the project's own paths; the body of the skill is the same across projects.

## Skills the pack could grow

Each of these packages a ritual or a document shape from this pack. None is included here as code; each is straightforward to write from the section it points at. If you add them to a project, they go under `.claude/skills/` in that project (the paths in the handoff and record templates are project-specific).

- **/handoff** — Drafts a handoff from the current state, following [shapes/handoff.md](shapes/handoff.md). The coordinator still edits and signs off before the user sees it.
- **/record** — Opens a dated record under `docs/history/` following [shapes/record.md](shapes/record.md). Fills in the date, session id, and branch; the session writes the rest.
- **/state** — Updates the state file against its discipline ([roles/coordinator.md](roles/coordinator.md) "Context, the state file, and handing over" and [shapes/state.md](shapes/state.md)). Overwrites rather than appends; prompts for changes rather than inventing them.
- **/paragraphs** — Prompts the session to write its paragraphs before touching code (see [rituals.md](rituals.md)). Reads the handoff and the design sections it points at first.

## Shape of a skill in this pack's style

The skills above share a shape worth noting:

- **Short.** One page of instructions, or less.
- **Reads the sources.** None invents facts the current documents don't hold. A skill that says "the project uses X" rather than "read X from the design and tell me what you find" has drifted.
- **Writes to a known shape.** Each produces a document in a shape the pack already defines, so the result is checkable against that shape.
- **No standing hooks.** None auto-triggers. The user invokes each when they want it.

## A note on which skills carry across projects

The rituals (where-are-we, paragraphs, check-before-agreeing, record-every-session, run-only-on-go) are the same across any project that uses this pack. The document-shape skills (handoff, record, state) bind to the project's paths, so each project that uses them wants its own installed copy.
