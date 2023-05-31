# San Francisco Crime
The data I will be using is from the San Francisco Police Department, a public dataset made available through DataSF (https://data.sfgov.org/).

You can see the running program with R here: [San Francisco Crime](https://www.kaggle.com/code/daffasuadaa/san-francisco-crime)

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

```R
#Importing file
crime <- read.csv("../input/san-francisco-police-department/Police_Department_Incident_Reports_2018_to_Present.csv")
```

``` R
#In this section, I remove some fields that are not important
crime <- crime %>%
  select(-c(CAD.Number,
            Report.Type.Code,
            Report.Type.Description,
            Filed.Online,
            Incident.Code,
            Incident.Subcategory,
            Incident.Description,
            Resolution,
            Intersection,
            CNN,
            Analysis.Neighborhood,
            Supervisor.District,
            Supervisor.District.2012,
            Point,
            Neighborhoods,
            ESNCAG...Boundary.File,
            Central.Market.Tenderloin.Boundary.Polygon...Updated,
            Civic.Center.Harm.Reduction.Project.Boundary,
            HSOC.Zones.as.of.2018.06.05,
            Invest.In.Neighborhoods..IIN..Areas,
            Current.Supervisor.Districts,
            Current.Police.Districts
            ))
```

``` R
#Data after removing some fields
head(crime)
```

```R
#Remove some data that does not have a location
crime_v2 <- crime[!(is.na(crime$Latitude) | is.na(crime$Latitude)),]

head(crime_v2)
```

```R
#Change data to capital letters
crime_v2$Police.District <- toupper(crime_v2$Police.District)

head(crime_v2)
```

The rest of my analysis, I decided to utilize Tableau. I was able to export the merged file I created earlier and import it into Tableau fairly easily. Tableau vizzes can only be displayed in Kaggle using Python, so you will have to use the link below to view the interactive version.

[Tableau](https://public.tableau.com/views/SanFranciscoCrime_16827829936970/DACrime?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link)

<img src="https://github.com/DaffaSuadaa/San_Francisco_Crime/assets/134934646/e59e7b99-c725-42ea-8d3c-3cc5db7fb58b" width="800" height="400">
