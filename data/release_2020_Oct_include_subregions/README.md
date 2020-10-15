# October 2020 Release - with sub-regions

 * The EIA Open Data portal provides sub-balancing authority level hourly demand data for certain BAs: 'CISO', 'ISNE', 'MISO', 'NYIS', 'PJM', 'SWPP', 'ERCO', and 'PNM'.
 * In general data collection at this granularity began in July 2018. The first hour of data for each region is listed here:
   * California Independent System Operator (CISO)
     * 2018-07-01 08:00:00
   * ISO New England (ISNE)
     * 2018-07-01 05:00:00
   * Midcontinent Independent System Operator, Inc. (MISO)
     * 2018-07-01 06:00:00
   * New York Independent System Operator (NYIS)
     * 2018-06-19 05:00:00
   * PJM Interconnection, LLC (PJM)
     * 2018-07-01 05:00:00
     * substantial data gap before 2018-09-18
   * Public Service Company of New Mexico (PNM)
     * 2018-07-01 08:00:00
     * Two subregions have no reported data: FREP and JICA
   * Southwest Power Pool (SWPP)
     * 2018-08-31 06:00:00
   * Electric Reliability Council of Texas, Inc. (ERCO)
     * 2019-05-27 06:00:00
 * Data for all regions and subregions used in this directory were querried on 14 October 2020.
 * We clean 2 full years of demand data by considering data from 1 Oct 2018 through 30 Sept 2020 after making the following exclusions:
   * sub-regional ERCO data are excluded from the imputation process because of their May 2019 data start date.
   * sub-regional PNM data are excluded from the imputation process because most of their subregions are small and yield a very high filtering rate for the `idential_run` filter and the `anomalous_region` filter.
   * a single PJM sub-region (PJM-RECO, https://www.eia.gov/opendata/qb.php?category=3390296&sdid=EBA.PJM-RECO.D.H) is excluded because the last reported value is in April of 2019.
 * The resulting imputation is performed on the 54 BAs minus 'CISO', 'ISNE', 'MISO', 'NYIS', 'PJM', 'SWPP' plus the sub-regions for 'CISO', 'ISNE', 'MISO', 'NYIS', 'PJM', 'SWPP' (excluding the one mentioned PJM subregion). This results in 113 geographic regions represented across 2 years of data.
 * Beyond the replacement of a few BAs with their sub-regions, the methodology remains unchanged for producing this updated set of cleaned demand data.
 * For comparison, we produced versions of the data summary tables that were found in the original paper. These modified tables reveal no substantial changes in performance of the anomaly identification or imputation methods.
   * Table 1: `anomalous_value_summary_subregions.csv`
   * Table 2: `anomalous_value_summary_post-imputation_screening_subregions.csv`
   * Table 3: `imputation_results_and_biases_subregions.csv`
   * These result files show similar performance in comparison with the original 54 BA method in terms of the relative fraction of hourly values originally filtered and the quantity of hours filtered on a second pass.

# Subdirectory documentation

The single subdirectory includes the 2 years of cleand data for the 113 subregions and BAs. The included subregions and BAs are:
 * AEC  
 * AECI  
 * AVA  
 * AZPS  
 * BANC  
 * BPAT  
 * CHPD  
 * CISO-PGAE  
 * CISO-SCE  
 * CISO-SDGE  
 * CISO-VEA  
 * CPLE  
 * CPLW  
 * DOPD  
 * DUK  
 * EPE  
 * ERCO  
 * FMPP  
 * FPC  
 * FPL  
 * GCPD  
 * GVL  
 * HST  
 * IID  
 * IPCO  
 * ISNE-4001  
 * ISNE-4002  
 * ISNE-4003  
 * ISNE-4004  
 * ISNE-4005  
 * ISNE-4006  
 * ISNE-4007  
 * ISNE-4008  
 * JEA  
 * LDWP  
 * LGEE  
 * MISO-0001  
 * MISO-0004  
 * MISO-0006  
 * MISO-0027  
 * MISO-0035  
 * MISO-8910  
 * NEVP  
 * NSB  
 * NWMT  
 * NYIS-ZONA  
 * NYIS-ZONB  
 * NYIS-ZONC  
 * NYIS-ZOND  
 * NYIS-ZONE  
 * NYIS-ZONF  
 * NYIS-ZONG  
 * NYIS-ZONH  
 * NYIS-ZONI  
 * NYIS-ZONJ  
 * NYIS-ZONK  
 * PACE  
 * PACW  
 * PGE  
 * PJM-AE  
 * PJM-AEP  
 * PJM-AP  
 * PJM-ATSI  
 * PJM-BC  
 * PJM-CE  
 * PJM-DAY  
 * PJM-DEOK  
 * PJM-DOM  
 * PJM-DPL  
 * PJM-DUQ  
 * PJM-EKPC  
 * PJM-JC  
 * PJM-ME  
 * PJM-PE  
 * PJM-PEP  
 * PJM-PL  
 * PJM-PN  
 * PJM-PS  
 * PNM  
 * PSCO  
 * PSEI  
 * SC  
 * SCEG  
 * SCL  
 * SOCO  
 * SPA  
 * SRP  
 * SWPP-CSWS  
 * SWPP-EDE  
 * SWPP-GRDA  
 * SWPP-INDN  
 * SWPP-KACY  
 * SWPP-KCPL  
 * SWPP-LES  
 * SWPP-MPS  
 * SWPP-NPPD  
 * SWPP-OKGE  
 * SWPP-OPPD  
 * SWPP-SECI  
 * SWPP-SPRM  
 * SWPP-SPS  
 * SWPP-WAUE  
 * SWPP-WFEC  
 * SWPP-WR  
 * TAL  
 * TEC  
 * TEPC  
 * TIDC  
 * TPWR  
 * TVA  
 * WACM  
 * WALC  
 * WAUW  
