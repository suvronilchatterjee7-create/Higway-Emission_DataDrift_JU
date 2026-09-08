# Dataset: Highway Traffic & Emissions

Highway traffic and emissions readings across 8 road segments, used for the
Data Drift hackathon (Srijan '26, CGU Dept. of Construction Engineering).

## Overview

| | |
|---|---|
| Rows | 4,120 |
| Columns | 22 |
| Date range | 2026-01-01 to 2026-03-14 |
| Frequency | Hourly |
| Road segments | 8 — A1, A2, B1, B2, C1, C2, D1, D2 |
| Exact duplicate rows | 108 |

## Columns

| Column | Type | Description |
|---|---|---|
| `timestamp` | datetime | Hourly reading time |
| `day of week` | string | Monday–Sunday |
| `road segment id` | string | One of A1/A2/B1/B2/C1/C2/D1/D2 |
| `x-coord`, `y-coord` | int | Segment location coordinates |
| `vehicles` | int | Vehicle count for the hour (some `unknown`/blank values) |
| `lane count` | int | Number of lanes (2–5) |
| `heavy vehicle pct` | float | Share of heavy vehicles (0–1) |
| `traffic density` | float | Vehicles per unit road length |
| `rain mm` | float | Rainfall in mm |
| `temperature C` | int | Temperature |
| `visibility m` | float | Visibility in meters |
| `road wetness index` | float | 0–1 wetness score |
| `ev percentage` | float | Share of electric vehicles (0–1) |
| `fuel mix index` | float | Composite fuel-type index |
| `avg speed kmph` | float | Average vehicle speed |
| `gore point` | int (0/1) | Whether segment is at a gore point (lane merge/split) |
| `distance to gore m` | int | Distance to nearest gore point |
| `CO2 emission` | float | CO2 output |
| `NOx` | float | NOx output |
| `PM2.5` | float | Particulate matter 2.5 output |
| `congestion` | string | Low / Medium / High |

## Known data quality issues

- **Duplicates**: 108 fully identical rows.
- **Blanks**: missing values in `vehicles` (82), `traffic density` (82),
  `rain mm` (82), `visibility m` (82), `avg speed kmph` (134),
  `CO2 emission` (82), `NOx` (184), `PM2.5` (186).
- **Bad values**: `vehicles` contains the literal string `"unknown"` in
  addition to numeric entries and blanks — needs coercion before use.
- No spelling-mistake variants were found in `day of week`, `road segment id`,
  or `congestion` — all values are clean/canonical (`Low`/`Medium`/`High`,
  full weekday names, `A1`–`D2`).

## Derived features (added during processing)

- `hour` — extracted from `timestamp`, used to find peak traffic hours.
- `traffic efficiency index` — derived from `avg speed kmph` and
  `traffic density` to score road performance.
