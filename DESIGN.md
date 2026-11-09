# Visual design guide: Equinix program site

A reusable description of the look, structure and behaviour of the Public
Sector Sales AI Activation Program site. Paste this into a new chat to
recreate the same system for a different program, then swap the content.
Everything here is plain HTML, CSS and JavaScript in one file; no framework,
no build step.

## 1. The idea in one paragraph

A two tone page. A dark navy program band at the top carries the title, a
live "today" pill, a one minute spoken welcome and an at-a-glance facts
panel. Below a thin red-to-blue ribbon, a light grey working surface holds
the program itself: one tab per week, each week a row of five expanding day
cards where one day is open wide and the other four collapse to slim spines.
Depth comes from layered gradients and a little grain, never from imagery.
One accent, the Equinix logo red, marks today and the rules. Navy marks the
selected week and the final day of each week. The content on a card is the
program brief's own text, laid out as numbered steps, with a short spoken
brief from a coach.

## 2. Tokens

```css
:root {
  --navy:    #0b1626;   /* band base, selected states, Friday days */
  --navy-2:  #16263d;
  --blue:    #1f4e9c;   /* gradient partner to navy */
  --blue-2:  #2a6fd6;   /* bright end of blue gradients */
  --red:     #e91c24;   /* Equinix logo red: today, rules, primary button */
  --red-dk:  #c9151d;
  --bg:      #f4f5f7;   /* page surface */
  --surface: #ffffff;   /* cards */
  --surface-2:#f8f9fb;  /* quiet panels inside cards */
  --line:    #e2e5ea;   /* hairlines */
  --line-2:  #c9ced6;   /* stronger hairlines, spine numerals */
  --text:    #111418;
  --text-2:  #4a5059;
  --muted:   #7a818c;
  --on-navy: rgba(255,255,255,.78);   /* body text on the band */
  --sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  --r: 10px; --r-sm: 6px;             /* radii: cards 10, chips 100px pills */
  --shadow: 0 1px 2px rgba(17,20,24,.06), 0 1px 1px rgba(17,20,24,.03);
}
body { background: linear-gradient(180deg, #f6f7f9 0%, #eef1f6 100%) fixed; color: var(--text); line-height: 1.55; }
:focus-visible { outline: 2px solid var(--red); outline-offset: 2px; }
```

Font: Inter from Google Fonts, weights 400, 500, 600, 700. Numerals are
tabular (`font-variant-numeric: tabular-nums`) wherever numbers line up.

## 3. Type scale

| Use | Size | Weight | Notes |
|---|---|---|---|
| Band title | `clamp(34px, 4.6vw, 54px)` | 700 | letter-spacing -.03em, line-height 1.06, second line in gradient text |
| Section title | `clamp(24px, 3vw, 32px)` | 700 | letter-spacing -.025em |
| Week title | `clamp(20px, 2.4vw, 26px)` | 700 | beside a 48px gradient numeral |
| Open card title | `clamp(22px, 2.3vw, 28px)` | 700 | letter-spacing -.025em |
| Body | 13 to 14px | 400 | `--text-2` for secondary copy |
| Eyebrows and labels | 10 to 11px | 600 | uppercase, letter-spacing 1.2 to 2px, `--muted` |
| Facts numerals | 30px | 700 | gradient text, white to pale blue |

Eyebrow pattern: an 18px by 2px red dash, then uppercase text in `--on-navy`
on the band or `--red` on the light surface.

## 4. The program band

```css
.hero {
  color:#fff; padding:68px 0 60px; position:relative; overflow:hidden;
  background:
    radial-gradient(900px 520px at 88% 10%, rgba(233,28,36,.42), transparent 60%),   /* warm red glow, top right */
    radial-gradient(760px 480px at 70% 110%, rgba(42,111,214,.55), transparent 62%), /* blue bloom, bottom */
    radial-gradient(640px 420px at 8% 90%, rgba(31,78,156,.45), transparent 60%),    /* blue, bottom left */
    linear-gradient(120deg, #0a1322 0%, #0f1f3a 55%, #132a4d 100%);                  /* navy base */
}
/* fine grain: an inline SVG feTurbulence tile at ~6% white, mix-blend-mode: overlay */
.hero::before { content:""; position:absolute; inset:0; background:var(--grain); opacity:.9; mix-blend-mode:overlay; pointer-events:none; }
/* a slow light sweep, 14s, alternate; disabled under prefers-reduced-motion */
.hero::after  { content:""; position:absolute; inset:-20% -10%; background:linear-gradient(105deg, transparent 38%, rgba(255,255,255,.07) 50%, transparent 62%); animation:sweep 14s ease-in-out infinite alternate; }
```

