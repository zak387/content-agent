# RAW — Value Post: "Your first newsletter tech stack" — 2026-W25

> Working raw file. Original draft + deepening (Joe Rogan-style interview) BEFORE rewriting. Don't draft until rich.

## Original draft (verbatim, lightly)
For an influencer/creator trying to get their first newsletter edition out but debating the tech stack, here's where to start.
1. **ESP (email sending platform)** — to send & host. Save time, consider only two: **Kit** and **beehiiv**.
   - Kit: great at workflow automations (remove cold subscribers every 30 days, welcome emails, add lead-magnet requesters to the newsletter). Great team & support.
   - beehiiv: lets your newsletter rank on Google + AI search; rich sponsor network to monetize early.
2. **Something to write & design.**
   - First instinct = dump into ChatGPT/Claude. Seems easy, but content ends up sounding like AI and doesn't capture your voice.
   - Instead: have AI ASK YOU questions to expand and enrich the content.
   - Design: get a ChatGPT subscription, have it produce graphics for the edition.
(Post trails off at design.)

## Gaps / where it's thin
- No clear DECISION rule: Kit vs beehiiv for a first-timer — which to pick?
- The "have AI interview you" method is the gold (it's literally Zak's own method) but underdeveloped — needs a concrete example.
- "Remove cold subscribers every 30 days" sounds counterintuitive — needs justification.
- Design via ChatGPT graphics is thin / possibly janky — be honest.
- No cost angle (first-timers care: can I do this free?).
- Missing the #1-mistake / contrarian core.

## Deepening (Joe Rogan-style Q&A)

### Round 1 (verbatim)
1. **Kit vs beehiiv, pick one:** gun to my head, I'd go with **Kit.**
2. **The AI-interview method (the differentiator):** "We don't want the AI to do the writing, the brainstorming, and the thinking for us. We want it to ask us the questions, because **the question is the pickaxe for the mind.**" Contrarian belief: you can't have AI do the writing for you. Have it ask you questions / interview you. Have it **act as Joe Rogan or a good interviewer** and ask a bunch of questions that expand on the content/idea you've produced, even if it's a rough idea.
3. **Why it works:** "You don't want AI to do the thinking for you, you want it to amplify your notes, thoughts, and reflections." (Or work with us at Sawa, where we write newsletters for creators — soft CTA.)
4. **Cold-subscriber line:** just an example → CUT.
5. **Design via ChatGPT:** "It definitely does the job."
6. **#1 mistake:** creators go "straight into selling." (Park as its own post — Zak wants this post focused on the tech stack, not mistakes.)

### Key lines to feature
- "The question is the pickaxe for the mind."
- "Have AI act as Joe Rogan and interview you" — meta + memorable.
- Soft CTA: or work with us at Sawa.

### Round 2 (verbatim)
1. **Getting people on the list:** the ESP gives you a signup form. To scale collection, use **ManyChat**. In the early days it's optional, not mandatory. (ManyChat is the tool.)
2. **AI-interview how-to:** DON'T reveal the exact setup here. **Tease it and prompt people to comment** if they want a tactical part-two. (Gated follow-up.)
3. **Deliverability / batching (he flagged "do more research"):** for someone who already has a list, break the send into batches. Don't send a first edition to all 10,000 at once; split into 4–5 batches to protect deliverability.
4. **Bare-minimum MVP stack:** an ESP + a way to make your newsletter known (stories, reels, posts). That's it.
- (Skipped: the ChatGPT-design specifics — keep design light, "it does the job.")

### Deliverability research (2026-06, cited) — for the batching section
- **His instinct is right** — it's about sender reputation. Mailbox providers judge the engagement of the first slice of each send.
- **If you already have a list:** send to your **most-engaged subscribers first**, then ramp in batches over days (e.g., 25% → 45% → rest). Don't blast a big or stale list at once; don't spike volume (a 5x spike undoes weeks of trust).
- **The real first-timer gotcha (most important):** authenticate your domain — **SPF, DKIM, DMARC** — before you send one email, or you land in spam. Gmail/Yahoo (Feb 2024) require all three above 5k/day, plus one-click unsubscribe. Kit/beehiiv walk you through this.
- **Beginner-from-zero nuance:** on Kit/beehiiv shared infrastructure most of this is handled. A true first-timer just needs to authenticate, add the unsubscribe, and not import + blast a huge cold list. Batching mostly matters once you have size/an old list.
- Sources: SMTP2GO warmup guide; Klaviyo/Iterable re-engagement; Mailjet SPF/DKIM.

### STATUS: rich enough to draft.
Structure: hook → ESP (pick: Kit; beehiiv alt) → how people get on the list (form, ManyChat optional) → write it (DON'T let AI write; have it INTERVIEW you — "the question is the pickaxe for the mind"; tease part-two CTA) → design (ChatGPT, does the job) → deliverability note (batch big/old lists, authenticate your domain) → MVP line (ESP + a way to make it known) → soft Sawa CTA.
