# Pirampady SC Subscriptions

An installable, offline-first web app for running the monthly subscription register of **Pirampady Sports Club** (Jaffna, Sri Lanka).

Members pay a monthly fee (Rs. 650 at the start; it can change from any month). Some pay part of it, some pay ahead. The club also pays an electricity bill each month, signed for by the provider. This app replaces the paper register:

- **Five sections:** Home, Members, Payments, Reports and More, in a bottom bar on the phone and a sidebar on the Mac.
- **Home:** cash in hand first, then money collected, spent and still due, this month's collection progress, money in and out for each month of the year, and the latest payments, bills and expenses.
- **Members:** search by name, filter by owing, paid up or paid ahead, and open any member for their balance, month-by-month status, payment history with receipts, and their slip.
- **Payments (month view):** record a full payment with one tap, record part payments, and complete them later with one tap.
- **Extra payments carry forward:** paying Rs. 750 against Rs. 650 marks the month paid and puts Rs. 100 towards the next month; a large advance fills the following months in order. Every month's total counts only the money used for that month, so the Rs. 100 is counted in the next month's total, never twice. The monthly account shows extra still held for later months separately.
- **Reports:** the yearly register PDF, member slips, the monthly account, expense and event bills, the CSV export, and the whole-year view: the full register, with each member's total paid and what is still due.
- **Automatic sums:** total collected, electricity paid, balance in hand, and dues counted from the club's start month up to the current month.
- **Electricity bill and signature** recorded for each month, with the date paid and an optional note.
- **Monthly account slip** (A5 PDF) for the whole club: the electricity bill, the month's collections (totals only, no names) and the calculation, from the balance brought forward to the balance in hand.
- **A4 landscape PDF** of the filled register (club logo, ticks, totals), shared straight to WhatsApp from a phone.
- **Club expenses:** ground maintenance, sports equipment (balls, nets), events and other costs. One bill can hold several items (for example grass cutting, petrol and a broom stick), each with its own amount and an automatic total. Saving an expense makes an **expense bill** (A6 PDF) listing the items, with a bill number and the club balance before and after, and every total includes it.
- **Events and tournaments:** each event's money is kept separate: members' contributions, sponsors and others, and its costs. Each event settles with the club balance: if the money isn't enough, the rest is taken from the club (saved as a club expense in the event's month, bill number matching the event, e.g. EVT-2611-ABCD → EXP-2611-ABCD); if money is left over, it is added to the club as other income (INC-2611-ABCD). Both follow the event as money comes in and can be switched off per event. An event bill (A5 PDF) shows who gave, what was spent, what came from the club and what is left.
- **Birthday fund:** cake money is kept completely separate from the subscription account. Each birthday records who gave how much (members and guests), what was spent (cake, candles...), and makes a birthday bill (A5 PDF); leftovers carry over to the next birthday.
- **PDF receipts** (A6) for each payment, with a receipt number, who collected the money and the member's balance.
- **PDF slips** (A5) for each member, sent one by one through WhatsApp, so every member sees only their own payments and dues; all slips can also be saved as one PDF for printing. A plain-text version is available too.
- **Styled signatures:** the collector's (e.g. *Y.Birunthaban*) on every receipt, slip and bill, and an "Accounts checked by" signature (e.g. *Kajenthirakumar*) on the monthly account, expense bills and the register, each in a choice of five script styles.
- **Private members:** a member can ask not to be named; the shared PDF shows their money as "Private contributions" so the totals still add up.
- **Inactive members:** mark someone who stopped coming as inactive from a chosen month. No fee is counted while they are inactive and they move out of the month's collection list (named underneath it instead). Every member keeps their name on the register and the PDFs; those months simply show "-" (no fee), and nothing shared with members calls anyone inactive. Unpaid months before still count. When they come back, the months in between stay free.
- **Across years:** money paid ahead carries into the next year, and anything still owed from an earlier year is brought forward into "Still due". A "Before <year>" column shows it on the sheet and the register when anyone has it.
- **Backup and restore** with a single JSON file, plus a CSV export for Excel.
- **Phone and Mac share one register**, synced through a private GitHub repository, and every change is kept as a version you can restore.
- **Two people, one register:** the collector and the accounts checker can both record on their own phones with their own access keys. Payments are merged one at a time (by receipt number), so separate payments recorded before a sync are never lost. If the same payment was changed differently on two phones, Home asks someone to choose the right version.
- **Change history:** every payment, expense, electricity bill and cash count is logged with who did it, when and the old amount. Deleting a payment cancels it instead: it stops counting but stays visible as cancelled.
- **Cash count:** enter the cash counted by hand and the app compares it with cash in hand, saving the result with the date and who counted.
- **Double-entry warnings:** typing the same amount again for the same member and month asks first, and the same payment recorded on two phones is flagged on Home ("Cancel the second" or "Both are right").
- **Bills & receipts page:** every receipt, expense bill, electricity bill, event and birthday bill, monthly account, donation receipt and handover voucher for the year, with search by number and filters (type, month, status, person). Bills are made again from the records when opened, so no PDFs are stored.
- **Check a bill:** receipts and bills carry a QR code and a 4-letter check code worked out from what the bill says. The QR code is a link to the app, so a phone's own camera opens it and the app checks the bill straight away (a browser without the register says where to check it). Typing the number and code, or photographing the QR code inside the app, shows whether the paper is genuine, changed since it was printed, cancelled, or not in the register.
- **Monthly approval:** the accounts checker approves a month, which saves its figures with the name and date. If anything in that month changes later, the month, Home and the account PDF show "Changed after approval" with the difference.
- **Donation receipts (DON-) and cash handover vouchers (HO-):** donations count as other income in the club balance; a handover records who holds the club cash (or a bank deposit) without changing the balance, signed by both people.
- **Each person's own signature:** receipts and expense bills carry the signature of whoever collected or paid, and the accounts checker can mark an expense **Checked** (any later change to the bill removes the mark).
- **App styles:** Elite (obsidian black, champagne gold and off-white; the main style), Classic (follows the phone's light or dark mode), Floodlight (a night stadium in club gold), Scoreboard (match-day kit) and Pearl (light frosted glass). Chosen in Settings for each device. PDFs use an obsidian header band with champagne-gold accents on white paper, so they print cleanly; the TO PAY and PAID UP stamps stay red and green.
- **Works fully offline.** Changes are saved on the device first and synced once it's back online.
- **Safe amounts:** amounts are whole rupees. "1,500", "Rs. 1500", "1500/-" and "1500.00" all mean Rs. 1,500; an amount with cents is refused with a clear message, never read as a different amount.
- **Changed on two phones:** if both phones change the same expense, event, birthday, donation, member or the settings before they sync, the newer change is used and Home asks which one is right (both are kept until someone chooses). Electricity bills for different months, and separate payments, are always both kept.
- **A new month while the app is open:** the app starts again by itself when the month changes, so "this month", "this year" and the dues move on.

## How it works

| Part | Approach |
|---|---|
| App shell | One `index.html` with plain JavaScript, no framework or build step |
| Offline | Service worker (`sw.js`) caches the app, fonts and libraries on first visit |
| Install | Web app manifest and icons, so it can be added to the iPhone home screen or the Mac Dock |
| Storage | `localStorage`, with each record stored under a path like `payments/2026-m01` and stamped with its last-change time |
| Sync | GitHub Contents API on a **private** data repo (`register.json`). Each sync reads the file, merges record by record, and writes back with the file's `sha`, so a save made at the same moment by the other device is merged again, never overwritten. Payments merge payment by payment and electricity month by month. For other records the app remembers when each one last matched the online copy (`psc.syncbase.v1`): changed on one phone, the newest change wins; changed on both, the newer is used and both are kept in `conflict/<id>` for someone to choose. A change is always stamped later than the version it replaces, so a phone whose clock is behind can't lose its change; a restored backup or version wins over older copies |
| History | `log/<id>` records (who, device, what, old and new amount); cancelled payments stay in the payment record under `x`; cash counts in `cash/<id>` |
| Version history | Every sync is a commit; the app lists them and can restore any version |
| Access | A fine-grained personal access token limited to the data repo (Contents: read and write), kept only on the user's devices |
| Part payments | Each month keeps a list of payments (amount, date, receipt number, collector); the month total is their sum |
| Receipts and slips | PDFs drawn on the device with jsPDF and handed to the share sheet (Web Share API) so they can be sent in WhatsApp; text versions open the member's chat with a `wa.me` link |
| Privacy | No member data is in this public repository; it lives only in the private data repo and on the user's devices |
| Carry forward | Each month is covered by its own payments plus any extra left from earlier months (`covered = min(fee, paid + carried)`), so only extras move forward and shortfalls stay on their month. Months with no fee (before joining, or inactive) use nothing and pass money on. A year starts with the extra left at the end of the year before |
| Month totals | A month's total is the money used for it (`covered`), so paid-in-full plus part payments always equal the total, and every rupee is counted once. "Balance in hand" on the dashboard is the cash held; the monthly account shows the club balance plus any extra held for later months |
| Monthly fee | A list of fees, each starting from a month (`settings.fees`: `"2026"` = from January 2026, `"2026-11"` = from November 2026). Every month uses the fee in force that month, so a new fee never changes earlier months or payments already made |
| Dues | The unpaid part of every month owed so far, plus fees left unpaid in earlier years. A member who owes nothing and has money in later months shows as paid ahead |
| Inactive months | Each member keeps a list of inactive periods (`from` month, `back` month or open). Those months are left out of the months owed; money paid in them is carried forward like any extra |
| QR codes | [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) (MIT) draws the codes on PDFs; [jsQR](https://github.com/cozmo/jsQR) (Apache-2.0) reads them from a photo, loaded only when scanning. Both in `vendor/` |
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
