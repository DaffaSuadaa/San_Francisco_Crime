# San Francisco Crime
The data I will be using is from the San Francisco Police Department, a public dataset made available through DataSF (https://data.sfgov.org/).

**Objective**
* Cleaning data
* See the full range and types of crime from 2018 to April 2023
* Mapping crime by district
* The most crime rate every day and hour
* The most crime category
* Incidents in the past year

### Preparations
* Police_Department_Incident_Reports_2018_to_Present.csv
* Historical Police Districts.geojson

``` R
#Loading libraries
library(tidyverse) 
#Path of list files
list.files(path = "../input")
```
