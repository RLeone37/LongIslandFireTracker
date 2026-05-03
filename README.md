# Long Island Fire Tracker

**Current version: v2.0.4**

A static GitHub Pages dashboard for tracking Nassau and Suffolk County working fire counts by year, month, battalion/division, and department.

## Files

- `index.html` — the dashboard application.
- `fires.json` — the data file loaded by the dashboard.

## Tabs

| Tab | Description |
|-----|-------------|
| **Overview** | Summary stat cards, annual totals bar chart, battalion/division share donut, average monthly pattern, and stacked-by-division chart |
| **Trends** | Year-over-year line and bar charts, battalion average bar chart, and a detailed annual trends table |
| **Battalions/Divisions** | Monthly fire grid broken down by battalion or division, with an Avg row |
| **Monthly Grid** | Full county monthly fire grid by year, with an Avg row |
| **Departments** | Sortable, searchable department table with per-year totals, averages, trends, and peak years |
| **In Progress** | Live-year tracking with projected full-year totals based on historical averages |
| **Records** | All-time records for the county, individual departments, and each calendar month |
| **Compare** | Side-by-side comparison of Nassau vs. Suffolk |
| **Update Data** | Password-protected data entry form for adding new fire counts |

## Data format

`fires.json` should include:

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

Each department/year entry uses a 12-number monthly array:

```json
"720 Hempstead": [1, 2, 0, 1, 0, 3, 1, 1, 2, 4, 0, 2]
```

Month order is January through December.

## Updating data

1. Open `fires.json` in GitHub.
2. Search for the department name, for example `720 Hempstead`.
3. Update the 12 monthly numbers.
4. Update `metadata.last_updated` to the actual last data update date.
5. Commit the change.

The dashboard header displays `Last data update:` using `metadata.last_updated`, not the site push/build date.

## Deployment notes

Place `index.html` and `fires.json` in the same GitHub Pages directory. If using a separate branch or `/docs` folder for Pages, both files must be in that published location.

## Versioning

This project uses [Semantic Versioning](https://semver.org/): `vMAJOR.MINOR.PATCH`

| Part | When to bump | Example |
|------|-------------|---------|
| **MAJOR** | Breaking change to `fires.json` format, or complete UI overhaul | `v2.0.0` → `v3.0.0` |
| **MINOR** | New tab, new chart, or new feature added | `v2.0.4` → `v2.1.0` |
| **PATCH** | Bug fix, label tweak, cosmetic change | `v2.0.3` → `v2.0.4` |

Update the version number in two places when releasing:
- The `# Long Island Fire Tracker` header in this README
- The comment at the top of `index.html`: `<!-- LI Fire Tracker vX.X.X | YYYY-MM-DD -->`

### Branch strategy

- **`main`** — live production branch, served by GitHub Pages. Never develop directly here.
- **`dev`** — working branch for all new features and UI changes. Test locally, then merge to `main`.
- **`hotfix/xyz`** — for urgent fixes branched off `main` when needed.

Data-only updates to `fires.json` can be committed directly to `main`. All `index.html` changes should go through `dev` first.

## Recent changes

- Battalions tab renamed to Battalions/Divisions.
- Most Active Division stat card now abbreviates "Division" to "Div" (consistent with "Bn" for Battalion).
- Average Monthly Pattern chart no longer highlights the peak month in orange — all bars now use the uniform blue style matching Nassau.
- Removed rolling-average wording, chart lines, and table columns from the index.
- Monthly Fire Grid now highlights only the current month name in the header, not the whole column.
- Battalion Monthly Grid now includes an `Avg` row matching the Monthly Fire Grid style.
- Header date changed to `Last data update:`.
- Dashboard now attempts to load `fires.json` with `cache: no-store` and shows a clear error message if the file is missing or invalid.
