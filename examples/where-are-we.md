# Example — where-are-we

Real where-are-we review from the author's project, 2026-11-05. The author's words on it ("This whole thing is exactly perfectly what I want"), recorded in the skill's own example, are what told the pack this ritual was worth packaging. See [README.md](README.md) for context.

The shape to look for: four sections only, in a fixed order — **Where we are** (one paragraph tied to the goal, then a job table), **What is next, and why**, **Left outstanding from earlier sessions**, **Possible problems, and things not yet decided**. Plain prose. No function names. No implementation detail. Numbers given with units and what they mean against their target ("about 15 times slower than the plan's real-time target"). Numbered items in the last section because each must stand on its own.

Notice that the last section — "Possible problems, and things not yet decided" — includes the session's own faults, not only external risks. That is on purpose.

---

## Where we are

This plan is about the neuron itself, which everything else in your goal is built from. Each neuron has a real grown tree and real ion channels, can be connected anywhere, can be changed while it runs, and all of it can be seen. The plan in force, the channel line of 2026-11-04, is judged by design §7: the neuron is done when you can connect any neuron to any other at any point, change either in any way its physics allows, and it behaves as it should.

The plan, start to end:

| # | job | what it gives you | status |
|---|---|---|---|
| 1 | The channel neuron | sodium, slow potassium and the M-current on trees grown from the Allen reconstructions | done |
| 2 | The channel editor | a library of channel types you can edit while the garden runs | done |
| 3 | C2: the CPU reference | a reference the GPU is checked against | done |
| 4 | C1: the interface's design | the mockup: panel, graph, regions, Move tool, routes, wiring by position | done ("Design is done") |
| 5 | C3a: old models removed | AdEx and the older model gone; the page opens on a channel garden | done |
| 6 | C3b: the operations | every change available to scripts while the garden runs | done |
| 7 | C1a: the interface, part 1 | the node graph, the Library, the View: you build gardens by hand | done |
| 8 | C6: the neuron tested | design §7 holds on everything tested; four cases where physics gives the opposite, reported | done |
| 9 | C10: tree dials | branch thickness and complexity; the soma drawn as a body | done |
| 10 | C8a: regions | groups in tissue of seven shapes, mixed or layered, moved and turned while running | done today |
| 11 | C1b: the interface, part 2 | the Space tab and the Move tool: you arrange gardens in space | now: its paragraphs to be rewritten |
| 12 | C8b: trees that keep clear | trees grow around each other instead of through each other | after C1b |
| 13 | C8c: routes | axons bundle into tracts, the delay following the bundle | after C8b |
| 14 | C9: wiring by position | senders chosen by distance, or by a topographic map | after C8c |
| 15 | C1c: the interface, part 3 | wiring by position on a connection's card; a neuron's senders shown | after C9 |
| – | Firing dynamics and channels tuned | the starting set's weak adaptation and its block under strong drive | "after the backbone"; no place in the order yet |
| 16 | C4: calcium | calcium inside the cell, and the channels it opens (SK, BK) | after the above |
| 17 | C5: more channel types | each from its paper, checked against its figures | when you choose |
| 18 | C7: speed | toward real time at 10,000 neurons | if you ask |
| later | Templates and building from data | outside this plan | when you bring templates and circuits back |

C8a, the latest, works only through scripts so far: there is no way yet to arrange regions by hand.

## What's next, and why

**C1b** gives you hand controls for regions:
- a Space tab, where you arrange groups into regions and layers;
- a Move tool, where you drag a region through the tissue or turn it, and see each connection's delay change as you go.

Without C1b, regions exist only for scripts.

## Left outstanding from earlier sessions

- **The starting channel set** fires, but adapts weakly and stops firing under strong drive. You asked for "the firing dynamics and channels" to be tuned after the backbone. The backbone (C2, C3a, C3b, C6) is now done, but that tuning has no job and no place in the order.
- **Speed:** the 10,000-neuron garden takes about 7.3 ms of GPU time for each 0.5 ms step in headless Edge, about 15 times slower than the plan's real-time target. It has never been measured in Firefox. It waits for C7, since you said speed is what you'd give up first.
- **C1a's check** has four faults of its own that come back in every run. Fixing them is a small job for whenever you want it.
- **Rebuilds:** after a wiring change (a connection, a count, where it lands, its fibre speed), a rebuild doesn't reproduce the axons exactly; after a placement change it does. This was left, possibly for C9.
- **Spikes in flight:** a spike travelling on an axon when a move regrows that axon can arrive twice or not at all. Not measured.
- **The public site:** publishing `channels` would leave the Tadpole guide pointing at a preset that no longer exists.
- **Housekeeping:** transcripts still to save, 64 worktrees still standing, and the audit waiting on your word.

## Possible problems, and things not yet decided

1. **The order of the rest of the plan.** Five spatial jobs come next in a row before anything returns to how neurons fire, and circuits sit outside this plan until you bring them back (design §8). C6 found design §7 holding on everything it tested, but you haven't said whether that makes the neuron "done". The design makes that the point where templates open. It's worth deciding whether the firing tuning waits behind C8b–C1c.
2. **C8b is the riskiest job left.** It costs time at 10,000 neurons, it interacts with the complexity dial and the decorative twigs, and with Regrow equal to a rebuild, a change regrows the later trees near it.
3. **The mockup has never been opened in your Firefox,** and C1b builds from it.
4. **Moving a big region will feel coarse on the 10,000-neuron garden.** A preview takes about 0.1 s, and a move lands about 0.45 s after you release it.
5. **My own process fault.** The handoffs for C8a and C1b asked builders to list function calls and internals in the paragraphs meant for you, and that's why C1b's read as they did. The fix belongs in the handoff: the paragraphs say what you'll be able to do and see, why, and where that differs from what you agreed. The calls and timings go in the record, for me to check.

Once we've settled this, I'll correct C1b's handoff and send its builder back to rewrite its paragraphs.
