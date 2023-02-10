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

![series2](https://user-images.githubusercontent.com/121902546/218170905-a0acd83b-268a-4e8b-b313-4ad657659e4a.png)

# Auto-ARIMA Model

ARIMA stands for Auto-Regressive Integrated Moving Averages. It's a popular methor for time series forecasting following the assumptions of a stationary and univariate series. ARIMA forecast the future based on past performance.

To implement ARIMA models we need to set up three parameters:

* p, referring to the auto-regressive term.
* d, the degree of differencing.
* q, the size of the moving average window.

In case of seasonality we can also set up the parameters P, D and Q. 

Auto-ARIMA searches for the best combination of (p,d,q)(P,D,Q) through analysis of AIC (Akaike Information Criterion) and BIC (Bayesian Information Criterion). If one chooses to not use Auto-ARIMA and proceed with ARIMA, it'll be necessary to make the series stationary (checking the stationarity through Dickey Fuller test, for example, and performing required transformations if needed). It'll also be necessary to determine the values of p and q.



In this analysis (using *stepwise = True* for faster analysis instead of fitting all hyper-parameters combinations) the best model found by Auto-ARIMA was ARIMA(1,1,0)(2,0,2), leading to the following results:

![series](https://user-images.githubusercontent.com/121902546/218174151-1a9bf9ac-7749-4445-840e-4fd113861d59.png)

Despite one outlier in our first measure, the model fits in a good degree with the train data and have a good forecast when compared to the test sample.

To evaluate the errors, three metrics were used - Mean absolute error (MAE), root mean squared error (RMSE) and Root Mean Squared Percentage Error (RMSPE).

![errors2](https://user-images.githubusercontent.com/121902546/218174550-f69eefb3-8e05-409b-b4c2-a30a10f4da91.png)


To check the commented code click [here](AutoArima_CarbonDioxide.ipynb).

To check a brief Power BI report with data about the sources of Carbon Dioxide emissions and Auto-ARIMA forecast grouped by trimesters, click [here](https://app.powerbi.com/view?r=eyJrIjoiODViOTVjZWMtNDY0NS00ZjlkLTg1ZGEtOWY5NGUxMWQ5MGY0IiwidCI6IjJjOTUwZWUxLWY4ZWYtNDY1MS05ZmRiLTIwZjRjNjk0ZTAzYyJ9).
