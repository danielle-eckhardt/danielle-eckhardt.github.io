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

### Key Findings

Please note, there was a lot of SAS 'programs' or queries that went into the ETL cleaning process that is not included on here before analyses were ran.


![image](https://user-images.githubusercontent.com/123992539/227017493-a353989b-721c-49ba-a922-7f2a78236396.png)

SAS Code:
```SAS
proc sgpanel data=bay_dtrans(where=(nox>0 and nox<201));
panelby EN / columns=4 novarname uniscale=all;
scatter x=Salinity y=Nox;
reg x=Salinity y=nox / lineattrs=(color=red thickness=2) nomarkers;
format EN en.;
rowaxis label='NO2 + NO3 (mmol/m³/d)';
colaxis label='Salinity (psu/d)';
run; quit;
```

