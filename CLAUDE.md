# ETF Tracker

Single-file mobile web app: `index.html` is the entire thing — HTML, CSS, and JS inline, no build step, no framework, no dependencies. Keep it that way; don't introduce tooling, bundlers, or frameworks unless explicitly asked.

## Deploy

Hosted on GitHub Pages. Deploy is: commit `index.html`, push to `main`. A GitHub Actions workflow auto-deploys on push — no manual build or upload step.

## Data

Everything lives in `localStorage` under the key `etf_v2`. No backend, no sync. State shape includes `transactions`, `targets`, `targetHistory`, `archivedTickers`, among others — read `defaultState()` for the full shape rather than assuming it's stable.

## Target history is prospective, not retroactive

Monthly $ targets per ETF are versioned in `state.targetHistory[ticker]` (a list of `{month, value}`), not read as a flat `state.targets[ticker]`. Any month-specific calculation — dashboard progress, rollover, holding accrual — must resolve the target via `targetForMonth(ticker, y, m)`, which returns whichever value was in effect for that month. `state.targets[ticker]` only holds the *current* convenience value shown in the Settings UI.

This split is deliberate: changing a target must only affect the month it's changed in onward. Past months keep whatever target was in effect at the time. If you touch target math, resolve it through `targetForMonth`, not a flat lookup — reverting to flat `state.targets[t]` for historical month math reintroduces a real bug (editing an allocation used to silently rewrite every past month's numbers).

## Archive, don't delete

Removing an ETF from the active list goes through `state.archivedTickers`, not deletion. Archived tickers keep their settings, targets, and currency so they can be restored. Permanent deletion (losing config for good) is a separate, explicit action — don't collapse the two.

## Confirm-bar history

`executeConfirm()` must capture `_confirmCallback` into a local variable *before* calling `dismissConfirm()`. `dismissConfirm()` nulls `_confirmCallback` as a side effect — capturing after calling it was a real bug that made every Confirm-bar action (archive, delete, reset, restore) silently no-op. Don't reorder this back.
