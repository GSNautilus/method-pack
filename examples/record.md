# Example — record

A short record of a small job. Read for the shape. See [README.md](README.md).

---

# J3 search — query: record, 2027-01-15

Record; binds nothing. Job J3 (`docs/plan/plan-2027-01-05.md`), the query half; handoff `docs/history/handoff-2027-01-14-j3-query.md`. Branch `j3-query` off `main` at `b3a2c1d`. Builder "Shelf J3 query builder". The user approved the paragraphs on 2027-01-14.

## What was built

- A `shelf search <query>` subcommand (`src/cli/search.ts`), registered in `src/cli/index.ts`.
- A query parser (`src/search/query.ts`): AND-ed bare words, quoted phrases, `tag:` and `author:` prefixes.
- A BM25 ranker (`src/search/rank.ts`), taking k1 and b from the design.
- An integration test with a 22-book fixture and 7 queries (`tests/search.test.ts`).

Committed at `e7f8a9b`.

## Choices and reasons

### Query parsing

Two-pass parser: first pass splits on whitespace honouring quotes; second pass separates `prefix:value` tokens from bare words. No parser library (user's standing instruction on dependencies).

Reserved prefixes are closed: `tag:` and `author:` as named in the design, no others. A prefix not in the set is treated as a bare word. The "plug-in new prefixes" question is deferred to J4 or later.

### Ranking

BM25 implemented from the standard formula: idf * (tf * (k1 + 1)) / (tf + k1 * (1 - b + b * |d| / avgdl)).

Default k1 = 1.2, b = 0.75 as the design proposes. **These are the parameters still awaiting user confirmation** (state file, waiting on user).

Tried k1 = 1.6 and b = 0.5 on the fixture as a sanity check; the expected ranking in the test holds under both, so the test does not pin the parameters tightly. Noted as a weakness of the fixture.

### Output format

One line per hit, score first (design §3). Chose four significant figures for the score, rounded. Reason: more precision is noise; fewer loses tie-breaks. Byte-for-byte checked against the design's example.

## Checks

| criterion | how | result |
|---|---|---|
| 1. BM25 ranking matches the formula | 7 ranking tests in `tests/search.test.ts` | passes |
| 2. Query parser handles each case | 4 parser tests (bare, quoted, `tag:`, `author:`) | passes |
| 3. CLI output byte-for-byte | 1 test against the design example | passes |
| 4. Integration test fails on old code | run against `b3a2c1d` | fails as expected |
| 5. Sample run in the report | below | — |

### Sample run

```
$ shelf search "deep work" author:newport
0.8321  Deep Work                Cal Newport        2016  #productivity
0.4102  So Good They Can't Ignore You  Cal Newport  2012  #career
```

## What remains

- The k1 and b defaults are still proposed, not confirmed. The report will ask the user.
- `tag:` and `author:` are the only prefixes; adding more is a J4 or later task.
- The index half (parallel J3 builder) must merge before this one to compile.

## Files touched

- `src/cli/search.ts` (new)
- `src/search/query.ts` (new)
- `src/search/rank.ts` (new)
- `tests/search.test.ts` (new)
- `src/cli/index.ts` (one line: register the subcommand)
