# 001: Report related issues, not causes

- **Status:** Accepted
- **Date:** 2026-11-16
- **Related:** G4, G5, G6

## Problem

The first idea was a brief that explains *why* each stock moved. Finding a real cause needs strong reasoning over many sources. The runtime model is Qwen 3.6 35B, a mixture-of-experts model with about 3B active parameters ([ADR 002](002-runtime-model-dingo-qwen.md)). It can classify and summarize, but cause claims from it would often be wrong and would sound confident.

## Options

| | A. Agent explains causes | B. Agent reports related issues only |
|---|---|---|
| Model job | Reasoning over prices + news | Classify and summarize each item |
| Fit for a mid-size model | Poor | Good |
| Can it be checked? | Hard: no ground truth for causes | Yes: verbatim quotes, name match, hand labels |
| Risk | Confident wrong answers | Missing context the user must judge |

## Decision

B. Code measures the move and splits it into market / sector / stock-specific parts (G1, G2). The agent tags each issue `direct` / `sector` / `macro` / `unrelated` with a verbatim quote and a confidence (G4) and summarizes it with a link (G5). It never says "X caused the move".

## Consequences / follow-ups

- Prompts and checks reject cause words ("because", "due to", "driven by", "caused").
- "Why It Moved" (feature 3) means market-driven vs. stock-specific, computed by code — not a cause.
- Optional G6 experiment: ask the models to name a cause and measure how often they are right, as a finding for the report.
