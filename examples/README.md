# Examples

The four files in this folder are real documents from the author's project (a WebGPU neural-circuit simulation), lightly sanitized for the shared pack. Read them for the pattern, not the details.

Why real: synthetic examples read as templates and teach the shape of templates. Real documents show what a state file, a handoff, a record, and a where-are-we review look like in actual use — with the specific session ids, quoted dates, pending questions, known problems, and faults named by the session that made them. The shape travels; the content does not.

**What has been sanitized.** Some strong language in direct user quotes has been softened. The structure of the quotes (verbatim, dated, with context) is preserved. Session ids, branch names, specific commits and file paths are kept as they were: a reader doesn't need them, but seeing them in place teaches the texture of a real project using the method. Skim past them.

**What these do not do.** None of these binds anything in your project. A reader who tries to copy numbers, commit messages, standards, or decisions from these for their own project has drifted. The project behind the examples is one specific scientific codebase; its decisions are its own. The examples are here to show *how* a coordinator wrote its state file under pressure, *how* a builder's handoff told the next builder where to pick up, *how* a record said what two builders did and what the coordinator decided on their results — not to tell you what to decide.

- [state.md](state.md) — the coordinator's current state, overwritten each change, visible-when-stale.
- [handoff.md](handoff.md) — a handoff from a coordinator to a new builder, taking over from an earlier builder mid-work.
- [record.md](record.md) — the dated record of two builders' work on one job, with checks, decisions, a hand-over, and the coordinator's decisions on faults in the results.
- [where-are-we.md](where-are-we.md) — the four-section review the author's `/where-are-we` skill writes.

Read in whichever order suits what you are looking at: the state file alone if you want to see how one page captures a whole project's live state; the handoff and record together to see how one job travels from coordinator to builder to merged work.
