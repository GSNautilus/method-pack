# Rituals

The short, repeated acts that keep the methods alive. The documents (plan, design, state, records) are the skeleton; the rituals are what keep it from going stiff.

Each ritual is cheap. Each catches a kind of drift the documents alone don't. None requires a slash-command: if your assistant supports them, see [skills.md](skills.md); if not, do it in prose.

## Paragraphs before building

Before a session (a builder, or any session about to do non-trivial work) writes any code, it writes a few paragraphs in plain prose:

1. **What it understands the job to be,** in the project's own terms. Not function names, not file paths, not call patterns — the thing the user cares about.
2. **What it will build,** in those same terms. If this part reads like "I will call X then write Y," it has drifted into a code plan and needs rewriting at a higher level.
3. **What done looks like,** and how the result will be judged against the job's standard.
4. **What it is unsure of,** and what it will do when it hits that uncertainty.

The user, or the coordinator, reads this against the design and the handoff before building starts. A paragraph mismatch is an hour of talk; a code mismatch is a day of rework.

This is where sessions most often leak: they skip the paragraphs and go straight to code, because code feels like progress. It is the single most catchable form of drift.

## Where are we

A plain-prose review of where the project stands, in four sections, in this order:

1. **Where we are.** One paragraph, tied to the goal and to the design's measure of done. If the project has a plan with numbered jobs, give the plan's jobs start to end in a table (place in order, job code and name, what it gives the user, status). Then one line on the latest job done and what it still lacks.
2. **What is next, and why.** The next job: what the user will be able to see or do once it is done, and why it comes now.
3. **Left outstanding from earlier sessions.** Each item a fact with its size and where it stands — known problems, things the user said to come back to, open threads, housekeeping.
4. **Possible problems, and things not yet decided.** Numbered. Each says what it rests on. Among them: decisions only the user can make, the riskiest work ahead, anything the user has not yet seen, and the session's own faults.

End with one line on what happens once this is settled.

**How it reads.** Plain, succinct prose for someone who knows the project. Not dumbed down; no function names, call names or file internals. Facts stated plainly; what isn't known, said so. The user's own words quoted where they set something. Numbers with their units and what they mean against their target ("about fifteen times slower than the plan's real-time target").

**Why it matters.** The author's phrase: *the drift canary*. If a session cannot write this clearly and succinctly from the sources, something has started drifting. The user's original words, quoted: "these paragraphs are kind of the unwritten canary in the coal mine for when things are drifting ... if you can't clearly and succinctly explain where we are in the project, what you are building, and why — then that is when you start building things that don't match my mental model."

**When to run it.** Weekly; at every major boundary; whenever you feel unmoored; whenever you suspect a session has lost the plot. Read from the sources (goal, design, plan, state, records, git log), not from memory.

## Check before agreeing

Standing rule, written into every role. Before agreeing with a proposal — the user's, another session's, or one of your own — look for what is wrong or risky in it against the goal, the design and the evidence. Raise that first.

Sessions are inclined to agree with whoever they are working with and to write confident text quickly. The check costs little; skipping it is where quiet errors enter. The author's own phrase for this tendency: *the agreeing tendency*.

A check that finds nothing says so: "I looked at this against §3 and the state file; I see nothing worth raising." That is an answer. A bare "yes" without a check is not.

The one caveat: this is not a licence to nitpick. Raise what would change what is done or whether it works. A choice at the responsible session's own level, recorded with a reason, is not a violation.

## Record every session

At the end of a session's piece of work, write a dated record under `docs/history/`. Even a short one. It gives:

- what was built or decided;
- what was measured and how;
- what remains and what is not tested;
- every file touched, by full path.

Records are permanent reference. They bind nothing — a later session may contradict a record if the design or new evidence says so. But a session without a record is invisible to the next one, and the work has to be re-found.

Records are short-form by default. Long investigations get their own document; a record points to it.

## Run only on "go"

A session does not start any long-running job, sub-session, large fan-out, or substantive build without a plain "go" from the user. Short of that, it may propose, draft, measure small things, read, and wait.

This is both a direction rule (don't build something the user hasn't agreed to) and a cost rule (fan-outs and long runs waste tokens and attention). On a project using sub-sessions in parallel, running one without the user's go can also break things other sessions are working on.

What counts as a go: the user's own words, verbatim, naming the thing. "Go," "yes do it," "proceed with job C4." Not inferred from earlier conversation; not inferred from a plan being written down. A plan is a plan; a go is a go.

## A note on ritual decay

Rituals decay when they are treated as boxes to tick. The paragraphs become a formality; the where-are-we becomes a template fill; the check becomes a phrase ("I've checked against the design") with no check behind it. When that starts happening, the symptom is usually the same: the sessions sound confident and the user feels unmoored.

The fix is not more process. The fix is to treat the ritual as what it is — a drift test — and when it fails, to pause and listen to what the failure is saying.
