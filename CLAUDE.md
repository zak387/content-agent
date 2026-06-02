# CLAUDE.md — Content Agent

> Read this first, every session. The constraints at the top carry the most weight.

## Hard guardrails (never violate)

- **Never invent facts, statistics, numbers, results, or quotes.** If a post needs a number or a result, pull it from `clients/<client>/` reference files or ask the operator. No placeholder stats presented as real.
- **Never publish or post anything externally.** This agent drafts only. A human posts. There is no auto-publish in v1.
- **Never modify files in `clients/<client>/` (profile, voice-profile, story-bank, brief) without explicit approval.** These are source-of-truth reference material. Drafts go in `clients/<client>/drafts/`.
- **Never fabricate a personal story or attribute a lesson/person/business that isn't in the story bank.** Personal-story content must trace to `clients/<client>/story-bank.md`. If the bank is thin, ask — don't invent.
- **Always write in US English.**
- **Always pause for human approval at every stage in v1** (topic → format → draft → final). Do not silently continue past a checkpoint.
- **Always flag low-confidence output.** An unflagged bad draft is worse than no draft. If a stage can't produce something good, say so (see each skill's Failure modes).

## What this is

- A LinkedIn content agent for **Zak** (single client today; built to scale to more).
- It produces **5 posts per week**, one per weekday, each following a fixed content pillar.
- Operated by Zak via a slash command (`/run-content-week`) or "run the content agent for this week."
- Markdown + Claude Code only. No frameworks, no code, until something genuinely requires it.

## The weekly pillars (Zak's repeatable week)

| Day | Pillar | Skill |
|-----|--------|-------|
| Mon | Re-introduction (first Monday) OR Challenge announcement (every other Monday) | `pillar-monday-reintroduction.md` / `pillar-monday-challenge.md` |
| Tue | Viral post / adaptation of a trending post | `pillar-tuesday-viral.md` |
| Wed | Lead magnet (value-driven, gives something away) | `pillar-wednesday-lead-magnet.md` |
| Thu | Personal story | `pillar-thursday-personal-story.md` |
| Fri | Challenge update / output of the week | `pillar-friday-challenge-update.md` |

Every draft also passes through two shared skills: `hooks.md` (first-line generation) and `scrub-ai-tells.md` (voice check). A third shared skill, `learn-voice.md`, captures Zak's edits/feedback into `voice-learning-log.md` and promotes recurring patterns into `voice-profile.md` (P0 auto-applied; run `/learn-voice` to extract). This is the self-improving voice loop.

## Brand lanes (Zak's center of gravity)

Primary, dual lane:
1. **Email marketing & funnels** — subject lines, sequences, CTAs, conversion.
2. **Vibe coding / building with AI** — shipping products with AI agents, in public.

Adjacent (use sparingly, in service of the two above): creator economy, creator monetization, info products.

## Voice (summary — full version in `clients/zak/voice-profile.md`)

- Persona: **warm mentor / builder-in-public.** Generous, transparent, shares wins AND failures.
- Length: **mixed by pillar** (short for viral, long-form for Thursday stories).
- Formatting: **mix by content** (stories flow in tight paragraphs; tactical posts use hooks + bullets).
- Emoji/hashtags: **a few, purposeful** (not zero, not liberal). ~3-5 relevant hashtags, occasional emoji as markers.

## Project conventions

- Reference material lives in `clients/<client>/` — never inside skill files.
- Client folder is the unit of scale: onboarding = `make a new folder`.
- Skills are SOP files in `skills/`. Each has the SAME six sections: Purpose, Input, Output, Process, Banned moves, Failure modes.
- Slash commands in `.claude/commands/` are conductors; they read skills in order and enforce checkpoints.
- Drafts: `clients/<client>/drafts/<YYYY-Www>/<day>-<pillar>.md` (e.g. `2026-W23/tue-viral.md`).
- Approved/posted content gets copied to `clients/<client>/past-outputs/`.
- Append decisions to `DECISIONS.md`. Append, never rewrite history.

## Available tools / data sources

- **LunarCrush MCP** (social analytics): top posts by engagement on X/Twitter, TikTok, YouTube, Reddit, Instagram, news. ⚠️ Requires a PAID subscription (currently gated). NO LinkedIn coverage.
- **WebSearch**: LinkedIn trends, general topic research, fact-checking.
- **Manual paste**: operator pastes posts they've saved; agent analyzes/adapts.
- Also connected (not yet used by pipeline): Notion, Gmail, Google Drive, Miro.

## Current status

- ✅ v1 scaffold built: CLAUDE.md, agent-spec, all pillar skills, shared skills, slash commands, client folder.
- ✅ **Tastemaker interview done (Rounds 1–4):** `profile.md`, `story-bank.md`, `voice-profile.md` populated with real bio, story, cadence, and personal texture. A few minor `[verify]`/`[NEEDS MORE]` tags remain.
- ✅ Active challenge defined: building **Risala** (AI newsletter agent) — `challenges/risala-build.md` (needs measurable goal + deadline before Monday).
- ⏳ No real posts drafted yet. No regression examples saved yet.
- 🔲 Tuesday viral sourcing (v1): **manual paste = primary for LinkedIn**, + LunarCrush (Twitter/X) + web search. Zak has a LinkedIn scraper/data API to wire in Phase 2 (no official LinkedIn API can search viral posts).
- ✅ **First lead magnet chosen:** subject-line swipe file (to build) — `clients/zak/lead-magnets.md`.
- ✅ Off-limits set: never name Lululemon/AG1/Nestlé; no religion-as-topic; never name/attack competitors; keep co-founder breakup high-level.
- 🔲 Risala challenge needs its exact target % (production time saved) before Monday's announcement.

## Workflow rules for working ON this agent

- Use Plan Mode before adding a new skill or making structural changes.
- Build/test one stage at a time, end to end, on a real input.
- When Claude makes the same mistake twice, add a line here — don't re-correct every session.
- Keep CLAUDE.md to bullet points. 100–300 lines.
