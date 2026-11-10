# Example — state file

Real state file from the author's project, as it stood on 2026-11-09. See [README.md](README.md) for context on how to read these. The shape to look for: header-with-when-written-at-which-commit-by-which-session, standing-instructions (verbatim quotes with dates), open-work-table (every row names who moves next), waiting-on-user, branches-table, pending-design-updates, known-problems (each with where the evidence is), next.

Notice: the state file is long. That is the point. A real state file for a many-session project is a page or so, dense with facts, and overwritten rather than appended. The texture matters; a shorter, neater version wouldn't teach the discipline.

---

# Coordinator state

Written: 2026-11-09, on `channels` after `d55baa77` (the user's list of 2026-11-09 taken into the plan; C17's and C18's builders started; C7 ended after round 4, merged at `1a1d3d11`), by the coordinator "Dendrite Garden coordinator handoff", `local_b828e769-b3e1-4010-890c-1b05b4d7d217`, on taking over from `local_eafa1976-d176-4aff-aaf2-1a6afe8fd5e9` (checked against git and the session list then: every branch head, merge and the tag as written here, no session running, the mismatches found corrected in the commit that wrote this line). Current, not cumulative (coordinator role §8): rows as they stood are this file in git history; closed items live in their records under `docs\history\`. The findings ledger, `C:\Users\Nautilus\Projects\Dendrite Garden\docs\coordination\findings.md`, has an empty Open table.

**Coordinator:** `local_b828e769-b3e1-4010-890c-1b05b4d7d217`, started by the user on 2026-11-09 from `C:\Users\Nautilus\Projects\Dendrite Garden\docs\history\handoff-2026-11-09-coordinator-36.md`. The user's message: "You are taking the coordinator role for Dendrite Garden, from local_eafa1976-d176-4aff-aaf2-1a6afe8fd5e9. Read your role's §2 list, then your handoff, C:\Users\Nautilus\Projects\Dendrite Garden\docs\history\handoff-2026-11-09-coordinator-36.md. Check the state file against git and the session list, and correct and commit any mismatch. Then tell me where we are, in the form of /where-are-we, and ask me for my list of small changes. Start no builder or run until I say."

**Mode:** per batch since C7 ended (the user: "let's work through those together"); continuous was set for C7 while the user was away (2026-11-09, the user: "I need you to be continuous", below in the standing instructions): the measuring and the fixes that won't change precision, carried on without waiting for the user, a brief Firefox window included (the user, 2026-11-09: "I said continuous. I said I wasn't here. Why did you stop for a firefox run? You are the coordinator."); kind-2 and kind-3 changes and runs over about 30 minutes wait for the user. Context: up to about 80 % was said to `local_eafa1976` and its builder for C7 (the user's words of 2026-11-09, below in the standing instructions); this coordinator at 19 % on taking over.

**Working:** two builders, started 2026-11-09 at the user's "Go, both", each on Opus 5.5 in the coordinator's permission mode (auto), each in its own worktree off `channels` at `d55baa77`, each to send its paragraphs before anything else: C17's, "C17: the interface list — paragraphs first", `local_f0e69a2e-03f9-4f73-ac66-dd6cbbf8ad71`; C18's, "C18: save and load — paragraphs first", `local_2330eb1e-2602-41cf-b842-34c8c15f5001`.

**The line of work:** `channels`; the main checkout is on it. A marker tag, `works-2026-11-08` at `a43f6a9` (the code as merged at `2d3f6ac`, before C4), at the user's "Can we put a marker down here as a place where everything pretty much works though as is, so we can go back here if needed if performance tanks etc.?" (2026-11-08); the repository has no remote, so it is local only.

**Design:** `C:\Users\Nautilus\Projects\Dendrite Garden\docs\design\neuron-model-foundation.md`, changed four times on 2026-11-08, last at the user's "Apply it" (§6: a garden carries and computes only the channel types it places; a type's first placement or last removal structural); before that, C4 cut to its core ("This all sounds good": HVA as two types and SK, a gate reading its compartment's calcium; the calcium at a channel's mouth, BK, calcium-dependent inactivation and LVA designed and listed in §8 as built later).

**Plan:** `C:\Users\Nautilus\Projects\Dendrite Garden\docs\plan\plan-2026-11-04-channels.md`, turned to speed on 2026-11-08 at the user's "Apply it, Patch resize is fine too. I mean things that happen constantly, not things that happen because I changed a setting or added something." Its §4: C16, the speed shown, ending with the baseline in Firefox (axons drawn and hidden); then C7, faster, in rounds, frame and step time only; after them the rest of the user's list of 2026-11-08, unordered. Where the work stands: C16 done and merged (`6a73c40`); C7 round 1 done and merged (`3ebd0600`); round 2 done and merged (`67748bb8`); round 3 done and merged (`a0b586ee`); round 4 done and merged (`1a1d3d11`); C7 ended there at the user's word (2026-11-09).

