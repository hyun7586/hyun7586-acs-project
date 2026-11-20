# 004: Run mode — one-shot CLI, scheduled once a day

- **Status:** Accepted
- **Date:** 2026-11-21
- **Related:** G3, G5, daily data collection

## Problem

Should the agent run all the time in the background, or only when asked?

## Options

| | A. Manual one-shot CLI | B. Same CLI, scheduled daily | C. Always-on service |
|---|---|---|---|
| How | `briefing run` writes the brief and exits | launchd/cron runs A every morning | A process waits for events |
| Complexity | Lowest | Low (same code + a schedule) | High (server, uptime) |
| Daily data collection | Only if I remember | Automatic | Automatic |
| Telegram delivery | Manual trigger | Arrives on its own | Arrives on its own |

## Decision

Build A; run it as B. The program is a one-shot CLI, so it works both by hand (demo) and on a schedule (collection, Telegram).

## Consequences / follow-ups

- The MacBook must be awake for the scheduled run → retry on the next wake; log missed days.
- dingo may be slow or down in the morning → retry, then local-model fallback ([ADR 002](002-runtime-model-dingo-qwen.md)).
- Chatting with the bot in Telegram would need C → out of scope.