Grain tile:
`url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='160' height='160'><filter id='n'><feTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='2' stitchTiles='stitch'/><feColorMatrix values='0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 .06 0'/></filter><rect width='100%' height='100%' filter='url(%23n)'/></svg>")`

Layout: a two column grid, `minmax(0,1.5fr) minmax(300px,.9fr)`, 48px gap.
Left: eyebrow, title (second line gradient `#ffd3d5 → #c9d8ff → #9fc4ff`),
a 16px summary in `--on-navy`, the today pill, the welcome listen button.
Right: the facts panel.

Facts panel: frosted glass. `background: linear-gradient(160deg, rgba(255,255,255,.12), rgba(255,255,255,.04))`,
1px border `rgba(255,255,255,.18)`, radius 12px, `backdrop-filter: blur(14px)`,
shadow `0 20px 50px rgba(0,0,0,.28), inset 0 1px 0 rgba(255,255,255,.18)`.
Inside: a 2 by 2 grid of numerals that count up when the band scrolls into
view, then a definition list (Dates, Cohort, Format) under a hairline.

Today pill: a glass capsule, `linear-gradient(90deg, rgba(255,255,255,.14), rgba(255,255,255,.06))`,
border `rgba(255,255,255,.22)`, blur 10px. Left: an uppercase tag with a
pulsing red dot. Middle: bold title and a one-line summary. Right: a red
gradient button `linear-gradient(135deg, #ff3b43, var(--red-dk))` with a
glow `0 6px 16px rgba(233,28,36,.35)`.

Ribbon under the band: 4px, `linear-gradient(90deg, var(--red) 0%, #ff6a70 22%, var(--blue-2) 60%, var(--navy) 100%)`.

Header above the band: 60px, white at 92% with blur, hairline bottom. Logo,
a 1px separator, the program name with a muted suffix, right-aligned nav
links, and a date capsule with a hairline border.

## 5. The working surface

Section eyebrow in `--red`, a section title, a short explanatory line in
`--text-2`, then a "rule" card: white, hairline border, a 3px red bar on the
left, 13px text, bold lead-in.

Week tabs: a sticky bar under the header, `rgba(244,245,247,.94)` with
blur. Each tab is a white pill with a hairline border, a small uppercase
"WEEK n" label in `--muted`, then the week name. The selected tab is
`linear-gradient(135deg, var(--navy-2), var(--blue))` in white with
`0 6px 16px rgba(31,78,156,.25)`.

Week header: a tinted panel, `linear-gradient(100deg, rgba(31,78,156,.10), rgba(233,28,36,.06) 70%, transparent)`,
1px border `rgba(31,78,156,.12)`, radius 12px. A 48px numeral in gradient
text `linear-gradient(180deg, var(--blue-2), var(--navy))`, the week name,
an uppercase line with dates and the week's verbs, the week outcome on the
right in `--text-2`, and a listen button for the coach's week brief.

Progress strip above the row: five 4px segments, grey for days ahead,
muted blue for past days, a red gradient for today.

## 6. Expanding day cards

The signature component. A grid of five columns; the open day gets `6fr`,
the others `1fr`, animated with
`transition: grid-template-columns .5s cubic-bezier(.22,.9,.3,1)`. Fixed row
height, 520px on desktop, 600px when the body falls to one column, and a
stacked list on phones where the open card expands in place.

Spine (closed day): white to pale blue `linear-gradient(180deg, #fff, #f3f6fb)`,
a day chip at the top (uppercase MON, hairline pill), the title set
vertically (`writing-mode: vertical-rl; transform: rotate(180deg)`), and at
the foot a 40px round badge with the day number in white on
`linear-gradient(135deg, var(--blue-2), var(--navy))` with
`0 6px 14px rgba(31,78,156,.28)`, then the date in small uppercase. Hover
lifts 2px and tints blue. Today's spine uses the red gradient badge.

