# Duels Analyzer Showcase

[Live Demo](https://duels-analyzer-showcase.streamlit.app)

A data‐driven dashboard that gathers and visualizes statistics from my GeoGuessr games.  
If you want to analyse your own games, please go [here](https://duels-analyzer.streamlit.app).

---

## Table of Contents

1. [Features](#features)
2. [Data & Analysis](#data--analysis)
3. [How It Works](#how-it-works)
4. [Getting Started](#getting-started)
5. [Libraries Used](#libraries-used)
6. [Screenshots](#screenshots)

---

## Features

- **Player Performance Metrics**

  - Total games played
  - Win/loss counts and win rate
  - Average score per Duel

- **Trend Analysis Over Time**  
  Visualize how score, win rate, and ranking have changed over weeks or months.

- **Country-based Insights**  
  See which countries or regions give you the highest average scores or most wins.

- **Interactive Charts & Tables**  
  Built with Plotly and Streamlit, hover for precise values, zoom into time stretches, or filter by date or map.

- **Self-Contained Data Pipeline**  
  All data cleaning, aggregation, and calculations happen under the hood; you get ready‐to‐read charts without worrying about Python scripts.

---

## Data & Analysis

1. **Data Source**

   - Base data contains a dictionary containing following data points for each round played:
     - Date and time of the match
     - My score
     - My distance to actual location
     - Country
       and many more...

2. **Key Computations**
   - **Win Rate**  
     `(Number of Wins) ÷ (Total Duels) × 100`.
   - **Average Score & Score Distribution**  
     Compute your mean, median, and quartiles of scores; visualize as histograms or box plots.
   - **Time Series Trends**  
     Group Duels by week or month to chart how your average score and win rate changed over time.
   - **Country‐Based Performance**  
     Group Duels by country and compute average score → highlights “best” and “weakest” countries.

---

## How It Works

1. **Data cleaning**
   - Convert raw JSON into a flat Pandas DataFrame.
   - Extract key columns:
     - `date` (timestamp of match)
     - `score` (your points)
     - `opponent` (opponent’s username/score)
   - Derive new columns:
     - `win` (boolean: did you finish 1st?)
     - `week` and `month` (for grouping).
2. **Compute Metrics**
   Using Pandas groupbys, calculate totals, means, and percentages for:
   - Win/Loss counts
   - Average score per country
   - Score trends by month
3. **Visualize**  
   Streamlit displays:
   - A header summary (cards with total Duels, win rate, average score)
   - Line charts for time‐series trends
   - Bar charts for map performance
   - Histograms of score distributions

---

## Getting Started

It is already running at streamlit cloud, you can just go there [https://www.duels-analyzer-showcase.streamlit.app](https://duels-analyzer-showcase.streamlit.app)

If you want to run it in your local, then

1. **Clone/download the repository**
2. **Install dependencies & run**
   ```bash
   pip install -r requirements.txt
   streamlit run main.py
   ```

---

## Libraries Used

- **Python**
- **Streamlit** for web-based dashboard
- **Pandas** for data manipulation
- **Plotly and Matplotlib** for interactive charts (line, bar, histogram)
- **NumPy** for numerical operations
- **pickle** to read JSON from `saved_data.pkl`

---

## Screenshots

> _Below are a few static previews. In the live Streamlit app, each chart is fully interactive (zoomable, hoverable, etc.)._

1. **Dashboard Summary**

   ![ ](/Screenshots/summary.png)

2. **Average distance by country**

   ![ ](/Screenshots/country_vs_distance.png)

3. **Compare any two metrices**

   ![ ](/Screenshots/compare_metrices.png)

4. **Number of games played**

   ![ ](/Screenshots/games_played_by_week.png)

---
