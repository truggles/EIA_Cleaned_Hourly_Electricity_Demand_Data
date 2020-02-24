The most granular results are for the 56 balancing authorities in this
directory.

At the balancing authority level, there are 4 values associated with
each hourly interval.

  * `raw demand (MW)` - the raw demand values as queried from EIA, missing values are filled with `MISSING` or `EMPTY`
  * `category` - the classification of each hourly `raw demand (MW)` value via the anomaly screening process
  * `cleaned demand (MW)` - cleaned demand values with missing and anomalous values replaced by imputed values
  * `forecast demand (MW)` - the day ahead value forecasted by the balancing authority returned from the EIA database. These values are *NOT* used anywhere in the cleaning process, but are kept for others as a reference

Two of the balancing authorities, SEC and OVEC, have significant
enough reporting problems that we do not impute cleaned data for them.
For these two balancing authorities there is no assicated file in this directory.
