---
name: Research company fundamentals
description: Pull SEC-sourced financial statements and daily fundamentals for equity research.
api: openapi/tiingo-openapi.yml
operations:
- getFundamentalsMeta
- getFundamentalsStatements
- getFundamentalsDaily
- getFundamentalsDefinitions
generated: '2026-07-22'
method: generated
---

# Research company fundamentals

Pull SEC-sourced financial statements and daily fundamentals for equity research.

1. Call `getFundamentalsDefinitions` (`GET /tiingo/fundamentals/definitions`) once to learn the available field codes.
2. Call `getFundamentalsMeta` (`GET /tiingo/fundamentals/meta?tickers=...`) to get each company's coverage window and `permaTicker` - use the permaTicker for delisted companies.
3. Statements: `getFundamentalsStatements` (`GET /tiingo/fundamentals/{ticker}/statements`) with `startDate`/`endDate`; set `asReported=true` to see original filings without later revisions (default false returns the most recent revised data).
4. Daily metrics (marketCap, peRatio, pbRatio, trailingPEG1Y): `getFundamentalsDaily` (`GET /tiingo/fundamentals/{ticker}/daily`).
5. Fundamentals beyond the DOW 30 requires the Fundamentals add-on; expect an authorization error without it.
