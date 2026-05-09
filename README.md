# ETF Tracker

A personal ETF investment tracker built as a single-file mobile web app. Designed to be used from your phone's home screen — no login, no account, no app store required.

Built with plain HTML, CSS, and JavaScript. Styled using the Claude / Anthropic brand colour palette.

---

## Features

### Overview
- Monthly progress dashboard with a completion ring
- Per-ETF progress bars showing spent vs. target
- Invested and remaining totals for the current month
- Navigate back through past months with the arrow controls
- Clear the current month's buys directly from this page

### Buy
- Record a buy with ETF, units, amount, currency, and date
- Both units and amount are required fields
- Date defaults to today — change it to backdate historical buys (automatically files to the correct month)
- "Needs attention" chips show which ETFs are furthest from target
- Currency label updates dynamically (AUD or USD) based on the selected ETF

### History
- Full buy log grouped by month, newest first
- Edit any transaction (ticker, units, amount, currency, date)
- Delete any transaction
- Export all history as a CSV file with columns: Record ID, Date, Month, ETF, Units, Amount, Currency

### Targets
- Set a monthly dollar target per ETF
- Allocation % calculated live next to each target
- Toggle currency (AUD / USD) per ETF
- Add new ETFs with ticker, currency, and target
- Delete ETFs (history is preserved)
- Reset all targets to $0

---

## Record IDs

Each buy is assigned a unique ID in the format `YYYYMMDD-NNN`, e.g. `20260509-001`. The sequence resets each day. This ID is included in CSV exports for reconciliation.

---

## Data storage

All data is stored in your browser's `localStorage`. This means:

- Data is private and stays on your device
- Data persists across sessions as long as you don't clear your browser storage
- Data does **not** sync across devices
- If you clear your browser/app data, your history will be lost — export a CSV regularly as a backup

---

## Hosting

This app is a single `index.html` file hosted on GitHub Pages.

**Live URL:** `https://yourusername.github.io/etf-tracker`

To update: replace `index.html` in this repo with the new version and commit. GitHub Pages rebuilds automatically within ~60 seconds.

---

## Tech stack

- Plain HTML / CSS / JavaScript — no frameworks, no build step
- [DM Sans](https://fonts.google.com/specimen/DM+Sans) and [DM Mono](https://fonts.google.com/specimen/DM+Mono) via Google Fonts
- Colour palette based on Anthropic / Claude brand colours (`#faf9f5`, `#141413`, `#d97757`)
- Mobile-first layout, max 430px wide, optimised for iPhone Safari
- `apple-mobile-web-app-capable` — add to home screen for full-screen experience

---

## Adding to iPhone home screen

1. Open the app URL in **Safari**
2. Tap the **Share** button (box with arrow)
3. Tap **Add to Home Screen**
4. Tap **Add**

The app opens full screen with no browser chrome, like a native app.

---

## Updating the app

1. Get the latest `index.html` from Claude
2. Go to this repo on GitHub
3. Click `index.html` → click the **pencil icon** to edit
4. `Cmd+A` / `Ctrl+A` to select all → paste the new file
5. Write a descriptive commit message (e.g. `Add price per unit field`)
6. Click **Commit changes**
7. Optionally: go to **Releases** → create a new release tag (e.g. `v1.2`)

---

## Releases

See [CHANGELOG.md](./CHANGELOG.md) for a full version history.
