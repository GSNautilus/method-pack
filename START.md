# The method pack

This folder is one person's way of working with a capable AI assistant (Claude, in the author's case) on projects that outlive any single session. It is written down so that a fresh session, pointed at this folder, can read it in one go and then be told *work as a coordinator*, *write me a handoff*, *run a where-are-we review*, *check this against the design before you agree*, and do it correctly, without inventing rules.

It is not a plugin, not a skill, and not a framework. There is no code to install. Nothing in here changes a session's default behaviour anywhere. A session reads this only when the user points at it, and only then.

## Who it is for

The methods grew out of one long-running project (a computational neuroscience codebase that outgrew any single session's context window) and have been sharpened there over months of real use. They are for projects of that kind: enough work that one session cannot hold the whole thing, enough lifespan that sessions have to pick up where other sessions left off. For a project that lives a day, you don't need any of this; use it on a project where you need it, and don't where you don't.

Written up here for two readers:

- The author, across their own projects, so the same patterns carry over without being reinvented each time.
- Anyone else who wants to try them. The vocabulary and the document shapes are plain prose; nothing in here needs the original project to make sense.

## How a reader uses it

**To use the methods on a project of your own:** read this folder end to end, then set up the documents the project calls for. The documents and the rituals do the work; this pack is their reference.

**To have a Claude session work this way on your project:** point it at this folder ("read the whole method-pack folder, in the order START.md says") before asking it to do anything substantive. Then say the thing: *be a coordinator for this project*, *write a handoff for the next session*, *run a where-are-we*, *check this against the design before you agree with it*. It will know what you mean.

## Setting up the pack on a new project

Read [onboarding.md](onboarding.md): the day-one moves, in order. Make the pack's pieces exist in your project before you point a session at them. Nothing heavy — the pack is additive, and you set up only what you need now.

## Read in this order

1. [vocabulary.md](vocabulary.md) — the words this pack uses, each with a short plain definition. Read this second (after this file). Later documents assume it.
2. [rituals.md](rituals.md) — the short, repeated acts that keep the methods alive (where-are-we, paragraphs-before-building, check-before-agreeing, record every session, run only on go).
3. [roles/](roles/) — the coordinator, builder and auditor role documents. Read in full when a project splits the work across separate sessions per role.
4. [shapes/](shapes/) — templates for the documents the methods rest on (state file, handoff, record, plan, goals, role).
5. [examples/](examples/) — real documents from one worked project (state file, handoff, record, where-are-we), showing the shapes in actual use.
6. [skills.md](skills.md) — the slash-commands the author uses alongside these methods, and what each does.

## What this is not

- **Not a framework or a plugin.** Nothing to install; nothing to configure.
- **Not a rulebook.** The *shapes* of the documents and the *roles* of the sessions are what hold. The exact wording is the author's; a user is expected to rephrase it in their own terms.
- **Not AI-specific in principle.** The patterns are about keeping intent intact across short-memory workers. They happen to be written for Claude because that is where they were developed; they would not change much for another capable assistant.

## A word on the author's project

Where this pack cites an example or a worked case, it is usually from the original project (a WebGPU neural circuit simulation). The pack never requires that project to make sense: examples are footnotes, not prerequisites.
