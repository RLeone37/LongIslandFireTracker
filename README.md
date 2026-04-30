# 🔥 New York Working Fires

A live web dashboard tracking Nassau County (and soon Suffolk County) Volunteer Fire Department working fire incidents from 2016 to present.

**Live site:** https://rleone37.github.io/nassau-fires
**Data source:** [zone2photo.com/Working-Fire-Lists](https://www.zone2photo.com/Working-Fire-Lists/)

-----

## 📊 Dashboard Features

- **Overview** — Annual totals, battalion breakdown, monthly averages
- **Trends** — Year-over-year analysis with rolling averages
- **Battalions** — Totals and monthly patterns per battalion (Battalions 1–9)
- **Heatmap** — Color-coded monthly fire frequency by year
- **Departments** — All 69 departments ranked, sortable, and searchable
- **In Progress** — Live year tracking with automatic projection based on historical averages
- **Update Tool** — Helper to generate correct values when entering new data
- **County Switcher** — Toggle between Nassau and Suffolk (Suffolk coming soon)

-----

## 📁 File Structure

```
nassau-fires/
├── index.html    ← The entire web app AND all fire data in one file
└── README.md     ← This file
```

> All fire data is embedded directly inside `index.html`. There is no separate data file.

-----

## ✏️ How to Update Fire Data

### When new fires are reported on zone2photo.com:

1. Go to your repository on GitHub
1. Click `index.html`
1. Click the **✏️ pencil icon** to edit
1. Press **Ctrl+F** and search for the department name (e.g. `720 Hempstead`)
1. Find the line for the correct year that looks like:
   
   ```
   "720 Hempstead":[2,1,3,0,1,2,0,1,0,2,1,3]
   ```
1. Update the number for the correct month — **Jan = first number, Dec = last**
1. Click **Commit changes** → **Commit changes** again
1. Site updates automatically within ~60 seconds

### Or use the built-in Update Tool tab in the dashboard:

1. Open the dashboard → click **✏️ Update Data** tab
1. Select the year and department
1. Enter the monthly counts
1. Click **Generate** then **Copy to Clipboard**
1. Paste into `index.html` on GitHub, replacing the old line for that department

-----

## 📋 Data Format

Each department has 12 numbers — one per month inside the `nassau` section:

```
"720 Hempstead": [2, 1, 3, 0, 1, 2, 0, 1, 0, 2, 1, 3]
//                Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec
```

-----

## 📅 Adding a New Year (e.g. 2027)

1. Open `index.html` on GitHub → ✏️ Edit
1. Press **Ctrl+F**, search for `years_in_progress`
1. Change `[2025,2026]` to `[2025,2026,2027]`
1. Search for `"2026":{` inside the nassau years section and copy that entire block
1. Paste it below and rename `"2026"` to `"2027"`
1. Set all monthly values back to `0`
1. Commit

-----

## 🏙️ Adding Suffolk County Data

Suffolk County is built into the dashboard and ready to activate. When you have the data:

1. Send the Suffolk fire data file
1. It will be parsed and embedded into the same `index.html`
1. The Suffolk button in the top-right header will become active

-----

## 📬 Data Coverage

|County |Years    |Status                        |
|-------|---------|------------------------------|
|Nassau |2016–2024|✅ Complete                    |
|Nassau |2025     |⏳ In progress — update monthly|
|Nassau |2026     |⏳ In progress — update monthly|
|Suffolk|—        |🔜 Coming soon                 |

**69 departments** across **9 battalions** — Nassau County, NY