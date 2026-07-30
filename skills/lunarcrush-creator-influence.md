---
name: Find and profile the top creators for a topic
description: Identify the most influential social accounts driving a topic on LunarCrush and profile their recent activity and reach.
api: https://lunarcrush.ai
operations: [search, creator, creator_posts, creator_time_series]
auth: Bearer API key (Authorization: Bearer <API_KEY>)
---

# Find and profile the top creators for a topic

Discover who is shaping the conversation around a topic and how their influence is trending.

## Prerequisites
- LunarCrush API key sent as `Authorization: Bearer <API_KEY>`.
- Base URL `https://lunarcrush.ai`, `?format=json` for structured output.

## Steps
1. **Locate** — if you only have a name/handle, call `search` (or `GET /search/{query}`) to resolve it to topics and creator accounts (each creator is identified by `{network}` + `{id}`).
2. **Top creators for a topic** — `GET /creators/{topic}` for a topic, or `GET /creators/_{category}/{sort}/{limit}` for a category (note the leading underscore on the category slug), e.g. `/creators/_cryptocurrencies` or `/creators/ethereum/mentions/100`.
3. **Profile** — call `creator` (or `GET /creator/{network}/{id}`) for the summary snapshot including `influencer_rank` (CreatorRank) and `followers`.
4. **Recent activity** — call `creator_posts` for their top posts and `creator_time_series` for how their reach/rank has moved over time.

## Rules
- `network` is the platform (`twitter`, `youtube`, `tiktok`, `reddit`, `instagram`); `id` is the platform account id (e.g. `/creator/twitter/44196397`).
- CreatorRank (`influencer_rank`): relative ranking across tracked creators.
- Read-only and safe to retry; result depth depends on subscription tier.
