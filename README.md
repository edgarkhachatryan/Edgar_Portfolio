# Edgar Portfolio


## [Time Series Forecast with horizon using electricity data](https://github.com/edgarkhachatryan/ExampleProjects/tree/master/ElectricityForecastWithTimeHorizon)

### Overview
The project is aiming to create a Deep Learning model electricity consumption forecast using previous consumption level. The dataset was taken from PJM Interconnection LLC, which a regional transmission organization in the US. Dataset contains total provided electricity data for 12 companies in Megawatts. The current project uses consumption data for 2 companies:
1. Duquesne Light (DUQ) and,
2. American Electric Power Co., Inc. (AEP).
DUQ provide electricity to the Allegheny and Beaver counties located in the eastern part of Pennsylvania, US inluding Pittsburgh city. AEP provides electricity to much broader territory, covering areas in Virginia, West Virginia, Ohio, Indiana, and Michigan.

First dataset contains hourly consumptions from "2005-01-01 01:00:00" to "2018-08-03 00:00:00" or 119,068 records in total.  
|      Datetime       | DUQ_MW |
|        :---:        | :---: |
| 2005-01-01 01:00:00 | 1364.0 |
| 2005-01-01 02:00:00 | 1273.0 |
| 2018-08-03 00:00:00 | 1656.0 |
 
Second dataset contains consumptions from "2004-10-01 01:00:00" to "2018-08-03 00:00:00" or 121,273  records.
|Datetime|AEP_MW|
| --- | --- |
| 2004-10-01 | 12379.0 |
| 2004-10-01 | 11935.0 |
| 2018-08-03 | 14809.0 |

| Command | Description |
| --- | --- |
| `git status` | List all *new or modified* files |
| `git diff` | Show file differences that **haven't been** staged |

|A|B|C|AA|
| --- | --- | --- | --- |
|Q|W   |    E | RR     |

### Exploratory visualizations
The following plots show the cyclic pattern of data. Moreover, cycles are seen on the daily and weekly basis as well as on seasonal (yearly) basis.
![Duquesne Light Electricity consumption 1st week.](/images/DUQ_cons1.png)
![Duquesne Light Electricity consumption 2nd week.](/images/DUQ_cons2.png)
![Duquesne Light Electricity consumption for 2 years.](/images/DUQ_cons3.png)


# [Project2]()
