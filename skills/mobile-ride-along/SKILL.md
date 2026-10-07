---
name: mobile-ride-along
description: Generates a 1,200-1,800 word narrative of a full day inside the life of a specific mobile app user — told in first person, present tense, with timestamps every 15-30 minutes and italicized inner thoughts. Surfaces the friction moments, the app-switching frustration, and the dream app the user wishes existed. Use before mobile-app-selector or mobile-money-map to develop deep empathy for the target user before locking a concept. Trigger phrases include "mobile ride-along", "ride-along on [user type]", "day in the life of a [mobile user]", "step into the shoes of a [user]", "what does a [user] do all day on their phone", or any request to understand a mobile user's daily reality.
---

# Mobile Ride-Along

Spend a day inside the head of the person you're building for. Walk away knowing when they reach for their phone, what breaks in their current apps, and the app they're quietly wishing someone would build.

## What This Skill Does

**Input:** A specific mobile app user type (e.g., "remote worker who tracks freelance projects", "restaurant server managing their shift schedule", "indie runner training for a 5K")

**Output:** A 1,200-1,800 word first-person narrative covering a full day — timestamps every 15-30 minutes, italicized inner monologue at every scene, friction costs throughout, and a "Dream App" close that captures the user's unfiltered wishlist. Grounded in real research from App Store reviews, Reddit, and YouTube.

This is empathy as raw material. You finish the narrative knowing what frustrates this person, in their language, before you've written a line of code.

## Why This Skill Exists

There's a gap between knowing facts about a mobile app user and understanding what their day actually feels like. Mobile industry download tells you the stats: what apps exist, what they charge, what users complain about. Mobile ride-along puts you in the user's body for 14 hours.

That difference matters because the most valuable app opportunities aren't the ones listed in forum posts. They're the friction moments that accumulate invisibly — the three-tap sequence they do reflexively, the app they switch to because their main one can't do one thing, the small thing that makes them close the app and just give up.

A discovery call is 30 minutes. A ride-along is a full day. This skill manufactures one in 90 seconds.

---

## The Four Mechanics That Make It Work

This skill produces slop if it ignores these. Enforce all four or the output fails.

### 1. Timestamps every 15-30 minutes

Every scene opens with a precise timestamp and a one-line location note. **"7:14 AM — Still in bed, phone in hand."** Not "morning." Not "early." A real time, every time. The timestamps are what turn a vague story into a forensic walk-through of how someone actually uses their phone.

### 2. Italicized inner monologue in every scene

Every timestamped scene includes at least one moment of *italicized* inner thought. The real app frustration isn't in what the user does — it's in what they think while doing it.

*"Why does this take three taps? I do this same thing every morning."*
*"I give up. I'll just screenshot it and deal with it later."*

The action is the symptom. The inner thought is the diagnosis.

### 3. Friction cost as a recurring thread

Every scene where an app fails or a workaround happens should tag a cost — time lost, task abandoned, goal deferred. Not as a big number, but as a constant background ache.

*"Ten minutes trying to export that, gone."*
*"Opened three apps to do what should be one step."*
*"Closed it again. Maybe next time."*

The accumulation by the end of the day is what makes the reader feel the problem.

### 4. The Dream App close

The last 25-30% of the narrative is the "Dream App" section — written from inside the user's head as a structured wishlist. What would the perfect app do? Not features — outcomes. Organized by the moments from the narrative.

This is the most valuable part. It's what the user would say if they had 20 free minutes and someone who actually listened.

---

## How to Use This Skill

### Step 1 — Research first, write second

Do not start writing until you have done real research. Search:

- Reddit: the subreddits where this user type hangs out (e.g., r/freelance, r/running, r/restaurantowners)
- App Store reviews: 1-3 star reviews of the 2-3 most popular apps for this user
- YouTube: "day in the life of a [user type]" vlogs, app review videos
- Twitter/X: "[user type] app" complaints, "[specific app name] annoying"
- Community posts: Facebook groups, Discord servers where this user talks

