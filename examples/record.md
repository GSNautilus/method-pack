# Example — record

Real record from the author's project, 2026-11-08, covering two builders' work on one job on calcium handling. See [README.md](README.md) for context. This record is long and technical. You don't need to follow the neuroscience; read for the shape.

The shape to look for:
- **What was built** (prose, in project terms).
- **The choices and their reasons** (one subsection per piece, each number cited to a paper or given its reason, design §9's "what a build chooses freely" written down).
- **A fault found and fixed** outside the job's own code (what to do when you spot a bug in neighbouring code while working).
- **A standard changed by the coordinator on the builder's challenge** (with the data behind the change; both measurements kept, named).
- **A cost reported, not judged** (how to put something to the user without pretending it is tested).
- **What is left** (an inventory for whoever takes over next).
- **Taken over: the second core builder** — a hand-over within a single record.
- **The runs of record** — each check with its figures, what passed, what did not, and the coordinator's decision for each.
- **A table at the end** mapping each criterion of the standard to the run that tested it and the result.

Notice that failures are kept, named, and reasoned about. The record does not hide a 0.0526 that was supposed to be under 0.05; it names it, says why, and reports the coordinator's decision to keep it that way.

---

# C4, calcium inside the cell, the core: the builder's record, 2026-11-08

Record; binds nothing. Job C4 as cut to its core, handoff `C:\Users\Nautilus\Projects\Dendrite Garden\docs\history\handoff-2026-11-08-c4-core.md`. Builder session in worktree `C:\Users\Nautilus\Projects\Dendrite Garden\.claude\worktrees\c4-core-c265af`, branch `claude/c4-core-c265af`, cut at `a3d1e22`. Coordinator `local_acadce82-73af-481e-b09b-eecf56fb0549`. The user approved the paragraphs on 2026-11-08 ("Approve").

## 1. What was built

- **The calcium** (design §2): in a library holding a calcium type or a gate reading calcium, each compartment's free calcium, the buffered single compartment of Helmchen, Imoto & Sakmann 1996 (Eq. 2, p. 1071; Neher & Augustine 1992's model): (1 + κ) dc/dt = I_Ca in ÷ (2F vol) − γ (c − rest), γ = the pumps' rate × the compartment's area ÷ its volume + the stores' uptake rate.
- **The calcium types' current** by GHK (`chGhk`), the amount a permeability (µm/s), the Membrane tab showing beside it the conductance it gives at rest.
- **A gate reading calcium alone** (kind `ca`): a Hill steady state and a time constant 1 ÷ (1 ÷ τ0 + rate × c), compiled into the kernel as the other forms are.
- **The library's new types**, placed in no group: `hvaR` (HVA, R-type), `hva` (HVA, L, N, P/Q), `sk` (SK).
- **The calcium's dials** per zone (`calcium.<zone>.buffer|pump|store`) through `window.garden` and the Membrane tab.
- **Shown:** the Calcium colour (View → Colour); a traced neuron's soma calcium and highest calcium in `garden.trace` and under the Probe's voltage.
- **The try-out:** `#debug&try=c4`.
- Built and committed, before its checks, at `0b4c19d`; the checks, the documents and the record at `671e67c`; the settings-carry fix at `846c8ed`. Stopped on 2026-11-08 at the user's word ("We should probably wrap up that builders work and handoff to a new builder"), before the layout by placed types (§2.12) and before any run of record.

## 2. The choices and their reasons (design §9)

### 2.1 How the calcium is stored and stepped

- Stored as one more number of each compartment's state, after its gates (`S = G + 1`), so that every path that keeps, copies and remaps the gates' state (the build, a regrown neuron at rest, a library change) carries it; at rest 64 nM.
- Stepped in each substep after the gates and the currents, at the substep's starting voltage and calcium, by its exact solution over the substep with the current held: c ← c − (c − rest)(1 − e^(−ah)) − I_Ca × kin. The exact solution keeps a fast clearing (no buffers, large rates) stable at any substep. Held at least 0.
- Only the calcium types feed it (design §2); a test-only inflow (`cell.caIn`) on the reference alone, for the jump check, as `Iext` is a test-only current.
- The resting level 64 nM: Helmchen 1996, p. 1073 ("Mean resting [Ca²⁺]i level was 64 ± 4 nM").

