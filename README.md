# econ5200-lab01-data-portfolio

# Data Quality Profiling — Big Mac Index

## Objective
This project audits the internal consistency of the Big Mac Index dataset and quantifies the survivorship bias introduced by restricting analysis to countries with complete historical panels.

## Methodology
- Reviewed the existing Purchasing Power Parity (PPP) computation and identified an error in which the numerator and denominator were transposed; corrected the calculation to reflect the proper price-ratio definition.
- Compared results generated from the full, unbalanced panel against results restricted to units with complete time coverage to test for survivorship bias.
- Quantified the direction and magnitude of the bias by computing the average Big Mac price under both the complete-panel and all-available samples, and by counting the number of periods (out of 45) in which the complete-panel average exceeded the all-available average.
- Developed `profile_dataframe()`, a reusable diagnostic function that reports:
  - Number of unique units and periods
  - Panel structure (balanced vs. unbalanced)
  - Count of units with complete records
  - Overall balance ratio
  - Per-column missingness percentages

## Key Findings
- The original PPP computation contained a numerator/denominator swap, which has been identified and corrected.
- Restricting the sample to countries with complete panels introduces measurable survivorship bias: the complete-panel average Big Mac price is **$0.08 (2.1%) higher** than the all-available average, and exceeds it in **33 of 45** periods.
- This suggests that countries with complete reporting histories tend to have systematically higher Big Mac prices than the broader, incomplete-panel sample — a pattern consistent with survivorship bias rather than a true cross-country trend.
- The `profile_dataframe()` utility, run on the full Big Mac panel, reported 57 units across 45 periods with a panel structure, only 25 of 57 units complete across all periods (unbalanced), and 7 columns with more than 10% missing data.
