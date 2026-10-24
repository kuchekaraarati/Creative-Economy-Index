# Creative Economy Readiness Index (Pilot)

A small pilot composite indicator ranking 15 countries on creative-economy
readiness, using World Bank data pulled through its API (Python, pandas).
Data source: World Bank, World Development Indicators (API). Pulled on 24 Oct 2026.
Dashboard: https://public.tableau.com/authoring/CreativeEconomyReadinessIndex/Sheet1#1

## Indicators
| Indicator | World Bank code | Why |
|---|---|---|
| Internet users (%) | IT.NET.USER.ZS | Digital access |
| R&D spending (% of GDP) | GB.XPD.RSDV.GD.ZS | Innovation capacity |
| ICT service exports (% of service exports) | BX.GSR.CCIS.ZS | Digital services |
| IP receipts (US$, log10) | BX.GSR.ROYL.CD | Creative and IP output |

## Method
1. Pull the latest available value per country (last 5 years checked).
2. Take log10 of IP receipts to reduce the effect of very large values.
3. Min-max scale each indicator to 0-100.
4. Average the available scores with equal weights; rank countries.

## Results
Top 3: South Korea (72.5), United States (69.0), Germany (65.1).
Bottom 3: Egypt (21.9), Kenya (9.4), Nigeria (5.0, based on 2 of 4 indicators).

## Data audit and limitations
- Nigeria has no R&D or IP receipts values; its score uses 2 of 4 indicators.
- Data years differ by country (e.g. India's R&D is from 2020).
- IP receipts are not divided by GDP, so large economies are favoured.
- India's ICT exports (48.6%) is an outlier that raises its rank.
- Equal weights are a simplifying choice, not a tested one.
- Pilot only: not a substitute for official creative-economy measurement.
- - The indicators are proxies: IP receipts cover all intellectual property
  (patents and software as well as copyright), and ICT exports are not
  creative-specific, so this measures broad readiness, not creative output.
- The 15 countries were chosen for convenience and are not a representative sample.

## Files
- creative_economy_table.csv: raw values and data years
- creative_economy_index.csv: scores and ranks
- creative_economy_index.ipynb: full code
- Final CSVs are also stored in cloud object storage (S3-compatible, Filebase).

## Reproduce
Open the notebook in Google Colab and run all cells from top to bottom
(Runtime > Run all). No setup needed.
