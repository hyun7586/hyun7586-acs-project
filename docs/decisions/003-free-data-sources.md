# 003: Free, keyless data sources

- **Status:** Accepted
- **Date:** 2026-11-16
- **Related:** G1, G2, G3

## Problem

The brief needs prices (incl. pre/after-hours), market and sector context, news, analyst rating changes, earnings and filings. Paid or rate-limited APIs would block daily runs and data collection.

## Options

Tested by direct calls on 2026-11-16:

| Source | Gives | Key | Verdict |
|---|---|---|---|
| yfinance | Daily + 5-min pre/post bars, `.news` (~10 items, 2–3 days), `upgrades_downgrades`, `calendar`, `earnings_dates`, SPY/QQQ/VIX/^TNX/sector ETFs | None | **Use** |
| Yahoo / Nasdaq / Google News RSS | Headlines + summaries + links | None | **Use** |
| SEC EDGAR (submissions API, Atom feed) | 8-K, 10-Q, 10-K filings | None (User-Agent with contact required) | **Use** |
| FRED | Macro calendar | Free key | Optional |
| Alpha Vantage | News, prices | Key, 25 requests/day | Not used |
| Finnhub | News, ratings | Key, free tier not confirmed | Not used |

## Decision

yfinance + RSS + SEC EDGAR. Title and summary only; no article-body crawling (paywalls, terms of use).

## Consequences / follow-ups

- yfinance is unofficial (scrapes Yahoo) and may break or rate-limit → cache locally; note in Limitations.
- Free news history is only 2–3 days → daily collection starts early in Sprint 1, or there is no evaluation data for G6.
- A new paid or key-based source needs a new ADR.
