# Integration (Phase 2) — LinkedIn viral sourcing via Apify

> Research dated 2026-06-02. Powers Tuesday's viral pillar by pulling public LinkedIn posts by keyword/niche with engagement data. NOT wired yet — needs Zak's Apify token + ToS sign-off.

## Recommended actors (both: no login/cookies → lower ban risk, keyword search, return engagement + post URL)

| Actor | Author | Price | Key inputs | Notable |
|---|---|---|---|---|
| **LinkedIn Post Search Scraper — Extract by Keyword** | `benjarapi` | **$3 / 1,000 posts** | keyword OR full search URL, **date filter (past-24h / week / month)**, content-type filter, sort relevance/date, filters by member/org/industry/title | Cheapest; best **date filtering** for "this week's viral"; rich output (URNs, ISO timestamp, engagement by type, reposts, media) |
| **LinkedIn Posts Search Scraper — No Login Required** | `apimaestro` | **$5 / 1,000 posts** | keyword/phrase, sort relevance/date_posted, filters by company/industry/job title | Most proven: 4.6★ (35 reviews), ~9.1K users |

**Pick:** `benjarapi` for the weekly viral run (cheapest + past-week filter). `apimaestro` if we want the most battle-tested.

Cost is negligible: ~200 posts/week ≈ **$0.30–$1.00/week**.

## What the actors return (enough to run the viral skill)
post text, author (name/headline/profile), engagement (reactions by type, comments, reposts), post URL, timestamp, media. → Rank by engagement, hand top 3–5 to Stage 1 of `pillar-tuesday-viral.md`.

## Wiring — CONFIGURED 2026-06-02 (Apify MCP)
Chosen path: **Apify MCP server**, configured in `/.mcp.json`:
```json
{ "mcpServers": { "apify": {
  "command": "npx",
  "args": ["-y", "@apify/actors-mcp-server", "--actors", "5QnEH5N71IK2mFLrP"],
  "env": { "APIFY_TOKEN": "${APIFY_TOKEN}" }
}}}
```
- Actor exposed: **`5QnEH5N71IK2mFLrP`** (Zak's chosen LinkedIn post-search actor; confirm its display name once connected).
- The token is read from env var **`APIFY_TOKEN`** — referenced, never hardcoded. `.env` is gitignored; `.env.example` documents it.
- ⚠️ **MCP servers load at session START.** The Apify tools (`mcp__apify__*`) appear on the NEXT session after `APIFY_TOKEN` is set in the environment — not mid-session.

### Setting the token securely (do NOT paste it in chat or commit it)
- In the Claude Code web environment: add `APIFY_TOKEN` as an environment variable / secret in the environment's settings.
- Or locally: copy `.env.example` → `.env` (gitignored) and put the token there.
- If a token was ever pasted in chat, **rotate it** in Apify Console → Settings → Integrations.

### Alternative path — REST (no MCP)
- `POST https://api.apify.com/v2/acts/5QnEH5N71IK2mFLrP/run-sync-get-dataset-items?token=$APIFY_TOKEN`
- Body per the actor's input schema (keyword, sort, maxPosts). Returns dataset items as JSON.

## To proceed (remaining)
- Set `APIFY_TOKEN` in the environment (rotated token).
- Confirm the actor's input schema field names (keyword/sort/date) once connected, so the Tuesday skill calls it correctly.
- Accept that **LinkedIn scraping is against LinkedIn's ToS** (gray area).
- Provide lane keywords (e.g. "email marketing", "newsletter growth", "cold email", "AI agents", "building in public").

## Caveats
- Engagement counts are "as-rendered" and can lag real-time.
- Only public posts; coverage varies by keyword.
- Actors can break when LinkedIn changes its markup — keep manual paste as the fallback.

## Sources
- benjarapi: https://apify.com/benjarapi/linkedin-post-search
- apimaestro: https://apify.com/apimaestro/linkedin-posts-search-scraper-no-cookies
- curious_coder: https://apify.com/curious_coder/linkedin-post-search-scraper
- 2026 comparison: https://use-apify.com/docs/best-apify-actors/best-linkedin-scrapers
