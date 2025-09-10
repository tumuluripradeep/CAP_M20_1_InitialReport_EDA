# CAP_M20_1_InitialReport_EDA

# Walmart Sales Forecast

## Problem
There are many seasons that sales are significantly higher or lower than averages. If the company does not know about these seasons, it can lose too much money. Predicting future sales is one of the most crucial plans for a company. Sales forecasting gives an idea to the company for arranging stocks, calculating revenue, and deciding to make a new investment. Another advantage of knowing future sales is that achieving predetermined targets from the beginning of the seasons can have a positive effect on stock prices and investors' perceptions. Also, not reaching the projected target could significantly damage stock prices, conversely. And, it will be a big problem especially for Walmart as a big company.

## Aim
My aim in this project is to build a model which predicts sales of the stores. With this model, Walmart authorities can decide their future plans which is very important for arranging stocks, calculating revenue and deciding to make new investment or not.

## Solution
With the accurate prediction company can:

- Determine seasonal demands and take action for this
- Protect from money loss because achieving sales targets can have a positive effect on stock prices and investors' perceptions
- Forecast revenue easily and accurately
- Manage inventories
- Do more effective campaigns

The solution involved the following steps:
1. Understanding, Cleaning and Exploring Data (Data Preprocessing and EDA)
2. Preparing Data to Modeling (Feature Engineering)
3. Modeling using Time Series Analysis (ARIMA, SARIMAX) and Regression Models (Linear Regression, Ridge Regression)

## Data Overview and Preprocessing Summary
The following datasets were loaded:

- **train.csv**: Contains historical sales data, including Store, Dept, Date, Weekly_Sales, and IsHoliday.  
- **test.csv**: Contains similar data to train.csv but without Weekly_Sales, used for making future predictions.  
- **stores.csv**: Provides information about each store, including Store, Type, and Size.  
- **features.csv**: Contains additional features related to stores and dates, such as Temperature, Fuel_Price, MarkDowns, CPI, Unemployment, and IsHoliday.

### Initial Data Inspection
- `train.csv`, `test.csv`, and `stores.csv` have no missing values.  
- `features.csv` has significant missing values in the MarkDown columns (MarkDown1–5), and some missing values in CPI and Unemployment.

### Feature Engineering Steps
- Created a combined **Store_Dept** identifier.  
- Extracted **Month** and **Year** from the Date column.  
- Calculated **Total_MarkDown** by summing MarkDown columns.  
- Performed **one-hot encoding** on the Store Type column.  
- Merged stores and features with train/test datasets.  
- Created **lag features** (Weekly_Sales_Lag1, Weekly_Sales_Lag2).  
- Calculated **rolling mean/std** of Weekly_Sales.  
- Extracted **Quarter** and **WeekOfYear**.  
- Filled missing values with 0.  

## Exploratory Data Analysis (EDA) Insights
Key findings include:

1. **Distribution of Store Types**: Type A most numerous, followed by B and C.  
2. **Distribution of Store Sizes**: Clustered with peaks around certain ranges.  
3. **Weekly Sales Distribution**: Highly skewed, with outliers and negative values (returns/adjustments).  
4. **Weekly Sales by Store**: Significant variation; some consistently higher or lower.  
5. **Weekly Sales by Department**: Certain departments (92, 95, 38, 41, 72, 67) outperform others.  
6. **Weekly Sales Over Time**: Seasonal peaks (holidays), overall upward trend.  
7. **Sales vs Temperature**: No strong correlation.  
8. **Feature Correlations**: MarkDown1–4, MarkDown2–3, and CPI–Unemployment correlated.  
9. **Average Sales by Store Type/Department**: Type A highest; Departments 92 & 95 strongest.  

## Model Performance Comparison

### ARIMA Model
- R²: 0.2379  
- RSE: 8572.6740  

### Linear Regression Model
- R²: 0.9654  
- RSE: 4243.9606  

### Ridge Regression Model
- R²: 0.9654  
- RSE: 4243.9606  

### Comparison
- **Regression models (Linear & Ridge)** outperform ARIMA significantly.  
- Regression benefits from **feature engineering** across multiple datasets.  
- ARIMA effective for single time-series subsets, but less so for large multi-factor datasets.  

## Conclusion
- Regression models are more effective for Walmart sales forecasting on this dataset.  
- Feature-rich models capture seasonality, economic indicators, and markdown effects better.  
- Accurate forecasts can help Walmart **manage inventory, optimize campaigns, reduce losses, and improve investor confidence**.
