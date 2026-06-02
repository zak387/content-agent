# DECISIONS.md

Append-only log of meaningful choices about the content agent. Newest at the bottom. One line each, with date and a short why.

---

- **2026-05-30** — Project kicked off: LinkedIn content agent for Zak, 5 posts/week, one per weekday pillar. Markdown + Claude Code, no frameworks.
- **2026-05-30** — Primary brand lanes set to dual: (1) email marketing & funnels, (2) vibe coding / building with AI. Creator economy/monetization/info products are adjacent, used in service of the two.
- **2026-05-30** — Output language: US English.
- **2026-05-30** — Human checkpoints: pause at EVERY stage for v1 (topic → format → draft → final). Will relax once specific stages earn trust.
- **2026-05-30** — Viral sourcing for Tuesday: web search + LunarCrush MCP (X/Twitter, Reddit, etc.) + manual paste. Decided NOT to build LinkedIn/Twitter API integration for v1 — defer to a later phase. LunarCrush has no LinkedIn coverage; LinkedIn trends come from WebSearch/manual paste.
- **2026-05-30** — Voice baseline: persona = warm mentor / builder-in-public; length mixed by pillar; formatting mixed by content; emoji/hashtags few & purposeful.
- **2026-05-30** — Client folder pattern adopted (`clients/<name>/`) even with one client, so onboarding new clients = new folder.
- **2026-05-30** — Skills implemented as plain SOP markdown in `skills/`, read on demand by slash-command conductors (chosen over native auto-discovered skills for deterministic, ordered pipeline execution).
- **2026-05-30** — Monday alternates: first Monday = re-introduction; subsequent Mondays = challenge announcement (30-day / 4-week, optionally 60-day).
- **2026-05-30** — Tastemaker interview completed (Rounds 1–4). profile/story-bank/voice-profile populated from Zak's real bio, businesses (Augmentum, Saulderson, MPWR, Allii, Sawa), mentors, voice notes, and personal texture.
- **2026-05-30** — Voice rule refined: Zak admires Sahil Bloom/Hormozi/Naval but explicitly dislikes staccato one-line layout and "X isn't Y, it's Z" antithesis. Voice profile borrows their hooks/structure/compression but keeps Zak's flowing, warm, non-choppy sentences.
- **2026-05-30** — Active challenge: build **Risala** (AI newsletter agent), 30 days, measured by newsletter production time saved (%). Exact target % still to confirm.
- **2026-05-30** — First lead magnet: subject-line swipe file (to build).
- **2026-05-30** — Off-limits finalized: never name Lululemon/AG1/Nestlé (prior agencies' clients); no religion-as-topic (biz-spirituality mindset OK); never name/attack competitors; keep Allii co-founder breakup high-level.
- **2026-06-02** — Voice-learning entry #1: Zak rewrote his own re-intro. Recalibrated voice profile to v1.1 — register is more casual/idiomatic than first thought (formality 5→4, expressiveness 7→8), energetic caps openers + gratitude/direct-address are core, rhythm mixes flowing sentences with deliberate short lines, natural rule-of-three idioms allowed. Cleared naming Augmentum Media & Saulderson Media (clients still off-limits). New facts: MPWR client made 5 figures from a course; Sawa serves education + ecommerce; Ziad = brother & partner. His re-intro saved as the W23 Monday draft.
- **2026-06-02** — LinkedIn viral sourcing: confirmed no official LinkedIn API can search viral posts. v1 = manual paste (primary for LinkedIn) + LunarCrush (Twitter) + web search. Zak has a third-party LinkedIn scraper/data API to wire in Phase 2 (ToS-gray; documented requirements in `pillar-tuesday-viral.md`).
- **2026-05-30** — Added self-improving voice loop, adapted from jzOcb/writing-style-skill. Chose NATIVE markdown version over the Python port: container is ephemeral (logs must live in-repo) and Claude does the diff/extraction directly (no external LLM CLI). New: `skills/learn-voice.md`, `clients/zak/voice-learning-log.md`, `/learn-voice` command, P0/P1/P2 tiers + 1–10 voice dimensions in voice-profile, wired into the review step.
