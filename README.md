# The Death of the 12th Man: How Home Advantage Is Fading in the Premier League

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue?logo=python)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Blog Post](https://img.shields.io/badge/Blog-Read%20the%20Article-purple)](https://ammartyabji.wixsite.com/mysite/post/the-death-of-the-12th-man-how-home-advantage-is-fading-in-the-premier-league)

> *I analysed 9,380 Premier League matches across 25 seasons to trace the slow death of home advantage and found that the real story is not about stadiums getting quieter. It is about away teams getting smarter.*

---

## The Question

In the early 2000s, home teams won roughly 46% of Premier League matches. By 2020/21 that had dropped to 38%. Was this COVID? Tactics? Something structural? This project uses 25 years of match data, econometric inference, and machine learning to find out.

---

## Key Findings

| Finding | Detail |
|---------|--------|
| Home advantage is declining | ~1 percentage point every 3–4 years since 2000 |
| COVID was an accelerant, not the cause | Home win rate: 46.5% → 41.6% (p=0.009), recovered only to 44.7% |
| Structural vs atmospheric advantage | Man City/Liverpool *improved* during COVID; Fulham collapsed from 44% → 10.5% |
| Form predicts direction, not draws | 61% binary accuracy; 0 draws predicted across 1,100 test matches |
| Team fixed effects add almost nothing | +0.1pp — form differentials capture momentum, not just squad quality |
| Model is stable over time | 60.9% ± 1.5% across 5 time-ordered CV folds |

---

## What's in the Notebook

The notebook is self-contained and runs end-to-end. Each section corresponds to a section of the blog post.

| Part | Topic | Methods |
|------|-------|---------|
| 1 | Data loading & feature engineering | Pandas, datetime parsing |
| 2 | Exploratory analysis | LOWESS smoothing, time-series visualisation |
| 3 | The COVID natural experiment | Two-sample t-tests, OLS with robust SEs (HC1) |
| 4 | Rolling form features | Lagged rolling windows — zero data leakage |
| 5 | Predictive modelling | Logistic regression, temporal train/test split |
| 6 | Statistical inference | `statsmodels` Logit, marginal effects |
| 7 | Multinomial logit | All three outcomes (H/D/A) simultaneously |
| 8 | Rolling cross-validation | `TimeSeriesSplit` — time-aware model evaluation |
| 9 | Deep dives | Fortress rankings, COVID by team, Big Six vs Rest, derbies, draw analysis |

---

## Methodology Notes

**Why a temporal split and not random CV?**  
Random splits leak future information. A model trained on 2024 data and tested on 2020 matches is not predicting — it is remembering. All evaluation uses a strict temporal cutoff: train on seasons before 2022, test on 2022 onwards.

**Why shift(1) in the form features?**  
To prevent data leakage. Each match only uses results from *previous* matches. Without the lag, the model would know the outcome of the match it is trying to predict.

**Why statsmodels alongside sklearn?**  
`sklearn` tells you how accurate a model is. `statsmodels` tells you *why* — with standard errors, z-statistics, and confidence intervals. Both are used deliberately.

**Why does the multinomial logit predict zero draws?**  
Because draws are structurally unpredictable from pre-match form data. Draw rates sit between 19–26% regardless of the form gap between teams. This is not a modelling failure — it is what the data says.

---

## Repo Structure

```
epl-home-advantage/
│
├── epl_home_advantage.ipynb   # Main notebook — start here
├── requirements.txt           # Python dependencies
├── README.md                  # This file
│
└── outputs/                   # All charts saved here (auto-created on run)
    ├── fig1_outcome_distribution.png
    ├── fig2_home_advantage_trend.png
    ├── fig3_goal_diff_trend.png
    ├── fig4_covid_experiment.png
    ├── fig5_model_comparison.png
    ├── fig6_marginal_effects.png
    ├── fig7_confusion_matrix.png
    ├── fig8_rolling_cv.png
    ├── deep_fig1_fortresses.png
    ├── deep_fig2_covid_by_team.png
    ├── deep_fig3_big_six_vs_rest.png
    ├── deep_fig4_rivalries.png
    └── deep_fig5_draws.png
```

---

## Getting Started

### 1. Clone the repo
```bash
git clone https://github.com/AmmardoesStats/epl-home-advantage.git
cd epl-home-advantage
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Download the dataset
Download `epl_final.csv` from [Kaggle](https://www.kaggle.com/datasets/marcohuiii/english-premier-league-epl-match-data-2000-2025) and place it in the root of the repo (same folder as the notebook).

### 4. Run the notebook
```bash
jupyter notebook epl_home_advantage.ipynb
```

Update the `FILEPATH` variable in Part 1 if your CSV is saved elsewhere.

---

## Dataset

**Source:** [English Premier League (EPL) Match Data 2000–2025](https://www.kaggle.com/datasets/marcohuiii/english-premier-league-epl-match-data-2000-2025)  
**Coverage:** 9,380 matches across 25 seasons  
**Key columns used:** `MatchDate`, `Season`, `HomeTeam`, `AwayTeam`, `FullTimeHomeGoals`, `FullTimeAwayGoals`, `FullTimeResult`, `HomeRedCards`, `AwayRedCards`

---

## Dependencies

See `requirements.txt`. Core libraries:

- `pandas`, `numpy` — data manipulation
- `matplotlib`, `seaborn` — visualisation
- `scipy` — statistical tests
- `statsmodels` — econometric inference (Logit, MNLogit, OLS)
- `scikit-learn` — predictive modelling and evaluation

---

## Read the Full Article

👉 [The Death of the 12th Man — Ammar Tyabji's Blog](https://ammartyabji.wixsite.com/mysite/post/the-death-of-the-12th-man-how-home-advantage-is-fading-in-the-premier-league)

---

## Author

**Ammar Tyabji**  
[GitHub: @AmmardoesStats](https://github.com/AmmardoesStats)

---

## License

MIT — free to use, adapt, and share with attribution.
