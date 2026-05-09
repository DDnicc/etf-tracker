# Changelog

All notable changes to ETF Tracker are documented here.

Format: `vMAJOR.MINOR` — Minor = new feature or improvement. Major = significant rebuild.

---

## v1.0 — Initial release
*May 2026*

First full working version of the ETF Tracker.

**Features shipped:**
- Overview dashboard with monthly progress ring and per-ETF progress bars
- Buy screen with ETF selector, units, amount, currency (AUD/USD), and date field
- Date field defaults to today; backdating files the buy to the correct month automatically
- Suggestion chips showing ETFs furthest from monthly target
- History screen grouped by month with edit and delete per transaction
- CSV export with Record ID, Date, Month, ETF, Units, Amount, Currency columns
- Record IDs in `YYYYMMDD-NNN` format (e.g. `20260509-001`)
- Targets screen with monthly $ target, allocation % per ETF, and currency toggle
- Add and delete ETFs dynamically
- Reset all targets to $0
- Clear current month's buys from Overview page
- Data persisted in browser localStorage
- Styled with Claude / Anthropic brand colour palette (`#faf9f5`, `#141413`, `#d97757`)
- DM Sans + DM Mono typography
- Mobile-first layout, add-to-home-screen capable on iPhone Safari

**Default ETFs configured:**
- IVV (AUD), VGE (AUD), QQQM (USD), IWLD (AUD), VHY (AUD), GOLD (AUD)

---

## How to update this file

When you release a new version, add a new section at the top following this format:

```
## v1.1 — Short description of what changed
*Month Year*

- What was added
- What was fixed
- What was removed or changed
```

Keep the most recent version at the top.
