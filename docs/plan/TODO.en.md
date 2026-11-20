# Implementation TODO

Korean version: [TODO.ko.md](TODO.ko.md). Each leaf item is about one GitHub issue. Branch names in brackets.

```
Stock Briefing Agent
├── S0. Setup (23 Nov, first Sprint 1 session)
│   ├── Write CLAUDE.md (placeholder → real rules)
│   ├── Python project skeleton: pyproject, src/briefing/, tests/, `briefing run` CLI entry point
│   ├── Config file: watchlist, sector ETF and aliases per stock, thresholds
│   ├── Check dingo connection + exact Qwen tag → fill the README stack table
│   └── Create Telegram bot + test sending a message (token in .env)
│
├── Sprint 1 (23 Nov – 13 Dec)
│   ├── G1 Measure the move            (feat/g1-measure-move)
│   │   ├── Fetch prices: daily bars + pre/after-hours (yfinance)
│   │   ├── Metrics: % change, gap, after-hours move, volume vs 20-day average
│   │   ├── Trend label: today's move × trend, volatility-normalized, "weak" flag, streak days
│   │   └── Tests: label cases on fixed data
│   ├── G2 Separate market vs. stock   (feat/g2-market-split)
│   │   ├── Fetch market (SPY/QQQ) and sector ETF moves
│   │   ├── Split into market / sector / stock-specific parts
│   │   └── Numeric tests
│   ├── G3 Gather issues               (feat/g3-gather-issues)
│   │   ├── News: yfinance .news + RSS (Yahoo, Nasdaq, Google News)
│   │   ├── Filings: SEC EDGAR (User-Agent set)
│   │   ├── Analyst rating changes + earnings dates / surprise
│   │   ├── Time-window filter + dedupe + name/ticker/alias match flag
│   │   └── Collection log per run
│   ├── Daily data collection          (feat/daily-collect)
│   │   ├── Save one raw snapshot per day locally (data/raw, not committed)
│   │   └── Scheduled run (launchd/cron) + retry on failure
│   ├── Interim output: Markdown report from G1–G3 only (numbers + issue list, no LLM)
│   └── Checkpoint (14 Dec): one-slide status + talk
│
├── Sprint 2 (21 Dec – 11 Jan)
│   ├── G4 Classify relevance          (feat/g4-classify)
│   │   ├── Rubric + stock profile input format
│   │   ├── Qwen prompt + JSON output {category, quote, confidence}
│   │   ├── Auto checks: quote exists, name match, ask twice, JSON format → "uncertain" on failure
│   │   └── Local-model fallback when dingo is down
│   ├── G5 Write and send the brief    (feat/g5-brief)
│   │   ├── Markdown rendering (numbers inserted by code)
│   │   ├── Number check (reject numbers written by the model)
│   │   └── Send short version to Telegram
│   ├── G6 Measure quality             (eval/g6-quality)
│   │   ├── Hand-label 150–200 collected news items (data/eval, committed)
│   │   ├── Precision / recall, confusion matrix, error types
│   │   ├── Qwen 3.6 35B vs a small local model
│   │   └── (Optional) cause-guessing experiment
│   └── Demo Day (11 Jan)
│       ├── Finish README install / run / demo section
│       ├── Demo script (10 min)
│       └── ERK report (incl. AI-use declaration, based on session logs)
│
└── Ongoing
    ├── Session log + PR for every session
    └── Update README Progress / Goals status
```
