---
name: mobile-blueprint
description: Takes a locked mobile app concept sentence and produces a complete, execution-ready 12-section build specification. Zero ambiguity — hand this document to Claude in a new session and building starts without clarifying questions. Covers concept summary, user profile, MVP features, user stories, data model, tech stack, integrations, screen map with navigation pattern, numbered build sessions, acceptance criteria, launch criteria, and App Store submission spec. Use this skill after mobile-app-selector has locked the concept sentence, or whenever someone says "blueprint", "build the spec", "design the app", "turn this concept into a build plan", "what do I actually need to build", or "create the build document". If invoked without a locked concept sentence already in context, ask for one before generating anything.
---

# Mobile Blueprint

Take the locked concept sentence and produce the complete specification that turns it into working software. This document is the handoff — from decision to execution.

## What This Skill Does

**Input:** A locked concept sentence: "I am building a [type] app for [specific user] that [solves specific problem]."

**Output:** A 12-section build spec. Not a wireframe. Not a mockup. Not a high-level summary. A document with enough detail that Claude in a fresh session can read it and start Session 1 without asking a single clarifying question.

**If no locked sentence is in context:** Ask for one before generating anything: "What are you building? One sentence — the app type, who uses it, and what problem it solves."

---

## The 12 Sections

Generate all 12. Never skip or merge sections. A blueprint with missing sections is incomplete.

---

### Section 1 — Concept Summary

Restate the locked sentence. Then in 2-3 sentences: who this is specifically for, what problem it solves, and why a mobile app is the right format for this (not a web app or a spreadsheet).

No gate score references — the blueprint may be run without going through the selector first.

---

### Section 2 — Who This Is For

One tight paragraph (3-4 sentences maximum): the user's role, their daily context, their current workaround, and the outcome they want.

This is not a persona document with demographics and a stock photo. It's a functional description that answers: what does this person do, why do they need this app specifically on their phone, what are they doing instead today, and what does a good day look like when the app is working?

---

### Section 3 — MVP Feature Set

List 3-5 features that **must ship** for the app to deliver its core value. Each feature gets one line: name and what it does.

Then a hard **NOT IN MVP** list below it — explicit features excluded from the first version. This list is as important as the feature list. Without it, scope creep kills the build timeline.

Format:

**Must Ship:**
1. [Feature name] — [what it does in one sentence]
2. ...

