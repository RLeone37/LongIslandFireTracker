# Long Island Fire Tracker

A static GitHub Pages dashboard for tracking Long Island fire counts by year, month, and department.

## Files

- `index.html` — the dashboard application.
- `fires.json` — the data file loaded by the dashboard.

## Data format

`fires.json` contains a metadata block and county/department entries:

```json
{
  "metadata": {
    "last_updated": "YYYY-MM-DD",
    "years_complete": [],
    "years_in_progress": []
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

## County structure differences

Nassau and Suffolk use different organizational structures:

- **Nassau** departments are grouped by **battalions**. Department numbers are plain integers (e.g. `720 Hempstead`).
- **Suffolk** departments are grouped by **divisions**. Department numbers use a dashed format (e.g. `1-1-0 Amityville`).

The dashboard detects which structure is in use and adjusts all labels and grouping logic accordingly. Battalion/division filters, charts, and table headers update automatically when switching between counties.

## Department data

Each department/year entry uses a 12-number monthly array (January through December):

```json
"720 Hempstead": [1, 2, 0, 1, 0, 3, 1, 1, 2, 4, 0, 2]
```

## Updating data

1. Open `fires.json` in GitHub.
2. Search for the department name.
3. Update the monthly numbers.
4. Update `metadata.last_updated` to the actual last data update date.
5. Commit the change.

The dashboard header displays `Last data update:` from `metadata.last_updated`, not the site push/build date.

## Deployment notes

Place `index.html` and `fires.json` in the same GitHub Pages directory. If using a separate branch or `/docs` folder for Pages, both files must be in that published location. The dashboard loads `fires.json` with `cache: no-store` and will show an error if the file is missing or invalid.
