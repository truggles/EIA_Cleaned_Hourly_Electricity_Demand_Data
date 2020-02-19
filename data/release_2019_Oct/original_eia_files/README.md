This directory contains the original raw demand data we queried from EIA on 10 September 2019.

At the balancing authority level, there are 2 values associated with
each hourly interval.

  * `demand (MW)` - the raw demand values as queried from EIA, missing values are denoted as `MISSING` while empty values are denoted as `EMPTY`.
  * `forecast demand (MW)` - the day ahead value forecasted by the balancing authority returned from the EIA database. These values are *NOT* used anywhere in the cleaning process, but are kept for others as a reference. The same `MISSING` and `EMPTY` categories are used here.

For those interested in reproducing the exact results of our screening and imputation
algorithms, these are in the input files to use.
