# ⚾ The Fantastic Four — MLB Betting Tracker

A free, shareable betting dashboard that reads live from your Google Sheet.  
No Tableau license. No login required. Anyone with the link can view it.

---

## 🚀 Setup (10 minutes)

### Step 1 — Deploy to GitHub Pages

1. Create a new GitHub repository (e.g. `fantastic-four-tracker`) — set it to **Public**
2. Upload `index.html` to the root of the repo (**Add file → Upload files**)
3. Go to **Settings → Pages → Source → Deploy from branch → `main` / `/(root)`**
4. Click **Save** — your site will be live in ~2 minutes at:  
   `https://YOUR_USERNAME.github.io/fantastic-four-tracker/`

### Step 2 — Publish your Google Sheet as CSV

1. Open the **MLB F4 2026** Google Sheet
2. Go to **File → Share → Publish to web**
3. First dropdown → select the **"MLB F4 2026"** tab (not "Entire document")
4. Second dropdown → change **"Web page"** to **CSV**
5. Click **Publish** → confirm → **copy the URL**

The URL will look like:
```
https://docs.google.com/spreadsheets/d/SHEET_ID/pub?gid=123456789&single=true&output=csv
```

### Step 3 — Connect the sheet

Open the live site → click **⚙ Setup** → paste the URL → click **Load Sheet**.

The browser saves it — anyone who visits sees live data on every page load.

> **To update the dashboard file later:** go to the repo → Add file → Upload files → upload the new `index.html` — GitHub Pages redeploys automatically within a minute.

---

## 📋 Column Reference

The tracker reads these columns from your sheet (positions B through N):

| Col | Field | Notes |
|-----|-------|-------|
| B | Date | e.g. `5/12/2026` |
| C | Bet ID | Sequential number |
| D | Home Team | |
| E | Away Team | |
| F | Team Bet On | Leave blank for totals/NRFI |
| G | Player or F5? | "First 5 innings" or player name for props |
| H | Over/Under | "Over" or "Under" |
| I | Line | Number (7.5, -1.5) — leave blank for moneylines |
| J | Market | `Total`, `Side`, `Spread`, or `NRFI` |
| K | Units | Stake in units (1.0, 0.5, etc.) |
| L | Odds | American odds: -110, +150, etc. |
| M | Result | `w`, `l`, or `p` — leave blank for pending |
| N | Gain/Loss | Units won/lost (positive or negative) |

---

## 📊 Dashboard Pages

### Dashboard
- Today's pending picks highlighted at the top (if any)
- Cumulative units P/L line chart over every settled bet
- Bet type W/L bar chart
- Color-coded form strip grouped by day with hover tooltips

### Analytics
- **Rolling Win Rate** — sliding 5-bet window with a 50% break-even reference line
- **Odds Bracket Performance** — W/L by bet price range (Heavy Fav → Big Dog), hover for ROI
- **Bet Type Breakdown** — full W/L chart by bet category

### Teams
- **Your Team Tracker** — card for every team you've explicitly backed, showing W-L, win %, units P/L, and a mini form strip. Click any card to open a detail modal with that team's full P/L chart and bet history.
- **MLB Hot & Cold** — live data from the free MLB Stats API (no key required), showing teams running 7-3 or better (hot) and 3-7 or worse (cold) in their last 10 games. Teams you've already bet on this season get an amber "On your radar" badge.

### History
- Full filterable bet history table — filter by bet type and result

---

## 📈 Tracking Recommendations

The sheet is solid — these tweaks would unlock deeper analysis:

### 1. Split "Player or F5?" into two columns
Currently this column holds both "First 5 innings" as a game modifier **and** player names for props. Split into:
- **Game Segment**: `Full Game` / `F5`
- **Player Name**: blank for game bets, fill in for props

### 2. Add a Confidence column (1–3)
Rate each pick before the game. After a full season, you can answer: *"Do my 3-star picks actually beat my 1-star picks?"* — the most valuable self-analysis a capper can do.

### 3. Standardize units to simple tiers
Stakes like `0.6666` and `0.7142` make ROI harder to read. Use clean tiers — **0.5u / 1u / 1.5u** — and use the Confidence column for weighting instead.

### 4. Add a Sportsbook column
Track where each bet was placed (DraftKings, FanDuel, BetMGM). Over a full season you'll see if you're consistently getting better prices at one book.

### 5. Add a Closing Line column *(advanced)*
Record the odds at game time next to the odds you got. Beating the closing line consistently is the strongest indicator of long-term edge — better than win percentage alone.

### 6. Use `p` for pushes
Enter `p` in the Result column for any push/refund. The dashboard already handles it, just needs the data.

---

## 🔄 How live updates work

```
Frankie updates the Google Sheet
        ↓
Anyone opens the site URL
        ↓
Browser fetches the published CSV directly from Google
        ↓
Dashboard recalculates all stats and re-renders
        ↓
Everyone sees today's data — no server, no Python, no cost
```

---

## 🛠 Tech Stack

| Tool | Purpose |
|------|---------|
| HTML / CSS / JS | Single-file app, no build step |
| [Chart.js](https://www.chartjs.org/) | All charts |
| [PapaParse](https://www.papaparse.com/) | Google Sheets CSV parsing |
| [MLB Stats API](https://statsapi.mlb.com) | Free, no key — hot/cold team data |
| GitHub Pages | Free hosting, auto-deploys on push |

---

*The Fantastic Four · MLB 2026 · Frankie Da Capper · Est. in Good Faith*
