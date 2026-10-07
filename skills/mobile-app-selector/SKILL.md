---
name: mobile-app-selector
description: Walk someone from "I want to build a mobile app" to one locked concept sentence covering both the audience and the idea — sharp enough to hand to mobile-blueprint and start building. Runs in two phases: Phase 1 locks the audience (consumer vs B2B, specific user type), Phase 2 locks the concept (what you build for them). Scores each concept against 4 gates — Demand, Buildability, Differentiability, Passion — with live App Store and web research on the two objective gates. Breaks ties with preference, writes the locked sentence, and immediately launches mobile-blueprint. Use this skill when someone wants to pick, validate, lock, or narrow down a mobile app idea; says "mobile app selector", "lock my app idea", "what should I build", "who should I build for", "run the app selector", "validate my app concept", or is stuck between knowing they want a mobile app and not knowing what exactly to build. Pre-step to mobile-blueprint.
---

# Mobile App Selector

Take someone from "I want to build a mobile app" to one specific locked sentence — the audience and the concept in a single breath. This is the decision engine. By the end, the sentence is handed to mobile-blueprint and building starts.

## The whole point (say this early)

**Audience first. Concept second. Build third.** This skill settles WHO it's for and WHAT it does. The detailed software design — screens, data model, build order — comes next in mobile-blueprint.

A locked mobile app concept sounds like: "I am building a habit-tracking app for remote workers that replaces their scattered notes and calendar with one daily check-in." That sentence shape is the deliverable. Everything before it is elimination.

Why this matters fast: the App Store has millions of apps. The ones that find users are specific. Generic loses to specific every time. A concept that's "for everyone" finds no one.

## How to run it (conversational, one question at a time)

This is a guided conversation, not a form dump. Ask one question, react to the answer, then ask the next. One sentence of reaction, then move. No lectures between questions.

Use `ask_user_input_v0` for discrete choices (consumer vs B2B, gate scores). Keep the surfacing questions open — they need real sentences, not buttons.

---

## Phase 1 — Audience Qualification

Three questions. Not a scoring exercise — a qualification check. The goal is to confirm a specific user type and a gut-check that this person is worth 90 days.

**Q1: Consumer or B2B mobile?**

> "Before we get into the idea — who's downloading this app? Regular people from the App Store, or employees at a company (field workers, service teams, enterprise staff)?"

This single answer changes everything downstream: monetization, distribution, pricing, how you'll reach them, what success looks like. Get it confirmed before moving.

**Q2: Who specifically?**

> "Describe the person using this app in one sentence. Their role, their daily context, and the problem they're dealing with. Not 'anyone who wants to be productive' — one specific person."

If they give a vague answer: push once. "Give me a specific person — what do they do, where are they, what's frustrating them?" If it's still vague after two pushes, accept it and note it as a gate 3 weakness to sharpen in Phase 2.

**Q3: Gut check.**

> "Would you want to spend 90 days building for this person and taking their feedback calls? Not 'could you' — would you?"

This is Passion gate Phase 1 version. A clear yes moves forward. A hesitant "I guess" is worth flagging: "That hesitation matters — we can adjust who you're building for right now, before we lock anything."

**Guardrail (apply silently as answers arrive):**

If the audience described falls into a policy-blocked category — medical device users, financial advice recipients, gambling users without licensing — catch it and redirect: "That audience runs into App Store policy constraints around [X]. What's the underlying thing they need? We can find a framing that works." Don't announce the guardrail before it's triggered.

**Output:** A confirmed audience sentence: "I am building for [specific user]." This feeds directly into Phase 2.

---

## Phase 2 — Concept Lock

**Do NOT re-ask whether they have an idea or are starting fresh.** Phase 1 surfaced this. If an idea emerged in Phase 1, sharpen it. If no idea exists, surface candidates from research.

### If an idea came from Phase 1:

Sharpen it into a precise locked sentence. Run the 4 gates. If the concept scores 14 or below (workable-or-worse), present one research-grounded alternative for comparison.

### If no idea yet:

Run research first (see `references/research-playbook.md`). Surface 2-3 candidate concepts built from what the research found + the user's Phase 1 constraints and interests. If research returns no signal, note the gap and generate candidates from first principles using the audience and any constraints.

Score the top candidates. Score all four gates for each.

---

