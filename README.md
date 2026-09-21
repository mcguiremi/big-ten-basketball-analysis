# Big Ten Basketball: Travel & Rest vs. Performance

Does traveling farther or getting less rest hurt a Big Ten men's basketball team's performance against expectation? This project builds a game-level dataset for the 2024–25 and 2025–26 Big Ten seasons and tests that question with correlation analysis, ANOVA, and OLS regression.

## Project Goal

Investigate whether travel distance and days of rest before a game affect how a team performs relative to a betting-market-style expectation.

## Methods

1. **Point spread & cover score** — for every game, an expected point spread is derived from each team's [KenPom](https://kenpom.com/) adjusted efficiency rating on the day of the game (`(home rating − away rating) × 0.70`, since Big Ten teams average ~70 possessions/game). The **cover score** is the actual margin minus that expected margin — positive means the home team outperformed expectations.
2. **Travel distance** — geodesic distance (in miles) between the away team's campus and the game site, computed with `geopy`.
3. **Rest days** — days since each team's previous game, computed separately for the home and away team.
4. **Statistical tests** — Pearson correlation, one-way ANOVA across rest-day groups, and three OLS regression specifications (linear, interaction, and quadratic).

## Key Finding

**No statistically significant relationship** between travel distance or rest days and cover score (all p > 0.05; best model R² = 0.009). See the notebook's Conclusion section for the full write-up and possible explanations for the null result.

## Repository Structure

```
├── college_bball_analysis.ipynb   # Full analysis notebook
├── data/
│   └── big_ten_results.csv        # Game results + efficiency ratings
├── requirements.txt
└── README.md
```

## Data Sources

- Game schedules and results: [Sports Reference](https://www.sports-reference.com/cbb/)
- Team efficiency ratings: [KenPom](https://kenpom.com/)

## Running It

```bash
pip install -r requirements.txt
jupyter notebook college_bball_analysis.ipynb
```

## Technologies Used

Python, pandas, NumPy, Matplotlib, SciPy, statsmodels, geopy