**NOT in MVP (build later):**
- [Feature excluded] — [why it's deferred]
- ...

---

### Section 4 — User Stories

5-8 user stories, one per MVP feature plus core flows.

Format: "As a [specific user], I want [specific action] so that [specific benefit]."

Each story should map to one MVP feature. If a feature requires multiple distinct user actions, write one story per action. Stories must be specific enough that acceptance criteria can be written against them.

---

### Section 5 — Data Model

List every table needed, its key fields, field types, and relationships. Plain English description first, then a formatted table.

Format per table:

**[Table name]**
Purpose: [what this table stores]

| Field | Type | Notes |
|---|---|---|
| id | uuid | primary key |
| ... | ... | ... |

Relationships: [e.g., "posts belongs to users via user_id"]

No ORM syntax. No migration scripts. Just the structure in plain English and table format.

---

### Section 6 — Tech Stack

State the stack and give one-line rationale per choice.

Default stack (deviate only with documented reason):

| Layer | Choice | Rationale |
|---|---|---|
| Mobile | React Native + Expo (managed workflow) | Claude-buildable, cross-platform, no native Xcode/Android Studio required |
| Backend / DB | Supabase | Postgres + auth + storage + real-time in one; RLS for security |
| Auth | Supabase Auth | Default; only use Clerk/Auth0 if enterprise SSO or existing user base requires it — document if deviating |
| Push notifications | Expo push notifications | Works without FCM/APNs setup complexity; EAS handles credentials |
| Payments | Stripe (if needed) | Standard; Expo-compatible |
| AI features | OpenAI API (if needed) | Claude also available; choose based on use case |
| Build + submission | EAS Build | App Store / Play Store binary generation without local Xcode |
| Hosting (API routes) | Supabase Edge Functions or Vercel | Edge Functions for DB-adjacent logic; Vercel for standalone API |

If any choice deviates from defaults: document the reason in the rationale column.

---

### Section 7 — Key Integrations

List every external API or service the app will connect to. For each:

- **Service:** [name]
- **Purpose:** [what it does in this app]
- **Auth pattern:** [API key in env var / OAuth / Supabase vault]
- **Required credentials:** [what needs to be in .env or Supabase vault]

If no external integrations are needed beyond Supabase: say so explicitly.

---

### Section 8 — Screen Map

State the navigation pattern first, with rationale:

- **Tab navigation** — for feature-parallel apps where users switch contexts equally (e.g., Home / Search / Profile)
- **Stack-only navigation** — for task-flow apps with a single linear path (e.g., onboarding wizard, checkout)
- **Drawer navigation** — for content-rich apps with many sections that don't need equal prominence
- **Mixed** — describe the top-level pattern and any nested stacks

Then list every screen:

**[Screen name]** (`StackName > ScreenName` or `Tab > Screen`)
- Renders: [what the user sees]
- Actions: [what the user can do]
- Navigates to: [which screen on which action]

Every screen that appears in the app must be listed. No implicit screens.

---

### Section 9 — Build Order

Number the sessions. Name each session by what it produces. Scope each to roughly 1-3 hours of focused work — specific enough to start without planning, completable before context gets unwieldy.

Format:

**Session 1: [What it produces]**
- [Task 1]
- [Task 2]
- [Task 3]

**Session 2: [What it produces]**
- ...

Sessions must be ordered by dependency — you can't build the home screen before the auth flow and the data tables exist. Foundation first, features second, polish last.

Typical session order for a standard app:
1. Expo project scaffold + Supabase schema + Row Level Security
2. Auth flow (sign up, sign in, session persistence)
3. Core data layer (main table CRUD + Supabase queries)
4. Primary screen(s) (the screen the user sees first after auth)
5. Secondary screens + navigation wiring
6. [Repeat per feature]
7. Push notification setup + handlers
8. Error states, loading states, empty states
9. App Store assets (icon, splash, screenshots scaffold)
10. EAS build + TestFlight submission

---

### Section 10 — Acceptance Criteria

One criteria block per MVP feature. Binary: pass or fail. No vague language.

Format per feature:

**[Feature name]**
- [ ] [Specific, measurable criterion — "First load renders in under 3 seconds on LTE" not "loads quickly"]
- [ ] [Another criterion]
- [ ] [Edge case handled — "Empty state shown when no data exists"]

Every MVP feature must have at least 2 criteria. Every criterion must be testable without interpretation.

---

### Section 11 — Launch Criteria

What must be true before the first real user touches this app. These are the minimum standards for launch — not polish, not nice-to-haves. The floor.

- [ ] All Supabase tables have Row Level Security enabled and tested
- [ ] Auth flow handles sign-up, sign-in, password reset, and session expiry
- [ ] No user data is exposed without authentication
- [ ] All MVP features pass their acceptance criteria
- [ ] App has been tested on a physical iOS device (not just simulator)
- [ ] Crash-free rate on first run > 95% (test 10 cold starts on device)
- [ ] App Store submission complete: binary uploaded, metadata complete, no known policy violations (approval is Apple's process — this criteria covers what you control)
- [ ] [Any app-specific criteria — e.g., "Payment flow tested end-to-end with Stripe test mode"]

---

### Section 12 — App Store Submission Spec

All the metadata Apple will ask for, specified now so there's no research needed at submission time.

**App Identity:**
- App Name: [30 chars max]
- Subtitle: [30 chars max — appears below the name on the App Store listing]
- Bundle ID: com.[developer].[appname]

**Description:**
[Full App Store description, under 4,000 characters. Lead with what the app does for the user in the first 2 sentences — that's what shows before "more." Include 3-5 key features. Close with a clear call to action.]

**Keywords:**
[Single text field, 100 characters max, comma-separated, no spaces after commas. Do not repeat words already in the App Name or Subtitle. Example: habit,tracker,daily,routine,productivity,goals,streaks,reminder]

**Categories:**
- Primary: [App Store category]
- Secondary: [App Store category, optional]

**Age Rating:** [4+, 9+, 12+, or 17+ — state which and why]

**Screenshots Required:**
- 6.5" iPhone (iPhone 14 Pro Max / 15 Pro Max): minimum 3, up to 10
- 12.9" iPad (optional unless you support iPad): minimum 3

**Privacy Policy URL:** [Required — must exist before submission]

---

### Section 13 — Interactive HTML Preview

Generate a complete, self-contained HTML file and write it to disk as `[app-slug]-preview.html` (e.g., `habit-tracker-preview.html`) in the current working directory. This file is the visual contract for the build — a browser-renderable, Playwright-testable simulation of every screen in the app. It is produced at the end of every blueprint session, without being asked.

**Requirements:**

1. **Single file, zero dependencies.** No CDN links, no npm, no external fonts. All CSS and JS inline in the `<html>` document.

2. **Phone frame.** Centered on the page. 390px wide, 844px tall (iPhone 14 viewport). Simple bezel via CSS `box-shadow` and `border-radius`. Background behind the phone is a neutral dark color so the frame is clear.

3. **All screens from Section 8.** One `<section data-screen="[screen-id]">` per screen. Only one screen is visible at a time — the rest are `display:none`. The `screen-id` must be a lowercase kebab-case slug matching the screen name (e.g., `data-screen="home"`, `data-screen="profile-edit"`).

4. **Navigation matches Section 8 pattern exactly:**
   - Tab navigation: a fixed bottom tab bar with `<button data-tab="[tab-id]">` elements; clicking a tab sets that screen to visible and marks the tab active.
   - Stack navigation: a header with a `<button data-back>` that returns to the previous screen; list items and CTAs use `data-nav="[target-screen-id]"` to push forward.
   - Mixed: implement both patterns in the appropriate nesting.

5. **Realistic placeholder data.** Not "Lorem ipsum." Data must reflect the actual app concept — real-feeling names, numbers, timestamps, categories, status labels. If the app is a job tracker, show real-looking job entries. If it is a habit tracker, show real-looking streaks.

6. **Mobile-first CSS.** Minimum 44px tap targets. 16px body font. Standard iOS-style spacing (16px horizontal padding). Colors and type that match the app's category (health apps are clean and white; finance apps are dark and precise; social apps are warm).

7. **Playwright attributes on every interactive element:** `data-testid="[descriptive-name]"` on all buttons, inputs, list items, and navigation elements. Screen containers get `data-screen`. Tabs get `data-tab`.

8. **Status bar mock at the top of every screen.** Single row: time left-aligned (9:41), signal + wifi + battery right-aligned (text symbols: use unicode or simple text, no images). 

9. **Screen transition JS.** Smooth instant switch (no animation needed — Playwright needs deterministic state). When a tab or nav target is clicked, hide all screens, show target, update active tab state.

**Minimum screens to render:** Every screen listed in Section 8. No implicit screens. If Section 8 lists 7 screens, the HTML has 7 `<section data-screen>` blocks.

---

## After the Spec Is Complete

After generating and writing the 12-section spec, immediately generate and write the Section 13 HTML preview file to disk. Then output this message:

"Blueprint done. Preview written to `[filename]-preview.html`.

To start building: open a new Claude Code session in your project directory, paste this document, and say 'Start Session 1.'

To stress-test the preview now: run the Playwright polish loop below."

Then output the Playwright polish loop script (inline, ready to run):

```js
// [app-slug]-polish.js
// Run: node [app-slug]-polish.js
// Iterates through every screen, screenshots each, reports layout issues.

const { chromium } = require('playwright');
const path = require('path');
const fs = require('fs');

const PREVIEW_FILE = path.resolve(__dirname, '[app-slug]-preview.html');
const SCREENS = [/* paste screen IDs from Section 8 here — e.g., 'home', 'detail', 'profile' */];

(async () => {
  const browser = await chromium.launch({ headless: true });
  const page = await browser.newPage();
  await page.setViewportSize({ width: 390, height: 844 });
  await page.goto('file://' + PREVIEW_FILE, { waitUntil: 'networkidle' });

  fs.mkdirSync('screenshots', { recursive: true });

  for (const screenId of SCREENS) {
    // Navigate to screen by clicking its tab or triggering its nav target
    const tab = await page.$(`[data-tab="${screenId}"]`);
    if (tab) await tab.click();
    else {
      const navEl = await page.$(`[data-nav="${screenId}"]`);
      if (navEl) await navEl.click();
    }
    await page.waitForTimeout(100);

    await page.screenshot({ path: `screenshots/${screenId}.png` });
    console.log(`Captured: ${screenId}`);

    // Check for overflow
    const overflow = await page.evaluate((id) => {
      const el = document.querySelector(`[data-screen="${id}"]`);
      if (!el) return 'SCREEN NOT FOUND';
      return el.scrollHeight > el.clientHeight ? `overflow: scrollHeight=${el.scrollHeight} clientHeight=${el.clientHeight}` : 'ok';
    }, screenId);
    console.log(`  Layout: ${overflow}`);
  }

  await browser.close();
  console.log('\nDone. Open screenshots/ to review each screen.');
})();
```

Replace `[app-slug]` and the `SCREENS` array with the actual values from Section 8. Run, review screenshots, tell Claude what looks off, and it will patch the HTML. Repeat until every screen passes.

---

## Guardrails

- Never skip or merge sections — all 13 must be present
- Section 3 NOT-IN-MVP list is required — scope fence is as important as scope
- Section 9 Build Order sessions must be named by their output, not generic "Step N"
- Section 10 acceptance criteria must be binary and specific — reject vague language
- Section 12 keywords: single 100-char field, comma-separated, no spaces, no title/subtitle word repetition
- Section 13 HTML file must be written to disk, not just displayed in chat
- No ORM syntax in Section 5 — plain English + table format only
- No em dashes anywhere in output (house style) — use period, comma, colon, parentheses, or spaced hyphen
