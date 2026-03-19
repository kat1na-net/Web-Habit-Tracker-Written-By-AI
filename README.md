# Web-Habit-Tracker-Written-By-AI
A personal habit tracker. Because I don't plan on learning web dev myself, I prompted claude to write this for me. 

Color me absolutely impressed - this is something that would have probably taken me hours to do. I do miss the artistic aspect of writing a cheeky web application myself, but in this case my time is finite and I wanted to work on other projects. I am noting that yes, this is written by AI. I had the idea, but did not put in the hours to make it. 

# README written by Claude

# Habit Tracker

A GitHub-style contribution heatmap for tracking daily habits. No backend, no dependencies — just two files. Update a JSON file, push to GitHub, done.

![dark theme heatmap with green contribution squares](https://img.shields.io/badge/theme-dark-0d1117?style=flat-square) ![no dependencies](https://img.shields.io/badge/dependencies-none-39d353?style=flat-square) ![github pages ready](https://img.shields.io/badge/github%20pages-ready-58a6ff?style=flat-square)

## Features

- GitHub-style heatmap showing the past 52 weeks
- Hover any cell to see exactly which habits were done or missed that day
- Per-habit color coding and streak counters
- Stats: current streak, best streak, days logged, average completion rate
- Falls back to demo data if `habits.json` isn't found yet

## Setup

### Local

```
habit-tracker/
├── index.html
└── habits.json
```

Open `index.html` in a browser. That's it.

### GitHub Pages

1. Create a new repository on GitHub
2. Push both `index.html` and `habits.json` to the root of `main`
3. Go to **Settings → Pages → Source** and set it to deploy from the `main` branch, root folder
4. Your tracker will be live at `https://yourusername.github.io/repo-name`

## Logging Habits

Edit `habits.json` directly. The format is:

```json
{
  "habits": ["Thesis", "HTB/LabShock", "Pentest+ Study", "RF Prep", "Exercise"],

  "log": {
    "2026-03-19": ["Thesis", "RF Prep", "Exercise"],
    "2026-03-20": ["Thesis", "HTB/LabShock", "RF Prep", "Exercise"],
    "2026-03-21": ["Thesis"]
  }
}
```

`habits` is the ordered list of all habits you want to track. `log` maps each date (`YYYY-MM-DD`) to an array of habit names completed that day. Dates with no entry are treated as unlogged — distinct from a day where you logged but completed nothing.

### Heatmap color levels

| Habits completed | Color |
|---|---|
| 0 / not logged | Dark gray |
| 1–25% | Dark green |
| 26–50% | Medium green |
| 51–75% | Bright green |
| 76–100% | Full green |

### Adding or renaming habits

Update the `habits` array in `habits.json`. Existing log entries referencing an old name will still appear in hover tooltips; they just won't match any habit card. To avoid orphaned entries, do a find-and-replace on the old name across the `log` object when renaming.

## Workflow

The simplest update loop:

```bash
# at end of day
nano habits.json        # add today's entry
git add habits.json
git commit -m "log: 2026-03-19"
git push
```

GitHub Pages will redeploy automatically within ~30 seconds.

## File Reference

| File | Purpose |
|---|---|
| `index.html` | The entire app — heatmap, stats, tooltip, styling |
| `habits.json` | Your habit definitions and daily log |

No build step, no Node, no package.json.


