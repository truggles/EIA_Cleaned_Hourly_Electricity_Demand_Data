Included in the table at the bottom of the main README is the mapping of each balancing authority to 13 geographic regions.
We provide regional aggregates corresponding to this mapping.
The regional files contain `raw demand (MW)` and `cleaned demand (MW)` values for each hour.
We replace cases of `MISSING` or `EMPTY` `raw demand (MW)` values with 0 before aggregating.

Region to BA mapping:  
CENT ['SPA', 'SWPP']  
MIDW ['AECI', 'EEI', 'LGEE', 'MISO']  
TEN ['TVA']  
SE ['AEC', 'SEPA', 'SOCO']  
FLA ['FMPP', 'FPC', 'FPL', 'GVL', 'HST', 'JEA', 'NSB', 'SEC', 'TAL', 'TEC']  
CAR ['CPLE', 'CPLW', 'DUK', 'SC', 'SCEG', 'YAD']  
MIDA ['OVEC', 'PJM']  
NY ['NYIS']  
NE ['ISNE']  
TEX ['ERCO']  
CAL ['BANC', 'CISO', 'IID', 'LDWP', 'TIDC']  
NW ['AVA', 'AVRN', 'BPAT', 'CHPD', 'DOPD', 'GCPD', 'GRID', 'GWA', 'IPCO', 'NEVP', 'NWMT', 'PACE', 'PACW', 'PGE', 'PSCO', 'PSEI', 'SCL', 'TPWR', 'WACM', 'WAUW', 'WWA']  
SW ['AZPS', 'DEAA', 'EPE', 'GRIF', 'GRMA', 'HGMA', 'PNM', 'SRP', 'TEPC', 'WALC']  

Full naming if it is not clear above:  
CENT : Central  
MIDW : Midwest  
TEN : Tennessee  
SE : Southeast  
FLA : Florida  
CAR : Carolinas  
MIDA : Mid-Atlantic  
NY : New York  
NE : New England  
TEX : Texas  
CAL : California  
NW : Northwest  
SW : Southwest  