**Declined:** the cortex patch with calcium (a small job at the user's ask, "Can we start a quick builder session to build our cortex patch with calcium added?"). The user, 2026-11-08: "No. I don't think we should build the cortex patch. I don't think Calcium works. It told me it takes literally THREE TIMES as much time now with Calcium. That's one ion. This is really bad, honestly." Nothing built; its worktree untouched at `775b624`.

## The user's standing instructions

- 2026-10-27: "Ask me before anything would archive or change something the plan doesn't name, and before any builder opens a Firefox window. The design and the role documents change only with my permission; if anything needs a change to either, or to the plan, draft it first with a full preview. If you need literature or more data, ask me for it first, listing authors, titles and years."
- 2026-10-28: "Don't write or change any memory without my explicit permission."
- 2026-10-28: "I don't want to spend ages pursuing tiny errors that circuits would absorb without any noticeable change and making the simulation run slower to achieve something that doesn't matter. I also don't want to spend days and days rerunning every single test every time anything changes. It seems like I have been sitting here running tests for weeks. I'm ready to see some real results that matter soon."
- 2026-10-28: "Of all the factors, I actually think simulation speed is the one I'm most willing to sacrifice if needed. Don't overblow that statement."
- 2026-10-29: "Please do not run unnecessary tests. There was NO reason for that repeated test. Can't you tell I'm losing patience for the constant repeat runs? The tests are getting out of control at this point."
- 2026-10-31: "Don't write or change any memory without my explicit permission. Don't start any run or builder unless I've clearly said go."
- 2026-11-01: "Do not start any run, builder or code, and do not apply any draft, until I have agreed what comes next. Anything that changes the design, the roles or the plan: draft it first with a full preview. Don't write or change any memory without my explicit permission. Everything you produce will be examined by auditors."
- 2026-11-01: "This is too much at once. The entire project is catastrophically broken - we aren't going to fix it all at once with this mess. One thing at a time. I'm not confident in your work or suggestions any more. Let's not pretend we can write this much without mistakes. One thing at a time."
- 2026-11-02: "We don't need to get stuck on every little thing. Just build it correctly from the beginning and we won't have foundational issues at every step that we have to hand tune."
- 2026-11-02: "We need to not have anything waiting on me before we start anything."
- 2026-11-04: "Let's keep an ongoing plan outline so I can stay on top of what's going on."
- 2026-11-05: "No, I tell you when to handoff" (after "I mean don't unnecessarily handoff right now."; it sets aside builder role §8's hand-over at 60%, for the user to say).
- 2026-11-06: "I WANT IT FIXED NOW. I don't want to see bugs we already fixed again."
- 2026-11-06: "we will defer checks to that new coordinator or later."
- 2026-11-08 (to the previous coordinator): "Let's not keep kicking me off the computer for this. Just do it headless. We can make sure the fixes work in Firefox at the end."
- 2026-11-08 (to the previous coordinator): "Speed still does need to be measured in Firefox to be final. But that's at the end. I don't want to not be able to use my computer while you work, that's not how we are going to work in general. Brief windows, yes. But otherwise, figure out another way. I get the computer first."
- 2026-11-08 (to the previous coordinator), on memory and the current-state document: "We have transcripts and history and other documents for that. That's not what claude.md or memory.md is for. Those are for clear, direct rules and policies. The quotes don't go in memory.md. Instead of following rules, you just quote me getting pissed at you for not following things I said but didn't make as rules. And then you still don't follow them, because now it's just a mess."
- 2026-11-09 (to the previous coordinator, during C7 round 2): "Okay. I'm going to leave for a while. Go ahead and measure - then go through and make any fix that won't change precision for now. You can keep going past your usual context limit if needed to ~80% at most. Same for the builder. If you think we should start a second builder session now in case so you have it without needing my permission, let me know. Otherwise, I need you to be continuous."
- 2026-11-09 (to the previous coordinator): "I said continuous. I said I wasn't here. Why did you stop for a firefox run? You are the coordinator."
- 2026-11-09 (to the previous coordinator): "Here is the frustrating part - my old words stopped you from following the new rules and opening a Firefox window when even the tiniest amount of logic would have told you that when I say I am not here, that means I am not using my computer, so you don't need permission to open a browser. I can tell you are able to bend my rules - because you just did it - I said I was back, why didn't you keep going? And instead of answering that question - you started the Firefox window. Do you understand how incredibly annoying that is? To wait until I'm back using the computer after I told you to use the time I was not using the computer to run the test?"
- 2026-11-09, starting this coordinator: "Start no builder or run until I say."
- The machine's budget, 2026-10-27: at most 8 CPU workers at any moment, one job at a time, headless Edge only when no CPU job runs, nothing beside a builder's work, the coordinator's included.

## Open work

| thread | owner | branch | status | next action | whose |
|---|---|---|---|---|---|
| C17, the interface list | its builder `local_f0e69a2e-03f9-4f73-ac66-dd6cbbf8ad71` | `claude/c17-interface-list-e978e2`, off `channels` at `d55baa77` | started at the user's "Go, both" (2026-11-09) on `handoff-2026-11-09-c17-interface-list.md`; port 9333. Its paragraphs came 2026-11-09 and are with the user; its question answered and one row of the standard reworded before any run. Settled with the builder before any run: the recorder is held by whoever needs it; the walk over only the held groups left out unless measured worth it. Its paragraphs approved by the user, 2026-11-09, asked "Approve C17's and C18's paragraphs?": "Approve both"; the approval relayed, the builder at work | the build (the switches, the top bar, paused landing, then the Ions options and the Channels fix); then its list of the runs of record | builder |
| C18, save and load | its builder `local_2330eb1e-2602-41cf-b842-34c8c15f5001` | `claude/c18-save-load-b6c479`, off `channels` at `d55baa77` | started at the user's "Go, both" (2026-11-09) on `handoff-2026-11-09-c18-save-load.md`; port 9334; beside C17 in the page's file (plan §1). Its paragraphs came 2026-11-09 and are with the user. Its first run done and confirmed (Known problems: a loaded garden's delays). The user, 2026-11-09, asked "If a file fails to load, must your running garden stay exactly as it was?": "Keep it untouched" | the builder: the independent parts, the mended build, load; then its list of the runs of record | builder |
| C19, the defaults | — | — | in the plan, after C18: from a file the user saves | after C18 | — |
| C20, templates | the coordinator with the user | — | in the plan: their design with the user first. Design §3 says "Templates come after the neuron is done (§7). Nothing depends on one now", so it changes with the user's permission; nothing drafted | the user's answers: which neurons make the basic set, and how much of the tuning is the builder's; then the design change drafted with a full preview | user |
| C21, a new cortex patch | — | — | in the plan, after C20 | its other improvements, and whether it stands beside the first patch or replaces it, from the user before its handoff | user |
| Housekeeping | the coordinator | — | finished sessions unarchived; 17 worktrees beside the main checkout, 15 of them finished and C17's and C18's in use; 21 transcripts not saved | archiving and removing at the user's word; the transcripts saved | user |

## Waiting on the user

- **Halving the substeps** (kind 3: about half of every neuron step; every result changes): the user's to judge.
- **A loaded garden's delays** (Known problems): told to the user on 2026-11-09 with the coordinator's view that nothing need change; the builder goes on unless the user says otherwise.
- **The plan's C18 to say what the user decided of a refused build** (2026-11-09: "Keep it untouched", Open work): a change to the plan's text, for the user's permission with the next change to the plan; until then the decision is here and in C18's handoff §3a.
- **The machine, with builders at once.** The user's budget of 2026-10-27 has "one job at a time, headless Edge only when no CPU job runs"; the handoffs have each builder wait for another session's run to end. Asked 2026-11-09, unanswered: whether short page checks in headless Edge may run side by side, and beside C20's search on the CPU.
- **For C17,** asked 2026-11-09, unanswered; the handoff builds without them and takes the answer when it comes: where the user looked for the Ions colour's options and what they expected; a mark of fixed size for "behind" in the top bar, or nothing (the handoff: nothing); the NMDA plateaus row of Stats kept or dropped (the handoff: kept).
- **For C20 and C21:** Open work.
- **The audit.** The user, 2026-11-08: "Okay, that triggers an audit dog. I want to know how many made up rules you've added at this point and how much they've insidiously poisoned the project." A starting message for an independent auditor, for the user to start, is in the previous handoff. No auditor session in the session list as of this writing.
- **A "what-are-we-doing" skill to replace the builders' paragraphs:** to discuss when the user chooses (the user, 2026-11-08: "Make a note to discuss with me a what-are-we-doing skill to replace the paragraphs in the future, since apparently even after doing this several dozen times you still haven't figure this out."). Nothing drafted.
- **A memory for the run time limit** ("every check run carries a hard time limit in its own command"): asked 2026-11-07, unanswered.
- **Archiving the finished sessions:** asked 2026-11-06, unanswered.

## Branches

| branch | head | merged into |
|---|---|---|
| `channels` | this file's commit | — (the line of work) |
| `claude/c17-interface-list-e978e2` | `d55baa77` (its base; C17's builder at work) | not merged |
| `claude/c18-save-load-b6c479` | `d55baa77` (its base; C18's builder at work) | not merged |
| `claude/c7-4-step-785943` | `d1fc7383` | `channels`, at `1a1d3d11` (C7 round 4) |
| `claude/c7-2-step-f2ee49` | `2d69dbd1` | `channels`, at `67748bb8` (C7 round 2) |
| `claude/c7-1-axons-076f81` | `16ddf3d5` | `channels`, at `3ebd0600` (C7 round 1) |
| tag `works-2026-11-08` | `a43f6a9` | on `channels` (the marker, before C4) |
| `main` | `bd75b4e` | in `channels`' history (the published pages) |
| `claude/c16-speed-shown-8a3ab6` | `3e2ef34` | `channels`, at `6a73c40` (C16) |
| `claude/c4-core-2-31b9fd` | `82e0428` | `channels`, at `a38e0ab` (C4) |

(The full table in the real file has twenty-plus more branches, all finished and merged. Elided here as repetition.)

## Pending design updates

- **One file for the user's rules: a proposal** (at the user's "Write up a proposal to fix this.", 2026-11-08): draft `draft-2026-11-08-rules-file.md`, not applied; kept for a later coordinator. The user, 2026-11-09: "The very first rule is completely not what I said - this is stupid and I'm over it. We can keep your proposal, but like I said, a smarter coordinator is going to have to handle that work. So frustrating." Its rule 1 does not say what the user said ("I get the computer first", "Brief windows, yes"): it adds "No run may need the user off the machine" and "Keep runs short", which the user did not say. Every proposed rule to be checked against the user's own words before it goes to them.

## Known problems

- **Calcium's cost where placed, before C7**: HVA and SK in every group 17.43 → 6.16 ms a step after C7 against 3.46 without calcium. Each compartment steps 4 gates without calcium and 9 with it, plus the calcium and the GHK current; the two HVA types share one activation curve, computed twice. Not explained further. The user: "I don't think Calcium works. It told me it takes literally THREE TIMES as much time now with Calcium. That's one ion."
- **Two of Almog & Korngreen's HVA figures outside the stated 0.05 of the peak** (C4's record §6): Fig. 3a 0.0526, Fig. 4b 0.0542; the paper's barium recordings and its calcium inactivation timing fit no single conversion.
- **This coordinator's faults (2026-11-09):** it wrote "windows moved" into C18's handoff, where the page's windows are only shown, hidden and resized (found by the builder, corrected before any run); it named only changes of the second kind for the regrown axons, where the records say every wiring operation; reading a builder's output, it ran a command with `cd` into the builder's worktree, which moved its own working folder there until it went back.
- **The previous coordinator's faults on C4:** a fitted model as authority; reading before paragraphs; 1,300-word "paragraphs" passed on; "the six papers" unlisted; C4 grown to 35 papers by its own rule that every number needs a measured source.
- **The checks have no time limit of their own** (a run hung 7 hours on 2026-11-07); every handoff since asks for one in each run's command.
- **I2[413]: one neuron in 10,000 is built differently on the page from the reference** (C13's record §3, run 14), located to the shared tree code; for the clean-up after C7.
- **An operation that wires grows its axons from the change's own seed**: a build from the settings makes the same neurons, records, synapses and background events and "does not make the same axons, paths or delays". In a garden built by hand every connection was made by such a change, so a garden saved and loaded (C18) comes back with other axon paths and some other delays. Measured by C18's builder, 2026-11-09, on ten cases: the settings, every synapse, its compartment and strength and every soma's place the same in all ten; 0 to 5.4 % of the garden's synapses with another delay, each by one step, two steps in one case.
- **Speed** (C16's baseline, Firefox 148 at 3440 x 1440): at the top speed (720 ms of garden time a second asked) the 10,000-neuron garden runs 63.0 ms a second at 3.94 fps with the axons drawn and 97.2 at 6.08 fps with them hidden, about 16 and 10 times slower than real time; its neurons 4.8 ms a step. With HVA and SK in every group: 24.1 and 27.9 ms a second, the neurons 17.6 ms a step (3.7 times).
- **The starting set** adapts weakly and blocks under strong drive; the user's to tune.
- **The machine:** a degraded P-core 0, an RMA planned. Compaction is off for every session.

## Next

1. C17 and C18 building, their paragraphs approved (2026-11-09). The coordinator answers each builder's message, brings C18's delay measurement and C17's finding on the Ions report to the user, confirms each result against its handoff's standard, and merges the first one confirmed; the other brings `channels` in first (plan §1). Each is shown to the user in Firefox before it is called done.
2. At the user's answers on templates: design §3's change drafted with a full preview, then C20's handoff.
3. The plan's remaining items (plan §4, the user's list of 2026-11-08) after the new list, their order not set.
4. The audit, as the user starts it; housekeeping at the user's word.
5. Nothing starts and no memory is written until the user has said so.
