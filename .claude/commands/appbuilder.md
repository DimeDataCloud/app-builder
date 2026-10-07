# App Builder Command

Invoked by: `/appbuilder [optional: idea in words]`, "run app builder", "build an app", "start app builder", "I want to build a mobile app", "launch app builder"

---

## On Invoke — Check for a Prior Session First

Before asking anything, check your project notes for any in-progress App Builder context: a prior locked sentence, research notes, partial concept work, or prior app ideas.

If found: surface it in one line — "Found a prior session: [one-line summary of what was being built]. Resume from where we left off, or start fresh?" Wait for the user to decide before proceeding.

If no prior session (or user chooses fresh): read `CLAUDE.md`, then start Phase 1 immediately.

---

## The Rule

**Never ask one question when two or more can be asked simultaneously.** Questions and research always run in parallel. Never fire a broad search with no target — wait until there's a named concept or category.

---

## Phase 1 — Intake

**Ask all 5 of these questions at once** (batched, single message — they're all independent, no question depends on another):

1. Do you have an app idea already, or are we finding one from scratch?
2. Describe it in one sentence if you have one: who uses it and what problem does it solve?
3. Consumer app (individuals download from App Store) or B2B mobile (enterprise teams, field workers)?
4. Have you seen any similar apps that do part of this? Name them if you can.
5. Any hard constraints — things you won't build, API or subscription costs to avoid, hard deadlines?

**Research timing:**

- If a concept or category was in the `/appbuilder` args when invoked: run searches immediately in the same response before presenting Phase 1 questions, so findings are ready for Phase 2
- If no args: run searches after Phase 1 answers arrive, before composing Phase 2 — not before
- Either way: check your project notes for prior app ideas, research notes, or competitor context on anything mentioned
- Never run "what's popular on the App Store" type searches with no target category — wait for signal

**Parallel searches to run (when there's a target):**
- App Store + web: competitors in the category, their pricing, top review complaints, last-update dates
- Reddit / forums: pain threads for the specific problem
- Check your project notes: prior research on this category or app type

---

## Depth Tools Offer (after Phase 1, before Phase 2)

After Phase 1 answers arrive and a concept or category is identified: offer the three depth tools before proceeding to Phase 2. Present as one batched offer — not three separate questions.

> "Before I score this — three research tools available that make Phase 2 sharper:
>
> - **Industry Download** — full competitor landscape, what users pay, App Store gaps in this space (runs silently, saves the report)
> - **Ride-Along** — a day in the life of your target user; surfaces hidden friction that scoring alone misses
> - **Money Map** — filters all the friction down to the one problem worth building
>
> Run any of these now, or skip straight to scoring?"

Wait for their answer. If they choose one or more: invoke the matching skill(s), run them, then proceed to Phase 2. If they skip: go straight to Phase 2.

Do not offer these if the user already has a specific locked concept and just wants to get to the blueprint fast — read the room.

---

## Phase 2 — Sharpen + Score

Synthesize Phase 1 answers + research. Then:

**If the user has a specific concept (answered Q1-Q2 with an idea):**

Present a sharpened version of their concept (sharper sentence, clearer audience). Identify 1-2 variations worth comparing only if research surfaced a meaningfully different angle. Ask:

1. Here's the sharpened version: [concept sentence]. Does this capture it, or does the angle need adjusting?
2. [Only if an alternative is worth considering]: Here's an adjacent angle the research surfaced: [alt]. Worth scoring this against yours, or lock in your idea?

**If no idea (scratch path — answered Q1 "from scratch"):**

Present 2-3 candidate concepts built from research + the user's interests and constraints from Phase 1. If research returned no signal (no competing apps, no complaints), generate candidates from first principles using the user's Phase 1 answers; note the research gap explicitly.

Ask:
1. Which of these resonates most? What feels off about the others?
2. Anything you'd add or remove from the strongest one?

**Research to run during Phase 2 (multiple parallel searches in the same response turn):**

Now that we have a target category:
- Deep dive on the 1-2 leading concepts: App Store review complaints on each competitor, Reddit/forum pain threads, download estimate proxies (review count × ~100 as rough proxy)
- Score Demand (1-5) and Differentiability (1-5) for each using live findings
- Pull competitor last-update dates — recency signals whether the space is active or stale

---

## Phase 3 — Lock + Launch

Present the full scorecard: each candidate concept with all 4 gate scores (Demand / Buildability / Differentiability / Passion) and the one-line research finding anchoring Demand and Differentiability.

Gate ownership:
- **Demand**: Claude scores from research findings
- **Buildability**: Claude scores from RN/Expo feasibility assessment
- **Differentiability**: Claude scores from App Store/web competition analysis
- **Passion**: User scores — ask directly: "How much do you actually want to work on this for 90 days?"

**If two candidates are within 2 points of each other:** Invoke the preference tiebreaker before asking for confirmation — "Scores are tied. Which one do you most want to work on for 90 days? That one wins."

**Ask these two questions at once:**

1. Does the winning score reflect reality, or does a gate need adjusting? (Tell me which one and why — e.g., "Demand should be higher, I've seen real complaints about this.")
2. Here's the locked sentence: [sentence]. Does this capture exactly what you're building?

**If the user adjusts anything:** Revise the score or sentence accordingly, present the updated version, confirm once more. Loop until both answers are yes — no limit on iterations.

**On both confirmed:**

Output exactly: "Locked: [sentence]. Launching blueprint..."

Then immediately invoke `mobile-blueprint` with the locked sentence as input. No pause. No "would you like to proceed?" No offer.

After `mobile-blueprint` finishes (spec written + `[app-slug]-preview.html` written to disk + Playwright polish script output), offer the next steps:

> "Blueprint done. Preview is at `[app-slug]-preview.html`.
>
> **Next — Playwright polish loop:** Run `node [app-slug]-polish.js`, paste the output or screenshots here, and I'll patch the HTML until every screen passes. Repeat until it looks publishable.
>
> **Or — GTM tools when you're ready:**
> - **Discovery Script** — exact questions to ask real users (consumer validation) or enterprise buyers (sales calls)
> - **Closer Deck** — 6-slide HTML presentation for beta launch or enterprise close
>
> What's next?"

If they want the Playwright loop: run `[app-slug]-polish.js` with Playwright, review output and screenshots, patch the preview HTML, rerun. Iterate until the user confirms every screen looks right.

If they want GTM tools: invoke the matching skill immediately.

---

## Final Step — Master Knowledge File

After all chosen tools have run (blueprint done + any GTM tools complete + Playwright polish loop finished), generate and write `[app-slug]-master.md` to disk. Do this automatically — do not ask.

This file is the single source of truth for the entire session. It contains:

**1. Locked Concept**
The final locked sentence and the gate scores (Demand/Buildability/Differentiability/Passion — each /5, total /20) that validated it.

**2. Market Research**
Key findings from any depth tools run (industry download, ride-along, money map). If none were run, pull the Demand and Differentiability evidence from the Phase 2 scoring research. Bullet points — interpreted findings only, no raw dumps. Include competitor names, top review complaints, and App Store gap.

**3. Full Build Spec**
All 13 sections of the blueprint verbatim. This is the build document.

**4. GTM Strategy**
If discovery script was generated: summarize the top 3-5 questions and the close strategy (beta invite or deployment proposal).
If closer deck was generated: state the deck file name and the key hook line from slide 1.
If neither was run: leave this section as "GTM tools not run this session."

**5. Session Knowledge**
Any non-obvious findings, decisions made, alternatives rejected, and constraints surfaced during the session. Things that would be lost if only the spec were saved. Format as a bullet list — one insight per bullet, plain language.

**Format:**

```
# [App Name] — Master Build File
Generated: [date]
Locked sentence: [sentence]

## Gate Scores
Demand: [score]/5 — [one-line evidence]
Buildability: [score]/5 — [rationale]
Differentiability: [score]/5 — [one-line evidence]
Passion: [score]/5 — [user's stated reason]
Total: [total]/20

## Market Research
[Bullet points from depth tools or Phase 2 research]

## Build Spec
[All 13 sections verbatim]

## GTM Strategy
[Discovery script summary or closer deck summary, or "not run"]

## Session Knowledge
[Bullet list of non-obvious findings and decisions]
```

Tell the user: "Master file written to `[app-slug]-master.md`. This file contains the full spec, research, GTM strategy, and session knowledge — everything needed to hand off or resume this build."

---

## Guardrails (enforce silently throughout)

- App Store policy-blocked concepts: medical device claims, unlicensed financial advice, gambling without license, carrier-level VOIP — catch when mentioned, redirect to an alternative framing. Don't lecture upfront.
- "Everyone" is not a user — push toward a specific person with a specific problem
- "It's like [existing app] but better" is not a differentiator — push toward the specific gap
- Never present a concept that requires hardware BLE, ARKit as the core mechanic, or native carrier APIs as the primary feature
