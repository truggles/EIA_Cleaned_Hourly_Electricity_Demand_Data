# EIA_Cleaned_Hourly_Electricity_Demand_Data
A repository for publishing and versionsing cleaned EIA hourly demand data

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3517197.svg)](https://doi.org/10.5281/zenodo.3517197)

Shield: [![CC BY 4.0][cc-by-shield]][cc-by]

This work is licensed under a [Creative Commons Attribution 4.0 International
License][cc-by].

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg


## Overview and Citation
The raw hourly electricity demand data queried from the
U.S. Energy Information Administration (EIA) show 2.2% of hourly values are missing.
We have developed a data cleaning process that consists of flagging anomalous demand values,
which constitute about 0.5% of the total data.
We impute missing demand values and the values flagged as anomalous using a
Multiple Imputation by Chained Equations (MICE) technique.
The MICE technique provides complete data sets without any extremely anomalous values.

Until we have a preprint manuscript available, please cite:

```
Tyler Ruggles, & David Farnham. (2019). EIA Cleaned Hourly Electricity Demand Data  
(Version v1.0_23Oct2019) [Data set]. Zenodo. http://doi.org/10.5281/zenodo.3517197
```

which details the data cleaning process used to create these final data sets.

The raw data were queried from the EIA database on September 10, 2019 and
spans from their initial data entries on 2015-07-01 05:00:00 UTC to 2019-08-31 23:00:00 UTC.
The first day of data has been removed because of significant reporting inconsistencies.



## Original Data Source
Original hourly demand data is collected from electric balancing authorities
by the U.S. Energy Information Administration (EIA) via Form-930.
Raw data is made available to the public through the EIA Open Data portal documented here:

<https://www.eia.gov/opendata/>

The specific hourly demand data used is originally located here:

<https://www.eia.gov/opendata/qb.php?category=2122628>

At the end of this README is a list of the 67 balancing authorities in the contiguous U.S.
Demand data is provided for the 56 balancing authorities which have demand.
The 11 balancing authorities that include generation only are denoted as such.

The EIA began collecting hourly demand data in July of 2015 and continuously publishes new values each day.

The reported demand value for each hour corresponds to the integrated mean value in megawatts over the previous hour.



## Available Cleaned Data
The final data product is available to everyone. As the hourly demand data
is a continuously growing data record in the EIA database, we plan to update
this repository with new cleaned data annually.

Data is stored in csv format with each row corresponding to an hour of demand information.
The date/time is recorded in column `data_time` as `YYYYMMDDTHHZ`. The `Z` indicates that all times are UTC.

The data can be accessed at different levels of geographic granularity
ranging from the most granular balancing authority level to the contiguous
U.S.

For reference, at the balancing authority level, we retain the original 
raw EIA demand data in the final cleaned product (`Raw Demand (MW)`). See the next section for details.

### Balancing Authority Level Data
The most granular results are for the 56 balancing authorities in this
[directory](https://github.com/truggles/EIA_Cleaned_Hourly_Electricity_Demand_Data/tree/master/data/release_2019_Oct/balancing_authorities "balancing_authorities"):

`data/release_2019_Oct/balancing_authorities/`

At the balancing authority level, there are 4 values associated with
each hourly interval.

  * `Raw Demand (MW)` - the raw demand values as queried from EIA, missing values are filled with `MISSING` or `EMPTY`
  * `Forecasted Demand (MW)` - the day ahead value forecasted by the balancing authority returned from the EIA database. These values are *NOT* used anywhere in the cleaning process, but are kept for others as a reference; similar to above missing values are filled with `MISSING` or `EMPTY`
  * `Classification` - the classification of each hourly `Raw Demand (MW)` value via the anomaly screening process
  * `Cleaned Demand (MW)` - cleaned demand values with missing and anomalous values replaced by imputed values

Two of the balancing authorities, SEC and OVEC, have significant
enough reporting problems that we do not impute cleaned data for them.
For these two balancing authorities, the `Classification` and `Cleaned Demand (MW)`
columns are filled with `NA` values.

### Regional Level Data
Included in the table at the bottom of this README is the mapping of each balancing authority to 13 geographic regions.
We provide regional aggregates corresponding to this mapping.
The regional files only contain the `Cleaned Demand (MW)` value for each hour.
This is because, in all cases, the cleaning is done at the balancing authority level.
Therefore, the other three values would be difficult to interpret in cases where any values are `NA` or missing.
The regional data is in this [directory](https://github.com/truggles/EIA_Cleaned_Hourly_Electricity_Demand_Data/tree/master/data/release_2019_Oct/regions "regions"):

`data/release_2019_Oct/regions/`

### Interconnects Data
There are three interconnects in the contiguous U.S. electric grid, <https://www.eia.gov/todayinenergy/detail.php?id=27152>.
Similar to the regional data files, we aggregate the balancing authority level results into the three interconnects.
*NOTE:* the contributions from Mexico and Canada are *NOT* included in these interconnect files.
The interconnect data is in this [directory](https://github.com/truggles/EIA_Cleaned_Hourly_Electricity_Demand_Data/tree/master/data/release_2019_Oct/interconnects "interconnects"):

`data/release_2019_Oct/interconnects/`

### Contiguous U.S. Data
All 54 balancing authorities (excludes SEC and OVEC as discussed above) are aggregated to create a
contiguous U.S. total. Please see this [directory](https://github.com/truggles/EIA_Cleaned_Hourly_Electricity_Demand_Data/tree/master/data/release_2019_Oct/contiguous_US "contiguous_US"):

`data/release_2019_Oct/contiguous_US/`



## Accessing the Data / Repository Checkout
To checkout the cleaned demand data and create a simple time series distribution
for your favorite balancing authority (ERCOT in the example) follow these commands if you have previously installed
the python libraries pandas and matplotlib.

```
git clone git@github.com:truggles/EIA_Cleaned_Hourly_Electricity_Demand_Data.git
cd EIA_Cleaned_Hourly_Electricity_Demand_Data
python -i
>>> import pandas as pd
>>> import matplotlib.pyplot as plt
>>> df = pd.read_csv('data/release_2019_Oct/balancing_authorities/ERCO.csv')
>>> df['date_time'] = pd.to_datetime(df['date_time'])
>>> fig, axs = plt.subplots(2)
>>> axs[0].plot(df['date_time'], df['Cleaned Demand (MW)'])
>>> axs[1].plot(df.loc[1000:1250, 'date_time'], df.loc[1000:1250, 'Cleaned Demand (MW)'])
>>> plt.show()
>>> exit()
```



## The MICE Imputation Process
We include a directory for people interested in further details of the imputation process.

`data/release_2019_Oct/imputation_details/`

This [directory](https://github.com/truggles/EIA_Cleaned_Hourly_Electricity_Demand_Data/tree/master/data/release_2019_Oct/imputation_details "imputation_details")
compresses the two corresponding files into a zip file. These files should only be used by those interested in the details
of the imputation process. See the README in that directory for more details.



## Table of Acronyms and Mappings
This table shows the 67 balancing authorities in the contiguous U.S. as well as their `Code` used to identify their
files within this repository. For a geographic map, please see:

<https://www.eia.gov/realtime_grid/>


| Code | Name | Time Zone | Region | Generation Only |
|------|------|-----------|--------|-----------------|
| AEC | PowerSouth Energy Cooperative | Central | Southeast |    |
| AECI | Associated Electric Cooperative, Inc. | Central | Midwest |    |
| AVA | Avista Corporation | Pacific | Northwest |    |
| AVRN | Avangrid Renewables, LLC | Pacific | Northwest | Yes |
| AZPS | Arizona Public Service Company | Arizona | Southwest |    |
| BANC | Balancing Authority of Northern California | Pacific | California |    |
| BPAT | Bonneville Power Administration | Pacific | Northwest |    |
| CHPD | Public Utility District No. 1 of Chelan County | Pacific | Northwest |    |
| CISO | California Independent System Operator | Pacific | California |    |
| CPLE | Duke Energy Progress East | Eastern | Carolinas |    |
| CPLW | Duke Energy Progress West | Eastern | Carolinas |    |
| DEAA | Arlington Valley, LLC | Arizona | Southwest | Yes   |
| DOPD | PUD No. 1 of Douglas County | Pacific | Northwest |    |
| DUK | Duke Energy Carolinas | Eastern | Carolinas |    |
| EEI | Electric Energy, Inc. | Central | Midwest |  Yes  |
| EPE | El Paso Electric Company | Arizona | Southwest |    |
| ERCO | Electric Reliability Council of Texas, Inc. | Central | Texas |    |
| FMPP | Florida Municipal Power Pool | Eastern | Florida |    |
| FPC | Duke Energy Florida, Inc. | Eastern | Florida |    |
| FPL | Florida Power & Light Co. | Eastern | Florida |    |
| GCPD | Public Utility District No. 2 of Grant County, Washington | Pacific | Northwest |    |
| GRID | Gridforce Energy Management, LLC | Pacific | Northwest | Yes |
| GRIF | Griffith Energy, LLC | Arizona | Southwest | Yes |
| GRMA | Gila River Power, LLC | Arizona | Southwest | Yes |
| GVL | Gainesville Regional Utilities | Eastern | Florida |    |
| GWA | NaturEner Power Watch, LLC | Mountain | Northwest | Yes |
| HGMA | New Harquahala Generating Company, LLC | Arizona | Southwest | Yes   |
| HST | City of Homestead | Eastern | Florida |    |
| IID | Imperial Irrigation District | Pacific | California |    |
| IPCO | Idaho Power Company | Pacific | Northwest |    |
| ISNE | ISO New England | Eastern | New England |    |
| JEA | JEA | Eastern | Florida |    |
| LDWP | Los Angeles Department of Water and Power | Pacific | California |    |
| LGEE | Louisville Gas and Electric Company and Kentucky Utilities Company | Central | Midwest |    |
| MISO | Midcontinent Independent System Operator, Inc. | Central | Midwest |    |
| NEVP | Nevada Power Company | Pacific | Northwest |    |
| NSB | Utilities Commission of New Smyrna Beach | Eastern | Florida |    |
| NWMT | NorthWestern Corporation | Mountain | Northwest |    |
| NYIS | New York Independent System Operator | Eastern | New York |    |
| OVEC | Ohio Valley Electric Corporation | Eastern | Mid-Atlantic |    |
| PACE | PacifiCorp East | Mountain | Northwest |    |
| PACW | PacifiCorp West | Pacific | Northwest |    |
| PGE | Portland General Electric Company | Pacific | Northwest |    |
| PJM | PJM Interconnection, LLC | Eastern | Mid-Atlantic |    |
| PNM | Public Service Company of New Mexico | Arizona | Southwest |    |
| PSCO | Public Service Company of Colorado | Mountain | Northwest |    |
| PSEI | Puget Sound Energy, Inc. | Pacific | Northwest |    |
| SC | South Carolina Public Service Authority | Eastern | Carolinas |    |
| SCEG | South Carolina Electric & Gas Company | Eastern | Carolinas |    |
| SCL | Seattle City Light | Pacific | Northwest |    |
| SEC | Seminole Electric Cooperative | Eastern | Florida |    |
| SEPA | Southeastern Power Administration | Central | Southeast | Yes   |
| SOCO | Southern Company Services, Inc. - Trans | Central | Southeast |    |
| SPA | Southwestern Power Administration | Central | Central |    |
| SRP | Salt River Project Agricultural Improvement and Power District | Arizona | Southwest |    |
| SWPP | Southwest Power Pool | Central | Central |    |
| TAL | City of Tallahassee | Eastern | Florida |    |
| TEC | Tampa Electric Company | Eastern | Florida |    |
| TEPC | Tucson Electric Power | Arizona | Southwest |    |
| TIDC | Turlock Irrigation District | Pacific | California |    |
| TPWR | City of Tacoma, Department of Public Utilities, Light Division | Pacific | Northwest |    |
| TVA | Tennessee Valley Authority | Central | Tennessee |    |
| WACM | Western Area Power Administration - Rocky Mountain Region | Arizona | Northwest |    |
| WALC | Western Area Power Administration - Desert Southwest Region | Arizona | Southwest |    |
| WAUW | Western Area Power Administration - Upper Great Plains West | Mountain | Northwest |    |
| WWA | NaturEner Wind Watch, LLC | Mountain | Northwest | Yes |
| YAD | Alcoa Power Generating, Inc. - Yadkin Division | Eastern | Carolinas | Yes   |