### 2.2 The GHK current in the voltage solve

- Its current at the substep's starting voltage into the row's right-hand side and its slope dI/dV into its diagonal, as an ohmic type's conductance and current enter: the backward-Euler step linearised about the starting voltage, as for every other current.
- Near 0 mV: u ÷ (1 − e^−u) and its derivative by their series within |u| < 0.1; measured against Hille's form in `arith.mjs`, within 1e−13.
- A calcium type has no reversal; the voltage bounds leave it out.

### 2.3 The calcium's dials and their starting set

- κ 122: the mean of Helmchen 1996's three estimates in layer 5's proximal apical dendrite (Table 1, p. 1074: 126 ± 21, 105 ± 14, 135 ± 17; "between 100 and 200", p. 1078).
- Clearing: Helmchen's 70 ± 7 ms at 36–37 °C (Table 1) brought to 34 °C by Markram, Helm & Sakmann 1995's Q10 of the decay, 2.8 (p. 8): 90.6 ms. γ = 123 ÷ 90.6 = 1.358 /ms in a dendrite 3 µm across (Helmchen p. 1077: radius 1–2 µm).
- The split, half and half between the membrane's pumps and the stores: Markram 1995's blockers (pp. 11–13) slowed the decay by shares of 0.37 and 0.31 against 0.52 and 0.62, overlapping. Half and half sits between their reading and their figures; and the pumps' half, being per area, makes a thin branch clear faster, as Helmchen p. 1080 has it. So the stores 0.679 /ms and the pumps 0.679 × 3 ÷ 4 = 0.509 µm/ms.
- Each the same in every zone, no spread, with that reason: the papers measured the proximal apical dendrite alone.

### 2.4 HVA (Almog & Korngreen 2009) and every conversion

Read in full, its figures checked against the text.
- **Two types,** R-type (`hvaR`) and the rest (`hva`): Fig. 4b's two components, the first removed by SNX-482 (p. 5).
- **Voltages:** the patches' voltages were not corrected for the −11 mV electrode and junction offset the authors measured (p. 2), and were recorded in 5 mM Ba, which shifts the activation 7 mV negative against 2 mM Ca (Fig. 1d, p. 3). Every curve of the gates moved by +7 − 11 = −4 mV to the garden's; the driving force at the true voltage (theirs − 11 mV).
- **Activation (m², Fig. 3a):** their fit, I/Gmax = m∞²(V − 59), m∞ V½ −14.2, k 9.8, uses a straight-line driving force reversing at 59 mV. Refitted as P m∞'(V)² GHK(V − 11) in 5 mM Ba, over −70 to +20 mV: V½ −7.35 mV, k 11.58 (within 0.54 pA/nS of a 42 pA/nS peak), so −11.35 mV in the garden's.
- **τh (Fig. 4c):** 50 + 22.1 e^(−((V − 20) ÷ 12)²) ms, measured in calcium (calcium-dependent inactivation in it), as a table, unscaled (the coordinator accepted this as the builder's choice, 2026-11-08). The text beside it has barium's inactivation slower than calcium's; but Fig. 4b's barium protocol, 150 ms at −10 mV, leaves 7 % of the current, which needs barium's voltage inactivation about as fast as Fig. 4c's. The figure's numbers are taken over the remark: a first choice of four times Fig. 4c's could not give Fig. 4b under its own protocol.
- **R-type's own activation:** the whole current's (Almog separates only its inactivation).
- **Temperature:** 21 °C (20–22 °C, p. 2); Q10 2.3, the garden's for the same lab's slow potassium in the same preparation; no Q10 for calcium channels in the papers in hand.

### 2.5 SK (Hirschberg, Maylie, Adelman & Marrion 1998)

- Its steady state the macroscopic Hill fit, 0.63 µM, coefficient 3.6 (p. 573).
- Its time constant 1 ÷ (1 ÷ 57.3 + k c), so that it deactivates with 57.3 ms when the calcium is removed and activates with 4.1 ms on a jump to 9.5 µM: k = (1 ÷ 4.1 − 1 ÷ 57.3) ÷ 9.5 = 0.0238 /ms per µM.
- Room temperature (p. 566), taken as 22 °C; Q10 2.3. Gating independent of voltage. −85 mV, the garden's potassium reversal.
- Its shift a factor on calcium: Bildl et al. 2004 shows calmodulin's phosphorylation moving the half-point fivefold (0.38 to 1.85 µM).

(Sections 2.6–2.8 omitted here for brevity: the library's shape rules, the Calcium colour and the trace, the try-out garden's amounts.)

### 2.9 A fault found and fixed outside C4's own code

`garden.trace` waiting (`o.wait` not false) read the trace ring through a slot index that a variable for the wait's length had taken the name of (`const k = Math.min(200, ms − done)` inside the loop, the slot's `k` outside it): it read slot 200, or the slot numbered by the milliseconds left, past the 32 slots, a GPU validation error each call ("Copy range … does not fit") and garbage rows. Found in this job's first try-out run. Fixed in `cortex.html`: each chunk read by `traceRead` from the neuron's own slot. Covered by `live.mjs rest`.

