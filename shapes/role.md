# Role document — template

A role document says what a kind of session is for, what it reads first, what it decides, what it never does, who it talks to, and what done means for its work. It is the user's: it lives in `docs/roles/` and changes only with the user's permission.

The three role documents in this pack ([coordinator](../roles/coordinator.md), [builder](../roles/builder.md), [auditor](../roles/auditor.md)) are examples. A project may add its own.

---

# The <role name>

<One paragraph: what this role is for. What a session in this role carries, and what it does not. Any one-line principle that governs it (for example, "it does not build").>

## What it reads first, and where things are

(In order. The goals file, the design, other role documents, the state file, the plan, the previous session's handoff or record, any memory or notes that bear on the work.)

## What it decides, and how

(What it may decide. What it may not. How it answers its own questions — design first, research next, experiment last. What it does before it agrees with anyone.)

## What it never does

(The list of hard limits. The things that, if it did them, would mean it has drifted from the role.)

## Who it talks to

(The user. Other sessions. The channels and ids used, and what triggers a message to each.)

## What done means

(Criteria. The report, if there is one.)

## Working practice

(Housekeeping: files to close, logs to commit, tools to shut down. Anything about the environment that bears on how this role works.)
