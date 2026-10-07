# App Builder

**Goal:** Mobile app from idea to execution-ready build spec. Solo-buildable with Claude. No dev team.

**Default Stack:** React Native + Expo (managed) + Supabase + Expo push notifications + EAS Build (App Store / Play Store)

---

## Core Path

Run in order. `/appbuilder` handles this automatically.

| Step | Skill | Output |
|---|---|---|
| 1 | `mobile-app-selector` | Locked sentence: audience + concept — auto-launches blueprint |
| 2 | `mobile-blueprint` | 12-section build spec + App Store submission spec + `[app-slug]-preview.html` |
| 3 | Playwright polish loop | Per-screen screenshots, layout audit, iterate until publishable |

**The preview file** (`[app-slug]-preview.html`) is a single self-contained HTML file written to disk at the end of every blueprint session. It renders every screen from Section 8 in a phone frame with working navigation, realistic data, and Playwright-addressable attributes (`data-screen`, `data-tab`, `data-testid`). No server, no npm, open in any browser or Playwright directly.

**The Playwright polish loop** (`[app-slug]-polish.js`) is output by the blueprint immediately after the preview file. It screenshots every screen, checks for overflow, and reports issues. Run it, show Claude the output or screenshots, and it patches the HTML. Repeat until every screen passes visual inspection.

---

## Depth Tools

Run any of these **before** `mobile-app-selector` for a stronger concept. None are required — `/appbuilder` handles research inline. Use these when you want a full deep dive.

- `mobile-industry-download` — Full market + competitor intelligence for the app space
- `mobile-ride-along` — Day-in-the-life narrative of the target mobile user; surfaces friction for money-map to quantify
- `mobile-money-map` — Identify and rank the specific problem worth building; filters by 5 mobile problem types + 3 hard filters

---

## Go-to-Market Tools

Run **after** the build.

- `mobile-discovery-script` — User interview (consumer) or enterprise sales call
- `mobile-closer-deck` — Beta launch brief or enterprise close deck (HTML, present in browser)

---

## Frameworks

**4 Gates** (scored 1-5 each, total /20):
- 17-20: Build it — green light
- 13-16: Workable — watch any gate scored 2 or below
- 9-12: Fix a gate first — real weakness
- <9: Pick another idea
- **Veto rule:** Any single gate scored 1 = automatic veto regardless of total

**Locked Sentence format:** `"I am building a [type] app for [specific user] that [solves specific problem]."`

**The 4 Gates:**
1. **Demand** — Real complaints exist, users spend on adjacent tools (research required)
2. **Buildability** — React Native/Expo feasible in 1-3 weeks (judgment)
3. **Differentiability** — Real App Store gap; not a dominated market (research required)
4. **Passion** — 90 days of user calls without dreading it (user judgment)

---

## App Store Guardrails

Fine: Camera / GPS / push notifications / biometrics / on-device AI

Blocked (redirect silently, don't lecture upfront): Hardware BLE as core mechanic, ARKit/ARCore as primary feature, carrier-level VOIP, medical device claims, unlicensed financial advice, gambling without license

---

## Skill Reference

```
skills/
  mobile-app-selector/    — concept locking (audience + idea in one pass)
  mobile-blueprint/       — build spec generator
  mobile-industry-download/ — market research
  mobile-ride-along/      — user empathy narrative
  mobile-money-map/       — problem validation
  mobile-discovery-script/ — validation + sales
  mobile-closer-deck/     — launch + close deck
```