A fault of C4's own, found by the trial of `live.mjs changes` (not of record): `garden.settings()` (`opsSettings`) carried each group's leak, channels and gates but not its calcium dials, so a garden rebuilt from its settings lost them. Fixed: the settings carry `calcium`. Covered by `live.mjs changes` and `live.mjs carried`.

### 2.10 The standard of item 5, changed by the coordinator on the builder's challenge (2026-11-08)

A trial of `precision.mjs` (not of record) gave this panel's own numbers, by plan §2's rule over its 8 neuron-inputs (every count kept by the three copies), as 0.001 ms, 0.05 ms and 0.2 mV: about 100 times tighter than C2's (0.1 ms, 1 ms, 2.5 mV). The GPU kept every count; 6 of 8 fell within them, 2 outside by microseconds. Followed with the copy: the GPU and the copies first part at the first spike's upstroke by about 0.001 mV, the GPU's value between the copies' own, and no jump anywhere: single precision's drift, which the copies' stand-ins understate over a long driven train, not a port fault. **The builder challenged the standard with that data; the coordinator decided:** item 5 is judged by plan §2's numbers over C2's panel and this one together, which are C2's, and reported also under this panel's own numbers, naming any neuron-input outside them with its figures. The reason, the coordinator's: this panel is small and short by the handoff, so its own numbers understate what single precision does. The calcium at each run's end stays within the stated 2 %.

### 2.11 What the library costs a garden that places no calcium type

The 10,000-neuron garden (11,000 neurons, 329,788 synapses), no calcium type placed, headless Edge (not a speed figure; the median of four rounds of five): the neuron kernel 4.57 ms a step at `a3d1e22` and 5.93 ms on this page, 30 % more. By the code: the six types make every neuron's state 3 vec4f a compartment instead of 1, its record 460 words instead of 196, three more types' branches each substep, and the calcium's step in every compartment. For unplaced types to cost nothing, the GPU's shape would follow the types the garden places, so that a type's first placement and its last removal would be structural, where design §6 has an amount land within a frame. The coordinator took the cost to the user with a recommendation (accept it now; "types a garden places no amount of cost nothing" in the optimization job after C4) and told the builder to change nothing in the library's layout on the GPU, nor to try skipping the calcium's step at rest, until the user answers.

### 2.12 The GPU's work laid out by the types a garden places (the user's choice, 2026-11-08; pending the design change)

