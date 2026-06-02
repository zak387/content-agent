---
description: Extract voice rules from Zak's recent edits/feedback and apply high-confidence ones to the voice profile.
argument-hint: "[client] (default: zak) [--apply to auto-apply P0]"
---

# Learn Voice

Run the improve+apply pass of `skills/learn-voice.md` for client `$1` (default `zak`).

1. Read `clients/<client>/voice-learning-log.md`, `voice-profile.md`, `banned-words.md`.
2. Cluster recurring patterns across recent log entries. Assign P0 / P1 / P2 confidence.
3. Recalibrate the 1–10 voice dimensions if edits consistently push a direction.
4. Apply:
   - **P0** → write into `voice-profile.md` (right section) and/or `banned-words.md`; add to the "Learned rules" changelog with date + evidence; bump voice-profile version by 0.1.
   - **P1** → list them and ask Zak which to promote; apply only on approval.
   - **P2** → leave in the log.
5. Print a summary: rules applied, rules proposed, dimension changes.
6. Append a line to `DECISIONS.md` for any P0 rule applied.

If there's not enough signal (fewer than ~3 voice edits), say so and stop — don't force weak rules.
