EU Healthcare Spending & Life Expectancy

A data visualisation project exploring the relationship between government healthcare spending and life expectancy, using open data from the World Bank.

What it does

Two interactive visualisations built with Python and Plotly:

Chart 1: Healthcare spending vs life expectancy across 191 countries (scatter plot)
Chart 2: Life expectancy change in the EU (2015→2019) grouped by whether countries increased or cut healthcare spending between 2010 and 2015 (connected dot plot)

Approach for chart 1:
Fetch spending and life expectancy data via API for 2010–2024
Fetch country metadata to get income group classification and filter out regional aggregates (e.g. "World", "Europe & Central Asia")
Merge datasets on countryiso3code + date
Select the latest year with data available for each country (2023 for 191 out of 193 countries)
Identify outlier countries per income group using regression residuals — countries whose life expectancy falls furthest below what their spending level would predict

Key finding
For the latest data available in 2023, the scatter plot reveals a logarithmic relationship: additional healthcare spending has a large impact at lower levels but shows diminishing returns at higher levels. Within each income group, certain countries significantly underperform relative to their spending — these are highlighted as larger markers on the plot.

For the relation between spendings in 2010-2014 and 5 years later, across the EU: EU countries that increased healthcare spending gained on average 0.84 years of life expectancy between 2015 and 2019 — nearly twice the gain of countries that cut spending. Croatia is noted as an outlier, having joined the EU in 2013.

Tools & libraries

Python, pandas, Plotly Express, requests, NumPy


Data

Countries: EU-27 for the second plot; the world for the first chart
Period: 2010–2019 (2020 excluded due to COVID distortion)
Source: All data is pulled live from the World Bank Open Data API, Development Indicators:
Health spending: Government health expenditure per capita, PPP (current international $) — indicator SH.XPD.GHED.PP.CD
Life expectancy: Life expectancy at birth, total (years) — indicator SP.DYN.LE00.IN
Income groups: Country metadata endpoint — used to classify countries into Low, Lower middle, Upper middle, and High income groups