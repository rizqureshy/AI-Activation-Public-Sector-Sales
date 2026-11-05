# Public Sector Sales — AI Activation Program

The standalone participant site for the Public Sector Sales **AI Activation Program**
(Nov 9 – Dec 11, 2026 · Thanksgiving week off · GTM Enablement).

One page plus a vendored `three.min.js` that powers the live WebGL
ink-cloud background — the same build as the Channel Sales Marathon site —
slow-drifting, domain-warped noise clouds on a black canvas; on every week
tab change the clouds take on that week's accent color, then settle back.
Degrades gracefully without WebGL2.

- **`index.html`** — the full participant site: the four weeks
  (Rethink AI · Customer and Partner Intelligence · Create Your AI Solution ·
  Account Strategy and Business Reviews), 20 activities with full briefs on
  flip cards — mission, timed steps, a starter prompt with a copy button,
  your cohort lens, your share, a check before you post, and the AI skill
  each one teaches — the Thanksgiving break, the three Week 3 build paths
  (agent · app · dashboard), a Copilot agent video row per week, the
  Submission Channel tab, the Finish Line (the Week 4 Business Review and
  the optional capstone), materials, the data rule, and key dates.

**Your context:** the picker above the week tabs (Federal Civilian · Defense
and Intel · SLED and higher ed · Partner Sales) switches the **Your lens**
section on every card. Remembered in the browser.

**Today:** the card for the current date carries a ring and the page opens
on the current week. Preview any day with `?date=YYYY-MM-DD`, for example
`index.html?date=2026-11-30`.

## Editing

All content is in the `DATA` block at the top of the page script in `index.html`:

- `WEEKS` — name, dates, accent, outcome, coaching focus, note, and the week's `videos`
  (set `youtubeId` to turn a "link coming" card into a YouTube link).
- `ACTS` — the twenty activities. The mission, skill and share line follow the
  four week activity plan; the steps, starter prompt, lenses and check are the
  daily guide layer, drafted for facilitator review.
- `ENGAGE_EMBED` — set to the cohort's Viva Engage group embed URL to show the
  feed in the Submission Channel tab (until then the tab links out).
- `MATERIALS` and `DATES`.

## Publish

GitHub Pages → Settings → Pages → deploy from the default branch, root.
Or copy `index.html` and `three.min.js` anywhere — the page is self-contained
apart from the Inter font from Google Fonts.
