# Data

All data come from NCI SEER*Explorer (https://seer.cancer.gov/statistics-network/explorer/),
Cancer Site: Thyroid, Graph type: Recent Trends. Retrieved on November 15, 2026.

## data/raw — yearly rates (used in the analysis)

| File | Statistic | Series | Years |
|---|---|---|---|
| incidence_all.csv | SEER Incidence, Observed rate | Both Sexes | 2000–2023 |
| incidence_by_sex.csv | SEER Incidence, Observed rate | Female, Male | 2000–2023 |
| incidence_by_stage.csv | SEER Incidence, Observed rate | Localized, Regional, Distant | 2004–2023 |
| mortality_all.csv | U.S. Mortality | Both Sexes | 2000–2024 |
| mortality_by_sex.csv | U.S. Mortality | Female, Male | 2000–2024 |

Common settings: All Races / Ethnicities, All Ages, All Stages (except the stage file).

Columns:
- `series` — group (Both Sexes, Female, Male, Localized, Regional, Distant)
- `year` — year of diagnosis (incidence) or year of death (mortality)
- `rate` — age-adjusted rate per 100,000
- `lower_95ci`, `upper_95ci` — 95% confidence interval of the rate
- `modeled_rate` — SEER's own joinpoint trend-line value (empty for stage, where SEER gives no trend)
- `count` — number of cases or deaths

How the files were made: the "Download Data" CSV export of SEER*Explorer dropped the year column
and rounded values, so the yearly values were copied from the data behind the SEER*Explorer graph
(the same numbers shown in its Data Table, at full precision).

## data/raw/seer_joinpoint — SEER's published trend estimates (for comparison only)

APC/AAPC tables exported from SEER*Explorer (incidence and mortality, overall and by sex).
These are SEER's results, not ours; they are used only to check our own calculations.

## Notes from SEER*Explorer

- Incidence: SEER Incidence Data, November 2025 Submission, SEER 21 registries.
- Rates are per 100,000 and age-adjusted to the 2000 U.S. Standard Population.
- Observed (not delay-adjusted) incidence rates are used; for stage only observed rates are available.
- SEER did not use the 2020 incidence rate in its trend fits because of the COVID-19 impact on diagnoses.
  Our analysis also excludes 2020 from regression fits and explains why.
- Stage is based on the Combined Summary Stage (2004+) recode.
