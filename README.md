# bitAgent

**openclaw recall gate score history and agent experiment logs.**

This repository is intentionally a **log-only sink**: it stores
reproducible recall-gate scoring runs against
[chikaharu/bitRAG](https://github.com/chikaharu/bitRAG)'s `main`
branch. There is **no source code** here and no source code is
planned.

## Commit format (forward-only)

Every recall-log commit follows the line format

```
recall: <upstream-ref>@<sha7> EN=<correct>/<total>@<k> JP=<correct>/<total>@<k>
```

Example:

```
recall: main@58076d31 EN=24/25@1 JP=28/30@1
```

- `<upstream-ref>` — branch name in `chikaharu/bitRAG` that was scored
  (typically `main`).
- `<sha7>` — first 7 hex chars of the bitRAG commit at scoring time.
- `EN`, `JP` — recall@k counts on the English / Japanese eval sets.
- `@<k>` — top-k cutoff used (default `@1`).

## Out of scope

- Source code (use [chikaharu/bitRAG](https://github.com/chikaharu/bitRAG)
  for the retrieval engine itself).
- Aggregated dashboards / plots (compute from the log on demand; do
  not commit derived data).
- History rewrite (the log is append-only and never squashed or
  rebased).

## Related

- [chikaharu/bitRAG](https://github.com/chikaharu/bitRAG) — upstream
  retrieval engine being scored.
- [chikaharu/bitGradient](https://github.com/chikaharu/bitGradient) —
  formalized DGD core (Cor 4 of bitRAG MAIN-B).
