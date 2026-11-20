# Agentic stack

Every tool and model is declared with its version. The stack may change; every change is logged here with a date.

| Role | Tool | Pinned version / tag | What it does |
| --- | --- | --- | --- |
| Build agent | Claude Code | 2.1.311, models `claude-opus-5-5`, `claude-sonnet-5-5` | Writes and tests the code under my direction |
| Runtime agent | Qwen 3.6 35B on the course server (dingo) | TBD: exact tag | Classifies and summarizes issues (G4, G5) |
| Comparison model | Small local model via Ollama | TBD | Baseline for G6 |
| Data | yfinance, Yahoo/Nasdaq/Google News RSS, SEC EDGAR | TBD | Prices, news, ratings, earnings, filings (no API keys) |
| Delivery | Telegram Bot API | — | Sends the morning brief |
| Language | Python | TBD | — |

### How I work with the agents

*   Claude Code builds the tools. Qwen calls them at runtime.
*   One goal per fresh session. Plans and progress live in files (`docs/`), not in the chat.
*   Each goal ends with a check script that must pass before the commit.
*   Commits made with AI help carry a `Co-Authored-By` line, so the commit history is the AI-use log.

## Change log

| Date | Change | Reason |
| --- | --- | --- |
| 2026-11-16 | Initial stack (pitch) | — |
