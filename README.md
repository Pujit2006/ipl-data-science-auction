# 🏏 IPL Data Science Auction: The Ultimate Team Builder

An educational browser game where you own an IPL-style franchise, scout players with data science, win them in a live auction and build the strongest squad under a ₹100 crore budget.

> **Data notice:** all players, names and statistics are **synthetic** (seeded random generation). They are **not** official IPL records and do not represent real people. Franchise names are fictional.

## 👥 Team Members

| Name | Roll No. |
|------|----------|
| Pujit Sahu | EC24I2003 |
| Aditya Prasad Misra | EC24I2025 |
| Shlok Prusty | EC24B1033 |

## 🔗 Play the game

**Live link:** `PASTE-YOUR-GITHUB-PAGES-LINK-HERE`

Or download this repository and open `index.html` in any modern browser (Chrome, Edge, Firefox, Safari). No installation, backend, API key or internet connection is needed.

## 🎯 Goal

Build the strongest cricket team with ₹100 crore and finish **#1 of 5** franchises in the season simulation.

## 🎓 Learning objectives

By the end of the game a player should be able to:

1. **Statistics:** calculate and interpret mean, median, standard deviation, minimum and maximum, and explain why consistency matters.
2. **Correlation:** read a Pearson correlation coefficient and a scatter plot, and explain why association is not causation (confounders).
3. **K-means clustering:** explain how K-means groups data, how K and inertia change the result, and how groups reveal undervalued players.
4. **Optimisation:** allocate a limited budget under constraints to get the best combined result, instead of picking the best individuals.

## 🕹️ How to play

1. **Home →** read the goal and start.
2. **Franchise:** pick one of 5 teams, each with a different advantage. The other four become AI rivals with different buying styles.
3. **Data Lab:** scout the 60 synthetic players in four tabs (Statistics, Correlation, Clusters, Optimisation). Star ☆ players to build a target list and complete the five analyst missions.
4. **Auction:** players come up one at a time in three sets (Marquee, Core, Rapid). Press **Bid**, **Jump** or **Pass** before the timer runs out. A card shows who bought each player and for how much. Do not bid above a player's Fair ₹.
5. **Squad Builder:** complete your squad. Unsold players can be signed at base price.
6. **Season:** every team plays every other team twice. Win probabilities come from team-strength calculations, not random winners.
7. **Results:** see your rank, score breakdown, an analyst report card, missions and achievements.

**Squad rules:** 11–15 players, at least 1 WK, 3 BAT, 3 BOWL and 1 AR, at most 6 overseas players, and the purse must always cover a minimum squad of 11 (₹0.5 cr per remaining spot).

**Player icons:** bat = batter, ball = bowler, gloves = wicketkeeper, bat and ball = all-rounder.

## 🧠 Data science concepts and how they are used

| Concept | What it does in the game | Implementation |
|---------|--------------------------|----------------|
| **Descriptive statistics** | Summarises players so you can spot who is good *and* steady. | Mean, median, standard deviation, min and max computed live for any role filter; histograms; consistency insight; player Rating combines average, strike rate, wickets, economy and consistency. |
| **Correlation** | Warns you not to judge a player by one stat. | Pearson r for any two features, interactive scatter plot with tooltips, and a "hold role constant" demo that shows a confounder. |
| **K-means clustering** | Groups similar players and exposes undervalued ones. | K-means written in JavaScript on min-max normalised features (batting average, strike rate, economy, wickets). Changeable K, animated iterations, centroids, inertia, an inertia-by-K comparison, labels derived from the centroids and a "hidden gem" per cluster. |
| **Optimisation** | Shows how to get the best squad from a limited budget. | 0/1 knapsack dynamic programming over (players picked, budget, overseas limit), with role minimums, compared against two greedy strategies. A Live advisor recomputes the best signings from your current purse and the players still available. |

## 🏆 Scoring

Team strength out of 100:

`0.32 × Batting + 0.32 × Bowling + 0.12 × Balance + 0.10 × Depth + 0.14 × Budget efficiency`

- **Batting / Bowling:** best 7 batters and best 5 bowlers in your XI.
- **Balance:** batting and bowling levels, and role coverage.
- **Depth:** quality of your best 4 bench players.
- **Efficiency:** XI quality relative to money spent.

Franchise perks modify one component (bigger purse, batting ×1.06, bowling ×1.06, depth ×1.15 or a 10% bid discount).

**Season:** win probability = logistic((strength A − strength B) / 6). Each pair meets twice, expected wins × 2 gives points.

**Game score:** `200 × (5 − rank position) + 5 × strength + 50 × achievements + 40 × missions`

## ✨ Features

- 5 fictional franchises with different advantages and 4 AI buying strategies (value hunter, star chaser, balanced builder, bargain hunter)
- Timed auction with live bidding feedback, explanations of AI bids, fair-value warnings and a sold card after each lot
- Target list with role tracking, saved in the browser
- Analyst missions, achievements and a report card showing what your decisions say about each concept
- Responsive, dark IPL-style interface; charts drawn on native Canvas (no libraries)

## 🛠️ Tech

HTML, CSS and vanilla JavaScript in a **single file** (`index.html`). Charts use the Canvas API. No frameworks, no backend, no external dependencies. The dataset is generated with a seeded random number generator (seed 7), so the same 60 players appear every time. Achievements, best score, target list and playtest entries are saved with `localStorage` in each user's own browser.

## 📁 Repository structure

```
.
├── index.html                  # The complete game
├── README.md                   # This file
└── docs/
    ├── PLAYTEST_REPORT.md      # Playtest table (real results only)
    └── screenshots/            # Optional: game screenshots
```

## 🧪 Playtest report

See [`docs/PLAYTEST_REPORT.md`](docs/PLAYTEST_REPORT.md). The same table is available inside the game under **Playtest**. Only real classmates' results are recorded there.

## ⚠️ Limitations

- Data is synthetic, so ratings, prices and percentages only mean something inside the game.
- Consistency is a generated score, not computed from innings-level data.
- There is no shared leaderboard (the game has no backend); scores are stored per browser.
- Mid-game progress is not saved; refreshing restarts the auction.
