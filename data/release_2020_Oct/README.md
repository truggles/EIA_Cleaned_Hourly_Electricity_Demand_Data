# October 2020 Release

 * Data in this subfolder queried on 28 Sept 2020.
 * This update adds one additional year of cleaned demand data bringing the total to 5 years
   * Cleaned data ranges from 2015-07-02 00:00:00 UTC to 2020-07-01 23:00:00 inclusive
   * All data used in this directory were querried on 28 September 2020.
 * Methodology remains unchanged for producing this updated set of cleaned demand data
 * We produced updated versions of the data summary tables that were found in the original paper. These updated tables reveal no substantial changes in performance of the anomaly identification or imputation methods.
   * Table 1: `anomalous_value_summary.csv`
   * Table 2: `anomalous_value_summary_post-imputation_screening.csv`
   * Table 3: `imputation_results_and_biases.csv`
 * We did check the mean absolute percentage error (MAPE) by calendar year to see if the 2020 data was noticably impacted by the COVID-19 pandemic and resulting changes in electricity demand.
   * No large biases were noticed for the year 2020 compared to other years with the exception of four regions comprising less than 1% of total continental US demand
     * BA, mean demand over all 5 years, number of imputed values over all 5 years
     * IPCO, 1,900 MW, 332
     * SPA, 71 MW, 319
     * TEPC, 1,500 MW, 912
     * NSB, 46 MW, 8,283 
   * NSB reported their last hourly demand value to EIA as 2020-01-08 05:00:00. Thus this 2020 MAPE check for this BA is not relevant. We are publishing the imputation results for NSB as-is. We recommend any user of NSB data discuss 2020 data with the NSB BA directly.
 * Diagnostic figure `large_diagnostic_figure_Oct_8.pdf` provides a visualization of all hourly values that were identified as anomalous throughout the 5 years of data. The figure is composed of three regions. 
   * 1) each BA has an associated column and the y-axis shows the timestamp, colored circle mark anomalous values. The color key is located at the bottom of the figure. 
   * 2) above region 1 the cumulative total of anomalous values for each BA (column) is shown split by filtering algorithm.
   * 3) adjacent to region 1 the cumulative total of anomalous values by filtering algorithm is shown for each timestamp.

# Subdirectory documentation

Subdirectories are laid out like the previous release in `data/release_2019_Oct/`. 
Please see the README.md files in there for documentation of exact directory content.