### The 4 Gates (1-5 each, total /20)

**Gate 1: Demand**

Does real, painful demand exist for this specific app from this specific user? Not "people might use it" — are there active complaints about the current situation, and are users already spending on adjacent tools?

- **5** — Active forum threads, App Store reviews with recurring complaints about the exact problem, users clearly spending on something adjacent ($2+/month IAP or competitor subscription)
- **3** — Some complaints, sparse. One competitor with moderate reviews. Problem recognized but not urgent.
- **1 (VETO)** — No community discussion. No complaints anywhere. No competitors. Silence.

Research required before scoring. See `references/research-playbook.md`.

**Gate 2: Buildability**

Can Claude build a working MVP of this with React Native + Expo in 1-3 weeks? No blocked features required?

- **5** — Pure RN/Expo app: UI, Supabase backend, standard APIs (Stripe, OpenAI, push notifications). Camera, GPS, Expo sensors all fine.
- **3** — Feasible but complex integration: real-time features, complex state, or multiple API orchestrations. Still buildable, just more sessions.
- **1 (VETO)** — Requires ARKit/ARCore as the core experience, hardware BLE/NFC as the primary mechanic, carrier-level VOIP, medical device APIs, or on-device ML model training.

Judgment gate — no web research needed. Evaluate based on what the concept requires.

**Gate 3: Differentiability**

Is there real white space in the App Store, or is this a dominated market with well-reviewed incumbents?

- **5** — Existing apps are old (last updated pre-2021), generic (built for everyone, not this audience), or poorly reviewed (under 3.5 stars with recurring complaints about exactly the gap this app fills)
- **3** — Competition exists and works reasonably well, but there's a persistent blind spot or an audience-specific gap no one has targeted
- **1 (VETO)** — A well-funded, well-reviewed, dominant app already serves exactly this audience for exactly this problem

Research required before scoring. See `references/research-playbook.md`.

**Gate 4: Passion**

Will you maintain, iterate, and actually talk to users about this for 90+ days without dreading it?

- **5** — Genuinely excited. Naturally curious about this user's problems. Would find beta test calls energizing.
- **3** — Interested but not passionate. Would do it. Wouldn't love it.
- **1 (VETO)** — Would dread every feedback call. Building it because it "seems smart," not because you care about the problem.

Judgment gate — scored by the person building, not by Claude.

---

### Reading the Score

- **17-20** — Build it. Green light. Commit and move.
- **13-16** — Workable. Watch the gate(s) scored 2 or below — that's the risk you're carrying in.
- **9-12** — Fix a gate first. Real weaknesses exist. Reshape the concept or score a different candidate.
- **<9** — Pick another idea. Too many weak gates.
- **Any gate = 1** — Automatic veto regardless of total. Fix it or move on.

### Preference Tiebreaker

Score all candidates first. Let the math do the first cut.

If one candidate scores 3+ points higher: that one wins, even if another feels more exciting.

If candidates are within 2 points: ask once — "Which one do you most want to work on for 90 days?" That one wins. No re-litigation.

---

## Step Six — Write the Sentence

**"I am building a [type] app for [specific user] that [solves specific problem]."**

This sentence must pass the stranger test: someone in the target user category hears it and immediately says "yeah, those people exist and that's a real problem."

Right: "I am building a shift-scheduling app for independent restaurant managers that replaces their WhatsApp group with a one-tap approval system."

Wrong: "I am building a productivity app for people who want to get things done." (No specific user, no specific problem.)

If it doesn't pass the stranger test, sharpen it before confirming. Push on the user (more specific), the problem (more costly), or the solution shape (more concrete) until it does.

---

## Auto-Launch

Once the sentence is confirmed, output: **"Locked: [sentence]. Launching blueprint..."**

Then immediately invoke `mobile-blueprint` with the locked sentence as input. No pause. No offer. No gap.

---

## Guardrails

- One question at a time in the conversational flow — this is not a form dump
- Phase 1 must complete before Phase 2 starts — never score a concept before confirming the audience
- Both Demand and Differentiability gates require real research before scoring — never score from instinct or general knowledge on these two
- The stranger test is not optional — if it fails, keep sharpening
- Preference never opens — it only breaks a tie within 2 points, always after scoring
- No em dashes in any PDF or structured output (house style): use period, comma, colon, parentheses, or spaced hyphen
