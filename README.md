## ITALIAN CITY AIR QUALITY DATA-MARCH-2004-TO-FEBRUARY-2005

## INTRODUCTION
I downloaded a dataset from kaggle.The dataset contains 9358 instances of hourly averaged responses from an array of 5 metal oxide chemical sensors embedded in an Air Quality Chemical Multisensor Device. The device was located on the field in a significantly polluted area, at road level,within an Italian city. Data were recorded from March 2004 to February 2005 (one year)representing the longest freely available recordings of on field deployed air quality chemical sensor devices responses. Ground Truth hourly averaged concentrations for CO, Non Metanic Hydrocarbons, Benzene, Total Nitrogen Oxides (NOx) and Nitrogen Dioxide (NO2) and were provided by a co-located reference certified analyzer.Missing values are tagged with -200 value.

## PROBLEM STATEMENT
Accurate forecasting of air pollutant concentrations can support environmental monitoring, public health interventions, and policy planning.This project develops and evaluates time-series forecasting models to predict CO concentration levels using historical air quality measurements, with the aim of identifying temporal patterns and improving short-term pollution forecasting.

## Exploratory Data Analysis
- Target distribution
- Time series plot
- Correlation heatmap ( ACF & PACF)

## Stationarity Testing
- ADF statistic
- p-value
- * The ADF test indicated stationarity of the target series, suggesting no regular differencing was required for ARIMA modeling.
 
## Seasonality Analysis
- STL Decomposition
- STL decomposition revealed strong recurring seasonal patterns, justifying exploration of seasonal forecasting models.

## Modeling Approach
- Baseline ARIMA
- Seasonal SARIMA
- Manual Tuning of SARIMA candidates

## Candidate Models Tested
| Model                   |
| ----------------------- |
| SARIMA(1,0,1)(1,1,1,24) |
| SARIMA(2,0,1)(1,1,1,24) |
| SARIMA(1,0,2)(1,1,1,24) |
| SARIMA(1,0,1)(2,1,1,24) |

- Candidate seasonal configurations were manually evaluated due to computational constraints of exhaustive seasonal auto_arima search.

## Forecast Results
- Model captures seasonality
- Misses some spikes

## Model Performance Comparison
| Model  | MAE   | RMSE  |
| ------ | ----- | ----- |
| ARIMA  | 1.144 | 1.411 |
| SARIMA | 1.055 | 1.294 |

- SARIMA outperformed ARIMA, indicating that incorporating seasonal dynamics improved predictive performance.

## Residual Diagnostics
- Residuals approximately centered around zero
- Limited autocorrelation remaining

## Conclusion
- * The SARIMA model was selected as the final forecasting model due to superior predictive performance and its ability to capture seasonal structure in the CO series.

## Limitations and Future Work
* - Difficulty predicting abrupt spikes
* - Model is univariate
* - Could improve with exogenous variables
