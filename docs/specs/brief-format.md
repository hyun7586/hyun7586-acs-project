# Brief format (golden sample)

**Status: Draft.** The sample below uses **made-up numbers and headlines** to show the format only. The time window line depends on ADR 005 (not decided yet).

Used by: interim report (#11), G5 (#14), checkpoint slide (#12). Agents writing `render.py` match this layout.

## Rules

- Every number comes from code (G1/G2). The agent only writes the one-line issue summaries.
- No cause words ("because", "due to", "driven by", "caused"). "Why it moved" shows the split, not a reason.
- Every issue line has a link. Items that failed the checks are listed under **Uncertain**, not hidden.
- No buy/sell advice. The footer says so.
- Order: market first, then stocks by absolute move, largest first.

## Markdown brief (`briefs/YYYY-MM-DD.md`)

```markdown
# Stock Briefing — 2026-12-01 (Tue)

Window: <from> → <to> (ADR 005) · Watchlist: 3 stocks · Generated 07:30 CET

## Market overview
| Index / rate | Move |
|---|---|
| S&P 500 (SPY) | -1.2% |
| Nasdaq 100 (QQQ) | -1.8% |
| VIX | 18.4 (+2.1) |
| 10Y yield | 4.21% (+0.05) |
| Semiconductors (SMH) | -2.9% |

## NVDA — -4.1% · pullback (uptrend, down today)
- Gap -1.5% · after-hours -0.6% · volume 1.8× 20-day avg · 2nd down day
- Why it moved: market -1.8% · sector -1.1% · own -1.2% → mostly market + sector

**Direct**
- Company files an 8-K on a supply agreement. [SEC](https://example.com)
- One analyst lowers the rating to Hold. [Yahoo](https://example.com)

**Sector**
- A major foundry reports lower monthly sales. [Nasdaq](https://example.com)

**Macro**
- Jobs report comes in above forecasts. [Google News](https://example.com)

**Uncertain**
- "AI stocks to watch this week" — relevance unclear. [Yahoo](https://example.com)

## KO — +0.3% · flat (sideways)
- Gap +0.1% · volume 0.9× 20-day avg
- Why it moved: market -1.2% · sector +0.2% · own +1.3% → mostly stock-specific

**Direct**
- No direct issues in the window.

---
Market moves and related issues only. Not financial advice; no buy/sell recommendations.
```

## Telegram message (short)

Same order, one line per stock, top 2 issues per stock, link to the full brief if hosted.

```
Stock Briefing 2026-12-01
Market: SPY -1.2% · QQQ -1.8% · VIX 18.4

NVDA -4.1% pullback · mostly market+sector
• 8-K: supply agreement (SEC)
• Rating cut to Hold (Yahoo)

KO +0.3% flat · mostly stock-specific
• No direct issues

Not financial advice.
```

## Open points

- Time window line (ADR 005)
- Trend label wording and "weak" display once thresholds are set
- Where the full brief is opened from Telegram (file attachment vs. link)
