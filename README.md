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

| Datetime | AEP_MW |
| :---: | :---: |
| 2004-10-01 01:00:00 | 12379.0 |
| 2004-10-01 02:00:00 | 11935.0 |
| 2018-08-03 00:00:00 | 14809.0 |

### Exploratory visualizations
The following plots show the seasonal patterns of data. Here are reprsented the daily, weekly and annual seasonality.
![Duquesne Light Electricity consumption 1st week.](/images/DUQ_cons1.png)
![Duquesne Light Electricity consumption 2nd week.](/images/DUQ_cons2.png)

Preliminary analysis of data shows seasonal nature of . Because, during summertime energy consumption increases. 
![Duquesne Light Electricity consumption for 2 years.](/images/DUQ_cons3.png)

Before feeding consumption data to ML model is should be standardized, but since it has strong seasonality, average of data should be timewise. For that a column should be added that represent the day of week and the hour of the day information.

| Datetime | Cons | WeekDayHour* | 
| :---: | :---: | :---: |
| 2005-01-01 01:00:00 | 1364.0 | 5_01 |
| 2005-01-01 02:00:00 | 1273.0 | 5_02 |
| 2005-01-01 03:00:00 | 1218.0 | 5_03 |
| 2005-01-01 04:00:00 | 1170.0 | 5_04 |
| 2005-01-01 05:00:00 | 1166.0 | 5_05 |

*Where fist digit represents the day of week and the last 2 the hour of the day.


![](/images/DUQ_act_forecast.png)
![](/images/DUQ_act_forecast_best.png)
![](/images/DUQ_act_forecast_worst.png)
