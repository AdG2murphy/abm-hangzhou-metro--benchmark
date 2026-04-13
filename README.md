# ABM Hangzhou Metro Benchmark

**Agent Benchmark Task**: Build an Agent-Based Model (ABM) from scratch to simulate passenger trips in the Hangzhou metro system.

## Task Overview

Given the Hangzhou metro network (4 lines, ~80 stations) with GIS data, operation parameters, and ~1.26M real AFC smart card records, build an ABM that simulates the full passenger journey and reproduces realistic travel times. Success requires **R² ≥ 0.70**.

## Repository Structure

```
├── gis/                          # Metro network geometry
│   ├── hangzhou_lines.json       # Line GeoJSON (geometry + attributes)
│   └── hangzhou_stations.json    # Station GeoJSON (names, coordinates, line assignments)
├── data/
│   └── afc_hangzhou.csv          # AFC smart card records (1.26M deduplicated trips)
├── network_config/
│   ├── station_sequence.csv      # Station order per line-direction
│   └── operation_parameters.json # Headways, capacity, speed, Logit params, etc.
├── reference_output/             # Baseline ABM results for validation
│   ├── passenger_records.csv     # Simulated vs real travel times (R²=0.77)
│   ├── validation_report.txt     # R² and RMSE summary
│   └── scatter_plot.png          # Scatter plot visualization
└── LICENSE                       # CC BY 4.0
```

## Input Data

| File | Description | Size |
|------|-------------|------|
| `gis/hangzhou_lines.json` | Metro line GeoJSON with geometry and attributes | 48 KB |
| `gis/hangzhou_stations.json` | Station GeoJSON with coordinates and line assignments | 49 KB |
| `data/afc_hangzhou.csv` | AFC records: card_id, o_station, d_station, start_time, end_time (minutes from midnight) | 78 MB |
| `network_config/station_sequence.csv` | Station order for each line-direction | 13 KB |
| `network_config/operation_parameters.json` | Operation parameters (headways, capacity, speed, Logit model params, etc.) | 2 KB |

## Reference Output

The reference ABM achieved **R² = 0.77** on Hangzhou with 1.26M passengers. Reference output is provided in `reference_output/` for cross-validation.

## Data License & Privacy

- All data is released under the **CC BY 4.0** license.
- AFC `card_id` values are hashed — no personally identifiable information (PII) is included.
- Station names and coordinates are publicly available geographic information.

## Citation

If you use this benchmark, please cite:

> Agent-HLE Benchmark: Hangzhou Metro ABM Task. UC Berkeley RDI, 2026.
