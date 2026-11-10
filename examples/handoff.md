# Example — handoff

A short handoff for one half of one job. Read for the shape. See [README.md](README.md).

---

# Handoff 2027-01-14: J3 search — query

Plan job J3 (`docs/plan/plan-2027-01-05.md`), the query half. Written by the coordinator "Shelf coordinator", who answers you.

**The go:** given by the user for the job; your paragraphs come first. **Your first act is your paragraphs (below), sent to the coordinator, and nothing else.**

**The point.** The index half of J3 (built in a parallel session) gives the tool a searchable record of titles, authors and notes. This job gives the user a way to ask the index questions: a `shelf search <query>` subcommand that returns ranked results.

## Read first

In this order:

1. `docs/GOALS.md`.
2. `docs/design/shelf.md`, §3 (search).
3. `docs/roles/builder.md`.
4. `docs/plan/plan-2027-01-05.md`, J3.
5. This handoff.

## The user's standing instructions that bind you

- 2027-01-05: "Nothing merged without an integration test that fails on the old code and passes on the new."
- 2027-01-05: "Show me a sample CLI run in the report before every merge."
- 2027-01-12: "Don't add runtime dependencies without checking first."

## The job

- **Level:** the query path — parsing the user's query, consulting the index, ranking, formatting output.
- **Fixed above this level** (design §3): the index's data structure; the scoring method (BM25, parameters k1 and b held as design parameters); the output format (one line per hit, score first).
- **Yours (design §9):** how the query is parsed; how the index is consulted; the exact shape of the output line; the fixtures for the integration test.

### What to build

1. A `shelf search <query>` subcommand in the CLI.
2. A query parser: bare words are AND-ed; `"quoted phrases"` match exactly; `tag:foo` and `author:bar` narrow results.
3. A BM25 ranker using the index's term frequencies.
4. Output formatting, byte-for-byte with the design's example.
5. An integration test with a ~20-book fixture and expected rankings for 5 or more queries.

**Not this job:** indexing (parallel builder); result caching; fuzzy matching; typo correction.

### Files

- `src/search/query.ts` (new)
- `src/search/rank.ts` (new)
- `src/cli/search.ts` (new)
- `src/cli/index.ts` (one line to register the subcommand)
- `tests/search.test.ts` (new)

### Where to work

- **Branch:** `j3-query`, off `main` at `b3a2c1d`.
- **Coordinator:** "Shelf coordinator" (by the tooling's message tool).

### Your paragraphs for the user

Three or four short paragraphs: what the user will be able to do with `search` when it is done; how a query is parsed in plain terms (what the user can write); what you will choose about output format where the design doesn't say; what you will not do. No code, no function names.

### The standard

1. **BM25 ranking matches the formula** on the fixture, against a reference computed from BM25 with k1 = 1.2 and b = 0.75.
2. **The query parser** handles bare words, quoted phrases, `tag:` and `author:` prefixes, with one test per case.
3. **The CLI output** matches the design's example, byte for byte.
4. **The integration test fails on `b3a2c1d`** and passes on your branch.
5. **A sample run** of each query kind in the report.

### Done

- Every criterion met, shown by the tests.
- Committed on `j3-query`, for the coordinator to confirm and merge.
- Sample run in the report (user's standing instruction).

## Report

For the user, a short paragraph: what they can now do with `search`. For the coordinator: the test output and the sample run.