The user, through the coordinator: "Lay out the GPU work by the types a garden actually places. Adding a new ion type definitely sounds like a change that can require a rebuild". The builder holds until the coordinator relays the design change as applied. (What it touches, by the code as it stands, is listed in the full record and summarised for the taker-over in §5.)

## 3. Reading the papers

Read for this job: Almog & Korngreen 2009 in full, its figures checked as images; Hirschberg 1998 pp. 567, 573, 578–579; Bildl 2004 pp. 849–851, 853; Helmchen 1996 pp. 1071–1080; Markram 1995 pp. 8, 11–13; Neher & Augustine 1992; Larkum 1999. Each number taken is given with its page in §2.

## 4. The checks, and every trial (none of record)

The checks are in `tools\grounded\c4\` (each one's header states its tolerances and samples, with their reasons, before any measurement): `arith.mjs`, `check-cpu.mjs`, `precision.mjs`, `same.mjs`, `live.mjs`, `try-load.mjs`.

(Trials elided; the full record lists each trial with its figures, including one trial that gave NaN and was fixed, and one precision trial where the GPU first fell outside the built panel's own numbers before the coordinator's decision in §2.10.)

## 5. What is left, for the builder who takes it over

1. **The layout by placed types** (design §6 as changed on 2026-11-08 at the user's "Apply it"). What it touches: an index of the placed types beside the library's, the records, the state, the library buffer and the kernel on it, the group settings and draws still on the whole library; `opsKindOf` giving an amount's kind by its value; the remap as `chLibChange` does it now; the Channels colour's pick; the checks' expected layouts.
2. **The checks brought to it:** `same.mjs` then expects the starting garden whole; `precision.mjs gpu`'s and `live.mjs`'s expected records and state on the placed index; `live.mjs changes` gains the structural placement and loses nothing; `c2\gpu.mjs build` and `c3b\check.mjs` will need the placed index too.
3. **The runs of record**, once, on the final code, after the run list goes to the coordinator.
4. **Shown to the user** in Firefox: `#debug&try=c4` with the Calcium colour on (the user is told before a Firefox window opens).

What a fresh builder may trip on:
- `kernel-replica.mjs` already names the soma's index `S`; the state's stride there is `SS`.
- The kernel's WGSL is assembled in JavaScript template strings: a newline inside a quoted string within `${…}` breaks the page; patch scripts written to files avoided two broken edits.
- `page-gen.mjs` must run after any change to `chan-core.mjs` or `trees-core.mjs`: the page holds a copy.
- A calcium type's `g` in the record and in `chComps` is a permeability (µm³/s), not nS.
- The trace's calcium lives in Misc's old `fx` words; the readback's `RB_GC` moved 512 words to make room for `RB_CA`.
- Almog's voltages: the gates at theirs − 4 mV, the driving force at theirs − 11 mV.
- `precision.mjs cpu` is single-threaded: 6 to 10 minutes; run it in the background with its time limit.

## 6. Taken over: the second core builder (2026-11-08)

Builder session in worktree `C:\Users\Nautilus\Projects\Dendrite Garden\.claude\worktrees\c4-core-2-31b9fd`, branch `claude/c4-core-2-31b9fd`, cut from `claude/c4-core-c265af` at `0e9576d`; `channels` merged in at `40dd4f7` (documents only, clean). Its paragraphs approved by the user on 2026-11-08 ("Approve"). §1 to §5 above are the first builder's and stand as written; what follows is this builder's.

### 6.1 The GPU's work laid out by the types a garden places

