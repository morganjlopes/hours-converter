# Hours Converter

A tiny in-browser tool that converts spreadsheet time values between `H:MM` (e.g. `159:21`) and decimal hours (e.g. `159.35`). Drop in an `.xlsx`, `.xls`, or `.csv` and download a converted copy.

**👉 Live demo: <https://morganjlopes.github.io/converter-hours/>**

Nothing is uploaded. Everything happens in your browser.

## Why

Payroll and timesheet exports often format totals as `HOURS:MINUTES` strings, which most accounting systems can't sum or import. This tool flips the whole sheet to decimal hours (or back) without losing the rest of the data.

## Features

- **Two-way conversion** — `H:MM → Decimal` or `Decimal → H:MM`
- **Smart cell detection** — only time-shaped strings or decimal-formatted numbers are touched. Names, phone numbers, dates, integer columns like "Worked days", and zero values pass through untouched
- **Round-trippable** — converted cells get a `0.00` number format so the reverse pass picks them up cleanly
- **No backend** — single static HTML page, no install, no signup, no data leaves your machine
- **Multi-sheet** — every worksheet in a workbook is processed

## Examples

| H:MM    | Decimal |
| ------- | ------- |
| 159:21  | 159.35  |
| 183:39  | 183.65  |
| 78:21   | 78.35   |
| 115:44  | 115.73  |

The math is just `hours + minutes / 60`, rounded to two decimals.

## Use it

Visit <https://morganjlopes.github.io/converter-hours/>, or open [`index.html`](./index.html) locally in any modern browser. Pick a direction, drop your file, and the converted copy downloads automatically. The output filename is `<original> (decimal hours).xlsx` or `<original> (H-MM hours).xlsx`.

## Run locally

```bash
git clone https://github.com/<your-username>/converter-hours.git
cd converter-hours
open index.html        # macOS
# or just double-click index.html
```

No build step. No dependencies to install — [SheetJS](https://sheetjs.com/) is loaded from a CDN.

## Deploy to GitHub Pages

```bash
git init
git add .
git commit -m "Initial commit"
gh repo create converter-hours --public --source=. --push
gh api -X POST repos/:owner/converter-hours/pages \
  -f 'source[branch]=main' -f 'source[path]=/'
```

The site will be live at `https://<your-username>.github.io/converter-hours/` within a minute or two.

## Related

- [Timestamp Converter](https://github.com/morganjlopes/converter-timestamp) — normalize spreadsheet timestamps to UTC and reformat

## Tech

- Plain HTML / CSS / vanilla JS — single file
- [SheetJS (xlsx)](https://github.com/SheetJS/sheetjs) `0.18.5` via jsDelivr
- Inline SVG favicon, no external assets

## License

MIT
