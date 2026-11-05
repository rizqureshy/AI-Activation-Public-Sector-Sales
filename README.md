# Public Sector Sales — AI Activation Program

The standalone participant site for the Public Sector Sales **AI Activation Program**
(Nov 9 – Dec 11, 2026 · Thanksgiving week off · GTM Enablement).

One page plus a vendored `three.min.js` that powers the live WebGL
ink-cloud background — the same build as the Channel Sales Marathon site —
slow-drifting, domain-warped noise clouds on a black canvas; on every week
tab change the clouds take on that week's accent color, then settle back.
Degrades gracefully without WebGL2.

## What's on the page

- **Hero** with a live **today pill** (today's activity, a countdown before
  Nov 9, the break notice in Thanksgiving week) and number tickers.
- **Weekly activities** — one tab per week. Each week is a row of five
  **expanding day cards**: the open day takes most of the width and shows the
  full brief in two columns (mission, timed steps, build paths · starter
  prompt with copy, your lens, your share, a check before you post); the other
  four collapse to slim spines. Click a spine, use the dots, the previous/next
  buttons, or ← → keys. Mark a day done; the spine, the dots and the week tab
  keep count. Every day has a link (`#/day/<id>`). Week 3 shows the three
  build paths and the Thanksgiving break band; each week has a Copilot agent
  video row.
- **Your context** — Federal Civilian · Defense and Intel · SLED and higher ed ·
  Partner Sales — switches the **Your lens** section on every day. Remembered
  in the browser.
- **Submission Channel** tab for Viva Engage.

The page is deliberately lean: the hero, then the weeks and the daily
activities. The interaction patterns (expanding cards, spotlight, number
ticker) are adapted from 21st.dev references and re-implemented in plain CSS
and JavaScript — no framework, no build step.

**Today:** the page opens on the current week with today's card open; add
`?date=YYYY-MM-DD` to preview any day, for example `index.html?date=2026-11-30`.

## Editing

All content is in the `DATA` block at the top of the page script in `index.html`:

- `WEEKS` — name, dates, accent, outcome, coaching focus, note, and the week's `videos`
  (set `youtubeId` to turn a "link coming" card into a YouTube link).
- `ACTS` — the twenty activities. The mission, skill and share line follow the
  four week activity plan; the steps, starter prompt, lenses and check are the
  daily guide layer, drafted for facilitator review.
- `ENGAGE_EMBED` — set to the cohort's Viva Engage group embed URL to show the
  feed in the Submission Channel tab (until then the tab links out).
- `MATERIALS` and `DATES` are kept in the data block for a later section.

## Publish

GitHub Pages → Settings → Pages → deploy from the default branch, root.
Or copy `index.html` and `three.min.js` anywhere — the page is self-contained
apart from the Inter font from Google Fonts.