- **What is placed**: a type with an amount centre above 0 in some zone of some group, or above 0 in some neuron's own values. A type placed in a zone that no tree of the group has is still placed: the GPU carries it, at no conductance; the simpler rule.
- **The placed index** (`chPlacedIndex`, `chPlacedOf`): the library with the placed types alone, in its order; `tw`, `gw` each placed type's and gate's place in the whole library, so that a neuron's numbers, computed on the whole library, are written on it.
- **The calcium carried only where a calcium type is placed**: a garden placing SK and no calcium type carries no calcium; SK's gate reads the resting level, compiled in. Nothing could move the calcium there (only the calcium types feed it), so the numbers are those of a carried calcium at rest: the reason.
- **The changes**: on the settings as they stand, the placed index of the result; the kernel compiled for it, the state remapped (gates kept by id, a new gate at its steady state, the calcium kept where both layouts carry it). A type's first placement or last removal: kind 3; every other amount within a frame.

### 6.3 The first builder's numbers checked against the papers

Read by one subagent of this session, which changed nothing in the repository. Every number of §2.3 to §2.5 found as the record gives it, page for page.

**A fault, fixed:** HVA's inactivation time constant (Fig. 4c) was put at the paper's voltage − 4 mV, the barium-to-calcium shift with the offset; but Fig. 4c was "recorded using Ca2+ application solution", so only the offset applies: now at theirs − 11 mV, its peak at +9 mV in the garden's voltages, not +16. No other number moved.

### 6.4 The try-out against Larkum, Zhu & Sakmann 1999 (the coordinator's request)

Larkum 1999: "single sodium action potentials initiated in the axon do not evoke a calcium action potential in the dendrite" (p. 338); a distal input coinciding with the back-propagating spike does, at 49 ± 4 % of the current it needs alone (BAC firing; 693 ± 18 µm from the soma; best 5 ms after the spike).

On the reference, the try-out's L5 neuron (its HVA amounts, no SK, no background, seed 4), one spike from a 3 ms soma pulse. In the five of six neurons whose trees have a tuft: the tuft to +30 to +39 mV, its calcium to 1.1 to 2.1 µM; so **at the try-out's amounts one back-propagating spike alone sets off a calcium event in the tuft, which Larkum's cells do not do**. With the tuft's HVA scaled down (0.6, 0.4, 0.3, 0.2, 0.1 of the try-out's, three neurons): in one neuron the spike alone no longer moves the tuft's calcium and the spike with half the distal threshold does — Larkum's coincidence; in the other two the spike alone still lifts the tuft's calcium. Not changed: the try-out is a demonstration and its firing not tuned (design §8); the amounts that would give BAC firing are tuning, the user's in the interface. Reported to the coordinator with these figures.

### 6.6 The runs of record (the user's go, relayed 2026-11-08: "Run C4's checks now …", "Yes, that order")

**Run 1, `node tools/grounded/c4/check-cpu.mjs`** (26 s):
- Item 2 on the reference, passes.
- Item 3, passes: every record word of three neurons against arith; GHK within 9.9e−14 of Hille's form; SK's curve and time constant, none off.
- Item 4, **two of seven outside their stated tolerance**: SK's curve and timing pass; Fig. 3c and Fig. 4c pass; Fig. 3a's I–V 0.0526 of the peak against 0.05, and Fig. 4b's availability 0.0542 against 0.05. Cause: no single barium-to-calcium conversion fits Almog's barium figures and their calcium τh within 0.05. Taken to the coordinator.
- Item 6, passes: every voltage within −84.7 to +78.8 mV, every calcium finite.

**Run 2, `node tools/grounded/c4/same.mjs`** (22 s), item 1 against `a3d1e22`:
- The starting garden (the background 0.25), passes whole: every step's NState of 18 neurons (369 spikes on both pages), every compartment, the whole gates' state, every record (196 words on both), the library buffer, word for word.
- C2's Part B (the background 1): every step's NState the same (2291 spikes on both) and every compartment the same, so it steps exactly as before; but its records (236 words against 272), gates' state and library buffer are not the same length: by design (the library's fifth type is placed nowhere). Taken to the coordinator with two ways to judge it.

