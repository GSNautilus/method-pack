# Example — state file

A short state file for the imagined Shelf project. Read for the shape. See [README.md](README.md).

---

# Coordinator state

Written: 2027-01-15, on `main` at `b3a2c1d` (J3 search in flight, two builders running), by the coordinator "Shelf coordinator". Current, not cumulative: closed rows live in their records under `docs/history/`.

**Mode:** per batch.

**Line of work:** `main`.

**Design:** `docs/design/shelf.md`, last changed 2027-01-10 (§3 search: scoring chosen as BM25, defaults still to be confirmed).

**Plan:** `docs/plan/plan-2027-01-05.md`. J1 core (done, merged `a1b2c3d`); J2 CLI (done, merged `d4e5f6a`); J3 search (now, two builders); J4 tags (next); J5 CSV import (later); J6 static web view (future).

## The user's standing instructions

- 2027-01-05: "Nothing merged without an integration test that fails on the old code and passes on the new."
- 2027-01-05: "Show me a sample CLI run in the report before every merge."
- 2027-01-12: "Don't add runtime dependencies without checking first."

## Open work

| thread | owner | branch | status | next action | whose |
|---|---|---|---|---|---|
| J3 search — index | builder A | `j3-index` | paragraphs approved 2027-01-14; building | the inverted index, then its tests | builder |
| J3 search — query | builder B | `j3-query` | paragraphs approved 2027-01-14; building | the ranking function and its tests | builder |

## Waiting on the user

- **BM25 defaults** (k1 = 1.2, b = 0.75 proposed): to confirm before J3 merges.

## Branches

| branch | head | merged into |
|---|---|---|
| `main` | `b3a2c1d` | — |
| `j3-index` | `c4d5e6f` | not merged |
| `j3-query` | `e7f8a9b` | not merged |

## Pending design updates

- None.

## Known problems

- **J1 core's atomic rename** assumes POSIX. The design doesn't say the tool must run on Windows, but the user asked last week. Not yet decided.
- **J2's `--help` output** wraps at the wrong width in narrow terminals. Minor; not in J3's scope.

## Next

1. J3's two builders report (expected today); confirm each, merge in order (index first, then query), show a sample `search` run to the user before each merge.
2. J4 tags: handoff drafted, with the user for review.
