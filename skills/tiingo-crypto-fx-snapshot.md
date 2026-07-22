---
name: Snapshot crypto and forex markets
description: Take a cross-market snapshot of crypto pairs and FX rates.
api: openapi/tiingo-openapi.yml
operations:
- getCryptoTopOfBook
- getCryptoPrices
- getForexTopOfBook
- getForexPrices
generated: '2026-07-22'
method: generated
---

# Snapshot crypto and forex markets

Take a cross-market snapshot of crypto pairs and FX rates.

1. Crypto top-of-book: `getCryptoTopOfBook` (`GET /tiingo/crypto/top?tickers=btcusd,...`, max 100 tickers); add `includeRawExchangeData=true` to see per-exchange OHLC underlying the aggregate.
2. Crypto history: `getCryptoPrices` (`GET /tiingo/crypto/prices`) with `tickers`, `startDate`/`endDate`, and `resampleFreq` (e.g. 5min, 1hour, 1day); optionally restrict `exchanges`.
3. FX quotes: `getForexTopOfBook` (`GET /tiingo/fx/top?tickers=audusd,...`) and history via `getForexPrices` (`GET /tiingo/fx/{ticker}/prices`).
4. For sustained real-time needs switch to the WebSocket feeds (wss://api.tiingo.com/crypto and /fx - see asyncapi/tiingo-websockets-asyncapi.yml) instead of polling: subscribe with `{"eventName":"subscribe","authorization":"<token>","eventData":{...}}` and handle messageType A/U/D/I/E/H frames.
5. Respect plan limits (429 = hourly/daily/monthly cap reached).
