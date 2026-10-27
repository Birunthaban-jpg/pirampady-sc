# Pirampady SC Subscriptions

An installable, offline-first web app for running the monthly subscription register of **Pirampady Sports Club** (Jaffna, Sri Lanka).

Members pay Rs. 650 a month. Some pay part of it, some pay ahead. The club also pays an electricity bill each month, signed for by the provider. This app replaces the paper register:

- **Month view:** record a full payment with one tap, record part payments, and complete them later with one tap.
- **Whole-year view:** the full register, with each member's total paid and what is still due.
- **Automatic sums:** total collected, electricity paid, balance in hand, and dues counted from the club's start month up to the current month.
- **Electricity bill and signature** recorded for each month.
- **A4 landscape PDF** of the filled register (club logo, ticks, totals), shared straight to WhatsApp from a phone.
- **Backup and restore** with a single JSON file, plus a CSV export for Excel.
- **Works fully offline**, and the data never leaves the device.

## How it works

| Part | Approach |
|---|---|
| App shell | One `index.html` with plain JavaScript, no framework or build step |
| Offline | Service worker (`sw.js`) caches the app, fonts and libraries on first visit |
| Install | Web app manifest and icons, so it can be added to the iPhone home screen or the Mac Dock |
| Storage | `localStorage`, with each record stored under a path like `payments/2026-m01` |
| Part payments | Each month keeps a list of payments (amount and date); the month total is their sum |
| Dues | `fee × months owed so far − paid this year`, counted per member and never below zero in the total |
| PDF | [jsPDF](https://github.com/parallax/jsPDF) and [jsPDF-AutoTable](https://github.com/simonbengtsson/jsPDF-AutoTable), bundled in `vendor/` |
| Fonts | Barlow and Barlow Condensed (SIL Open Font License), bundled in `fonts/` |

## Run it

It is hosted with GitHub Pages. To run it locally:

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

The service worker only runs over `https://` or `localhost`.

## Releasing an update

Change `VERSION` in `sw.js` whenever files change. Installed copies then show an **Update** button.
