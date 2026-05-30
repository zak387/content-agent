---
description: Draft a single post for one day/pillar, end to end with checkpoints.
argument-hint: "<day: mon|tue|wed|thu|fri> [client] (default client: zak)"
---

# Draft a Single Post

Draft ONE post for day `$1` (client `$2`, default `zak`). Use this to build/test one stage in isolation or fill a gap.

1. Load `clients/<client>/` reference files.
2. Map the day to its pillar skill:
   - `mon` → ask: re-intro or challenge? → `skills/pillar-monday-reintroduction.md` or `skills/pillar-monday-challenge.md`
   - `tue` → `skills/pillar-tuesday-viral.md`
   - `wed` → `skills/pillar-wednesday-lead-magnet.md`
   - `thu` → `skills/pillar-thursday-personal-story.md`
   - `fri` → `skills/pillar-friday-challenge-update.md`
3. Run the skill's 4 stages, pausing at every CHECKPOINT.
4. At the Draft checkpoint use the **structured feedback step** from `run-content-week.md` §2 (checklist or one concrete sentence; inject into the next attempt).
5. Stage 4: run `skills/hooks.md` then `skills/scrub-ai-tells.md`.
6. On approval, save to `clients/<client>/drafts/<YYYY-Www>/<day>-<pillar>.md`.

Rules: US English. Never invent facts/stats/stories. Pause at every checkpoint. Flag low-confidence output.
