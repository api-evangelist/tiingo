---
name: Scan ticker-tagged market news
description: Retrieve curated, ticker-tagged financial news for one or more companies.
api: openapi/tiingo-openapi.yml
operations:
- searchAssets
- listNews
generated: '2026-07-22'
method: generated
---

# Scan ticker-tagged market news

Retrieve curated, ticker-tagged financial news for one or more companies.

1. Resolve fuzzy company names to tickers with `searchAssets` (`GET /tiingo/utilities/search?query=...`), using `exactTickerMatch=true` when you already have a symbol.
2. Call `listNews` (`GET /tiingo/news`) with `tickers` (comma-separated), optional `source` domains (e.g. bloomberg.com), and `startDate`/`endDate` bounds on publishedDate.
3. Page with `limit` (default 100, max 1000) and `offset`; sort with `sortBy=publishedDate` or `crawlDate`.
4. Each article carries `tickers[]` and `tags[]` assigned by Tiingo's tagging algorithm - filter client-side for precision.
5. The News API requires an account with news access; a `401`/`403` means the token's plan does not include it.
