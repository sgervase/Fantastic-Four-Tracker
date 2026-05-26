# The Fantastic Four — MLB Betting Tracker

https://sgervase.github.io/Fantastic-Four-Tracker/

A live MLB betting dashboard that reads directly from a Google Sheet and displays stats, charts, and team analysis.

## Description

The Fantastic Four is a single-file web dashboard built for tracking daily MLB bets. It pulls data from a published Google Sheet CSV on every page load, so the tracker updates automatically as bets are entered. The dashboard is organized into four pages: Dashboard (cumulative P/L and form), Analytics (rolling win rate and odds breakdown), Teams (per-team performance cards with a detail modal and live MLB hot/cold data), and History (filterable bet table). It is hosted free on GitHub Pages and requires no server, no login, and no paid software. 

### Google Sheet Column Structure

The tracker reads columns B through N in this order:

* B — Date (e.g. 5/12/2026)
* C — Bet ID (sequential number)
* D — Home Team
* E — Away Team
* F — Team Bet On (leave blank for totals and NRFI)
* G — Player or F5 (enter "First 5 innings" for F5 bets, player name for props)
* H — Over/Under direction (Over or Under)
* I — Line (the number, e.g. 7.5 or -1.5 — leave blank for moneylines)
* J — Market (Total, Side, Spread, or NRFI)
* K — Units staked
* L — Odds in American format (e.g. -110, +150)
* M — Result (w, l, or p — leave blank for pending bets)
* N — Gain/Loss in units (positive or negative)

## Help

If the site loads but shows no data, confirm the Google Sheet is published as CSV (not Web page) and that the correct tab is selected before publishing.

If charts appear blank when switching tabs, click the Refresh button in the header to force a reload.

If the MLB hot/cold section shows unavailable, the MLB Stats API may be temporarily down. The rest of the dashboard is unaffected.

```
The site can always be reset to demo data by clearing the saved URL:
localStorage.removeItem('f4_url') — run this in the browser console
```

## Authors

Built for Frankie Da Capper and the Fantastic Four.

## Version History

* 1.0
    * Four-tab layout: Dashboard, Analytics, Teams, History
    * Live Google Sheets CSV integration
    * Interactive team detail modal with per-team P/L chart
    * MLB Stats API hot/cold team feed

## License

No license — personal project.

## Acknowledgments

* [Chart.js](https://www.chartjs.org/) — charts
* [PapaParse](https://www.papaparse.com/) — CSV parsing
* [MLB Stats API](https://statsapi.mlb.com) — free MLB standings and streak data
* [GitHub Pages](https://pages.github.com/) — free static hosting
