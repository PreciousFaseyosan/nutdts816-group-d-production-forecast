# NUTDTS 816 Group Project, Group D

Forecasting monthly gas and oil production across 58 Texas production sales points.

**Group members:** Faseyosan Precious Oluwagbohunmi, Salaam Olawumi Suliat
**Course:** NUTDTS 816 Time Series Analysis, MSc Data Science, NUTM 
**Lecturer:** Dr Tolulope Adesina

> _Forecasting question and approach: to be written by the group._

## Repository layout

```
data/
  production_sales_points.csv              monthly production, 58 coded sales points, Jan 1993 - Apr 2026
  production_sales_points_summary.csv      one row per sales point: start, last production, active/inactive
  production_sales_points.PROVENANCE.txt   source, columns, how the file was built, caveats
  nymex_prices.csv                      Henry Hub and WTI prices, May 2026 - Apr 2027
  price_assumptions.csv                 BTU factor, price differentials, price scenarios
  nymex_prices.PROVENANCE.txt           price sources and the revenue formula
notebooks/                              (to be added) the runnable Colab notebook
```

## Data in one paragraph

Production volumes come from the Railroad Commission of Texas (public record), summed from
well level to sales-meter level. Sales points are coded SP01 to SP58; 37 were still producing in
2026. Volumes are gross monthly totals (MCF of gas; barrels of oil, with condensate counted as oil). Prices are
NYMEX Henry Hub and WTI (actual settlements for months already delivered, the futures strip
for later months) and are used only to express volume forecasts as indicative gross revenue.
Read both PROVENANCE files before modelling.

## Loading the data (Colab)

```python
import pandas as pd
url = 'https://raw.githubusercontent.com/<user>/<repo>/main/data/'
df = pd.read_csv(url + 'production_sales_points.csv', parse_dates=['date'])
summary = pd.read_csv(url + 'production_sales_points_summary.csv')
prices = pd.read_csv(url + 'nymex_prices.csv', parse_dates=['date'])
```
