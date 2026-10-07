---
name: mobile-industry-download
description: Advanced understanding tool for mobile app markets. Use when someone names a mobile app category, target user type, or competitive space and wants genuine deep comprehension — not just enough to pitch, but enough to think like an insider. Covers the market mechanics, existing mobile app landscape (ratings, downloads, review complaints, gaps), what users pay for, where pain lives, and where opportunity exists. Runs silently by default — saves the report, does not output unless asked. Trigger phrases include "mobile industry download", "download the [category] app market", "research [category] apps", "understand the [niche] mobile space", "what apps exist for [audience]", "competitive research on [app category]".
---

# Mobile Industry Download

Advanced understanding of a mobile app market. Not "enough to build" — genuine insider comprehension of who's in the space, what users love and hate, where the money is, and where the gaps live.

## What This Skill Does

**Input:** A mobile app category, target audience, or competitive space.

**Output:** Deep market intelligence across 13 sections — how the market works, who the users are, what apps already exist and how they're reviewed, what users pay, where the real pain lives, and where opportunity exists for a new app to win.

You go from "I want to build in this space" to knowing exactly what you're up against, what's already been tried, and what the users wish existed.

---

## How to Use This Skill

### Default Behavior: Silent Mode

**Run silently. Do not output the report to the user.**

1. **Scope it.** "Productivity apps" is too broad. "Habit tracking apps for remote workers" is right. "Time tracking apps for freelancers" is right. The narrower the scope, the more useful the output.
2. **Research first. Always.** Search App Store reviews, Reddit communities, YouTube app review videos, Twitter/X complaints, industry blogs, and competitor app pages. Do not generate generic answers from training data.
3. **Build the full report internally.** All 13 sections. Hold it in context.
4. **Save the report.** Write the completed report to `research/[topic-slug]/YYYY-MM-DD-mobile-industry-download.md` (or wherever your project keeps research notes).
5. **Confirm silently.** Tell the user one line only: "Mobile industry download on [topic] complete — saved. Ask me anything or say 'show report' to see the full output."

### Override: Show Output

If the user says "show me", "show report", "output the download", "what did you find", or similar — output the full report.

---

## Output Structure

Deliver in this exact order. Use markdown headers. Vague is useless — be specific.

---

### 1. What This Market Is (Real Definition)

Cut through the category label. Define this mobile app market honestly.

- What kind of apps actually live here? What do they do?
- Who are the real users — not the marketing persona, the actual people downloading
- What problem is the market built around at its core?
- What does "success" look like for a user in this space? (not downloads — what does the user actually achieve)
- What does the marketing say vs. what practitioners (users) know?

---

### 2. Mobile App Landscape

This section is the most important adaptation from the standard industry download. Research this thoroughly.

For each of the top 3-5 apps in this space:

| App Name | Rating | Est. Downloads | Last Updated | Key Complaints | Key Strengths |
|---|---|---|---|---|---|
| [Name] | [X.X stars] | [~Xk-Xm est.] | [Month Year] | [Top 1-2 complaints from reviews] | [What users praise] |

**Download estimate method:** Review count × ~100 is a rough proxy. Flag this as an estimate. A 1,000-review app likely has 50K-500K downloads. Use ranges, not precise numbers.

**Recency signals:** An app last updated in 2020 with no new reviews is a different competitive signal than one updated last month. Note this explicitly.

**What to look for in reviews:**
- Recurring 1-3 star complaints (these are the gaps a new app can fill)
- What users switched from, and why
- What they say the app is still missing
- Whether users mention specific missing features repeatedly

---

### 3. How the Market Actually Works

Mechanics of this app category:

- What is the core interaction loop? What does the user do every session?
- How often do users engage? (daily, weekly, situational)
- What makes users stick vs. delete? (what drives retention in this category)
- What are the known failure modes? (why apps in this space get deleted or abandoned)
- How does this category compare to web alternatives — why does mobile win here?

---

### 4. Who the Users Are

Not demographics — behavioral profile:

- What triggers someone to download an app in this category?
- What are they doing before they find this app? (the workaround)
- What does their usage pattern look like? (daily check-in, occasional reference, task-based)
- Why do most users eventually churn? (the pattern behind "I deleted it after 3 weeks")
- What makes a small subset become power users?

---

### 5. Business Model and Economics

How money flows in this category:

- Dominant monetization: freemium / subscription / one-time purchase / IAP / ad-supported
- Typical pricing tiers: what users accept vs. what feels expensive for this category
- What conversion rate from free to paid looks like in this space (1-5% is typical for freemium)
- What drives upgrades: feature gates, usage limits, cosmetics?
- App Store take rate impact: 30% cut on subscriptions (15% after year 1) — does this affect pricing?
- Annual vs. monthly subscription dynamics (annual locks in retention; monthly bleeds)

