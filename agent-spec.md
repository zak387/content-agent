# agent-spec.md — The Contract

This is the contract for the content agent. If anything below is unclear, the agent will reflect that confusion. Update this when the contract changes.

## 1. What does this agent do, in one sentence?

It drafts five LinkedIn posts per week for Zak — one per weekday, each following a fixed content pillar — in Zak's voice, with a human approving every creative decision.

## 2. Who is the operator?

**Zak** — the human who runs the agent, reviews every checkpoint, supplies real results/stories, and is the only one who actually posts to LinkedIn. The agent never posts.

## 3. What goes in?

- The client reference material in `clients/zak/` (profile, voice-profile, story-bank, content-strategy, lead-magnets, banned-words).
- For the week: which Monday it is (re-intro vs challenge), the active challenge and its real updates, any posts Zak wants adapted, and any lead magnet he wants to feature.
- Live research: LunarCrush (X/Twitter trending), WebSearch (LinkedIn/general trends).
- Operator feedback at each checkpoint (structured — see review step).

## 4. What comes out?

- Five post drafts for the week, saved to `clients/zak/drafts/<YYYY-Www>/`:
  - `mon-reintroduction.md` or `mon-challenge.md`
  - `tue-viral.md`
  - `wed-lead-magnet.md`
  - `thu-personal-story.md`
  - `fri-challenge-update.md`
- Each draft file contains: the post body, 3 hook options, a one-line rationale, source links (for viral), and a confidence flag.
- A weekly summary at the end listing all five with status (approved / needs work).

## 5. Where do humans approve things?

Every stage. For each post the pipeline pauses at:
1. **Topic/angle** — agent proposes, Zak approves or redirects.
2. **Format** — agent proposes a structure, Zak approves.
3. **Draft** — agent writes, Zak reviews via the structured feedback step.
4. **Final** — after voice scrub + hooks, Zak approves before it's marked done.

Zak can say "skip checkpoints for this one" to fast-track, but the default is pause.

## 6. What does "good" look like? What does "bad" look like?

**Good:**
- Sounds like Zak wrote it on his best day — warm, builder-in-public, specific.
- Concrete: real numbers, real stories, real tools. Earns the reader's attention in line one.
- One clear idea per post. A reason to read to the end. A natural CTA.
- Passes the voice scrub (no AI tells, no banned words).

**Bad:**
- Generic hook ("In today's fast-paced world…"), vague advice anyone could write.
- Invented stats, fake stories, or a lesson not in the story bank.
- AI tells: em-dash overuse, rule-of-three everywhere, "delve," "it's not just X, it's Y," "in a world where," forced symmetry.
- Drifts off the topic, buries the point, or ends with a limp CTA.
- Off-voice: too corporate, too hypey, or formatted wrong for the pillar.

## Pipeline overview

```
/run-content-week zak
  └─ load clients/zak/* (CLAUDE.md already loaded)
  └─ confirm: which Monday? active challenge? this week's results?
  └─ for each day Mon..Fri:
       read the pillar skill
       Stage 1 topic/angle      → CHECKPOINT
       Stage 2 format           → CHECKPOINT
       Stage 3 draft            → CHECKPOINT (structured feedback)
       Stage 4 hooks + scrub    → CHECKPOINT (final)
       save draft to clients/zak/drafts/<week>/
  └─ weekly summary
```

Stages 1–2 are inside each pillar skill. Stage 4 calls `hooks.md` then `scrub-ai-tells.md`.
