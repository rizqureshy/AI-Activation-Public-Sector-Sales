# Public Sector Sales AI Activation Program

The participant site for the Public Sector Sales **AI Activation Program**: four weeks, twenty short activities, November 9 to December 11, 2026, with a break for Thanksgiving week. US cohort: Federal Civilian Sales, Defense and Intelligence Sales, SLED including higher education, and Public Sector Partner Sales. From GTM Enablement.

Static HTML, CSS and JavaScript. No build step: open `index.html`, or publish the repository root.

## What is on the page

- **Today:** a panel that knows the date. On a program day it leads with that activity. Before November 9 it counts down to Day 1. In Thanksgiving week it says so and names the resume date. After December 11 it closes the program. Preview any day with `?date=YYYY-MM-DD`, for example `index.html?date=2026-11-30`.
- **Your cohort:** choose Federal Civilian, Defense and Intel, SLED and higher ed, or Partner Sales. The examples in every guide follow the choice. Remembered in the browser only.
- **Program:** what we heard and how the program responds, the four week journey, the rhythm, the data and quality rule.
- **Weeks:** one tab per week with five day cards. Each card opens the full guide: why it matters, the brief, five timed steps with a timer, a starter prompt with the parts to replace highlighted, the cohort lens, a Viva Engage share template, the AI skill, a check before posting, previous and next. Week 3 guides add the build path choice (agent, app, dashboard). Every guide has its own link, `#/activity/<id>`.
- **Progress:** mark activities done, see a ring and per week bars, copy a one line summary. Browser only; nothing is sent anywhere.
- **Learn:** short Copilot agent videos per week. Each entry shows a placeholder until its YouTube id is added.
- **Share:** the Viva Engage area, with what a good share looks like. Shows the cohort feed once the embed URL is set.
- **Materials** and **key dates**, with a calendar file of twenty all day entries.

## Editing

Everything is in `program.js`: the program, the four audiences, the weeks (dates, outcome, coaching focus, videos), the twenty activities, the Week 3 paths, materials, key dates and the rhythm. The page renders from it; `app.js` and `activation.css` do not need to change for content edits.

- The brief, AI skill and share line of each activity are from the four week activity plan. The why, steps, starter prompt, cohort lenses, share template and check are the daily guide layer, drafted for facilitator review.
- **Add a video:** set `youtubeId` on the entry in `weeks[n].videos`. The tile becomes a click to play embed (YouTube's no cookie domain).
- **Show the Viva Engage feed:** set `program.engage.embed` to the group embed URL.
- **Mark a material ready:** add `url` to its entry in `materials`.
- Copy rule: no em dashes. `npm test` checks it.

## Checks

```bash
npm install
npm test          # the content model: twenty weekday activities in date order, none in the break, every guide complete, steps that add to 15 to 20 minutes, videos with a link slot
npm run test:e2e  # the page in a browser with every external request blocked: Today at five dates, cohort and path choices, the guide and its timer, copy and its fallback, progress, routes, the calendar file, reduced motion, phone width
node tests/tools/shot.mjs <url> <out.png> [width] [height] [script]   # screenshot helper
```

If the installed Playwright browser does not match, point `PW_CHROMIUM` at a Chromium binary.

## Publish

GitHub Pages: Settings, Pages, deploy from the default branch, root. Or copy the folder to any static host. Fonts, logos, styles and scripts are local; the page makes no external request until a video is played or Viva Engage is embedded.
