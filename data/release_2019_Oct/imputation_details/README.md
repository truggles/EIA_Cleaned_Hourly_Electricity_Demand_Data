This directory contains a zip file to cut the size of the two corresponding
files in half. These files will only be used by researchers interested in the details of the
MICE imputation method. The two files are:

  * `all_impute_csv_MASTER.csv` containing an index column, one for the `date_time` field, `imp_index` ranging from 1-16 denoting which of the 16 chains the row belongs to, then the 54 balancing authorities with imputed results.
  * `mean_impute_csv_MASTER.csv` contains the same columns above except it lacks the `imp_index` field as it is the mean of the 16 chains.

The 54 columns with balancing authority acronyms as headers correspond to what is called `cleaned demand (MW)`
throughout the rest of this repository.

The values in `mean_impute_csv_MASTER.csv` correspond to the imputed values found throughout the rest of this repository.
