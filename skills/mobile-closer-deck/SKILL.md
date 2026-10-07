---
name: mobile-closer-deck
description: Generates a complete, self-contained HTML presentation for launching a mobile app to beta users or closing an enterprise mobile deployment contract. Takes the locked app concept and either a launch brief (B2C mode) or a discovery call transcript (enterprise mode) and outputs a 6-slide HTML file you open in Chrome and present immediately. B2C mode frames the App Store opportunity, target user pain, concept preview, traction plan, PMF metrics, and launch timeline. Enterprise mode uses the same 6-slide structure with the prospect's numbers, gap math, deployment proposal, and performance guarantee. Trigger phrases include "build my closer deck", "mobile launch deck", "create the presentation for [app]", "build the sales deck for this mobile client", "turn this discovery call into a presentation", or any request to generate a launch or close deck for a mobile app.
---

# Mobile Closer Deck

Turn a locked app concept or a discovery call into the exact HTML presentation that either launches your mobile app to beta users or closes an enterprise deployment contract. A real, ready-to-present file — open in Chrome, share screen, present.

## What This Skill Does

**Input:** The locked concept sentence (always required) + either:
- B2C mode: the target user, the App Store opportunity, and a traction plan
- Enterprise mode: a discovery call transcript or detailed notes with the prospect's numbers

**Output:** A complete, self-contained HTML presentation file. 6 slides. Keyboard navigation. Professional styling. Open in Chrome and present immediately.

This is not a slide outline. Not a markdown summary. A working file.

---

## Two Modes

Choose based on what you're building toward:

**B2C Launch Mode** — Pitching your app for beta users, app launch, early adopter recruitment, or presenting at a demo event. The audience is individual users or people who will help spread the app.

**Enterprise Mode** — Closing a B2B mobile deployment contract. The audience is a business decision-maker who just finished a discovery call and needs to see the dollar math before signing.

---

## The 6-Slide Structure

Every closer deck has exactly 6 slides. Don't add. Don't subtract. Don't reorder.

---

### B2C Launch Mode — Slide Descriptions

**Slide 1: The Problem**
The target user's specific pain — in their language. Not generic productivity frustration. The specific thing they abandon, the specific workaround they hate, the specific goal they fail to achieve. Use real language from App Store reviews or forum research if available.

**Slide 2: Why Mobile**
Why this problem is solved on a phone and not a web app. What makes the phone the right format — always with you, context-aware, location-aware, camera-capable, instant-notification-capable. This slide justifies the format choice.

**Slide 3: The App**
The locked concept sentence, large and centered. Then 3-5 bullet points describing what the MVP does — framed as outcomes the user achieves, not features. No tech jargon. End with: "Available on iPhone. [Target launch date or 'Coming soon']."

**Slide 4: Traction Plan**
How the first 100 users find this app. Specific channels and tactics — App Store Optimization (ASO) keywords, specific Reddit communities, specific Facebook groups, relevant YouTube creators, specific Twitter/X communities, beta tester recruitment approach. Not generic "social media." Real channels where this specific user type already gathers.

**Slide 5: How We'll Know It's Working**
3 specific metrics that signal product-market fit for this app. Pick from: Day 7 retention rate (target >25%), daily active users, streak completion rate, average sessions per week, App Store rating after 50 reviews, specific user-defined goal completion rate. Each metric gets: the number to hit, and why that number means the app is working.

**Slide 6: The Plan**
A clean timeline from now to launch. Broken into: Build (sessions 1-X, X weeks), Beta (test with [N] users, X weeks), Launch (App Store submission, target date). Close with one sentence on what you're asking for: "Looking for 20 beta testers. Reply to join the list."

---

### Enterprise Mode — Slide Descriptions

**Slide 1: Where They Are Today**
The prospect's current operational state, in their numbers. Big visible metrics from the discovery call: staff count, current tool/workflow, volume of the affected task per week. Not invented — pulled directly from what they said on the call.

**Slide 2: What This Is Costing Them**
Quantify the pain in dollars per month. Use the prospect's numbers from Slide 1 to do the calculation. Be conservative — underestimate, so the math feels safe when they scrutinize it.

**Slide 3: What's Possible**
The new state after the app is deployed. Specific dollar figure: recoverable staff hours × hourly rate, or recovered revenue per month. Use conservative recovery percentages (20-30% is more credible than 80%).

