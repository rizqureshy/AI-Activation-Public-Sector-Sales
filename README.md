# Public Sector Sales AI Activation Program

The participant site for the Public Sector Sales **AI Activation Program**:
four active learning weeks, twenty short daily activities, November 9 to
December 11, 2026, with a pause for Thanksgiving week. US cohort: Federal
Civilian Sales, Defense and Intelligence Sales, SLED including higher
education, and Public Sector Partner Sales. From GTM Enablement.

One page, plain HTML, CSS and JavaScript, no build step. The only outside
resources are the Inter font from Google Fonts and the YouTube players.

## What's on the page

- **Program band.** The title, a live today pill (today's activity, a
  countdown before November 9, the pause notice in Thanksgiving week), a one
  minute spoken "how the program works", and the at-a-glance facts.
- **Weekly activities.** One tab per week. Each week header carries the
  outcome and a half minute spoken brief from the coach: the week's focus and
  what you will learn to do. Each week is a row of five expanding day cards.
  The open day shows the activity as the program brief states it: the mission
  laid out as numbered steps, one per sentence, the AI skill, and the keep and
  share line, plus a short spoken brief with one example. The other four days
  collapse to slim spines. Click a spine, use the dots, the previous and next
  buttons, or the arrow keys. Every day has a link (`#/day/<id>`).
- **Week 3.** The build environment, the Customer Source Pack components, the
  two assigned tutorials, and each day's assigned video chapter. Chapters and
  tutorials play inside the page (YouTube's no-cookie embed); a chapter plays
  from its start to its end time.
- **Submission Channel.** A tab for the Viva Engage community, with what a
  good share looks like.

**Today.** The page opens on the current week with today's card open. Add
`?date=YYYY-MM-DD` to preview any day, for example `index.html?date=2026-11-30`.

## Audio

The spoken briefs were generated with ElevenLabs (voice Kristen, model
eleven_v4). The files are in `audio/`, the scripts in `audio/scripts.json`:
`welcome`, `week1` to `week4`, and one per day (`w1-mon` to `w4-fri`). One
brief plays at a time; the button shows progress and time left, and changing
week or day stops playback.

## Editing

All content is in the `DATA` block at the top of the page script in
`index.html`:

- `WEEKS`: name, dates, outcome, coaching focus, note, and the brief
  duration. Week 3 also carries the build environment line and the two
  tutorials (`videos`, with their YouTube ids).
- `ACTS`: the twenty activities: mission, AI skill and keep and share line,
  word for word from the program brief, plus the brief duration. Week 3 days
  carry `watch`, the assigned chapter with start and end seconds.
- `PACK`: the Customer Source Pack components shown in Week 3.
- `ENGAGE_EMBED`: set to the cohort's Viva Engage group embed URL to show the
  feed in the Submission Channel tab. Until then the tab links out to Viva
  Engage.

## Publish

GitHub Pages: Settings, Pages, deploy from the default branch, root. Or copy
`index.html`, `brand/` and `audio/` to any static host.
