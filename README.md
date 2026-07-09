# Week 6 — Advanced Python Analysis: AAPL Historical Stock Data

**AnalystLab Africa Internship — Batch B (June–August 2026)**
**Intern:** Okoli Amarachi Veronica (Amara)

## Overview

This project applies advanced Python techniques — data transformation, time-series analysis, and feature engineering — to 5 years of Apple Inc. (AAPL) historical stock market data, as part of Week 6 of the AnalystLab Africa Data Analytics Internship.

## Dataset

- **Source:** Yahoo Finance, retrieved programmatically via the [`yfinance`](https://pypi.org/project/yfinance/) Python library
- **Ticker:** AAPL (Apple Inc.)
- **Period:** July 7, 2021 – July 6, 2026 (1,254 trading days)
- **Fields:** Date, Open, High, Low, Close, Adjusted Close, Volume

> Note: Yahoo Finance's website has gated direct CSV downloads for historical data behind sign-in/subscription for this ticker. Data was instead retrieved directly in Python using `yfinance`, which pulls the same underlying data Yahoo Finance publishes.

```python
import yfinance as yf

df = yf.download("AAPL", start="2021-07-07", end="2026-07-07", auto_adjust=False)
df.columns = df.columns.get_level_values(0)
df = df.reset_index()
df.to_csv("AAPL.csv", index=False)
```

## Techniques Applied

**Data Transformation (Pandas)**
- Data cleaning: datetime conversion, chronological sorting, duplicate removal, missing-value handling
- Filtering, sorting, and grouped aggregation (monthly resampling)
- Calculated columns (Daily Range, Typical Price)
- Data formatting and restructuring (currency/volume formatting, Year × Month pivot table)

**Time-Series Analysis**
- Date component extraction (Year, Month, Day of Week)
- Daily percentage change
- 7-day and 30-day rolling (moving) averages
- Monthly returns via month-end resampling
- Day-of-week performance comparison

**Feature Engineering**
- Daily Price Change (absolute and %)
- 7-day and 30-day Moving Averages
- 30-day rolling volatility, annualized
- Cumulative return since dataset start
- Trend flag (price vs. its own 30-day moving average)

## Visualizations

1. AAPL Closing Price Trend (5-Year)
2. AAPL Daily Trading Volume (5-Year)
3. Closing Price with 7-Day and 30-Day Moving Averages
4. AAPL Monthly Returns (%)
5. Annualized 30-Day Rolling Volatility

## Key Insights

- AAPL's closing price rose from **$144.57** (Jul 2021) to **$312.66** (Jul 2026) — a total return of **+116.3%**
- Price traded above its 30-day moving average **55%** of the time, with ~97 MA crossover events over the 5 years
- Annualized volatility averaged **~26%**, spiking to **~70%** around April/May 2025 — the same window containing the two most extreme single-day moves in the dataset (+15.3% and -9.25%)
- **34 of 60 months (57%)** had positive returns; best month was July 2022 (+18.9%), worst was December 2022 (-12.2%)
- No statistically meaningful day-of-week trading effect was found
- Average daily volume was **~65.3 million shares**, peaking at **~318.7 million shares** on Sept 20, 2024

## Repository Contents

| File | Description |
|---|---|
| `Week6_AAPL_Advanced_Python_Analysis.ipynb` | Full analysis notebook — cleaning, transformation, time-series analysis, feature engineering, visualizations, findings |
| `Week6_AAPL_Insight_Summary.docx` | 1–2 page insight summary report with embedded visualizations |
| `AAPL.csv` | Raw dataset used for analysis |
| `README.md` | This file |

## Tools Used

Python, pandas, NumPy, Matplotlib, Seaborn, yfinance, Jupyter Notebook

## Author

Okoli Amarachi Veronica — Data Analytics Intern, AnalystLab Africa (Batch B)

#Python #DataAnalysis #TimeSeriesAnalysis #Pandas #DataScience #Analytics #AnalystLabAfrica