**Slide 4: The Gap**
One visual. Two cards. Left card: today (cost, what's broken). Right card: after deployment (outcome, dollar recovery). This is the slide that closes the deal. The math speaks. Let it land — pause here during the presentation.

**Slide 5: What I'll Build and Deploy**
The offer in their language. Bullet points framed as outcomes for their team ("staff shifts confirmed 60 minutes faster"), not features ("AI scheduling engine"). 4-6 bullets maximum. No tech jargon.

**Slide 6: Investment**
Setup fee + monthly. Frame against the gap from Slide 4. Performance guarantee. Example: "$X to set up, $Y per month. We guarantee [specific outcome] in your first 30 days or we work for free until we do."

---

## Slide HTML Patterns

Use these exact patterns. The shell template comes from the closer-deck asset pipeline. These are the slide-specific injection patterns.

### B2C — Slide 3 Pattern (The App)

```html
<div class="slide">
  <div class="eyebrow">The Solution</div>
  <h1 class="headline">{LOCKED_CONCEPT_SENTENCE}</h1>
  <ul class="bullets">
    <li><span class="check">✓</span><div>{Outcome-framed benefit 1}</div></li>
    <li><span class="check">✓</span><div>{Outcome-framed benefit 2}</div></li>
    <li><span class="check">✓</span><div>{Outcome-framed benefit 3}</div></li>
    <li><span class="check">✓</span><div>{Outcome-framed benefit 4}</div></li>
  </ul>
  <div class="cta">Available on iPhone · {LAUNCH_DATE or "Coming Soon"}</div>
</div>
```

### Enterprise — Slide 4 Pattern (The Gap)

```html
<div class="slide">
  <div class="eyebrow">The Gap</div>
  <h1 class="headline">The distance between where you are<br>and <span class="accent">where you could be</span></h1>
  <div class="compare">
    <div class="compare-card">
      <div class="compare-label">Today</div>
      <div class="compare-value">{CURRENT_COST}/mo</div>
      <div class="compare-sub">{Description of current broken workflow}</div>
    </div>
    <div class="compare-card highlight">
      <div class="compare-label">After Deployment</div>
      <div class="compare-value">{RECOVERABLE_VALUE}/mo</div>
      <div class="compare-sub">Same team, better tools</div>
    </div>
  </div>
</div>
```

### Enterprise — Slide 6 Pattern (Investment)

```html
<div class="slide">
  <div class="eyebrow">The Investment</div>
  <h1 class="headline">A <span class="accent">${MONTHLY}/month</span> investment<br>to recover <span class="accent">${RECOVERABLE}/month</span></h1>
  <div class="investment">
    <div class="invest-card">
      <div class="invest-amount">${SETUP_FEE}</div>
      <div class="invest-period">One-time setup · configuration · deployment</div>
    </div>
    <div class="invest-card">
      <div class="invest-amount">${MONTHLY}<span style="font-size:0.5em;color:#888;font-weight:500"> / mo</span></div>
      <div class="invest-period">Ongoing service · month-to-month</div>
    </div>
  </div>
  <div class="guarantee">
    <strong>Performance guarantee:</strong> If we don't deliver {SPECIFIC_OUTCOME} in your first 30 days, we work for free until we do.
  </div>
</div>
```

---

## HTML Output Instructions

1. Use the `closer-deck` asset template shell (same as the original closer-deck skill's assets — reuse the HTML template, CSS, and navigation JavaScript)
2. If this is the first time the template is being used: build a self-contained HTML file with embedded CSS and JavaScript. No external dependencies. Must open offline in Chrome.
3. Populate the 6 slide patterns with the prospect's or app's specific data
4. Save the file as `closer-deck-[app-or-client-name].html`
5. Output the file for the user to open in Chrome

---

## Companion Delivery Script

After the HTML file, output a markdown delivery script the presenter reads from a second screen during the presentation.

```markdown
# Delivery Script — {App or Client Name}

## Pre-presentation
- Open the HTML file in Chrome before the call
- Keep this script on a second screen
- Share the Chrome window, not the script

## Slide 1: [Slide title]
**Say:** "[What to say in 1-2 sentences]"
**Goal:** [What you want them to feel or confirm]

## Slide 2: [Slide title]
**Say:** "[What to say]"
**Goal:** [What you want]

[...repeat for each slide...]

## The close (after Slide 6)
**Say:** [Exact closing line]
**Then:** Shut up. Wait for them to respond first.

## If they hesitate:
[2-3 likely responses and what to say]
```

---

## Guardrails

- Enterprise mode: never invent a dollar figure — only use numbers from the discovery call. If a number wasn't mentioned, flag it for the user to fill in.
- B2C mode: screenshot placeholders are fine for screen previews — note "placeholder screenshot" in the slide. Use real screenshots if the app exists.
- One offer only (enterprise mode) — no three-tier pricing. Three options create decision paralysis on a sales call.
- The performance guarantee (enterprise) must be specific: "If we don't [measurable outcome] in 30 days, we work for free until we do." Never "if you're not satisfied."
- House style: no em dashes anywhere. Period, comma, colon, parentheses, or spaced hyphen only.
- Slide 4 (enterprise — The Gap) does most of the closing. Pause after presenting it. Let the math land. Do not rush to Slide 5.
