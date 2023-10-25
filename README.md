README 
Racial Differences in Parent Response to COVID-19 Schooling Policies
Micah Y. Baum and Brian Jacob


*******************************
This package contains all the code and publicly-available data used in Baum & Jacob (2023): Racial Differences in Parent Response to COVID-19 Schooling Policies. 
All code and analyses should be attributed to Micah Y. Baum and Brian Jacob. You can contact the authors at mybaum@umich.edu and bajacob@umich.edu with any questions. 
*******************************


*******************************
Software Requirements 
*******************************
With one exception, all analyses were conducted in Stata 17.0 SE. 
The master do-file 00_paper_shell.do recreates all analyses conducted in Stata. 
Make sure to input the relevant working directory. 
The full script took approximately 8 hours to run on a Macbook Air (M2) with 16GB of RAM.

Figure S1 is a map generated in R. 
Stata do-file 12_map_data_build.do creates the dataset that is then imported into R. 
The map was made using RStudio 3.02 from the script figure_s1.R. 

District-level partisanship measures were originally generated in ArcGIS Pro 3.1 using the approach described in the paper Data Appendix. 
The district-level measures are included in the replication package as Excel files. 


*******************************
Directions for Use
*******************************
This replication package contains raw data, cleaned final datasets, code, and output files. 

The code provided allows users to re-create nearly all variables used in the analyses (with two exceptoins noted below). 
Users can adapt the code for their own purposes. 
To run all or part of the data cleaning code, refer to the scripts in the "code/build" folder. 

The replication package also includes the final cleaned datasets used in analyses. 
To re-run any analyses, refer to the scripts in the "code/output" folder. 

Lastly, the package contains raw output files underlying the tables and figures in the published version of the paper. 


*******************************
Data Availability
*******************************
With two exceptions, all data in the paper are publicly-available. 
When publicly-available, data can be accessed from the websites linked below.
All data should be cited appropriately as requested by the relevant institutions.

Data from the American Enterprise Institute and Fordham Institute were generously provided by researchers involved in the relevant projects. 
We have not included the raw datasets in the replication file but our analytic dataset contains the final cleaned variables.
Interested researchers should reach out to the following individuals:
-- AEI: Nat Malkus
-- Fordham: Amber Winkler, Janie Scull, Dara Zeehandelaar

All access links below are up-to-date as of 10/24/2023. 


*******************************
Datasets (listed in order of appearance in code)
*******************************

