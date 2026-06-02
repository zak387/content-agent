# Skill: Learn Voice (self-improving voice capture)

> Native adaptation of the writing-style-skill (jzOcb/writing-style-skill): observe → improve → auto-apply. Turns Zak's edits and feedback into durable voice rules. Claude does the diffing directly — no external scripts.

## Purpose
Capture every piece of voice feedback (an edit Zak makes, or checklist/sentence feedback at a checkpoint) and convert recurring patterns into durable rules in `voice-profile.md` / `banned-words.md`, auto-applying only high-confidence ones.

## Input
- A draft (the agent's version) + Zak's edited final version, OR his structured feedback at a draft checkpoint.
- `clients/<client>/voice-learning-log.md` (append-only history).
- `clients/<client>/voice-profile.md` and `banned-words.md`.

## Output
- A new entry appended to `voice-learning-log.md` (the observation).
- On an improve pass: updated `voice-profile.md` (P0 rules applied, dimensions recalibrated, version bumped), P1 rules proposed for approval, P2 archived in the log.

## Process
### 1. OBSERVE (every time Zak edits a draft or gives feedback)
Append one log entry with: date, pillar/post, the specific before → after snippet(s), Zak's stated reason (checklist items or his sentence), and a one-line "what this implies about voice." If he only approved with no change, record `no_change` (that's positive signal too). Keep snippets short — the changed part, not the whole post.

### 2. IMPROVE (run on demand via `/learn-voice`, or after ~5 new entries)
- Scan recent log entries and cluster recurring patterns (phrasings he cuts, structures he adds, words he swaps, length he trims/expands).
- Assign confidence:
  - **P0 — high:** the same pattern appears in **2+ separate edits/sessions.** Strong, repeated signal.
  - **P1 — medium:** appears once but is clearly deliberate.
  - **P2 — low:** a single, ambiguous, or possibly topic-specific change.
- Recalibrate the **voice dimensions (1–10)** if edits consistently push one direction (e.g. he keeps trimming → raise conciseness).

### 3. APPLY
- **P0 →** write the rule into the right section of `voice-profile.md` (DO / DON'T / Substance / Register / Reference writers) and/or add a banned item to `banned-words.md`. Add it to the "Learned rules" changelog with date + evidence. Bump the voice-profile version by 0.1.
- **P1 →** present to Zak: "I noticed X — make it a rule?" Apply only on yes.
- **P2 →** leave archived in the log; do not touch the profile.
- Never silently delete Zak's hand-written rules — refine or append, and log what changed (rollback = revert the commit).

## Banned moves
- Don't invent a rule that isn't grounded in an actual edit/feedback entry.
- Don't auto-apply P1 or P2 — only P0.
- Don't capture one-off **topical** edits (a fact fix, a different example) as **voice** rules. Tag those `non-voice` and skip.
- Don't overwrite the whole voice profile — make surgical edits and keep the changelog.

## Failure modes
- **Thin log** (fewer than ~3 voice edits) → say "not enough signal yet — need a few more edits before I extract rules," and don't force weak rules.
- **Conflicting rules** (a new edit contradicts an existing rule) → surface the conflict to Zak and ask which wins; don't silently flip.
- **Ambiguous edit** (can't tell if it's voice or just this post) → log as P2 and wait for a second instance.
