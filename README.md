# Creative Economy Readiness Index (Pilot)

A small pilot composite indicator ranking 15 countries on creative-economy
readiness, using World Bank data pulled through its API (Python, pandas).

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

## Data audit and limitations
- Nigeria has no R&D or IP receipts values; its score uses 2 of 4 indicators.
- Data years differ by country (e.g. India's R&D is from 2020).
- IP receipts are not divided by GDP, so large economies are favoured.
- India's ICT exports (48.6%) is an outlier that raises its rank.
- Equal weights are a simplifying choice, not a tested one.
- Pilot only: not a substitute for official creative-economy measurement.

## Files
- creative_economy_table.csv: raw values and data years
- creative_economy_index.csv: scores and ranks
- notebook.ipynb: full code
## Reproduce
Run the notebook in Google Colab; no setup needed.
