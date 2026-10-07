---
name: mobile-money-map
description: Takes everything known about a mobile user type or app category and finds the one painful, specific, Claude-buildable problem worth building a mobile app for. Filters every candidate through the 5 Mobile Problem Types and 3 Hard Filters, then ranks the survivors and picks one. Use after mobile-industry-download and mobile-ride-along to convert research into a decision. Trigger phrases include "mobile money map", "find the problem worth building for [user/category]", "what should I build for [mobile user]", "rank the mobile app opportunities", "which problem is worth solving", or any request to identify the specific problem to target in a mobile app.
---

# Mobile Money Map

Take everything you know about a mobile user and find the one painful, specific, Claude-buildable problem worth turning into an app. One problem. Ranked. Picked. Done.

## What This Skill Does

**Input:** A specific mobile user type, ideally with mobile-industry-download and mobile-ride-along already run on them. Raw research, friction moments from a ride-along, or both.

**Output:** A ranked list of 3-5 specific problems, each filtered through the 5 Mobile Problem Types, the React Native/Expo buildability test, and the recurring-value test — ending with one clear pick and the rationale for why it's the right first target.

By the end, you know exactly which problem is worth bringing into mobile-app-selector.

## Why This Skill Exists

Most people get stuck at "I know my user but I don't know what to build." They've done the research. They've seen the friction. But they can't commit to a single problem because every option looks like it might be the wrong one.

Mobile money map kills that paralysis with hard filters. Most "opportunities" fail at least one of three tests — not painful enough, not buildable with RN/Expo in reasonable time, or not something users need repeatedly. Run them through the filters and only the real opportunities survive.

---

## The 5 Mobile Problem Types

Every problem mobile-money-map surfaces gets categorized into one of five types. These are the only categories worth pursuing for a Claude-built mobile app. If it doesn't fit one of these five, it's the wrong problem.

1. **Task repetition on phones** — Something the user does manually on their phone every day or every week that should be automated or made one-tap. The same sequence of actions, repeated. They'd pay to make it take 5 seconds instead of 5 minutes.

2. **Broken notification/awareness workflow** — The user misses important events because there's no smart alert system. They check too many apps to find out what changed. The cost is missed appointments, missed opportunities, or reactive work instead of proactive.

3. **Outdated or clunky existing app** — The dominant app in the space was built in 2015, has a terrible UI, doesn't support current iOS/Android features, has no AI, and users hate it but keep using it because there's no better alternative. The bar to beat is low.

4. **Data siloed between apps** — The user manually bridges two tools that should talk to each other. They export from one app, paste into another, or screenshot one to reference in another. An app that creates the bridge would eliminate the manual step.

5. **New capability from phone hardware** — Something that wasn't possible before becomes possible because of the phone's camera, GPS, on-device AI, accelerometer, or sensors. The phone unlocks something that a web app can never do as well.

---

## The Three Hard Filters

Every problem must pass all three. Fail any one and it's cut. No soft passes.

### Filter 1: The Pain Filter

Can users describe what they abandon, delete, or give up on without a solution to this problem? Does it cost them time, money, or a meaningful goal?

For consumer apps: "annoying" is not enough. Users must be able to describe a specific thing they stop doing or a specific outcome they fail to achieve because of this problem.

For B2B mobile: Can the business quantify the cost per month? "It's frustrating" fails. "$3,000 a month in miscommunication costs because our staff can't coordinate shifts" passes.

### Filter 2: The React Native/Expo Buildability Filter

Can Claude build a working MVP of this app using React Native + Expo (managed workflow) + Supabase in 1-3 weeks?

**Passes:** UI components, database reads/writes, push notifications, camera access, GPS, Expo sensors, OpenAI integration, Stripe, third-party REST APIs, real-time Supabase subscriptions.

**Fails:** ARKit/ARCore as the core experience, hardware BLE/NFC as primary mechanic, carrier-level VOIP, medical device API integration, on-device ML model training, native modules that require Xcode/Android Studio to modify.

If the core value proposition requires a failed feature — it's the wrong problem. Find the adjacent version that doesn't.

### Filter 3: The Recurring Value Filter

Will users need this repeatedly? Is this a problem that keeps happening? Can this sustain ongoing engagement (daily, weekly, or event-triggered)?

