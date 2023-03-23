## Nitrogen and Phosphorus Budgets in Estuaries Along the Texas Coast
The focus of this project was to conduct a meta-analysis on water quality over an extended period of time using **SAS 9.4**. This project is currently undergoing preparations to be published as a chapter in the new environmental report on freshwater inflow to Texas estuaries. This document is a very condensed version of the actual project.


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
SAS Code:
```SAS
proc means data=DM.precip_ghcnd noprint;
by Estuary;
var Precip;
output out=precip_est_avg mean=Precip;
run;
```

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


#### Salt

Daily salinity values in the bay systems of all 8 estuaries exhibit significant year-to-year variability. ANOVA testing (p<0.001, n=139560) showed statistically different average salinity values in each estuary's bay systems. Post-hoc analysis using Tukey's HSD indicated that salinity values followed this order: ULM < LLM < NC < MA < LC < GE < TS < SN, with the Upper Laguna Madre Estuary (ULM) having the highest and Sabine-Neches Estuary (SN) having the lowest salinity averages. <br>
![image](https://user-images.githubusercontent.com/123992539/227275822-0f329f81-cdfa-4ff3-8bd5-61e9e7ac808b.png) <br>
SAS Code:
To creat the salinity time series graph,
```SAS
proc sgplot data=baysal_series;
styleattrs 
datasymbols=(circlefilled asterisk diamondfilled square starfilled circle trianglefilled plus)
datalinepatterns=(solid);
	series x=Year y=sal_mean / markers
	group=Estuary
	smoothconnect;
	xaxis interval=year label='Year';
	yaxis label='Salinity (S)';
run; quit;
```
To perform the ANOVA,
```SAS
proc glm data=sal_h2o plots(maxpoints=none);
class Estuary;
model salinity = Estuary;
means Estuary / tukey;
run;
quit;
```

#### Nutrients

A principal component analysis (PCA) assessed the relationship between daily average nutrient values with inflow balance and salinity. PC1 and PC2 explained 59% and 24% of the data variability, respectively. Inflow balance and dissolved inorganic nitrogen (DIN), as well as total phosphorus (TP), were positively correlated with each other on PC1, while inflow balance was inversely correlated with salinity. Total organic nitrogen (TON) was orthogonal to inflow balance. Estuary sample score results followed a climate gradient pattern. The analysis suggests that hydrology is a strong driver of nutrient levels in Texas estuaries. <br>

![image](https://user-images.githubusercontent.com/123992539/227278730-cc461563-31aa-4cbe-bcff-b70a5abb0f2a.png) <br>
SAS Code:
```SAS
proc standard data=Summ out=wx mean=0 std=1 replace ;
 var Inflow_Balance RT Salinity NH4 NO2 NO3 TP DIP TKN DIN TON;
run;
title 'Principal components analysis, water data standardized N(0,1)';
proc factor data=wx method=principal rotate=varimax nfactors=3  
            preplot nplot=3 plots(flip)=(scree initloadings(vector) loadings(vector))  
            out=Scores outstat=pcsstat;
     var Inflow_Balance Salinity DIN TON TP;
	 run;
```

A graph of de-transformed daily nutrient averages and their standard errors was created for each estuary in Texas. The high DIP and TP concentrations in the Trinity-San Jacinto Estuary could explain its position on the PC2 axis. Additionally, the graph shows that the Upper Laguna Madre has higher TKN levels compared to other estuaries in Texas. <br>
![image](https://user-images.githubusercontent.com/123992539/227279572-c4d360f3-807e-4459-8700-3c252e437d70.png) <br>
SAS Code:
```SAS
proc sgplot data=bay_npmeans;
  scatter x=en y=dNH4 / yerrorupper=uNH4 yerrorlower=lNH4 markerattrs=(symbol=squarefilled size=12) ;
  yaxis label='NH4 (mmol/m³)';
  xaxis label='Estuary' values=(1 to 8 by 1) offsetmin=.05 offsetmax=.05;
  format EN en.;
  inset "A" / noborder position=topleft;
  run; quit;
```
Repeated code with the other nutrient variables.

### Conclusion ###

This study highlights the relationship between hydrology and water, salt, and nutrient dynamics in Texas estuaries. While precipitation drives inflow and subsequently salinity and nutrient budgets, other factors such as human activities and biological processes also influence nutrient dynamics. Different estuaries are exposed to various factors that affect nutrient sources and sinks, and the impact of these factors can vary. Physical, chemical, and biological processes, such as river discharge and phytoplankton activity, also play a role. Human activities, such as damming and wastewater treatment, can strongly affect nutrient dynamics. The high levels of phosphorus in the Trinity-San Jacinto Estuary can be attributed to the surrounding urbanization and high population density in Harris, Chambers, Galveston, and Brazoria County. The use of detergents, urine, and fecal matter containing phosphorus in this area is released through the wastewater treatment plants, leading to a substantial amount of phosphorus being introduced into the estuary. Concentration of multiple wastewater treatment plants in one area can further exacerbate this issue, resulting in significant effects on estuarine processes. Like the Trinity-San Jacinto Estuary, the Upper Laguna Madre Estuary's nutrient levels are not solely influenced by hydrology. Its unique geography and habitats, such as tidal mudflats and seagrass beds, create an environment favorable to organic nitrogen proliferation, resulting in the highest TKN concentrations in Texas estuaries. Additionally, this estuary is mainly fed by sewage discharge and agricultural runoff.
