# Skill: Scrub AI Tells (Voice Check)

## Purpose
The final quality gate. Take a near-final draft and strip AI tells, enforce the voice profile and banned-words list, and confirm it sounds like the operator wrote it.

## Input
- A draft post (any pillar).
- `clients/<client>/voice-profile.md` and `clients/<client>/banned-words.md`.

## Output
- A cleaned draft.
- A short note listing what was changed and why (so the operator learns the pattern).
- A confidence flag: PASS / PASS WITH NOTES / FLAGGED.

## Process
1. Read the draft aloud in your head. Does it sound like a human who's done this for years, or like an assistant?
2. Run the AI-tell checklist and fix each hit:
   - Em-dash overuse → replace most with periods or commas. Allow at most one per post.
   - Rule-of-three lists used for rhythm ("faster, cleaner, smarter") → break the pattern.
   - "It's not just X, it's Y" / "isn't about X, it's about Y" antithesis → rewrite plainly.
   - "In today's world / in a world where / in the age of" openers → cut.
   - "delve, leverage, unlock, harness, elevate, navigate, tapestry, testament, realm, landscape, foster, robust, seamless, game-changer, supercharge" → replace with plain words.
   - Empty hedges: "It's worth noting," "Needless to say," "At the end of the day."
   - Forced symmetry / balanced clauses that no human would speak.
   - Overuse of "—" emoji-bullets or perfectly parallel bullet lists when prose is more natural.
   - Generic CTA ("What do you think? Comment below!") → make it specific or cut.
3. Enforce `banned-words.md` (operator's personal no-list).
4. Check voice profile: persona, length-by-pillar, formatting-by-content, emoji/hashtag level (few & purposeful).
5. Confirm US English spelling.
6. Verify every factual claim/number traces to reference material. Any that don't → FLAG.
7. Output the cleaned draft + change note + confidence flag.

## Banned moves
- Do NOT rewrite the post's substance or change its point — this is a polish pass, not a redraft.
- Do NOT remove the operator's distinctive phrasings just because they're informal.
- Do NOT add hashtags/emoji beyond the "few & purposeful" level to seem engaging.
- Do NOT pass a draft with an unverifiable stat as PASS — it must be FLAGGED.

## Failure modes
- Draft is fundamentally off-voice (not fixable by polish) → return FLAGGED with a one-line diagnosis and send it back to the draft stage, don't band-aid it.
- A required reference (e.g. a real number) is missing → FLAG and ask the operator rather than inventing.
