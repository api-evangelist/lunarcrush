---
name: Get a real-time social snapshot for a topic
description: Pull the current social-intelligence snapshot, historical trend, and top posts for any crypto, stock, or trending topic from LunarCrush.
api: https://lunarcrush.ai
operations: [topic, topic_time_series, topic_posts]
auth: Bearer API key (Authorization: Bearer <API_KEY>)
---

# Real-time social snapshot for a topic

Use LunarCrush to understand the current social conversation around any asset or subject.

## Prerequisites
- A LunarCrush API key. Send it on every request as `Authorization: Bearer <API_KEY>`.
- Base URL: `https://lunarcrush.ai`. Add `?format=json` for machine-readable output (default is markdown; `?format=csv` also available).

## Steps
1. **Summary snapshot** — call the `topic` tool (or `GET /topic/{name}?format=json`). Read `galaxy_score`, `alt_rank`, `sentiment`, `interactions`, `posts_active`, and `social_dominance` for the current state.
2. **Trend** — call `topic_time_series` (or `GET /topic/{name}/time-series?interval=1m&bucket=day&format=json`). Use `interval` (1d,1w,1m,3m,6m,1y,all) OR explicit `start`/`end` (YYYY-MM-DD) with `bucket` (hour|day). Compare recent buckets to spot momentum shifts.
3. **Evidence** — call `topic_posts` (or `GET /topic/{name}/posts?format=json`) to pull the top posts by interactions that are driving the numbers.

## Rules
- Topic slugs may contain letters, numbers, spaces, `#`, and `$` (e.g. `bitcoin`, `$nvda`, `$fartcoin`).
- The API is read-only; requests are safe to retry. Access depth depends on subscription tier — check with the `auth` tool if data looks truncated ("Limited data mode").
- Galaxy Score is 0–100 (above 50 is above-average health); AltRank is a relative rank where lower is stronger.
