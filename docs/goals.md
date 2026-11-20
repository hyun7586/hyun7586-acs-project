# Goals and objectives

Each goal has a check that decides whether it is done.

| # | Goal | Done when | Status |
| --- | --- | --- | --- |
| G1 | **Measure the move.** % change, gap, pre/after-hours move, volume vs 20-day average, trend label (up / down / flat / pullback / rebound) per stock | Fixed test cases pass | ☐ |
| G2 | **Separate market vs. stock.** Split each move into market (SPY/QQQ), sector-ETF and stock-specific parts | Numeric tests pass | ☐ |
| G3 | **Gather issues.** Collect items from the [data sources](decisions/003-free-data-sources.md) in the time window, remove duplicates, mark name/ticker matches | Collection log for every run | ☐ |
| G4 | **Classify relevance.** The agent tags each news item `direct` / `sector` / `macro` / `unrelated` with a verbatim quote and a confidence | Output passes the JSON schema check | ☐ |
| G5 | **Write and send the brief.** Markdown note + Telegram message. Numbers come from code, not from the model | Automatic checks pass before sending | ☐ |
| G6 | **Measure quality.** Hand-label ~150–200 news items and compare them with the agent: precision/recall per category, Qwen 3.6 35B vs. a small local model | Accuracy table in [`evals/`](evals/) | ☐ |