**Consumer passes:** Daily active use potential (habit apps, tracking apps, communication apps), or event-triggered use that happens regularly (travel, fitness events, recurring workflows).

**Consumer fails:** One-time setup, one-time data import, single-use reference tools with no repeat engagement.

**B2B passes:** Ongoing operational workflow (shift scheduling, inventory, client follow-up), anything that happens on a recurring business cadence.

**B2B fails:** One-time migration, one-time analysis, one-time training content.

---

## How to Use This Skill

### Step 1 — Gather raw signal

- If mobile-ride-along output is available: extract every friction moment and every Dream App feature
- If mobile-industry-download output is available: extract the pain points ranked by severity, and the market gaps section
- If neither is available: do fresh research — App Store 1-3 star reviews, Reddit threads, forum posts about friction with current tools

### Step 2 — Categorize through the 5 Mobile Problem Types

For each candidate problem, identify which of the 5 types it belongs to. Discard anything that doesn't fit clearly.

### Step 3 — Apply the 3 Hard Filters

Run each remaining candidate through:
- Pain Filter: can users describe the specific cost?
- Buildability Filter: RN/Expo in 1-3 weeks?
- Recurring Value Filter: ongoing engagement potential?

Cut anything that fails any filter. No exceptions.

### Step 4 — Rank the survivors

Rank survivors by: pain intensity × buildability ease × engagement frequency. The highest-scoring problem is the pick.

### Step 5 — Output the ranked report and the one pick

---

## Output Structure

### Section 1: The Candidate Problems (Ranked)

A ranked list. For each problem:

- **Problem name** (in the user's own language — from research, not invented)
- **Mobile Problem Type** (which of the 5 it fits)
- **Cost to the user** (time, money, or goal — specific estimate from research)
- **Pain Filter:** Pass / Fail + one-line rationale
- **Buildability Filter:** Pass / Fail + one-line rationale
- **Recurring Value Filter:** Pass / Fail + one-line rationale
- **Score:** 1-10

Show all candidates — including failures — so the reader sees the reasoning.

### Section 2: Why the Failed Candidates Failed

A short section on 1-3 problems that almost worked but got cut, with the specific filter that killed them. Builds pattern recognition for next time.

### Section 3: The Top 3 Survivors — Deep Dive

For each of the top 3:

**The Specific Problem**
- What's actually broken (plain language — no jargon)
- The exact moment in the user's day it hurts (reference ride-along timestamp if available)
- What they currently do instead (the workaround)

**Why It Has Legs**
- The recurring cost: how often, how much (time or money), in what context
- Why existing apps don't fix it
- The Mobile Problem Type it falls into and why that type matters here

**The App Shape**
- What the MVP does in one paragraph
- Why RN/Expo can build this (the specific mechanics)
- The engagement pattern (when and why users open it)

### Section 4: The Pick

One clear paragraph:

> **"If you only attack one of these first, attack [#1]. Here's why."**

Then 3-5 sentences: why it beats the other two, what makes it lowest-risk to build, and what the user should do next (bring this to mobile-app-selector to lock the concept).

---

## Pro Tips

- **Don't fight the filters.** If a problem is exciting but fails the Buildability filter, it's still a fail. Discipline here saves weeks of building something that can't be executed in RN/Expo.
- **Favor the unsexy.** If three indie developers on Twitter are already pitching solutions to this problem, supply is saturated. Look one layer deeper into the friction.
- **Use ride-along friction moments directly.** If the ride-along narrative had a 2:45 PM scene where the user closed the app and screenshotted instead — that's a problem candidate. Pull it verbatim.
- **Watch out for one-shot problems disguised as recurring.** "Help them set up their workout plan" is a one-time setup. "Log every workout and track progress over time" is recurring. The difference is everything.
- **Quantify aggressively.** "Wastes time" is useless. "15 minutes of manual re-entry per shift, 5 shifts per week = 75 minutes per week" is gold.

---

## When to Use This Skill

Use after mobile-industry-download and mobile-ride-along to convert research into a decision.
Use when you have a user type but don't know which problem to target.
Use when you have multiple friction observations and need to pick one.
Use before mobile-app-selector — money-map finds the problem, app-selector locks the concept.

Don't use without at least some raw signal (research or ride-along output).
Don't use to find "clever" problems — the boring, recurring ones are the right ones.
