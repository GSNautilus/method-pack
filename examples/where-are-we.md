# Example — where-are-we

A short four-section review. Read for the shape. See [README.md](README.md).

---

## Where we are

Shelf is a command-line reading list. The plan in force is about making the records searchable: J1 (core) and J2 (CLI) are done; J3 (search) is now splitting across two parallel builders.

The plan, start to end:

| # | job | what it gives you | status |
|---|---|---|---|
| 1 | J1 core | books stored, read back, listed | done |
| 2 | J2 CLI | add, list, remove, show subcommands | done |
| 3 | J3 search | a `search` subcommand with ranked results | now |
| 4 | J4 tags | add tags, filter by them | next |
| 5 | J5 CSV import | pull in a Goodreads export | later |
| 6 | J6 static web view | an HTML catalogue of the collection | future |

J3 is in flight: the index half is building (builder A), the query half beside it (builder B). Both have the user's approval on their paragraphs.

## What's next, and why

**Merging J3** once both builders report. The coordinator merges the index first (the query depends on it), confirms each against its standard, and shows a sample `search` run to the user before each merge.

One pending decision: the BM25 parameters (k1 = 1.2, b = 0.75 proposed). Both merges wait on that.

## Left outstanding from earlier sessions

- **J2's `--help` wrapping** on narrow terminals. Minor, not scheduled.
- **The Windows question.** J1 chose POSIX atomic renames without the design naming a platform. Not yet decided.

## Possible problems, and things not yet decided

1. **BM25 parameters** are a user call, not confirmed. The J3 fixture doesn't pin them tightly — the same expected ranking holds under several values. That weakness is a J4 or later concern.
2. **Index-and-query coupling.** If the index's record of a term differs from what the query expects, the query will compile but return empty. The coordinator does a one-off sanity check after each merge.
3. **Windows support** is not in the design and not in the plan. If the user wants it, it is its own job and belongs in the plan before J4.

Once BM25 is confirmed and J3 merges, the next decision is J4's scope: just tagging, or tagging plus a `tag:` prefix extension in search.
