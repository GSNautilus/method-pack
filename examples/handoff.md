# Example — handoff

Real handoff from the author's project, 2026-11-08: a coordinator handing a job to a new builder, taking over from an earlier builder mid-work. See [README.md](README.md) for context. The shape to look for: taking-over context (what the earlier builder did and what is left), "the go" (how the builder's work begins), the point (what this job is for, in the user's terms), read-first (the reading list, in order), the user's standing instructions that bind the builder (verbatim from the state file), the job (level, fixed-above, yours, what-to-build numbered, not-this-job), the files, your paragraphs for the user (plain prose first, before any code), the standard (each criterion with its reason), runs, done, report.

Notice how specific "what-to-build" is, and how the standard sets tolerances and samples before anything is measured. Both are chosen to make drift catchable before it costs rework.

---

# Handoff 2026-11-08: C4, calcium inside the cell, the core

Plan job C4 (`C:\Users\Nautilus\Projects\Dendrite Garden\docs\plan\plan-2026-11-04-channels.md` §4), as cut to its core on 2026-11-08. Written by the coordinator `local_acadce82-73af-481e-b09b-eecf56fb0549`, who answers you (SendMessage). It replaces `handoff-2026-11-08-c4-calcium.md` (record now).

**Taking over (2026-11-08).** C4's first core builder, "C4: calcium, the core — paragraphs first" (`local_dc4dbf40-0fdf-4cd9-8e1f-ce32651657eb`), built the core and wrote its checks on `claude/c4-core-c265af` (`0b4c19d`, `671e67c`, `846c8ed` and what it commits on wrapping up), its record `docs\history\c4-core-2026-11-08-record.md` on that branch. The user then changed the design so that a garden carries only the types it places (item 9 below), and said: "We should probably wrap up that builders work and handoff to a new builder". You are that new builder. You start from its last commit and its record: what it built, each choice and its reason, its trials, and what is left. Left, as the coordinator knows it: item 9, which changes the layout the first builder built (every neuron carrying all six types); the checks brought to it; the runs of record. Its record is a builder's record: check what you take from it against the code and the papers, as builder role §2 says of the history.

**The go:** given by the user for the job; your paragraphs come first (plan §1). Plan §1: "**Before starting anything, reading included,** each builder sends a few paragraphs on exactly what it will do and why, showing it understands what the job is for and why each of its sources is wanted; it starts only after the user approves them". **Your first act is your paragraphs (below), sent to the coordinator, and nothing else.**

**The point.** The channel neuron has no calcium inside it. This job gives it the calcium the user wants now and no more: one calcium in every compartment, the calcium channels that feed it (HVA, as two types), its current by the Goldman–Hodgkin–Katz equation, SK reading it, and the calcium shown on the tree and in a trace. What it is for, in the garden: calcium you can see, as imaging shows a real neuron; dendritic calcium spikes, as in a layer 5 tuft; and adaptation over a train, which the starting set lacks. The user, 2026-11-08, after C4 had grown to 35 papers: "This sounds like things have spiraled out of control, you don't need this many papers."; then "Let's cut it down"; asked "Take this core for C4?": "Yes, this core". **So: build from the sixteen papers in hand, ask for none, and where they don't give a number, choose it and record why (design §9).** Keep the job to what is listed here; anything that would add to it goes to the coordinator before you do it.

## Read first

In this order (builder role §2):
1. `C:\Users\Nautilus\Projects\Dendrite Garden\docs\GOALS.md`.
2. `C:\Users\Nautilus\Projects\Dendrite Garden\docs\design\neuron-model-foundation.md`: §2 (the channels, calcium outside, calcium inside), §3 (a calcium type's amount, a gate's shift along calcium, the calcium per zone), §5, §6 (item 1; item 2, a regrown tree starts from rest), §7, §8 (what of calcium waits), §9.
3. `C:\Users\Nautilus\Projects\Dendrite Garden\docs\roles\builder.md`.
4. Memory files in `C:\Users\Nautilus\.claude\projects\C--Users-Nautilus-Projects-Dendrite-Garden\memory\`: `close-test-browsers.md`, `user-browser-firefox.md`, `build-to-design-not-code.md`, `git-corrupt-loose-object.md`, `old-presets-not-maintained.md`.
5. The plan: §1, §2 (the precision rule), C4 in §4.
6. This handoff.
7. `C:\Users\Nautilus\Projects\Dendrite Garden\docs\history\c4-calcium-2026-11-08-record.md`: the reading of the sixteen papers by C4's earlier builder, every number with its page. Record, binding nothing; it is where you start, and you check any number you take against its paper.
8. The first core builder's record, `docs\history\c4-core-2026-11-08-record.md` in your worktree: what is built and why, each choice, its trials, what is left.

As reference when the work reaches them (record): `channel-editor-2026-11-04-record.md` (the library, the gate forms, the generated kernel), `c2-reference-2026-11-04-record.md` (the reference and how plan §2's numbers were measured), `channels-2026-11-04-record.md` §2 with `tools\grounded\chan\na-activation.mjs` (a type checked against its paper by the paper's own protocol). `CLAUDE.md` gives the code and every check by command.

**Where:**
- **Branch:** your own worktree, cut from `claude/c4-core-c265af` at the first core builder's last commit. Your first act after reading: merge `channels` into it (documents only since `a3d1e22`: this handoff, the design and plan as changed), `git merge --no-ff channels`, and check it merged clean and touched no code.
- **Ports:** 9335 for the checks that name it, 9333 for those that name 9333. One headless browser at a time.
- **The machine:** before any run, check `tasklist` for `msedge.exe` and `node.exe` and wait for another session's run to finish; stop only your own processes, by PID; close every browser and runner when done. The user may be in Firefox.
- **Every run carries a hard time limit in its own command** (`timeout <seconds> node …`), about three times its estimate and never under 10 minutes (on 2026-11-07 a run hung for seven hours holding the GPU).
- **Coordinator:** `local_acadce82-73af-481e-b09b-eecf56fb0549`, by SendMessage. Its documents are in the main checkout, `C:\Users\Nautilus\Projects\Dendrite Garden\`.

**The user's standing instructions that bind you** (verbatim, from the state file):
- 2026-10-27: "Ask me before anything would archive or change something the plan doesn't name, and before any builder opens a Firefox window. The design and the role documents change only with my permission; if anything needs a change to either, or to the plan, draft it first with a full preview. If you need literature or more data, ask me for it first, listing authors, titles and years." (Through the coordinator; for this job, no literature is asked for.)
- 2026-10-28: "Don't write or change any memory without my explicit permission."
- 2026-10-28: "I don't want to spend ages pursuing tiny errors that circuits would absorb without any noticeable change and making the simulation run slower to achieve something that doesn't matter. I also don't want to spend days and days rerunning every single test every time anything changes."
- 2026-10-28: "Of all the factors, I actually think simulation speed is the one I'm most willing to sacrifice if needed. Don't overblow that statement."
- 2026-10-29: "Please do not run unnecessary tests. There was NO reason for that repeated test."
- 2026-11-02: "We don't need to get stuck on every little thing. Just build it correctly from the beginning and we won't have foundational issues at every step that we have to hand tune."
- 2026-11-05: "No, I tell you when to handoff". When you pass 60% of your context, say so once to the coordinator and keep working; keep your record current.
- 2026-11-06: "I WANT IT FIXED NOW. I don't want to see bugs we already fixed again."
- The machine's budget, 2026-10-27: at most 8 CPU workers at any moment, one job at a time, headless Edge only when no CPU job runs.

## The job

**Its level:** the channel neuron's calcium: the calcium in each compartment, the calcium types' current, a gate that reads calcium, the new library types, and how the calcium is set, carried, changed and shown.

**Fixed for you, above that level** (the design and plan): one calcium in each compartment as the buffered single compartment, through its volume, at the garden's resting level when nothing flows, all of it but 1 part in (1 + the buffers' capacity) bound, cleared by the membrane's pumps and the stores' uptake; only the calcium types feed it (not NMDA's calcium); the calcium types' current by GHK, from the calcium inside and the garden's 1.2 mM outside, with no reversal of its own; a gate that reads calcium reads its compartment's calcium, its shift a factor on calcium; the calcium's dials per zone, the buffers' capacity, the pumps' rate and the stores' uptake rate, changed within a frame; HVA as two types, R-type and the rest (L-, N- and P/Q-type together), from Almog & Korngreen 2009; SK from Hirschberg 1998; the starting garden as it is; plan §2's rule.

**Yours (design §9):** how the calcium is stored and stepped; how the GHK current enters the voltage solve and is computed near 0 mV; each compartment's volume from its grown pieces; the gate form that reads calcium; each type's numbers from its paper and every conversion (barium to calcium, Almog's straight-line driving force to GHK, junction potentials, temperature), each with its reason; every number the papers don't give, among them each type's temperature factor, R-type's own activation (Almog separates only its inactivation), HVA's inactivation speed in barium (Almog's was measured in calcium) and the share of clearing between pumps and stores, each chosen with its reason in your record; the Calcium colour's scale; the try-out garden.

### What to build

1. **The calcium** in every compartment and the axon start's, in the code the page and the reference share (`tools\grounded\chan-core.mjs`), the reference (`tools\grounded\model.mjs`, `neuron.mjs`), the kernel's copy (`tools\grounded\gpu\port\kernel-replica.mjs`) and the neuron kernel (`cortex.html`); each compartment's volume from its grown pieces (`tools\grounded\trees-core.mjs`), every tree and reduction otherwise unchanged. A regrown tree starts from rest.
2. **The calcium types' current** by GHK, its amount a permeability, shown beside it as the conductance it gives at rest (design §3).
3. **A gate that reads calcium alone** (SK's), as a standard form of the library, compiled into the kernel as the others are, with its shift along calcium. A gate reading calcium and voltage together is not this job (it comes with BK).
4. **The library's new types,** beside the first three, placed in no group: HVA's two types (Almog & Korngreen 2009) and SK (Hirschberg 1998).
5. **The calcium's dials** per zone in a group's settings, through `window.garden` and the node's Membrane tab, carried by the settings so a rebuild makes the same garden; a calcium type's permeability and the new gate form in the Library's editor.
6. **Shown** (design §5): the calcium in its own colour on the drawn tree (View → Colour); a picked neuron's trace showing its calcium beside its voltage.
7. **A garden of its own** for the user (`#debug&try=c4`, or on the garden menu if you propose it): layer 5 cells with HVA placed where Almog and the reading put it (the tuft among it), SK placed, driven so the calcium moves, a tuft's calcium spike shows where the amounts give one, and SK slows firing over a train. A demonstration, not a standard (design §8); firing not tuned.
8. **Kept current:** `CLAUDE.md` (its last section, "About this file and handoffs", unchanged), `docs\reference.md`, `docs\guide-agents.md` (with an example), `docs\inventory.md`. Write paths with an editor, not `sed`, and grep your docs for `docshistory|toolsgrounded|C:Users` before you report.
9. **A garden carries only the types it places** (design §6 and plan C4, changed 2026-11-08 at the user's "Apply it"): the GPU's work, each neuron's state and record, laid out by the types placed in the garden, so that a garden carries and computes only those; the calcium carried and stepped only in a garden that places a calcium type; a type's first placement in a garden that holds none of it, or its last placement removed, a structural change through the queue; an amount changed where the garden already holds the type, within a frame. The library still holds the six types; placing is what brings one onto the GPU. The user: "Lay out the GPU work by the types a garden actually places. Adding a new ion type definitely sounds like a change that can require a rebuild". How it is laid out is yours (design §9); the reference builds the same layout from the settings.

**Not this job** (design §8, the ions to come): the calcium at a channel's mouth; BK; calcium-dependent inactivation; HVA's third type; LVA; a gate reading calcium and voltage together. Nor NMDA's calcium, a saturating pump, release from the stores, other channel types, speed (C7) or I2[413] (C7).

### The files

- The shared code: `C:\Users\Nautilus\Projects\Dendrite Garden\tools\grounded\chan-core.mjs`, `trees-core.mjs`, `neuron-core.mjs` if a draw needs it; the page's copy written by `tools\grounded\page-gen.mjs`.
- The reference: `tools\grounded\model.mjs`, `neuron.mjs`, `net.mjs`, `connection.mjs`; the kernel's copy, `tools\grounded\gpu\port\kernel-replica.mjs`.
- The page: `C:\Users\Nautilus\Projects\Dendrite Garden\cortex.html`.
- The checks: C2's in `tools\grounded\c2\` (`panel.mjs`, `standard.mjs`, `gpu.mjs`); yours in `tools\grounded\c4\`; the model for a type against its paper, `tools\grounded\chan\na-activation.mjs`.
- The papers: `C:\Users\Nautilus\Projects\Dendrite Garden\docs\papers\` (for this job: Almog & Korngreen 2009, Hirschberg 1998, Bildl 2004, Helmchen 1996, Markram 1995, Neher & Augustine 1992; the others as the reading record shows a need).
- Your record: `C:\Users\Nautilus\Projects\Dendrite Garden\docs\history\c4-core-<date>-record.md`.

(In your worktree, the same paths under its own folder.)

### Your paragraphs for the user

Three or four short paragraphs of plain prose, about 200 to 300 words in all; no headings, bullets, numbered lists, bold or long quotes. From the documents alone, before you open any paper. In the user's terms: what calcium gives the garden and why it is cut to this core; what they will be able to do and see when it is done (the try-out garden, the Calcium colour, the trace, the new controls; their own gardens unchanged until they place a calcium type); which paper each new type comes from and which numbers you will have to choose because no paper in hand gives them; what you will not do. Taking over, they also say what is already built, what you will change (item 9) and what is left before the user can open it; and they come from the documents and the first builder's record, before you open any paper or change anything. Held to the "where are we" test: no function names or internals; where you are unsure what something is for, say so.

### The standard

Each check by arithmetic written apart from the code it checks (design §7 item 2), in `tools\grounded\c4\` with an `arith.mjs` that imports none of the code it checks. State each tolerance and sample with its reason before you measure, and do not change them after (builder role §3). Kept small, as the user asks: each criterion once, on the final code.

1. **A garden with no calcium type placed builds and steps as before, and costs what it did** (plan C4; design §6, a garden carries only the types it places). The starting garden and C2's panel Part B, built and run on the GPU over the same steps at the same seed on the page at `a3d1e22` and on your final page: every record word, the spikes and the voltages the same, word for word. The 10,000-neuron garden with no calcium type placed, its neuron kernel's GPU time a step on both pages (`tools\grounded\chan\cost10k.mjs`, headless Edge, said as such): the same within the spread of repeated rounds, which you state before measuring. A difference is a fault until its cause is found (builder role §3).
2. **The calcium does what design §2 says,** on the reference and read back from the GPU: from rest, a known calcium charge into a compartment raises its free calcium by the charge over (2F × its volume × (1 + the buffers' capacity)); it returns to rest at the rate the pumps, the stores' uptake, the membrane and the volume give; the resting level holds with nothing flowing; an NMDA plateau with no calcium type placed leaves it at rest.
3. **Each dial sets what design §3 says** (design §7 item 2): the buffers' capacity, the pumps' rate and the stores' uptake rate read back as the numbers the equations use; a calcium type's current read back as GHK gives it, at several voltages and inside calcium levels; SK's gate read back as its curve against calcium, and its shift as that curve moved by the factor.
4. **Each new type against its paper,** run through the paper's own protocol in its conditions (its ions through GHK, its temperature, its holding and steps): HVA's activation and its time constants, R-type's and the rest's inactivation (Almog & Korngreen 2009, their figures 3 and 4); SK's calcium curve and its opening and closing times (Hirschberg 1998, p. 567 and p. 578); within the paper's stated spread where it gives one, otherwise a tolerance you state with its reason; each figure redrawn beside the paper's for the coordinator to look at.
5. **The GPU computes what the reference computes** (design §7 item 1; plan §2). Plan §2's numbers measured again on the small panel below; the GPU judged by plan §2's numbers over C2's panel and this one together, which are C2's (0.1 ms, 1 ms, 2.5 mV), and reported also under this panel's own numbers, naming any neuron-input outside them with its figures (decided by the coordinator on 2026-11-08 on the first builder's challenge: this panel, small and short, understates what single precision does; C2's neurons carry no calcium type and step as before by item 1); the calcium at each run's end within 2 % of the reference's.
6. **Nothing blows up** (design §7 item 3): the buffers' capacity, the pumps' rate and the stores' uptake rate at their extremes (zero included), the calcium types at large amounts, in the try-out garden and the panel; the calcium finite and the voltages bounded.
7. **Changes while it runs:** a calcium dial changed within a frame, each neuron keeping its place in the spread and its calcium; a type's amount changed within a frame where the garden already holds the type; a calcium type placed in a garden that holds none of it, its last placement removed, and the gate form added (structural, through the queue), each landing as the reference's build of the settings as they then stand, the garden then carrying only the types it places; the new controls making the calls a twin makes through `window.garden`.
8. **Carried:** a garden with calcium types placed and its dials set, rebuilt from its settings, the same word for word.

**Reported, not judged:** the 10,000-neuron garden's GPU time a step with HVA and SK placed in one group, and in every group, beside item 1's figure, so the user knows what calcium costs a garden that uses it.

**Known, not yours to chase:** one neuron in 10,000 (I2[413]) grows a different tree on the page from the reference; leave it out by name. After `window.__cg.profile` a page's neurons are not sound; take no measurement after it in the same page.

### Runs

Before any run of record, send the coordinator one list: each run's command, its criteria, its machine time and what it covers, and the total. A run over about 30 minutes goes to the user first. Trials while building are yours; keep them few and short, and tell the coordinator before a third trial of the same check. A run that fails is a finding: its figures and its cause, found and fixed, and the rows the fix touches rerun, each in your record. A fix that would change the design or a criterion goes to the coordinator first.

### Done

- The calcium built as above, shown by the runs, every criterion's result in your dated record, with every file and output by full path and every number's source (paper and page) or reason.
- The documents kept current (item 8), `node tools\grounded\page-gen.mjs` run, `git fsck --no-dangling` clean, committed on your branch for the coordinator to confirm and merge into `channels`.
- Shown to the user in Firefox (plan §1): the try-out garden on your branch, with the Calcium colour on; tell the coordinator what to look at.

## Report

For the user, at most about 150 words of plain prose, held to the same test: what they can now do and see, what failed and why, what was fixed. Then, for the coordinator: the table of runs and criteria, the outputs and the record.
