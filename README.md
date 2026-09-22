# Snowman Logistics — Business Analytics Case Study

A small end-to-end analysis of **Snowman Logistics Ltd (NSE: SNOWMAN)** — India's
only listed pure-play cold-chain logistics company — built to apply MSc Business
Analytics coursework (Business Statistics, Advanced Data Analytics, Data
Management, Supply Chain Strategy) to a real, public dataset.

Rather than a narrative report, this project shows the analysis *worked out in
code*: cleaning, exploratory analysis, and regression in a Colab notebook, plus
a formula-driven Excel workbook that cross-checks the same regression
independently — all against the same 13 quarters of disclosed financial
results (Jun 2023 – Jun 2026) and 12 years of annual results (FY2015 – FY2026).

## Why Snowman Logistics

Picked as a case study in the same broad vertical as a fresh-produce /
agritech supply-chain business — the underlying operating problem (matching
perishable, seasonal, multi-client demand to a fixed physical network without
over- or under-building) is close enough to be genuinely useful to compare
against, while being a public company with clean, verifiable disclosures.

## What's in here

```
snowman-logistics-analysis/
├── README.md
├── quarterly_results.csv                    # raw, as filed — 13 quarters
├── annual_results.csv                       # raw, as filed — 12 fiscal years
├── quarterly_results_enriched.csv           # engineered features (growth rates, margins), computed in the notebook
├── Snowman_Logistics_Analysis_Colab.ipynb   # full analysis: cleaning, EDA, 2x OLS regressions, forecast, charts — data embedded, open directly in Colab
├── Snowman_Logistics_Analysis.xlsx          # formula-driven cross-check of the regression (SLOPE/INTERCEPT/RSQ/FORECAST)
├── chart1_revenue_trend_regression.png
└── chart2_net_margin_volatility.png
```

## Methods used, and which coursework they map to

| Technique | Where | Coursework link |
|---|---|---|
| Data cleaning, feature engineering (growth rates, margins, fiscal-quarter tagging) | `Snowman_Logistics_Analysis_Colab.ipynb` | Data Management |
| Exploratory data analysis / seasonality check | `Snowman_Logistics_Analysis_Colab.ipynb` | Business Statistics |
| Simple linear regression (revenue trend, OLS) with a 95% prediction interval | `Snowman_Logistics_Analysis_Colab.ipynb` | Advanced Data Analytics |
| Multiple linear regression (net-profit driver analysis) with a VIF multicollinearity check | `Snowman_Logistics_Analysis_Colab.ipynb` | Advanced Data Analytics |
| Formula-driven growth analysis, `SLOPE`/`INTERCEPT`/`RSQ`/`FORECAST` (regression cross-checked independently) | `Snowman_Logistics_Analysis.xlsx` | Business Statistics |
| Supply-chain framing of the results (capacity vs. utilization, segment mix) | this README, below | Supply Chain Strategy |

## Headline findings

- **Revenue trend:** OLS regression of sales on a quarter index gives a slope
  of **≈ Rs 3.24 crore/quarter** (R² = 0.62), extrapolating to **≈ Rs 164 cr**
  for the next quarter (95% prediction interval: Rs 138–190 cr). R² of 0.62
  means the linear trend explains about 62% of quarter-to-quarter variation —
  real growth, but with meaningful noise the trend line doesn't capture.
- **Seasonality:** average sales are highest in the Apr–Jun quarter (₹152 cr)
  and lowest in Oct–Dec (₹133 cr) across the 13 quarters — consistent with a
  business whose institutional/QSR client demand softens slightly in winter.
- **Profit drivers:** in the multiple regression of net profit on sales,
  depreciation, interest, and other income, **only interest expense is
  statistically significant** (p = 0.04) in this small sample (n = 13) — and
  it's a drag, as expected for a capex-heavy, debt-funded warehouse operator.
  The model's own diagnostics (adj. R² = 0.35, VIF up to 6.7 on depreciation)
  say plainly that 13 quarters isn't enough data to fully separate these
  effects — a caveat the analysis states rather than hides.
- **Net margin is thin and volatile:** three of the last thirteen quarters were
  loss-making (Dec 2024, Sep 2025, Dec 2025) — flagged by the notebook's
  net-margin calculation.
- **Long-run revenue CAGR (FY2015–FY2026): ≈ 10.4%/year** (computed in
  the notebook from the annual data) — for reference, one industry estimate
  (Mordor Intelligence) puts the *forward-looking* India cold-chain logistics
  market CAGR at ~5.9% (2026–2031). The periods aren't directly comparable
  (historical vs. forward-looking, company vs. market), but the gap is large
  enough to be suggestive that Snowman has been growing faster than the
  broader market, not just riding it — worth confirming against a historical
  market-size series if one is available.

## Data source and caveats

- Both CSVs are transcribed from **[screener.in's Snowman Logistics results
  page](https://www.screener.in/company/SNOWMAN/)**, which aggregates
  quarterly and annual results as disclosed in the company's NSE/BSE filings.
- This is *disclosed accounting data only* — no operational data (warehouse
  utilization, pallet counts, fleet size) is available at quarterly
  granularity, so the regressions here are financial, not operational. A
  fuller supply-chain analysis would need that data directly from the company
  (investor presentations give point-in-time figures, not a time series).
- Sample size is small (13 quarters) for the multiple regression in
  particular — treat coefficients as directional. This is stated in the
  notebook's own output, not just here.

## Running it

**In Colab (recommended):** open `Snowman_Logistics_Analysis_Colab.ipynb`
directly — either via GitHub's "Open in Colab" (see badge below, once added),
or by uploading the file to
[colab.research.google.com](https://colab.research.google.com) — then Run
All. The data is embedded in the notebook itself, so no file upload or setup
is needed.

**The CSVs and the Excel workbook** are included as the underlying data and
an independent cross-check of the notebook's regression. Both can be viewed
directly on GitHub or downloaded and opened locally (Excel or LibreOffice for
the `.xlsx`) — no extra setup required.