Open card head: `linear-gradient(120deg, #fff 0%, #eef3fb 70%, #e6eefb 100%)`,
red tinted for today (`#fdeeee`, `#fbe3e4`), deeper blue for Friday.
A row of chips: day and date (red outline on today), a dashed "Day n of 20",
"15–20 min" in muted. The title at 22 to 28px. The day number as a 140px
watermark numeral, weight 800, bottom right, in gradient text at 16% to 2%
blue (red on today). Action buttons top right as small uppercase pills.

Open card body: two columns, `1.15fr 1fr`, 28px gap, scrollable.
Left: the mission as numbered steps on a vertical track. The track is a 2px
line `linear-gradient(180deg, var(--blue-2), rgba(31,78,156,.15))`; each step
has a 20px gradient dot with a 3px white ring, and the opening verb of the
sentence in bold navy (bold red on today).
Right: optional "watch first" chapter chips, the AI skill as a tag
(`linear-gradient(135deg, #eef3fb, #e3ebf8)`, border `rgba(31,78,156,.18)`,
star icon), and the keep-and-share card: white to `#f6f8fc`, a 1px gradient
border red to blue built with a masked pseudo-element, a small red icon tile,
an uppercase label, the share line in 13.5px medium, and a muted footer.

Day navigation under the row: "Previous day" and "Next day" pills, five
dots in the middle (the current one wider and navy gradient), and a hint
that arrow keys move between days.

Friday is the week's synthesis: its spine has a navy top bar, its badge a
"WEEK SYNTHESIS" navy pill.

## 7. Buttons and small parts

- Primary action: red gradient pill with glow (today pill button, Viva
  Engage button).
- Secondary: white pill, hairline border `--line-2`, uppercase 11px, darkens
  on hover.
- Chips: 100px pills, 10 to 12px, hairline borders; dashed border means
  pending or optional.
- Listen button: a white pill with a 34px round gradient play icon (red
  gradient in the band and on today's card, blue elsewhere), a bold label,
  a muted subtitle, and the duration. While playing the icon shows a pause
  glyph with a soft pulsing ring, and the pill fills from the left with a
  translucent gradient to show progress; the time counts down.
- Inline video player: 16:9, 6px radius, black, a round close button top
  right, a small uppercase caption bottom left. Opens at the top of the card
  body or under the tutorial row.

## 8. Motion

- Panel change: fade and 8px rise over 350ms with `cubic-bezier(.22,.9,.3,1)`;
  cards stagger in at 50ms each.
- Hover lifts: 1 to 2px with a soft blue shadow.
- Band light sweep: 14s, alternate, very faint.
- Everything respects `prefers-reduced-motion: reduce`: no sweep, no
  stagger, no panel animation.

## 9. Behaviour that makes the page feel alive

- The page knows the date. It opens on the current week with today's card
  open. The today pill shows today's activity, a countdown before the start,
  a pause notice in an off week, and a closing message after the end.
  `?date=YYYY-MM-DD` previews any day.
- Arrow keys move between days; Enter opens a focused spine.
- Every day has a shareable link, `#/day/<id>`.
- Audio briefs: a welcome in the band, a coach brief per week, a short brief
  per day. One plays at a time; changing week or day stops playback.
- Video chapters play inside the page from a start to an end time.

## 10. Content rules

- Activity text comes from the program brief unchanged: mission, skill,
  keep-and-share. The mission is shown as one step per sentence with the
  opening verb bold. Nothing is paraphrased or expanded on the card.
- Spoken briefs are where the coaching lives: easy going, concrete, one
  example, under 50 seconds a day and under 30 seconds a week.
- No em dashes in copy. Dates written in words on cards ("Wed · Nov 18").
- No icons or emoji on cards; numbers do the work.

## 11. Voice

ElevenLabs, voice "Kristen" (warm, relaxed, American, made for tutorials),
model eleven_v4. Scripts kept in `audio/scripts.json` beside the files.

## 12. Responsive breakpoints

- 1120px: card body drops to one column; row height 600px.
- 900px: band becomes one column; nav hides; day row becomes a stacked list
  with the open day expanded in place; action buttons move under the title.
- 720px: tighter gutters (18px); header shows the logo and date only.
