# Skill: Tuesday — Viral Post / Adaptation

## Purpose
Find a currently-trending post or angle in Zak's lanes (email/funnels, building with AI; adjacent: creator economy/monetization, info products) and adapt the *structure and angle* — never the words — into an original post in Zak's voice.

## Input
- Zak's lanes from `content-strategy.md`.
- Research sources (in priority order for v1):
  1. **Manual paste (PRIMARY for LinkedIn)** — Zak drops in 3–5 viral LinkedIn posts he's saved from his niche. Highest-quality signal; the only reliable LinkedIn source until the scraper API is wired.
  2. **LunarCrush MCP** — `search`, `topic_posts`, `keyword_posts` for top X/Twitter / Reddit posts by engagement. ⚠️ **Currently GATED — requires a paid LunarCrush subscription** (returns "subscription required" otherwise). Don't rely on it until Zak upgrades.
  3. **WebSearch** — strong for trend *intelligence* (algorithm shifts, best formats) and for mining curated "viral post example" roundups to reverse-engineer mechanics. CANNOT return a live engagement-ranked feed of this week's niche posts.
- `voice-profile.md`.

### Phase 2 (future) — LinkedIn scraper/data API
Zak has a LinkedIn scraper/data API (Apify / Bright Data / RapidAPI / Phantombuster-type). NOT wired yet — start manual. **Researched Apify options + wiring plan: see `integrations/linkedin-apify.md`** (recommended actor: `benjarapi` LinkedIn Post Search, $3/1k posts, no cookies, past-week filter). To wire it, capture from Zak:
- Provider + endpoint(s) and how it's called (REST? MCP? CLI?).
- Auth (key/header) and where the secret lives (env var — never commit it).
- Search inputs it supports: keyword, hashtag, profile, date range.
- What it returns: post text, author, engagement counts, post URL, timestamp.
- Rate limits / cost per call.
Once known, add a step 0 to Stage 1 that queries it for lane keywords and ranks by engagement, with manual paste as fallback. NOTE: LinkedIn scraping is ToS-gray — confirm Zak accepts that before automating.

## Output
- Draft → `clients/zak/drafts/<week>/tue-viral.md`.
- MUST include: the source post link(s), why it's working (the mechanic), and the original adaptation.
- Usually short-to-medium, punchy.

## Process
1. **Stage 1 — Find + pick.** Gather 3–5 trending posts/angles in-lane: **ask Zak to paste saved LinkedIn posts first**, supplement with LunarCrush (Twitter) + WebSearch. For each: link, engagement signal, and the *mechanic* that made it work (format, contrarian take, list, story arc). Recommend one. → CHECKPOINT.
2. **Stage 2 — Format.** Map the chosen mechanic to Zak's topic. Propose the structure (the pattern to borrow). → CHECKPOINT.
3. **Stage 3 — Draft.** Write an ORIGINAL post using the mechanic, with Zak's own example/take. Cite nothing fake. → CHECKPOINT.
4. **Stage 4 — Hooks + scrub.** Run `hooks.md` then `scrub-ai-tells.md`. → CHECKPOINT.

## Banned moves
- NEVER copy the source post's wording, structure verbatim, or rip a specific anecdote. Borrow the *mechanic*, not the content. This is adaptation, not plagiarism.
- Don't adapt something outside Zak's lanes just because it's viral.
- Don't present the source's claims/numbers as Zak's.
- Don't chase a trend that contradicts Zak's positioning or values.

## Failure modes
- LunarCrush returns nothing useful for a niche term (it skews crypto/finance/sports) → fall back to WebSearch, then ask Zak to paste posts. Note which source was used.
- Nothing trending fits the lanes this week → tell Zak, and offer to instead build an original post on an evergreen lane topic rather than force a bad fit.

## Negative examples
- ❌ Rewriting a viral post with synonyms swapped in — that's plagiarism with extra steps.
- ❌ Adapting a viral "I made $100k in 30 days" post by inventing Zak's own fake number.
- ✅ (shape) Borrow the *format* "Everyone says X. Here's why they're wrong. [3 reasons]." and fill it with Zak's genuine contrarian take on email open rates.
