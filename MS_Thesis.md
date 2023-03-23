## Nitrogen and Phosphorus Budgets in Estuaries Along the Texas Coast
The focus of this project was to conduct a meta-analysis on water quality over an extended period of time using **SAS 9.4**. This project is currently undergoing preparations to be published as a chapter in the new environmental report on freshwater inflow to Texas estuaries. 


### Summary
This study examined how hydrology affects nutrient budgets in Texas estuaries using biogeochemical budget modeling based on the Land Ocean Interactions in the Coastal Zone ([LOICZ](https://www.sciencedirect.com/science/article/pii/S2213305416300054)) guidelines. Results showed that precipitation is a driving factor in water budgets and hydrology is strong driver of nutrient concentrations. However, nutrient levels were elevated in two estuaries due to other external factors such as urbanization and agricultural runoff. The Trinity-San Jacinto Estuary had higher phosphorus levels, while the Upper Laguna Madre Estuary had higher nitrogen levels. These findings suggest that changes in hydrology and environmental conditions can impact estuarine nutrient dynamics and affect biological productivity and water quality.

### Data Sources

1. Texas Water Development Board (TWDB) <br>
```Contains all the water data including gaged flows, ungaged flows, modeled flows, diversions, and evaporation rates from 1940-2020```
2. National Oceanic & Atmospheric Administration (NOAA) Global Historical Climatology Network (GHCN) database <br>
```Contains all the precipitation data at weather stations nearest to each estuary from 1940-2020```
3. Texas Parks & Wildlife Department (TPWD) <br>
```Contains all the salinity data in each bay system and their adjacent gulf stations offshore from 1977-2020```
4. Texas Commission of Environmental Quality (TCEQ) <br>
```Contains all of the nutrient data in each bay system and their adjacent gulf stations offshore from 1969-2020```

### Data Cleaning

Please note that there were numerous SAS programs involved in the data cleaning process (i.e., extract, transform, load) prior to conducting analyses. However, these are not included here in order to streamline and condense the presentation of my work.
Summary of the cleaning process:
- Imported all raw data from four external organizations into SAS, including files in txt and csv formats.
- Removed any irrelevant columns from the dataset.
- Conducted a normality test on all variables to assess their distribution using the proc univariate command, and generated plots to visualize the results.
- For variables that showed evidence of non-normality, a natural log transformation and then detransformation was performed before conducting further analyses.
- Standardized the units of water, salt, and nutrient values to cubic meters per day to facilitate comparison.
- Organized the data by grouping first by station and then by estuary.

### Key Findings

#### Water

The Sabine-Neches Estuary (SN) had the highest average annual precipitation, while the Upper Laguna Madre Estuary (ULM) had the lowest, indicating a northeast to southwest climate gradient along the Texas coast. <br>
![image](https://user-images.githubusercontent.com/123992539/227271676-d62a8392-1140-4074-a5fe-671170fe5f70.png) <br>


A correlation analysis showed a significant monotonic relationship (p < 0.0001) between precipitation and freshwater inflow balance, with increasing precipitation corresponding to an increase in freshwater inflow balance. <br>
![image](https://user-images.githubusercontent.com/123992539/227273055-ac6cc81d-6353-4ed9-a9c6-3a128c49817d.png) <br>
SAS Code:
```SAS
proc sort data=water (where=(Estuary='SN')) out=sn_water; by Estuary; run;
title;ods html close; ods html; 
proc corr data=sn_water spearman PLOTS=SCATTER(NVAR=all);
var VB pax;
run;
```
SAS code was repeated 7 more times for the remaining estuaries. <br>


SAS Code:
```SA
