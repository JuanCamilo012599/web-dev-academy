# TradeForge — Trading Strategy App

## Status

Idea — not started. Shelved as of 2026-08-16: deprioritized in favor of the core SDET roadmap
and its Phase 12 portfolio projects. Revisit later, not currently being worked. Details to be
filled in with Juan (existing Pine Script work referenced but not yet described here).

## Problem Statement

Build an app around existing trading-strategy logic (previously written in Pine Script for
TradingView) — scope, target platform, and whether it stays on TradingView vs. becomes a
standalone app are still open.

## Open Questions

- What does the existing Pine Script strategy do, and does it need to be ported (e.g. to
  Python) or just wrapped/automated?
- Standalone app, broker API integration, or TradingView-hosted? Live trading, paper trading,
  or backtesting only?
- Data source and hosting: local script vs. cloud-deployed service?

## Roadmap Connections

None currently. Its old connections (cloud hosting, containerizing, IaC, monitoring) were tied
to the Cloud Engineer plan and no longer apply under the SDET curriculum — this project isn't
mapped to any current phase. Could plausibly resurface later as a capstone-under-test target
(something to write Playwright/API tests against), but that's undecided; not a live plan.

## Next Steps

- Write down what the current Pine Script strategy actually does, in plain language.
- Decide the smallest useful first version (e.g. a backtester) before scoping the full app.
