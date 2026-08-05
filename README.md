# MahaRECAST

**Maharashtra Cadre Reforms Portal** — a digital home for the Government of Maharashtra's General Administration Department (GAD) cadre data, Recruitment Rules (RR) analysis, and cadre-reform tracking across the state's departments.

Built for the Quality Council of India's Maharashtra Cadre Reforms engagement: turning Recruitment Rules, pay scales, exam schemes and cadre classifications that used to live scattered across departmental files and old Government Resolutions into one searchable, comparable, standardised digital record — currently covering 1,167+ cadres across 44 departments and 101 establishments.

## What's in here

- `index.html` — the public landing page introducing the reform, the "before vs after" story, and headline numbers.
- `dashboard.html` — the working dashboard: Overview, RR Analysis, Compare, Data, Competency/Capability mapping, Links, and Annexure tabs. Loads live cadre data from a published Google Sheet at runtime, and can export views to Excel and Word.
- `rr-generator.html` — a Recruitment Rules generator for drafting department/establishment-specific RR documents in the standard government notification format.
- `landing-map.png`, `landing-seal.png` — imagery used on the landing page.

## Stack

Pure static HTML/CSS/JS. No build step, no backend, no server-side secrets.

- [SheetJS](https://sheetjs.com/) (`xlsx.js`) for reading/writing Excel data client-side
- [Chart.js](https://www.chartjs.org/) for dashboard visualisations
- [`docx`](https://docx.js.org/) (bundled inline) for generating Word documents client-side
- React + Babel Standalone + Tailwind (via CDN) for the RR generator
- Live cadre data comes from a published Google Sheet, fetched as CSV at runtime — see **Data source** below.

## Running it locally

No install, no build required. Serve the folder with any static file server, e.g.:

```bash
npx serve .
```

or open `index.html` / `dashboard.html` directly in a browser. Serving over `http://localhost` (rather than `file://`) is recommended since a couple of features fetch cross-origin data.

## Deployment

Currently deployed on [Vercel](https://vercel.com) as a zero-config static site. Any static host (Vercel, Netlify, GitHub Pages) works out of the box — there's nothing to build.

## Data source

`dashboard.html` and `index.html` fetch cadre data at runtime from a Google Sheet published as CSV (see the `SHEET_ID` constant near the top of the `<script>` block in each file). The sheet must stay shared as "Anyone with the link can view" for the dashboard to load data.

Because that ID lives in client-side code, anyone who opens the deployed dashboard (or reads this repo) can find it — **treat the sheet itself, not this repo, as the sensitive asset.** Don't put anything in it you wouldn't want visible while the dashboard is live.

## Status

Actively evolving. Dashboard theming is mid-rework — RR Analysis and a few remaining tabs are still being migrated to the current warm-ivory visual theme; Overview is done.

---

Maintained by the [Quality Council of India](https://www.qcin.org/) for the Government of Maharashtra's cadre reforms initiative.
