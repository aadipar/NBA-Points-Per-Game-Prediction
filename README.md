# NBA Points-Per-Game Prediction

A regression project that trains four ML models (Linear, Ridge, Random Forest and Gradient Boosting) in order to predict an NBA player's PPG in the following season. 

## Problem Statement

Given the MP, USG%, OBPM, and AST% of a given NBA player, predict the player's PPG in the next season. 

## Data

**Samples**: 1371 year-end statlines of NBA Players from 2021-2024
**Features**: 4 features + 1 numeric target

| Feature | Type | Description |
|---------|------|-------------|
| Usage Percentage (USG%) | float | Estimate of the % of team plays used by a player while he was on the floor |
| Offensive Box Plus Minus (OBPM) | float | A box score estimate of the offensive points per 100 possessions a player contributed above a league-average player, translated to an average team |
| Minutes Played (MP) | float | Total amount of minutes played during the season |
| Assist Rate (AST%) | float | An estimate of the percentage of teammate field goals a player assisted while he was on the floor |
| **Points Per Game (PTS)** | **float** | **Points Per Game in the next season** |

## Source

All data sourced from https://www.basketball-reference.com/

### Advanced Data

- https://www.basketball-reference.com/leagues/NBA_2021_advanced.html
- https://www.basketball-reference.com/leagues/NBA_2022_advanced.html
- https://www.basketball-reference.com/leagues/NBA_2023_advanced.html
- https://www.basketball-reference.com/leagues/NBA_2024_advanced.html

### Per Game Data (used to source PPG for every player in every season)

- https://www.basketball-reference.com/leagues/NBA_2021_per_game.html
- https://www.basketball-reference.com/leagues/NBA_2022_per_game.html
- https://www.basketball-reference.com/leagues/NBA_2023_per_game.html
- https://www.basketball-reference.com/leagues/NBA_2024_per_game.html
- https://www.basketball-reference.com/leagues/NBA_2025_per_game.html


## Project Structure
NBA_Future_PPG_Prediction/
├── data/
│   ├── advanced_2021.csv
│   ├── advanced_2022.csv
│   ├── advanced_2023.csv
│   ├── advanced_2024.csv
│   ├── pergame_2021.csv
│   ├── pergame_2022.csv
│   ├── pergame_2023.csv
│   ├── pergame_2024.csv
│   ├── pergame_2025.csv
├── notebooks/
│   └── 01_eda.ipynb
│   └── 02_model_building.ipynb
└── requirements.txt

## Key Findings
1. PTS is very right skewed, which is to be expected(very few players will be scoring lots). This indicates that a linear regression may not be the most accurate model for predictions, and a tree-based model may perform better
2. MP and GS are the strongest predictors of PTS, but they are also very correlated with each other, meaning that only one of them should be included as a final feature
3. Age is not a strong predictor, as it is not strongly correlated with PTS
4. While the amount of playing time (MP, GS) is strongly correlated with PTS, TS% is not, which indicates that the *opportunity* to shoot is more important than the scoring efficiency of the player
5. USG%, OBPM, PER, and AST% have strong correlation with PTS, which suggests that players with larger offensive roles tend to score more
6. There is significant multicollinearity in the model, such as the with the aforementioned MP and GS, WS and OWS/DWS, and BPM/OBPM and PER. This supports the aforementioned suggestion that a linear model may struggle significantly, while a tree-based model may perform significantly better

## Tech Stack
pandas, matplotlib, seaborn, scikit-learn

# How to run
1. Install requirements
2. Download data
3. Run `01_eda_and_data_cleaning.ipynb`
4. Run `02_model_building.ipynb`
