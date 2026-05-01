# Long Island Fire Tracker

A static GitHub Pages dashboard for tracking Nassau County fire counts by year, month, battalion, and department.

## Files

- `index.html` — the dashboard application.
- `fires.json` — the data file loaded by the dashboard.

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

## Recent changes

- Removed rolling-average wording, chart lines, and table columns from the index.
- Monthly Fire Grid now highlights only the current month name in the header, not the whole column.
- Battalion Monthly Grid now includes an `Avg` row matching the Monthly Fire Grid style.
- Header date changed to `Last data update:`.
- Dashboard now attempts to load `fires.json` with `cache: no-store` and shows a clear error message if the file is missing or invalid.

## Deployment notes

Place `index.html` and `fires.json` in the same GitHub Pages directory. If using a separate branch or `/docs` folder for Pages, both files must be in that published location.
