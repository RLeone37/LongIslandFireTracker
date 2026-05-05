# Changelog

All notable changes to Long Island Fire Tracker are documented here.

This project follows [Semantic Versioning](https://semver.org/): `vMAJOR.MINOR.PATCH`

| Part | When to bump | Example |
|------|-------------|---------|
| **MAJOR** | Breaking change to `fires.json` format, or complete UI overhaul | `v2.0.0` → `v3.0.0` |
| **MINOR** | New tab, new chart, or new feature | `v2.0.7` → `v2.1.0` |
| **PATCH** | Bug fix, label tweak, or cosmetic change | `v2.0.7` → `v2.0.8` |

---

## [v2.0.8] — 2026-05-04

- Battalion/Division Monthly Grid now highlights the current month column header, matching the county-wide Monthly Fire Grid

## [v2.0.7] — 2026-05-03

- Most Active Battalion/Division stat card now auto-scales font size to prevent text from being cut off
- Removed logo from header
- Removed colored dot indicators from all chart and graph titles
- Chart titles upgraded: brighter text color, added bottom border separator
- Chart cards now have a 2px accent-colored top border
- Section headers restyled: CSS bar element replaces text character, fire-orange color, heavier weight
- Battalion/division labels reformatted to ordinal-first across all charts, legends, and tables (e.g. "1st Battalion", "3rd Division") for Nassau and Suffolk
- Battalion/Division Share and Stacked charts now use full spelled-out labels consistent with the above format
- Departments table column header now reads "Battalion" or "Division" depending on county (was abbreviated "Bat.")
- Department names no longer display "F.D." suffix in any table across Nassau and Suffolk
- Most Active Dept stat card (Overview) now correctly strips "F.D." from the displayed department name
- Removed proportional bar indicators from department name cells in the Departments table

## [v2.0.6] — 2026-05-03

- Average Monthly Pattern chart (Overview) peak bar no longer highlights in orange — all bars now uniform blue
- Annual Totals bar chart (Overview) peak bar no longer highlights in red — all bars now uniform blue
- In Progress tab subtitle updated from "Solid = actual" to "Red = actual" for clarity

## [v2.0.5] — 2026-05-03

- Added logo to header beneath title

## [v2.0.4] — 2026-05-03

- Replaced last data update date in header with version number
- Added version comment at top of `index.html`

## [v2.0.3] and earlier

- Battalions tab renamed to Battalions/Divisions
- Most Active Division stat card abbreviates "Division" to "Div" (consistent with "Bn" for Battalion)
- Average Monthly Pattern chart no longer highlights the peak month — all bars use uniform blue
- Removed rolling-average lines and table columns
- Monthly Fire Grid highlights only the current month name in the header
- Battalion Monthly Grid includes an Avg row matching the Monthly Fire Grid style
- Header date label changed to `Last data update:`
- Dashboard loads `fires.json` with `cache: no-store` and shows a clear error if the file is missing or invalid