National Center for Education Statistics Common Core of Data (CCD): 
-- datasets: 
---- school characteristics files, 2017-2022
---- school and district directories, 2016-2022
---- district shapefiles and office addresses, 2016-2022
---- school longitudes and latitudes, 2016-2022 
---- district membership (enrollment) files, 2012-2022
---- school membership (enrollment) files, 2016-2022
---- free and reduced price lunch, 2019 
-- availability: public 
---- school/district enrollment, characteristics, and directory data (https://nces.ed.gov/ccd/)
---- geographic data (https://data-nces.opendata.arcgis.com/)
---- free and reduced price lunch (https://nces.ed.gov/ccd/elsi/tableGenerator.aspx)

Social Security Administration
-- datasets:
---- 2017 MSA to county crosswalk
-- availability: public
---- https://www.nber.org/research/data/ssa-federal-information-processing-series-fips-core-based-statistical-area-cbsa-and-metropolitan-and

American Community Survey (2019)
-- datasets:
---- county population density
--availability: public
---- https://www.socialexplorer.com/explore-maps (or many other sources)

US Department of Agriculture
-- datasets:
---- 2013 county rural urban continuum codes 
-- availability: public 
---- https://www.ers.usda.gov/data-products/rural-urban-continuum-codes.aspx

US Census 
-- datasets:
---- 2019 Current Population Survey
-- availability: public
---- https://cps.ipums.org/cps/ 

Fordham Institute
-- datasets:
---- 2012 Union Strength Index 
-- availability: upon request to Fordham Institute

National Right to Work Committee
-- datasets:
---- 2022 right-to-work status 
-- availability: public
---- https://nrtwc.org/

National Council on Teacher Quality 
-- datasets:
---- 2019 state-level collective bargaining legality 
-- availability: public 
---- https://www.nctq.org/contract-database/collectiveBargaining

Harvard Dataverse 
-- datasets:
---- 2016 president precinct-level returns 
-- availability: public
---- https://dataverse.harvard.edu/dataverse/medsl_president

Stanford Education Data Archive
-- datasets:
---- district and school demographics and test scores, 2009-2018
-- availability: public 
---- https://exhibits.stanford.edu/data/catalog/db586ns4974

COVID-19 School Data Hub
-- datasets: 
---- district and school-level learning modes, 2020-21
-- availability: public 
---- https://www.covidschooldatahub.com/

New York Times COVID-19 Dashboard
-- datasets: 
---- 2020-21 county-level COVID-19 deaths, hospitalizations, mask-wearing, and vaccinations  
-- availability: public 
---- https://github.com/nytimes/covid-19-data

American Enterprise Institute
-- datasets:
---- 2021-22 school masking data
-- availability: upon request to AEI


*******************************
Folder Structure and Code Description
*******************************
The package downloads with the folder structure listed below. 
Keep this folder structure to run the package. 
Data are stored in the "data" folder and output is generated in the "output" folder. 

code
-- 00_paper_shell.do: runs Stata code for entire paper 
-- build
---- 1_lea_geo.do: identifies geographic identifiers for public school districts 
---- 2a_grade_enr_clean.do: cleans public school district enrollment data (2012-2022)
---- 2b_charter_grade_enr_clean.do: cleans charter school enrollment data (2016-2022)
---- 2c_charter_pub_assign.do: assigns charter schools to the nearest public district to identify competition sets for each public district
---- 3_union_strength_clean.do: calculates state-level measures of teacher union strength 
-------- will not run without union strength data 
---- 4_district_vote_share.do: calculates district vote shares for Donald Trump in 2016 presidential election
---- 5_seda_clean.do: cleans school district demographic and test score data from the Stanford Education Data Archive
---- 6_learning_modality_v2.do: measures district learning modes at start of 2020-21 school year 
---- 7_covid_severity_2020_2021.do: generates a range of measures of local COVID severity and health precautions (including vaccination and masking rates)
---- 8_aei_mask_required.do: cleans AEI data on school masking policies from 2021-22
-------- will not run without AEI data 
---- 9_make_time_invariant_district_file_v6.do: merges the cross-sectional datasets created in do-files 1-8 into a single district-level file
---- 10_instr_construct.do: generates instruments for learning modes/mask policies used in IV models 
---- 10b_imp_instr_construct.do: calculates same instruments for robustness checks that include larger samples of districts
---- 11_prep_offtrend.do: prepares analytic panel dataset with one observation per district-year-race/age group. Also generates Table S15
---- 11b_prep_offtrend_imp.do: prepares analogous analytic dataset for robustness models that include districts with imputed learning modes
---- 11c_prep_offtrend_no_min_size.do: prepares analogous analytic dataset for robustness models that include districts of all sizes
---- 11d_pub_ch_prep_offtrend_regs.do: prepares analogous analytic dataset for robustness models where the outcome is enrollment in public + charter schools in a given area
---- 12_map_data_build.do: prepares dataset used to generate paper Figure S1 (the map of learning modes/mask policies)

--output
---- output_shell.do: generates all but one paper figure and table (Figures 1-4, Tables S1-S16 excluding Table S15, Figures S2-S5)
---- figure_s1.R: generates paper Figure S1


data (size in parentheses)
-- AEI_Masking (empty)
-- CCD (45.0GB unzipped, XX zipped)
---- characteristics (172MB)
---- directory (558MB)
---- District_Shapefiles (5.1GB)
---- geocode (192MB)
---- membership (32.3GB)
---- misc (21MB)
---- temp (<1 MB)
-- Covid_Cases (1.1GB)
-- District_LearningModel (57MB)
-- District_Partisanship (193MB)
-- Precincts_Shapefiles (2.2GB)
-- School_LearningModel (253MB)
-- SEDA (615MB)
-- Union_Strength (raw Fordham data are missing) (107MB)

output 
-- all paper figures and tables in raw format
