# HB Health Dashboard

Personal blood work tracking dashboard built with vanilla HTML/CSS/JS and Chart.js. Designed for GitHub Pages hosting.

## Pages

- **index.html** — Blood Work Dashboard with trend charts for all parameters (lipids, thyroid, liver, kidney, vitamins, inflammatory markers, CBC) and expert diagnosis
- **diabetes.html** — Diabetes & Complications deep-dive with organ-specific risk assessments, trajectory analysis, and priority action plan
- **tracking.html** — Blood Sugar & BP Tracking with manual entry, file import (Apple Health XML, Google Fit JSON, CGM CSV), and live charts

## Tech Stack

- Vanilla HTML/CSS/JavaScript (no build step)
- Chart.js 3.9.1 (CDN)
- Google Material Design styling
- Google Fonts (Roboto, Google Sans)

## Data

All blood work data lives in `data/bloodwork.json`. To update after new lab results:

1. Open `data/bloodwork.json`
2. Add the new date to the relevant `dates` array
3. Append the new value to each test's `values` array (use `null` if a test wasn't performed)
4. Update `latestValue`, `latestDate`, and `status` fields

## Deployment — GitHub Pages

### First-time setup

```bash
# 1. Navigate to the project folder
cd "Claude Outputs/Himanshu Health/hb-health-dashboard"

# 2. Initialize git repo
git init

# 3. Create .gitignore (optional — nothing to ignore for a static site, but good practice)
echo ".DS_Store" > .gitignore

# 4. Stage all files
git add .

# 5. Initial commit
git commit -m "Initial commit: HB Health Dashboard"

# 6. Create the GitHub repo (using GitHub CLI — install with: brew install gh)
gh repo create hb-health-dashboard --public --source=. --remote=origin

# --- OR if you prefer manual repo creation ---
# Go to https://github.com/new
# Create repo named "hb-health-dashboard" (public)
# Then link it:
# git remote add origin https://github.com/YOUR_USERNAME/hb-health-dashboard.git

# 7. Push to GitHub
git branch -M main
git push -u origin main

# 8. Enable GitHub Pages
gh api repos/{owner}/{repo}/pages -X POST -f source.branch=main -f source.path=/

# --- OR manually ---
# Go to: Settings → Pages → Source: "Deploy from a branch" → Branch: main → Folder: / (root) → Save
```

### Your site will be live at:
```
https://YOUR_USERNAME.github.io/hb-health-dashboard/
```

### Updating the site

```bash
# After editing any files:
git add .
git commit -m "Update: description of changes"
git push
# GitHub Pages auto-deploys within ~60 seconds
```

## Privacy Note

GitHub Free plan requires public repos for GitHub Pages. The data contains personal health information. Options to consider:

- **Accept public** — the URL is obscure and not indexed by default
- **GitHub Pro ($4/mo)** — enables private repo GitHub Pages
- **Add `robots.txt`** — prevents search engine indexing (already done: add a `robots.txt` with `Disallow: /` if desired)

## File Structure

```
hb-health-dashboard/
├── README.md
├── index.html          # Blood Work Dashboard
├── diabetes.html       # Diabetes & Complications
├── tracking.html       # Blood Sugar & BP Tracking
└── data/
    └── bloodwork.json  # All lab data
```
