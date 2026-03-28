---
name: yfinance-fetch
description: Fetches historical OHLCV price data and news for a stock ticker using the yfinance Python library
---

# yfinance-fetch Skill

Fetches historical price data and recent news for any stock ticker supported by Yahoo Finance, including Swedish stocks on Nasdaq Stockholm (suffix `.ST`).

## Usage

Run the following Python script via Bash:

```python
import yfinance as yf
import json
from datetime import datetime, timedelta

ticker = "INVE-B.ST"  # replace with target ticker
period = "10y"        # options: 1y, 2y, 5y, 10y, max

stock = yf.Ticker(ticker)

# Historical OHLCV
hist = stock.history(period=period)
hist_json = hist.reset_index().to_json(orient="records", date_format="iso")

# Recent news
news = stock.news

# Basic info
info = {
    "name": stock.info.get("longName"),
    "currency": stock.info.get("currency"),
    "exchange": stock.info.get("exchange"),
    "sector": stock.info.get("sector"),
}

output = {
    "ticker": ticker,
    "info": info,
    "history": json.loads(hist_json),
    "news": news[:10]  # latest 10 headlines
}

print(json.dumps(output, indent=2, default=str))
```

## Install dependency

```bash
pip install yfinance
```

## Swedish Stock Tickers (Nasdaq Stockholm)

Append `.ST` to the ticker symbol:
- Investor AB B share → `INVE-B.ST`
- Volvo B → `VOLV-B.ST`
- Ericsson B → `ERIC-B.ST`

## Output Schema

```json
{
  "ticker": "INVE-B.ST",
  "info": { "name", "currency", "exchange", "sector" },
  "history": [{ "Date", "Open", "High", "Low", "Close", "Volume" }],
  "news": [{ "title", "link", "publisher", "providerPublishTime" }]
}
```
