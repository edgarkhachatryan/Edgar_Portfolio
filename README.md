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

| Datetime | Cons | WeekDayHour* | meanCons* |
| :---: | :---: | :---: | :---: |
| 2005-01-01 01:00:00 | 1364.0 | 5_01 | 1483.9 |
| 2005-01-01 02:00:00 | 1273.0 | 5_02 | 1420.0 |
| 2005-01-01 03:00:00 | 1218.0 | 5_03 | 1375.9 |
| 2005-01-01 04:00:00 | 1170.0 | 5_04 | 1354.1 |
| 2005-01-01 05:00:00 | 1166.0 | 5_05 | 1346.5 |

*Where fist digit represents the day of week and the last 2 the hour of the day.
*Mean consumption is calculated as an average of all consumptions having the same WeekDayHour.

To standardise data th following formula is used: standadized value{i} = log(consumption{i}) - log(mean consumption{i}).

### Model
To predict 1 week ahead (168 hours) model employing previous 4 weeks data (672 hours). Training and test sets are selected as 52 weeks each. So, the input layer has 672 x 1 (1 variable) shape and the output layer has 168  neurons. To predict the confidence intervals as well, additional 2 output layers (for 90% and 10%) should be added. The training has been done on 70 epochs. The evolution of forecast based on mean absolute percentage error (MAPE), which is calculated by the following formula.

![](/images/mape.jpeg)

The average MAPE for the first 3 months was 4.24%.

![](/images/DUQ_act_forecast.png)

The best prediction with 2.63% MAPE is shown below.

![](/images/DUQ_act_forecast_best.png)

The worst prediction with 5.97% MAPE is the following.

![](/images/DUQ_act_forecast_worst.png)
