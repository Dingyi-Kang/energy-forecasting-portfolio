# Energy forecasting portfolio (Texas / ERCOT)

Personal projects on public data, built in 2026. Every project uses a
written evaluation protocol fixed before modeling, chronological validation, a final holdout opened
once, and paired block-bootstrap confidence intervals. All comparisons are internal (no public
leaderboard exists for these tasks). Not affiliated with ERCOT, any utility or any employer.

| Project | Question | Main result (holdout / test) |
|---|---|---|
| [ercot-load-forecasting](https://github.com/Dingyi-Kang/ercot-load-forecasting) | Day-ahead hourly ERCOT system load, using only data available at 18:00 the day before | Ensemble (LightGBM + Kalman ridge + Chronos-2): 2026 Jan-Sep MAPE 1.86% (MAE 1,112 MW) vs 4,286 MW seasonal naive |
| [ercot-zone-transformer-forecasting](https://github.com/Dingyi-Kang/ercot-zone-transformer-forecasting) | Probabilistic load for 8 ERCOT weather zones: fine-tuned foundation model vs transformer from scratch vs LightGBM | LoRA fine-tuned Chronos-2: 19% lower quantile loss than LightGBM quantile regression (2025 test) |
| [texas-temperature-mos](https://github.com/Dingyi-Kang/texas-temperature-mos) | Correct GFS/ECMWF temperature forecasts for 11 Texas load cities | LightGBM post-processing: MAE 1.00 C vs 1.32 C raw blend (-24%) |
| [texas-retail-electricity-usage](https://github.com/Dingyi-Kang/texas-retail-electricity-usage) | Usage per meter for ERCOT load-profile classes; monthly Texas retail sales | Fine-tuned Chronos-2 WAPE 4.78% vs 6.50% LightGBM |
| [london-smart-meter-analytics](https://github.com/Dingyi-Kang/london-smart-meter-analytics) | Household forecasting, K-means segmentation and price response (5,566 London homes) | High-price events -6.1% consumption (difference-in-differences, placebo null) |
| [ercot-4cp-peak-alerts](https://github.com/Dingyi-Kang/ercot-4cp-peak-alerts) | When to alert large customers about likely monthly system peaks (4CP) | Peak forecast Brier 0.099 vs 0.143 climatology; selected alert rule failed on test, analysed in the model card |
| [energy-analytics-sql](https://github.com/Dingyi-Kang/energy-analytics-sql) | Star-schema warehouse and SQL analyses of load, prices, weather and meters | 8 analyses (window functions, regression in SQL), each cross-checked in pandas |

## Running
`ercot-load-forecasting` downloads and builds the shared ERCOT load and weather tables
(`~/ML_forecast/data/processed`); the other projects read from there, so clone it as `~/ML_forecast`
and build it first. Raw data are not committed; each README lists the public sources and licences
(ERCOT, Open-Meteo CC BY 4.0, Iowa Environmental Mesonet, EIA, Low Carbon London CC BY 4.0).
