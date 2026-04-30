# 🔥 Long Island Fire Tracker

A live web dashboard tracking Nassau County (Suffolk coming soon) Volunteer Fire Department working fire incidents from 2016 to present.

**Live site:** https://rleone37.github.io/nassau-fires  
**Built by:** Robert Leone

-----

## 📊 Dashboard Tabs

|Tab          |Description                                                                  |
|-------------|-----------------------------------------------------------------------------|
|📊 Overview   |Annual totals, battalion share, monthly averages, stacked trends             |
|📈 Trends     |Year-over-year analysis, rolling averages, battalion comparisons             |
|🚒 Battalions |Totals and monthly patterns per battalion with sparklines                    |
|🌡️ Heatmap    |Color-coded monthly fire frequency by year, current month highlighted        |
|🏠 Departments|All 69 departments with sparklines, trend arrows, best year, zero-fire counts|
|⚡ In Progress|Live 2026 tracking with automatic year-end projection                        |
|🏆 Records    |All-time county and department records, monthly peaks, zero-fire streaks     |
|⚖️ Compare    |Side-by-side comparison of any two years with department-level diffs         |
|🔒 Update Data|Passcode-protected data entry tool                                           |

-----

## 📁 File Structure

```
nassau-fires/
├── index.html    ← Entire web app + all fire data in one file
└── README.md     ← This file
```

> All fire data is embedded directly inside `index.html`. There is no separate data file.

-----

## ✏️ How to Update Fire Data

1. Go to your GitHub repository
1. Click `index.html` → click the **✏️ pencil icon** to edit
1. Press **Ctrl+F** and search for the department name (e.g. `720 Hempstead`)
1. Find the line for the correct year:
   
   ```
   "720 Hempstead": [2, 1, 3, 0, 1, 2, 0, 1, 0, 2, 1, 3]
   //                Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec
   ```
1. Update the number for the correct month
1. Click **Commit changes** → **Commit changes** again
1. Site updates automatically within ~60 seconds

### Using the built-in Update Tool

Open the dashboard → click **🔒 Update Data** → enter passcode → select year and department → enter monthly counts → click **Generate** → **Copy to Clipboard** → paste into GitHub.

-----

## 📋 Data Format

12 numbers per department, one per month (Jan = first, Dec = last):

```json
"720 Hempstead": [2, 1, 3, 0, 1, 2, 0, 1, 0, 2, 1, 3]
```

-----

## 📅 Adding a New Year (e.g. 2027)

1. Open `index.html` on GitHub → ✏️ Edit
1. Ctrl+F → search `years_in_progress`
1. Change `[2026]` to `[2026,2027]`
1. Search for `"2026":{` inside the nassau years section
1. Copy that entire block, paste below it, rename `"2026"` to `"2027"`
1. Set all monthly values to `0`
1. Also add `2026` to `years_complete` and update `last_updated`
1. Commit

-----

## 🏙️ Adding Suffolk County Data

Suffolk County is built into the dashboard and ready to activate. When data is available, send the source file and it will be parsed and embedded — the Suffolk button in the header will become fully active.

-----

## 📬 Data Coverage

|County |Years    |Status       |
|-------|---------|-------------|
|Nassau |2016–2025|✅ Complete   |
|Nassau |2026     |⏳ In progress|
|Suffolk|—        |🔜 Coming soon|

**69 departments · 9 battalions · Nassau County, NY**