# Karoo Crawl — Edition 01

A single-page, self-contained brand site for the Karoo Crawl: a dawn run at
Tierkloof, in the Swartruggens above the Tankwa plains, Western Cape.

**Friday 21 August 2026, 05:00** — two hours and eleven minutes before sunrise.

## What it is

One HTML file. No build step, no dependencies, no network requests. Open
`index.html` in a browser and it runs.

The whole page is a timeline. Scroll position drives a single progress value,
and everything reads off it: the sky gradient, the ridge silhouettes, the star
field fading out, the sun climbing, a rail clock counting 05:58 → 07:40, and the
logo wordmark crossing from white to brand blue as the ground turns cream.

## Structure

| | |
|---|---|
| `index.html` | The entire site — markup, CSS, JS, and the embedded font |
| `logo.svg` | The lockup as standalone vector, inlined into the page |

Inside `index.html`:

- **Sky engine** — six keyframes of sky/ridge colour, smoothstep-interpolated
  and written to CSS custom properties on every scroll frame.
- **Nine-segment LCD** — the alarm clock's display is built from the standard
  seven segments plus two diagonals, so `K` renders as an actual `K`.
- **Temperature panel** — mean August air temperature by hour, plotted over a
  full day against a zero baseline.
- **Star field** — canvas, with a denser diagonal band standing in for the
  Milky Way.

## Data

Temperatures are **climatological, not live**: hourly means for 14–28 August
across 2015–2025 (325 days) from ERA5 reanalysis via
[Open-Meteo](https://open-meteo.com/), sampled at 33.13°S 19.77°E, 649 m.

The coldest hour of the morning is 07:00 — which is essentially sunrise. That
is not a quirk of the averaging; it is how dawn works.

Sunrise/sunset for the date come from the same source.

## Fonts

Headings are set in **Nighty DEMO** by [Dharmas Studio](https://dharmasstudio.com/nighty),
embedded as a base64 `@font-face`.

> ⚠️ **Nighty DEMO is licensed for personal use only.** Commercial use is
> expressly prohibited by the bundled licence, and a commercial or corporate
> licence must be purchased from the foundry for any revenue-generating use —
> including merchandise. If this project ever becomes commercial, license the
> font or swap it out.

The demo cut contains **only A–Z and a–z** — no digits, no punctuation. Numerals
are therefore pinned to a condensed grotesk throughout, and headings are written
without punctuation so nothing falls back mid-sentence.

## Accessibility

- Full `prefers-reduced-motion` support — animation and reveals are disabled.
- The temperature chart carries a visually-hidden data table and a descriptive
  `aria-label`.
- Mark colours were checked for contrast against both the night and cream
  grounds; the wordmark crosses colour precisely because brand blue measures
  2.04:1 on the pre-dawn sky.

## Licence

Code is free to use. The **font and the logo artwork are not** — see above for
the font, and the Karoo Crawl lockup remains the project's own mark.
