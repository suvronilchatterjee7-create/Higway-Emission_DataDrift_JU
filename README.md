# Highway Emission Data Drift — Srijan '26

Data cleaning, feature engineering, KPI analysis, and dashboarding of a
highway traffic and emissions dataset, built for **Data Drift**, hosted by
the Department of Construction Engineering, Srijan '26 (11 April 2026).

## Problem Statement

You're a data analyst in a city's traffic management department. Smart
highway systems combine clean energy, traffic tech, and engineering to cut
vehicle emissions. This project analyzes hourly traffic and emissions data
across highway segments to surface congestion patterns, environmental
impact, and insights that support smarter, lower-emission highway
management decisions.

Full problem statement: [`Data drift problem statement 3.pdf`](./Data%20drift%20problem%20statement%203.pdf)

## Repository Structure

```
.
├── data/            # raw and cleaned datasets
├── notebooks/        # analysis and feature-engineering notebooks
├── submissions/       # dashboard (Excel) and presentation deliverables
├── Data drift problem statement 3.pdf
└── LICENSE            # MIT
```

## Dataset

Hourly readings across 8 road segments (A1, A2, B1, B2, C1, C2, D1, D2),
covering ~4,120 rows from January to March 2026.

**Fields:** timestamp, day of week, road segment id, x/y-coordinates,
vehicle count, lane count, heavy vehicle %, traffic density, rainfall,
temperature, visibility, road wetness index, EV %, fuel mix index, average
speed, gore point flag, distance to gore, CO2/NOx/PM2.5 emissions, and
congestion level (Low/Medium/High).

**Data quality issues found and cleaned:**
- 108 exact duplicate rows
- Missing values across vehicle count, traffic density, rainfall,
  visibility, average speed, and all three emission columns
- A literal `"unknown"` string mixed into the numeric vehicle-count column

## Work Completed

- **Data cleaning** — deduplication, missing-value handling, type coercion
- **Feature engineering** — `hour` (extracted from timestamp),
  `traffic efficiency index` (derived from speed and density)
- **Data analysis** — peak traffic hours, slowest road segments,
  congestion-prone zones, CO2 emissions by congestion level, rainfall vs.
  speed, top emission hotspots, heavy-vehicle % vs. congestion, low-visibility
  zones
- **Advanced analysis** — gore-point impact on speed/congestion, simulated
  EV adoption effect on CO2, density–speed non-linearity, anomaly detection,
  road segment ranking by efficiency index
- **KPIs** — total traffic volume, average speed, average CO2 emissions,
  emissions per vehicle, traffic efficiency index
- **Dashboard** — built entirely in Excel (`submissions/`)
- **Presentation** — one-slide insights deck (`submissions/`)

## How to Run

1. Clone the repo and open the notebooks in `notebooks/` in order.
2. Raw data lives in `data/`; cleaned output is written back there.
3. Open the Excel file in `submissions/` for the dashboard and KPIs.

## License

MIT — see [LICENSE](./LICENSE).

## Author

Suvronil Chatterjee
