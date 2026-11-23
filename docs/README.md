# Docs index

Read in this order: project [README](../README.md) → [CLAUDE.md](../CLAUDE.md) (rules) → decisions → the spec and plan of the goal you work on.

| Doc | What | Status | Updated |
|---|---|---|---|
| [goals.md](goals.md) | Goals G1–G6: checks and status | Active | 2026-11-21 |
| [agentic-stack.md](agentic-stack.md) | Tools, models, how I work with agents, stack change log | Active | 2026-11-21 |
| [architecture.md](architecture.md) | Module flow, `src/` layout | Draft | 2026-11-23 |
| [specs/brief-format.md](specs/brief-format.md) | Brief output format (golden sample) | Draft | 2026-11-23 |
| [CONTRIBUTING.md](CONTRIBUTING.md) | Branches, commits, PRs, session logs | Active | 2026-11-18 |
| [decisions/001](decisions/001-no-cause-claims.md) | Report related issues, not causes | Accepted | 2026-11-16 |
| [decisions/002](decisions/002-runtime-model-dingo-qwen.md) | Runtime model: Qwen 3.6 35B on dingo | Accepted | 2026-11-16 |
| [decisions/003](decisions/003-free-data-sources.md) | Free, keyless data sources | Accepted | 2026-11-16 |
| [decisions/004](decisions/004-run-mode.md) | Run mode: one-shot CLI, scheduled daily | Accepted | 2026-11-21 |
| [plans/TODO.en.md](plans/TODO.en.md) | Implementation TODO tree ([KO](plans/TODO.ko.md)) | Active | 2026-11-21 |
| [evals/](evals/) | Prompt and model evaluation results | Empty | — |
| [sessions/](sessions/) | Agent session logs | Paused until development starts | 2026-11-20 |

## Repository layout

```
README.md          project summary, goals, stack, install/run
CLAUDE.md          rules for coding agents + change log
src/               source code
docs/
  decisions/       why X, not Y (ADRs)
  specs/ plans/    design and task plan per goal
  evals/           prompt and model evaluation results
  sessions/        agent session logs
```

Data policy: raw collected data (`data/raw/`) is never committed; hand-labelled evaluation data (`data/eval/`) and small test fixtures (`tests/fixtures/`) are. Secrets live in `.env` (template: `.env.example`) and are never committed.

## Folders

- `decisions/`: one file per decision, `NNN-<title>.md`, from [`_template.md`](decisions/_template.md). Never edit an accepted decision's content; write a new one that replaces it.
- `specs/`: `<goal>-<name>.md` (e.g. `g1-measure-move.md`): inputs, outputs, rules, check. Approved before coding.
- `plans/`: task plan per goal with `- [ ]` checkboxes; the plan file carries the state between sessions.
- `evals/`: one file per prompt or model version, with the data used and the scores.

Update this table in the same PR when a doc is added or its status changes.
