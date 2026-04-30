# 🔥 Nassau County Working Fires

A live web dashboard tracking Nassau County Volunteer Fire Department working fire incidents from 2016 to present.

**Data source:** [zone2photo.com/Working-Fire-Lists](https://www.zone2photo.com/Working-Fire-Lists/)

-----

## 📊 Dashboard Features

- **Overview** — Annual totals, battalion breakdown, monthly averages
- **Trends** — Year-over-year analysis with rolling averages
- **Battalions** — Totals and monthly patterns per battalion (Battalions 1–9)
- **Heatmap** — Color-coded monthly fire frequency by year
- **Departments** — All 70 departments ranked and searchable
- **2025/2026** — In-progress year tracking with automatic projection based on historical averages
- **Update Tool** — Helper to generate the correct JSON when entering new data

-----

## 🛠️ Setup (First Time Only)

### Step 1 — Create a GitHub Account

If you don’t have one: [github.com/signup](https://github.com/signup)

### Step 2 — Create a New Repository

1. Click the **+** icon (top right) → **New repository**
1. Name it: `nassau-fires`
1. Set it to **Public**
1. **Do not** check “Add README” (you already have one)
1. Click **Create repository**

### Step 3 — Upload Your Files

1. On the new empty repo page, click **uploading an existing file**
1. Upload `index.html` and `README.md`
1. Click **Commit changes**
1. Then click **Add file → Create new file**
1. Name it: `data/fires.json` (typing the slash creates the folder automatically)
1. Paste the entire contents of `fires.json` into the editor
1. Click **Commit changes**

### Step 4 — Enable GitHub Pages (Free Hosting)

1. In your repo, click **Settings**
1. Scroll down to **Pages** (left sidebar)
1. Under *Source*, select **Deploy from a branch**
1. Branch: **main** | Folder: **/ (root)**
1. Click **Save**
1. Wait ~60 seconds, then your site is live at:
   `https://YOUR-USERNAME.github.io/nassau-fires`

-----

## ✏️ How to Update Fire Data

### When a new fire is reported on zone2photo.com:

**Option A — Edit directly on GitHub (easiest, no software needed)**

1. Go to your repository on GitHub
1. Click `data` → `fires.json`
1. Click the **pencil icon** ✏️ (top right of file view)
1. Use **Ctrl+F** to find the department name (e.g. `"720 Hempstead"`)
1. Update the number for the correct month (months are in order: Jan=first number, Dec=last)
1. Scroll down → click **Commit changes** → **Commit changes** again
1. Site updates automatically within ~60 seconds

**Option B — Use the built-in Update Tool tab in the dashboard**

1. Open the dashboard → click **Update Data** tab
1. Select the year and department
1. Change the monthly counts
1. Click **Generate JSON** then **Copy to Clipboard**
1. Paste the copied line into `fires.json` on GitHub (replacing the old line for that department)

-----

## 📋 Data Format

`data/fires.json` stores all fire counts. Each department has an array of 12 numbers — one per month:

```json
"years": {
  "2025": {
    "120 Floral Park":  [1, 0, 0, 2, 0, 1, 0, 0, 0, 0, 0, 0],
    "160 Mineola":      [0, 0, 1, 0, 0, 0, 2, 0, 0, 1, 0, 0]
  }
}
```

Index: `[Jan, Feb, Mar, Apr, May, Jun, Jul, Aug, Sep, Oct, Nov, Dec]`

### Adding a New Year (e.g. 2027)

1. Open `fires.json` on GitHub
1. Find `"years_in_progress"` near the top and add the new year: `[2026, 2027]`
1. Copy the entire `"2026": { ... }` block, paste it below, and rename it `"2027"`
1. Set all monthly values back to `0`
1. Commit

-----

## 📁 File Structure

```
nassau-fires/
├── index.html        ← The entire web app (single file)
├── data/
│   └── fires.json    ← All fire data — THIS is what you edit
└── README.md         ← This file
```

-----

## 📬 Data Coverage

|Years    |Status                        |
|---------|------------------------------|
|2016–2024|✅ Complete                    |
|2025     |⏳ In progress (update monthly)|
|2026     |⏳ In progress (update monthly)|

**70 departments** across **9 battalions** (Nassau County, NY)