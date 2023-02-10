# AutoArima_carbonemissions

This dataset uses information of monthly/annual carbon dioxide emissions from electricity generation (1973-2016) provided by *eia* (U.S Energy Information Administration). Data is broken down by fuel type.

The dataset can be found on [Kaggle](https://www.kaggle.com/datasets/txtrouble/carbon-emissions).

## Data Dictionary

The variables used for the time series forecasting were:

* YYYYMM: Date(year/month)
* Value: Values of carbon dioxide emissions from electricity generation in MMT units (Million Metric Tons of Carbon Dioxide)

Other important variable in this dataset is the description of the source of emission which will be shown in a Power BI report at the end of this project.

## Data Pre-Processing

* Data cleaning was performed removing duplicated rows and missing data.
* YYYYMM was set as the dataframe index. All columns, besides Values were dropped.
* The data split between train-test samples was performed as following:
      - Train sample: January/1973 to December/2010.
      - Test sample : Janyary/2010 to July/2016.


# Auto-ARIMA Model







To check the commented code click [here](AutoArima_CarbonDioxide.ipynb).

To check a brief Power BI report with data about the sources of Carbon Dioxide emissions and Auto-ARIMA forecast in trimesters, click [here](https://app.powerbi.com/view?r=eyJrIjoiODViOTVjZWMtNDY0NS00ZjlkLTg1ZGEtOWY5NGUxMWQ5MGY0IiwidCI6IjJjOTUwZWUxLWY4ZWYtNDY1MS05ZmRiLTIwZjRjNjk0ZTAzYyJ9).
