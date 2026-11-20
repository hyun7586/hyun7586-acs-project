# Stock Briefing Agent

A CLI agent that watches the US stock market and tells you how it moved and what issues came with it.
Code measures the moves; the runtime agent (Qwen on dingo) classifies and summarizes related issues.
Goals G1–G6: [docs/goals.md](docs/goals.md). Stack: [docs/agentic-stack.md](docs/agentic-stack.md). Plan: [docs/plans/](docs/plans/).

## Rules (always)

| Area | Rule | Why |
|---|---|---|
| Numbers | Every number in a brief is computed and inserted by code. The model never writes numbers | [ADR 001](docs/decisions/001-no-cause-claims.md) |
| Claims | The agent reports issues in the same time window and how they relate. It never says "X caused the move" | [ADR 001](docs/decisions/001-no-cause-claims.md) |
| Advice | No buy/sell advice, no trading, no price targets | Scope |
| Runtime model | Qwen 3.6 35B on dingo, 64k context, one request at a time. One stock per call, ≤10 news items per call | [ADR 002](docs/decisions/002-runtime-model-dingo-qwen.md) |
| Data | Keyless free sources only (yfinance, RSS, SEC EDGAR). Title + summary only, no article-body crawling | [ADR 003](docs/decisions/003-free-data-sources.md) |
| Secrets | Never commit `models.json`, `.env`, the dingo key or the Telegram token. Never print them | Course rule |
| Data in git | Raw collected data (`data/raw/`) is never committed. Hand-labelled eval data (`data/eval/`) is | Repo policy |
| Workflow | One goal per session, on its own branch. A check (tests/script) must pass before a commit. Follow [docs/CONTRIBUTING.md](docs/CONTRIBUTING.md) | Graded process |
| Language | Everything in the repo is English, except `*.ko.md` files | Graded report |

## Common mistakes (do not)

- ❌ Let the model output a % change, price or volume, or copy one from its text into the brief
- ❌ Write "because", "due to", "driven by", "caused" about a move in agent output or prompts
- ❌ Hard-code tickers, aliases, sector ETFs or thresholds in code — they live in the config file
- ❌ Hide items that fail the checks — mark them "uncertain" and show them with their link
- ❌ Send more than one stock, or a whole news feed, in one dingo call
- ❌ Add a paid or key-based data source without a new ADR
- ❌ Commit without the `Co-Authored-By` trailer when an agent wrote the change
- ❌ Write or run session logs before the user says logging has started

## Where things live

| What | Where |
|---|---|
| Doc index (status of every doc) | [docs/README.md](docs/README.md) |
| Decisions (why X, not Y) | [docs/decisions/](docs/decisions/) |
| Design per goal, before code | [docs/specs/](docs/specs/) |
| TODO tree and task plans per goal | [docs/plans/](docs/plans/) |
| Prompt and model evaluation results | [docs/evals/](docs/evals/) |
| Session logs | [docs/sessions/](docs/sessions/) |

Code is the source of truth for behaviour. If a doc disagrees with the code, fix or delete the doc and note it below.

## Change log

| Date | Change | Target | Reason |
|---|---|---|---|
| 2026-11-20 | Placeholder created | CLAUDE.md | Agent docs structure (#3) |
| 2026-11-21 | Rules, common mistakes, doc map; ADR 001–004 added | CLAUDE.md, docs/ | Adopt rule table + change log + ADRs from reference repos |
| 2026-11-21 | Goals and stack links point to docs/goals.md, docs/agentic-stack.md; ADR 004 accepted | CLAUDE.md | README split into docs |
