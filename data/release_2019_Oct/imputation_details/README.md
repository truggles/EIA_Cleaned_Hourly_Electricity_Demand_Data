This directory contains a zip file to cut the size of the two corresponding
files in half. These files will only be used by researchers interested in the details of the 
MICE imputation method. The two files are:

  * `long_format_16_MICE_chains.csv` containing 56 columns, one for the `date_time` field, then the 54 BAs with imputed results, lastly is `imp_index` ranging from 1-16 denoting which of the 16 chains the row belongs to.
  * `mean_of_16_chains.csv` contains the same 55 columns above except it lacks the `imp_index` field as it is the mean (in log space) of the 16 chains.

The 54 columns with BA acronmys as headers correspond to what is called `Cleaned Demand (MW)`
throughout the rest of this repository.

Again: The final (mean) imputed demand for each hour is taken after converting all values
into log space and is the mean imputed value for each
hour from the 16 chains. After taking the mean in log space, the resulting value is exponentiated back to linear space.

The values in `mean_of_16_chains.csv` correspond to the imputed values found throughout the rest of this repository.

The `date_time` field is recorded in a slightly different format from the other files, it uses `YYYY-MM-DDTHH:00:00Z`.

These files include data from July 1, 2015 which is cut from the final files because of reporting irregularities during the first day of reporting data to the EIA.
