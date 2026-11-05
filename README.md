# Public Sector Sales — AI Activation Program

The standalone participant site for the Public Sector Sales **AI Activation Program**
(Nov 9 – Dec 11, 2026 · Thanksgiving week off · GTM Enablement).

One page, no build step, no dependencies beyond the Inter font. A clean,
purpose built design: a navy program band at the top, built from layered
mesh gradients (deep blue with a warm red glow and fine grain, all CSS, no
image files), with the live today pill and the at-a-glance facts, then a
light working surface for the weekly activities with gradient washes on the
week headers and the open day. One accent, the Equinix logo red, marks today and the data rule;
navy marks the Friday synthesis and the selected week.
Day cards carry their day number rather than an icon.

## What's on the page

- **Program band** with the title, a live **today pill** (today's activity, a
  countdown before Nov 9, the pause notice in Thanksgiving week) and the
  at-a-glance facts with number tickers.
- **Weekly activities** — one tab per week. Each week is a row of five
  **expanding day cards**: the open day takes most of the width and shows the
  activity as the program brief states it: the mission laid out as numbered
  steps, one per sentence of the brief, the AI skill and the keep-and-share line;
  the other four collapse to slim spines. Click a spine, use the dots, the
  previous/next buttons, or ← → keys. Every day has a link (`#/day/<id>`). Week 3 shows
  the build environment, the Customer Source Pack components, the two assigned
  tutorials, and each day's video chapter. Chapters and tutorials play inside
  the page (YouTube's no-cookie embed), a chapter from its start to its end time.
- **Audio briefs.** A one minute "how the program works" brief in the program
  band, a thirty second "what this week is about" brief in each week header
  (what you'll learn to do and the Monday to Friday flow), and a short spoken
  brief on every day card: what to do, in an easy
  going voice, with one example. Generated with ElevenLabs (voice: Kristen,
  model eleven_v4); the files are in `audio/`, the scripts in
  `audio/scripts.json`. One brief plays at a time; the button shows progress
  and time left.
- **Submission Channel** tab for Viva Engage.

The page is deliberately lean: the program band, then the weeks and the
daily activities, with the activity text taken from the full program brief
(November 2026) and nothing added to it. The expanding day cards and the
number tickers are adapted from 21st.dev references and re-implemented in
plain CSS and JavaScript.

**Today:** the page opens on the current week with today's card open; add
`?date=YYYY-MM-DD` to preview any day, for example `index.html?date=2026-11-30`.

## Editing

All content is in the `DATA` block at the top of the page script in `index.html`:

- `WEEKS` — name, dates, accent, outcome, coaching focus, note; Week 3 also
  carries the build environment line and the two tutorials (`videos`, with
  their YouTube ids).
- `ACTS` — the twenty activities: mission, AI skill and keep-and-share line,
  word for word from the program brief. Week 3 days carry `watch`, the
  assigned chapter with start and end seconds.
- `PACK` — the Customer Source Pack components shown in Week 3.
- `ENGAGE_EMBED` — set to the cohort's Viva Engage group embed URL to show the
  feed in the Submission Channel tab (until then the tab links out).

## Publish

GitHub Pages → Settings → Pages → deploy from the default branch, root.
Or copy `index.html`, `brand/` and `audio/` anywhere — the page is
self-contained apart from the Inter font from Google Fonts and the YouTube
players.
