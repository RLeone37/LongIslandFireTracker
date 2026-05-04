# Long Island Fire Tracker

**Current version: v2.0.7**

A static GitHub Pages dashboard for tracking Nassau and Suffolk County working fire counts by year, month, battalion/division, and department.

## iOS Web App (Add to Home Screen)

The dashboard can be installed on an iPhone or iPad as a full-screen web app:

1. Open the live site in **Safari**: https://rleone37.github.io/LongIslandFireTracker/
2. Tap the **Share** button (box with an arrow pointing up) in the Safari toolbar.
3. Scroll down and tap **Add to Home Screen**.
4. Edit the name if desired (e.g. "LI Fire Tracker"), then tap **Add**.
5. The app icon will appear on your Home Screen and launch in full-screen mode without the Safari browser chrome.

> **Note:** Add to Home Screen only works in Safari on iOS. It will not appear as an option in Chrome or other iOS browsers.

## Links

- **Live site:** https://rleone37.github.io/LongIslandFireTracker/
- **Dev preview:** https://raw.githack.com/rleone37/LongIslandFireTracker/dev/index.html

## Files

- `index.html` — the dashboard application
- `fires.json` — the data file loaded by the dashboard

## Tabs

| Tab | Description |
|-----|-------------|
| **Overview** | Summary stat cards, annual totals bar chart, battalion/division share donut, average monthly pattern, and stacked-by-division chart |
| **Trends** | Year-over-year line and bar charts, battalion average bar chart, and a detailed annual trends table |
| **Battalions/Divisions** | Fire totals broken down by battalion or division, filterable by year, with monthly breakdown charts and a summary table |
| **Monthly Grid** | Full county monthly fire grid by year with an Avg row; secondary grid filterable by battalion/division |
| **Departments** | Sortable, searchable department table with per-year totals, averages, trends, peak years, and zero-fire year counts |
| **In Progress** | Live-year tracking with projected full-year totals based on historical averages, plus range comparison against historical min/avg/max |
| **Records** | All-time records for the county, individual departments, and each calendar month |
| **Compare** | Side-by-side year-to-year comparison with monthly and battalion/division breakdowns |
| **Update Data** | Password-protected data entry form for adding or correcting monthly fire counts |

## Data format

`fires.json` structure:

```json
{
  "metadata": {
    "last_updated": "2025-12-31",
    "years_complete": [2016, 2017, 2018, 2019, 2020, 2021, 2022, 2023, 2024, 2025],
    "years_in_progress": [2026]
  },
  "counties": {
    "nassau": {
      "name": "Nassau County",
      "departments": [],
      "years": {}
    },
    "suffolk": {
      "name": "Suffolk County",
      "departments": [],
      "years": {}
    }
  }
}
```

Each department entry under `years` uses a 12-number monthly array (January through December):

```json
"720 Hempstead": [1, 2, 0, 1, 0, 3, 1, 1, 2, 4, 0, 2]
```

## Updating data

1. Open `fires.json` in GitHub.
2. Search for the department name, e.g. `720 Hempstead`.
3. Update the 12 monthly values.
4. Update `metadata.last_updated` to the actual date of the last data entry.
5. Commit the change.

Data-only updates to `fires.json` can be committed directly to `main`. All `index.html` changes should go through `dev` first.

## Deployment

Place `index.html` and `fires.json` in the same GitHub Pages directory. If using a `/docs` folder or a separate branch for Pages, both files must be present in that published location.

## Versioning

This project follows [Semantic Versioning](https://semver.org/): `vMAJOR.MINOR.PATCH`

| Part | When to bump | Example |
|------|-------------|---------|
| **MAJOR** | Breaking change to `fires.json` format, or complete UI overhaul | `v2.0.0` → `v3.0.0` |
| **MINOR** | New tab, new chart, or new feature | `v2.0.7` → `v2.1.0` |
| **PATCH** | Bug fix, label tweak, or cosmetic change | `v2.0.6` → `v2.0.7` |

Update the version number in two places when releasing:
- The version line at the top of this README
- The comment at the top of `index.html`: `<!-- Long Island Fire Tracker vX.X.X | YYYY-MM-DD -->`

## Branch strategy

- **`main`** — live production branch, served by GitHub Pages. Never develop directly here.
- **`dev`** — working branch for all features and UI changes. Test locally, then merge to `main`.
- **`hotfix/xyz`** — for urgent fixes branched off `main` when needed.

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for full version history.

## License

© 2026 RLeone37. All rights reserved. See [LICENSE](LICENSE) for details.

This project is not open source. No part of the code, data, or documentation may be copied, modified, or used in any form without explicit written permission from the author.
