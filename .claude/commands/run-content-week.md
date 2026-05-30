---
description: Run the full weekly content pipeline — drafts 5 LinkedIn posts (Mon–Fri), pausing for approval at every stage.
argument-hint: "[client] (default: zak)"
---

# Run Content Week

You are the **conductor**. The skills are the musicians. Run the week one post at a time, end to end, pausing at every checkpoint. Never auto-continue past a checkpoint.

Client: `$1` (default `zak`).

## 0. Load context
1. Read `clients/<client>/profile.md`, `voice-profile.md`, `story-bank.md`, `content-strategy.md`, `lead-magnets.md`, `banned-words.md`.
2. If `story-bank.md` or `profile.md` are `[PENDING]`/empty, warn that Monday (re-intro) and Thursday (story) will be weak and offer to run `/tastemaker-interview` first.
3. Ask the operator three setup questions:
   - Is this the **first Monday** (re-introduction) or a **challenge Monday**?
   - What's the **active challenge** this cycle (for Mon-announce and Fri-update)?
   - Any posts to adapt (Tue) or a specific lead magnet to feature (Wed)?
4. Determine the week folder `clients/<client>/drafts/<YYYY-Www>/` and create it.

## 1. For each day Mon → Fri
Read the matching pillar skill and run its 4 stages. **Stop at every CHECKPOINT** and wait for the operator.

| Day | Skill |
|-----|-------|
| Mon | `skills/pillar-monday-reintroduction.md` OR `skills/pillar-monday-challenge.md` |
| Tue | `skills/pillar-tuesday-viral.md` |
| Wed | `skills/pillar-wednesday-lead-magnet.md` |
| Thu | `skills/pillar-thursday-personal-story.md` |
| Fri | `skills/pillar-friday-challenge-update.md` |

At **Stage 4** for every post: run `skills/hooks.md` then `skills/scrub-ai-tells.md` before the final checkpoint.

## 2. The structured feedback step (use at the Draft checkpoint, Stage 3)
Do NOT regenerate blind on vague feedback. Present the draft, then ask the operator to either:

**(A) Pick from this checklist** (one or more):
- [ ] Voice is off
- [ ] Structure is wrong
- [ ] Too generic
- [ ] Too long / too short
- [ ] Missing or weak CTA
- [ ] Drifts off topic
- [ ] AI tells present
- [ ] Hook is weak
- [ ] Factually wrong / unverified claim

**(B) Or write one concrete sentence** on what to change.

Then inject the SELECTED items + their concrete fix directly into your next attempt, and tell the operator what you changed in response. Each iteration must be meaningfully different from the last — iterate toward right, don't resample.

If the operator approves: save the draft to the week folder and move on.

## 3. Save + summarize
- Each approved post → `clients/<client>/drafts/<week>/<day>-<pillar>.md` with: post body, 3 hook options (chosen one marked), one-line rationale, source links (Tue), confidence flag.
- After all 5: print a summary table — day, pillar, status (approved / needs work), confidence.
- Append any meaningful choices to `DECISIONS.md`. Update the status section in `CLAUDE.md` if anything changed.
- Remind the operator: nothing is posted — these are drafts for him to publish.

## Rules
- US English. Never invent facts/stats/stories. Pause at every checkpoint. Flag low-confidence output.
