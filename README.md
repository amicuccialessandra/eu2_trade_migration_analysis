# Trade Openness and Net Migration in the EU27

An empirical project using Stata to examine the relationship between trade openness and net migration across EU27 countries over 2013–2023.

## Research question

Are changes in a country’s extra-EU trade openness associated with changes in its net migration rate, accounting for economic conditions, permanent country characteristics and common annual shocks?

## Data

The analysis combines Eurostat data on:

- Net migration.
- Total population and population by sex.
- Extra-EU exports and imports.
- GDP and gross fixed capital formation.
- HICP inflation.

The resulting panel covers **27 countries over 11 years**, with **297 country-year observations**.

Trade openness is measured as extra-EU exports plus imports relative to GDP. Net migration is expressed per 1,000 inhabitants.

## Data preparation

The script imports and reshapes source datasets, checks country-year uniqueness and merges them into a panel.

Validation includes checks on population consistency, variable ranges, missing values and panel coverage. It then constructs trade-to-GDP ratios, GDP per capita, investment rates and demographic shares.

## Empirical approach

The baseline specification includes:

- Country and year fixed effects.
- Trade openness as the main explanatory variable.
- Controls for log GDP per capita, investment as a share of GDP and inflation.
- Standard errors clustered by country.

Additional specifications separate exports from imports and include the female population share as a demographic control. The script also tests the joint significance and equality of the export and import coefficients.

## Results

The results documented in the script show a negative but statistically insignificant association between extra-EU trade openness and net migration.

Log GDP per capita is positively and significantly associated with net migration in all three specifications. Separating exports from imports does not yield statistically significant trade coefficients, and adding the demographic control leaves the main estimates largely unchanged.

These results describe conditional associations and should not be interpreted as causal effects.

## Files

- `eu27_trade_migration_analysis.do`: data preparation, validation, variable construction, panel regressions and descriptive figures.

## Running the analysis

1. Obtain the required Eurostat CSV extracts:
   - `migr_netmigr.csv`
   - `demo_pjan.csv`
   - `ext_intratrd.csv`
   - `gdp.csv`
   - `hicp.csv`
2. Update the `global data` path at the beginning of the do-file.
3. Ensure the extracts contain the dimensions and units expected by the script: trade, GDP and investment in million euros; population and migration in persons; and inflation in percent.
4. Create an `output` subfolder inside the data directory.
5. To export the regression table, install the optional `estout` package using `ssc install estout`.
6. Run the do-file in Stata.

The script reads local CSV extracts; it does not download data automatically.

## Outputs

- Intermediate datasets and the analytical panel.
- A regression table in RTF format, when `esttab` is installed.
- Three descriptive figures for 2023:
  - GDP concentration across EU27 countries.
  - Trade openness and net migration.
  - Population composition by sex.