**Run 3, `node tools/grounded/chan/cost10k.mjs`** (headless Edge):
- `a3d1e22`'s page: 5.560, 4.392, 4.380, 4.411 ms; median 4.411, range 1.180.
- This page, no calcium type placed: 5.076, 4.264, 4.326, 4.326 ms; median 4.326, range 0.812. The medians 0.085 ms apart, within 1.180: **passes**. The first builder's whole-library layout cost 5.93 ms against 4.57: that cost is gone.
- Reported, not judged: HVA and SK placed in one group alone 6.630 ms; in every group 14.590 ms.

**The coordinator's decisions on runs 1 and 2** (2026-11-08):
- Run 1: keep the corrected τh (it follows Almog's recording conditions, Fig. 4c in calcium), keep the tolerance and the conversion. Fig. 3a (0.0526) and Fig. 4b (0.0542) stand as **two comparisons outside 0.05**, with their cause named. Nothing changed to make them pass (design §7: the figures and the cause reported).
- Run 2: Part B judged also by the words both pages carry, matched by type and gate key ("Every record word the same" was the coordinator's wording, written without the case of a library holding a type its garden places nowhere). `same.mjs` gained the matched comparison, and Part B was run once more: as written, its records differ (236 against 272 words), by design; **matched, every word the same**: 10,530 record words, 21,782 words of state, 177 of the library buffer, over the four types both carry.

**Run 4, `node tools/grounded/c4/precision.mjs gpu cpu judge`** (9 min, single-threaded):
- 8 of 8 neuron-inputs pass by plan §2's numbers (C2's). Reported also on this panel's own numbers: 5 within, 3 outside by their mean shift alone (0.0011 to 0.0019 ms against 0.001); their largest shifts within 0.05 ms and their soma within 0.2 mV: single precision's drift over a long driven train, the copies' stand-ins understating it.
- **The calcium at each run's end** (item 2 read back from the GPU), GPU against reference over the 192 compartments more than 1 nM from rest: within 0.65 % of the distance from rest, against 2 %: passes.

**Run 5, `node tools/grounded/c4/live.mjs`** (all four parts, about 7 min):
- `rest`: passes.
- `changes`: passes, 18 steps, each landing as stated and every record against the reference's build of the settings as they then stand, word for word.
- `carried`: passes.
- `blowup`: passes.

### 6.7 Every criterion of the handoff's standard, as it stands

| item | run | result |
|---|---|---|
| 1. A garden with no calcium type placed builds and steps as before | `same.mjs` | the starting garden word for word, whole (369 spikes); Part B steps word for word (2291 spikes) and, matched by type and gate key, every word the same; as written its records differ (236 against 272 words), by design |
| 1. Its cost, the 10,000-neuron garden | `cost10k.mjs` (headless Edge) | 4.33 ms a step against 4.41 at `a3d1e22`, within the larger of the rounds' ranges (1.18 ms): passes. Reported: HVA and SK in one group 6.63 ms, in every group 14.59 ms |
| 2. The calcium does what design §2 says | `check-cpu.mjs calcium`, `live.mjs rest`, `precision.mjs judge` | passes on the reference and on the GPU (the calcium at each run's end within 0.65 %) |
| 3. Each dial sets what design §3 says | `check-cpu.mjs dials` | passes: none off |
| 4. Each new type against its paper | `check-cpu.mjs papers` | SK's curve, activation and deactivation, Almog Fig. 3c and Fig. 4c within; **Fig. 3a (0.0526) and Fig. 4b (0.0542) outside 0.05**, their cause in run 1 above |
| 5. The GPU computes what the reference computes | `precision.mjs` | 8 of 8 within plan §2's numbers; on this panel's own numbers 3 outside by their mean shift alone (0.0011 to 0.0019 ms against 0.001) |
| 6. Nothing blows up | `check-cpu.mjs blowup`, `live.mjs blowup` | passes on the reference and the GPU |
| 7. Changes while it runs | `live.mjs changes` | passes, 18 steps |
| 8. Carried | `live.mjs carried` | passes |

Not done in this job: the try-out shown to the user in Firefox (the coordinator tells the user what to look at); the merge into `channels`, the coordinator's.