---

### 6. What Users Already Pay For

The tools, apps, and subscriptions this user type currently buys. With real pricing where findable.

| App/Tool | Monthly Cost | What It Does | Top Complaint |
|---|---|---|---|
| [specific name] | $X/mo | [what it solves] | [why people still complain] |

This section answers "would they pay for something new?" in one glance.

---

### 7. Pain Points Ranked by Severity

The 5-8 most common frustrations in this market. Ranked by how often they appear in reviews and how acutely users feel them.

For each:
- The pain in the user's exact language (quote if possible from reviews/forums)
- What it costs the user (time wasted, goal not achieved, money lost)
- Why existing apps don't fix it
- Whether this pain is growing, stable, or shrinking

Format:
> **Pain:** "The sync breaks every time I switch devices and I lose everything" (App Store 1-star review language)
> **Cost:** ~2 hours/month rebuilding lost data; erodes trust in the app
> **Why unsolved:** Most apps sync through proprietary backends, not conflict-free local-first architecture
> **Trend:** Growing — more users on multiple devices

---

### 8. What Keeps Users Up at Night

The 3-5 deepest fears this user type has — things that would make them switch apps instantly if triggered. Written in their language.

Not the polished concerns they'd list in a survey. The actual anxieties. Pull from 1-star reviews, Reddit rants, Twitter complaints.

---

### 9. Language Dictionary

How insiders in this app category actually talk. Pull from real App Store reviews, Reddit threads, YouTube comments.

**Core vocabulary** — 10-15 terms users use daily with precise meaning (how practitioners use them, not dictionary definitions)

**Pain phrases (verbatim)** — real quotes from reviews describing frustration ("I tried to X but it...")

**Success phrases (verbatim)** — real quotes describing what users celebrate ("Finally an app that...")

**Red flags** — things that trigger immediate 1-star reviews or deletes in this category

---

### 10. How the App Store Dynamics Work Here

Category-specific App Store intelligence:

- Top keywords in this category (what users search for)
- What the top-ranked apps have in common (rating floor, review count threshold, update frequency)
- Whether this is a category with stable rankings or frequent churn
- What triggers a featured placement (if this category gets featured)
- Rating sensitivity: do small rating drops hurt downloads in this category?

---

### 11. Market Gaps and Opportunities

Specific gaps — apps that don't exist, features that are consistently missing, audiences that are underserved. This is where opportunity lives.

For each gap:
- What is missing (specific, not "better UX")
- Who suffers most from its absence
- Why hasn't it been built? (technical, market size, distribution problem)
- Rough opportunity size

---

### 12. Regulatory and Platform Constraints

Rules that affect apps in this category:

- App Store policies that apply (age rating requirements, data privacy rules, specific category restrictions)
- Any regulatory considerations (HIPAA, COPPA, financial advice disclaimers, etc.)
- Data privacy requirements (what user data this category typically collects, what disclosures are required)
- Platform differences: iOS vs Android dynamics in this specific category

---

### 13. Go-to-Market Intelligence (Include When Relevant)

Include this section when the context is a launch or product strategy decision. Skip when the download is purely for understanding.

- Where these users gather (specific subreddits, Facebook groups, Discord servers, YouTube channels)
- How successful apps in this category first found their users
- What proof points users need before they'll pay (free trial, specific feature, specific social proof)
- ASO (App Store Optimization) angle: what keywords and review patterns drive installs in this category

---

## Research Standards

**Non-negotiable:**
- App Store ratings and review complaints must come from actual research — no fabrication
- Download estimates must be labeled as estimates with the methodology noted
- User quotes must be from actual reviews or forum posts, not synthesized
- Pain points must be validated by real sources — not generic "users might want X"

**Where to look:**
- App Store: search the category, read top apps' most recent 1-3 star reviews
- Google Play: same approach
- Reddit: subreddits where this user type discusses the category
- YouTube: app review videos, comments on "best [category] app" videos
- Twitter/X: searches for "[app name] complaint" or "[category] app frustrating"
- ProductHunt: launch pages and comments for apps in this space
- App Store review aggregators: AppFollow, Sensor Tower (free tier), AppFigures

**What to avoid:**
- Vendor marketing copy
- Generic "AI overview of the category" without real data
- Press releases
- Academic papers on mobile app usage (too abstract)

---

## Scope Check Before Running

If the input is too broad, push back:

- "Productivity apps" → too broad; ask: what kind of productivity, for whom, in what context?
- "Health apps" → too broad; ask: fitness, mental health, nutrition, medical?
- "Social apps" → too broad; ask: what social interaction? for whom?
- "Habit tracking apps for remote workers" → specific enough, proceed

The narrower the scope, the more useful the output. A 13-section report on "shift scheduling apps for independent restaurant owners" is 10x more useful than one on "business apps."
