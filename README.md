# Bug bounty reports 2025–2026 (training corpus)

Collected 2026-09-20 for model training.

## What is in this repo

| Path | Purpose |
|---|---|
| `data/hackerone_catalog_2025_2026.jsonl` | Metadata for **1,259** publicly disclosed HackerOne reports dated 2025 or 2026 |
| `data/training_fulltext_top80.jsonl` | Full report text + metadata for a high-signal subset (top bounty/severity/votes) |
| `data/training_writeup_summaries.jsonl` | Short public writeup summaries + source URLs (not full copyrighted articles) |
| `reports/hackerone/{id}.md` | Same full texts as markdown |
| `writeups/public_writeups_2025_2026.json` | Writeup index |
| `SOURCES.md` | Provenance |

## Counts (HackerOne disclosed, this snapshot)

- 2025 disclosed: 587
- 2026 disclosed: 672
- With a listed bounty: 107
- Severity mix in the two-year catalog: critical 100, high 229, medium 468, low 229, none/unrated 233

## Training notes

Use `training_fulltext_top80.jsonl` as the first supervised/continued-pretrain slice.

Suggested fields:

- `text` — report body
- `title`, `weakness`, `severity`, `program` — labels
- `url` — always keep for attribution and to drop records if a program un-discloses

Do **not** treat redacted writeups as ground-truth exploit recipes against live targets. Many 2025–2026 Medium posts omit program names on purpose.

## GitHub upload

The collector account `zubzubuuzb` is connected but the GitHub token cannot create repositories (`403 Resource not accessible`). Create an empty repo, grant the connector Contents: Read and write plus Administration or Contents+Metadata, then ask to push this folder.

Suggested remote:

```
gh repo create bug-bounty-reports-2025-2026 --private --source . --push
```
