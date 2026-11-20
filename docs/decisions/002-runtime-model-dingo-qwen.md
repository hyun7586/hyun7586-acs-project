# 002: Runtime model — Qwen 3.6 35B on the course server (dingo)

- **Status:** Accepted
- **Date:** 2026-11-16
- **Related:** G4, G5, G6, [ADR 001](001-no-cause-claims.md)

## Problem

The agent needs an LLM at runtime to classify and summarize news. Claude Code is used to build the project; the runtime model is a separate choice.

## Options

| | A. Qwen 3.6 35B on dingo | B. Small local model (Ollama, MacBook M5 16 GB) | C. Cloud API |
|---|---|---|---|
| Cost | Free (course server) | Free | Paid per token |
| Quality | Mid-size MoE | Lower | Highest |
| Limits | 64k context, shared, one request at a time, may be slow or down | Limited by 16 GB RAM | Key + budget |
| Course fit | The class model | Allowed if declared | Allowed if declared |

## Decision

A, with B as a fallback and as the comparison baseline in G6. The model's job is kept small: one stock per call, at most ~10 pre-filtered news items, fixed JSON output.

## Consequences / follow-ups

- Pin the exact model tag in the README stack table at the first Sprint 1 session.
- Never commit the dingo key or `models.json`.
- Retry and fall back to the local model when dingo is down (G4).