Pull real app names, real friction patterns, real vocabulary, real workarounds. If you can't name the specific apps they use and when they use them, you haven't researched enough.

### Step 2 — Map the day's structure

Before writing, outline:
- Wake / morning routine
- Start of primary activity (work, workout, commute, etc.)
- Mid-day context switch
- Afternoon peak load or peak friction
- Evening wind-down or wrap-up

For each segment: identify 1-2 moments where an app is involved and either helps or fails.

### Step 3 — Write the narrative (1,200-1,800 words)

First person, present tense. Conversational. Sensory details where they help. Dialogue when it makes a moment real. Real app names throughout. Real friction — don't sanitize. Real people close apps and give up and screenshot things to deal with later. Show all of it.

### Step 4 — Close with the Dream App (300-500 words within total)

Structured by the moments from the narrative. Every wish in the Dream App section should point back to a specific friction moment from the day.

---

## Output Format

```
# A Day in the Shoes of [ROLE/USER TYPE]

## [TIMESTAMP] — [LOCATION / CONTEXT]

[Narrative paragraph(s)]

*"[Inner monologue]"*

[Continue narrative. Include specific app names. Include friction cost.]

---

## [TIMESTAMP] — [LOCATION / CONTEXT]
[...]

---

[8-12 timestamped scenes covering the full day]

---

## THE DREAM APP

If someone built the perfect app for my situation, here's what it would do.

### First thing in the morning:
- [Feature grounded in a specific morning scene]
- [Feature grounded in a specific morning scene]

### When I'm in the middle of [primary activity]:
- [Feature grounded in a specific midday scene]
- [Feature grounded in a specific midday scene]

### At the end of the day:
- [Feature grounded in a specific end-of-day scene]
- [Feature grounded in a specific end-of-day scene]

### The thing that would make me never delete it:
- [The one thing that would create a habit loop]

### Old way vs. dream app:
**Old way:**
- [Friction 1 from the narrative]
- [Friction 2 from the narrative]
- [Friction 3 from the narrative]

**Dream app:**
- [Outcome 1]
- [Outcome 2]
- [Outcome 3]

That's a real day. And that's exactly where an app that [locked concept sentence] would change everything.
```

---

## Pro Tips for Better Output

- **Use the real job title.** "Freelance graphic designer" not "creative person." "Restaurant server" not "hospitality worker." The wrong title in the first line breaks credibility.
- **Name the real apps.** Notion, Todoist, Trello, Toggl, Bereal, Strava, MyFitnessPal, Slack — whatever this person actually uses. Invented app names read as fiction.
- **Build cumulative friction.** Each small failure should add weight. By 4 PM the reader should feel what the user feels — tired of their own phone not working for them.
- **The Dream App is not a pitch.** It's the user's own voice imagining what they wish existed. No "and that's where my app comes in" — let mobile-money-map make the connection later.
- **Don't sanitize real behavior.** Real users leave apps mid-task. They screenshot things because they can't export them. They use 4 apps to do what should be 1 step. Show the real workarounds.

---

## When to Use This Skill

Use before mobile-app-selector or mobile-money-map to develop user empathy.
Use when entering a user type you've never personally been.
Use before discovery calls — the narrative gives you vocabulary and specific questions.

Don't use without real research — fabricated narratives are obvious to people in the target category.
Don't use to write marketing copy — this is for your understanding, not their consumption.

---

## Stacking With Other Depth Tools

Mobile ride-along is most powerful when stacked:

1. **mobile-industry-download** — market facts, competitor landscape, what users pay
2. **mobile-ride-along** — embodied day, friction moments, Dream App vocabulary
3. **mobile-money-map** — filters those friction moments down to the one worth building

Each feeds the next. Industry download primes vocabulary. Ride-along surfaces friction. Money map filters to the opportunity.
