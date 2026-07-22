---
name: Pull end-of-day price history for backtesting
description: Fetch split- and dividend-adjusted daily OHLCV history for a US equity or ETF.
api: openapi/tiingo-openapi.yml
operations:
- getDailyMeta
- getDailyPrices
generated: '2026-07-22'
method: generated
---

# Pull end-of-day price history for backtesting

Fetch split- and dividend-adjusted daily OHLCV history for a US equity or ETF.

1. Authenticate every request with the account API token: either append `?token=<token>` or send the header `Authorization: Token <token>` (see conventions/tiingo-conventions.yml).
2. Optionally call `getDailyMeta` (`GET /tiingo/daily/{ticker}`) to confirm the ticker exists and read its `startDate`/`endDate` coverage window.
3. Call `getDailyPrices` (`GET /tiingo/daily/{ticker}/prices`) with `startDate` and `endDate` (YYYY-MM-DD). Use `resampleFreq` (daily, weekly, monthly, annually) to downsample and `sort` (prepend `-` for descending) to order results.
4. For large pulls prefer `format=csv` - it is 4-5x faster than JSON.
5. Symbology: share classes use dashes, e.g. `BRK-A`, `SPG-P-J`.
6. On `429`, you have hit the hourly/daily/monthly plan limit - back off until the window resets (hourly limits reset each hour; daily at midnight EST). Never retry in a tight loop.
