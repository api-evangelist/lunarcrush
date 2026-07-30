---
name: Rank cryptocurrencies by social and market signal
description: Retrieve and sort the LunarCrush cryptocurrency universe by social and market metrics to surface movers and momentum.
api: https://lunarcrush.ai
operations: [cryptocurrencies, list, topic]
auth: Bearer API key (Authorization: Bearer <API_KEY>)
---

# Rank cryptocurrencies by social and market signal

Surface the strongest (or weakest) crypto assets by combining LunarCrush social metrics with market data.

## Prerequisites
- LunarCrush API key sent as `Authorization: Bearer <API_KEY>`.
- Base URL `https://lunarcrush.ai`, `?format=json` for structured output.

## Steps
1. **List the universe** — call the `cryptocurrencies` tool (or `GET /category/cryptocurrencies/{sort}/{limit}?format=json`). Sort by a metric key such as `percent_change_24h`, `galaxy_score`, `alt_rank`, `social_dominance`, or `interactions`; cap with `limit`.
2. **Filter by category/sector** — use the `list` tool to pull topics within a category filtered by sector when you need a narrower slice than the whole market.
3. **Drill in** — for any candidate, call `topic` on its slug to read the full metric snapshot before acting on the ranking.

## Rules
- Metric keys are exact (see the metrics glossary): `galaxy_score`, `alt_rank`, `close`, `percent_change_1h/24h/7d`, `interactions`, `posts_active`, `contributors_active`, `sentiment`, `social_dominance`, `market_cap`, `market_dominance`, `volume`, `circulating_supply`, `topic_rank`.
- AltRank: lower is stronger. Galaxy Score: higher (0–100) is healthier.
- Read-only and idempotent. Depth of the list (number of assets, full vs limited metrics) is governed by subscription tier.
