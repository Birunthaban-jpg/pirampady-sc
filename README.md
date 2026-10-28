# Pirampady SC Subscriptions

An installable, offline-first web app for running the monthly subscription register of **Pirampady Sports Club** (Jaffna, Sri Lanka).

Members pay Rs. 650 a month. Some pay part of it, some pay ahead. The club also pays an electricity bill each month, signed for by the provider. This app replaces the paper register:

- **Month view:** record a full payment with one tap, record part payments, and complete them later with one tap.
- **Whole-year view:** the full register, with each member's total paid and what is still due.
- **Automatic sums:** total collected, electricity paid, balance in hand, and dues counted from the club's start month up to the current month.
- **Electricity bill and signature** recorded for each month, with the date paid and an optional note.
- **Monthly account slip** (A5 PDF) for the whole club: the electricity bill, the month's collections (totals only, no names) and the calculation, from the balance brought forward to the balance in hand.
- **A4 landscape PDF** of the filled register (club logo, ticks, totals), shared straight to WhatsApp from a phone.
- **Club expenses:** ground maintenance, sports equipment (balls, nets), events and other costs. Saving an expense makes an **expense bill** (A6 PDF) with a bill number and the club balance before and after, and every total includes it.
- **PDF receipts** (A6) for each payment, with a receipt number, who collected the money and the member's balance.
- **PDF slips** (A5) for each member, sent one by one through WhatsApp, so every member sees only their own payments and dues; all slips can also be saved as one PDF for printing. A plain-text version is available too.
- **Styled signatures:** the collector's (e.g. *Y.Birunthaban*) on every receipt, slip and bill, and an "Accounts checked by" signature (e.g. *Kajenthirakumar*) on the monthly account, expense bills and the register, each in a choice of five script styles.
- **Private members:** a member can ask not to be named; the shared PDF shows their money as "Private contributions" so the totals still add up.
- **Backup and restore** with a single JSON file, plus a CSV export for Excel.
- **Phone and Mac share one register**, synced through a private GitHub repository, and every change is kept as a version you can restore.
- **Works fully offline.** Changes are saved on the device first and synced once it's back online.

## How it works

| Part | Approach |
|---|---|
| App shell | One `index.html` with plain JavaScript, no framework or build step |
| Offline | Service worker (`sw.js`) caches the app, fonts and libraries on first visit |
| Install | Web app manifest and icons, so it can be added to the iPhone home screen or the Mac Dock |
| Storage | `localStorage`, with each record stored under a path like `payments/2026-m01` and stamped with its last-change time |
| Sync | GitHub Contents API on a **private** data repo (`register.json`). Each sync reads the file, merges record by record (newest change wins, deletions travel as tombstones), and writes back with the file's `sha`, so a clash is detected and merged again |
| Version history | Every sync is a commit; the app lists them and can restore any version |
| Access | A fine-grained personal access token limited to the data repo (Contents: read and write), kept only on the user's devices |
| Part payments | Each month keeps a list of payments (amount, date, receipt number, collector); the month total is their sum |
| Receipts and slips | PDFs drawn on the device with jsPDF and handed to the share sheet (Web Share API) so they can be sent in WhatsApp; text versions open the member's chat with a `wa.me` link |
| Privacy | No member data is in this public repository; it lives only in the private data repo and on the user's devices |
| Dues | `fee × months owed so far − paid this year`, counted per member and never below zero in the total |
| PDF | [jsPDF](https://github.com/parallax/jsPDF) and [jsPDF-AutoTable](https://github.com/simonbengtsson/jsPDF-AutoTable), bundled in `vendor/` |
| Fonts | Barlow and Barlow Condensed, plus five script fonts for the signature (Herr Von Muellerhoff, Mrs Saint Delafield, Great Vibes, Alex Brush, Allura), all SIL Open Font License, bundled in `fonts/` |
| Signature | Drawn from the chosen script font onto a canvas, trimmed to the ink and placed into the PDFs as a PNG |

## Run it

It is hosted with GitHub Pages. To run it locally:

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

The service worker only runs over `https://` or `localhost`.

## Releasing an update

Change `VERSION` in `sw.js` whenever files change. Installed copies then show an **Update** button.
