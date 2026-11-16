# Open Data ELT Mini-Project: Lisbon Weather 2025

Lesson 6 Mini-Project, Building a Data Workflow (part 2). Author: Allan Antonio Canales Corea

## Data source
[Open-Meteo Historical Weather API](https://open-meteo.com/en/docs/historical-weather-api) (free, no API key). Daily weather for Lisbon (lat 38.72, lon -9.14) from 2025-01-01 to 2025-12-31.

## Workflow (ELT)
1. Extract: request the daily data from the API (with error handling and checks).
2. Load raw: save it unchanged to `data/raw/raw_weather_lisbon.csv`.
3. Transform with pandas: rename columns, convert dates, compute new columns (average temperature, temperature range, month, rainy day flag), drop missing rows, aggregate by month.
4. Load processed: save `data/processed/output.csv` and `data/processed/monthly_summary.csv`.

## How to run
```
pip install -r requirements.txt
jupyter notebook Lesson6_Data_Workflow_Allan_Canales.ipynb   # then run all cells
```
Internet is needed for the API call. After running, confirm that `data/processed/output.csv` exists.

## What the output contains
`output.csv` has 365 rows (one per day) and these columns: `date, temp_max_c, temp_min_c, rain_mm, wind_max_kmh, temp_avg_c, temp_range_c, month, month_name, rainy_day`.

Example:
```
date,temp_max_c,temp_min_c,rain_mm,wind_max_kmh,temp_avg_c,temp_range_c,month,month_name,rainy_day
2025-01-01,12.9,6.6,0.0,15.4,9.75,6.3,1,January,False
2025-01-02,15.0,5.8,0.0,10.0,10.4,9.2,1,January,False
```
`monthly_summary.csv` has 12 rows with days, average/max/min temperature, total rain and rainy days per month.

## Main results
Average temperature 18.09 C, hottest day 2025-06-29 (40.7 C), total rain 975.1 mm in 107 rainy days, rainiest month November (193.6 mm).
