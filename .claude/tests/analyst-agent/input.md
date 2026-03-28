# Test: Investor AB Seasonal Pattern

## Input to analyst-agent

Ticker: `INVE-B.ST`

Test hypothesis: Stock historically declines Feb 19 – Apr 8 and recovers from Apr 9.

Use fetcher-agent to pull 10yr historical data for `INVE-B.ST`, then pass to analyst-agent.

## What to verify

1. Seasonal pattern analysis covers Feb–Apr window for past 10 years
2. Signal is produced (Strong Buy / Buy / Hold / Avoid)
3. Reasoning references seasonal pattern specifically
4. Output JSON matches the schema defined in analyst-agent.md
5. If pattern is found in fewer than 5 years, agent flags low confidence
