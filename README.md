# Econometric Data Retrieval from FRED

This repository demonstrates the steps to pull econometric data from the Federal Reserve Economic Data (FRED) API. It includes Python scripts and markdown tables detailing various macroeconomic variables, their transformations, and methodologies for aggregating data to a consistent annual level.


| Variable Number | Variable Name at Level                                    | Variable Name at Transformation         | Need to Perform Transformation | Calculation of Transformation                                | FRED Availability Level   | Interpolation/Extrapolation/Aggregation |
|------------------|----------------------------------------------------------|----------------------------------------|-------------------------------|------------------------------------------------------------|--------------------------|----------------------------------------|
| 1                | Real Gross Domestic Product (GDPC1)                      | GDP Growth Rate                        | Y                             | (Current GDP - Previous GDP) / Previous GDP * 100          | Quarterly                | Aggregation (Annual average)          |
| 2                | Unemployment Rate (UNRATE)                               | N/A                                    | N                             | N/A                                                        | Monthly                  | Aggregation (Annual average)          |
| 3                | Consumer Price Index (CPIAUCNS)                          | Inflation Rate (CPI)                  | Y                             | (Current CPI - Previous CPI) / Previous CPI * 100          | Monthly                  | Aggregation (Annual average)          |
| 4                | Personal Consumption Expenditures (PCE)                  | Inflation Rate (PCE)                  | Y                             | (Current PCE - Previous PCE) / Previous PCE * 100          | Monthly                  | Aggregation (Annual average)          |
| 5                | Industrial Production Index (INDPRO)                     | Industrial Production Growth Rate      | Y                             | (Current IP - Previous IP) / Previous IP * 100              | Monthly                  | Aggregation (Annual average)          |
| 6                | Federal Funds Rate (FEDFUNDS)                            | N/A                                    | N                             | N/A                                                        | Daily                    | Aggregation (Annual average)          |
| 7                | 10-Year Treasury Yield (GS10)                            | N/A                                    | N                             | N/A                                                        | Daily                    | Aggregation (Annual average)          |
| 8                | 30-Year Treasury Yield (GS30)                            | N/A                                    | N                             | N/A                                                        | Daily                    | Aggregation (Annual average)          |
| 9                | 3-Month Libor (EFFR as alternative)                      | N/A                                    | N                             | N/A                                                        | Daily                    | Aggregation (Annual average)          |
| 10               | S&P 500 Index (SP500)                                   | N/A                                    | N                             | N/A                                                        | Daily                    | Aggregation (Annual average)          |
| 11               | Dow Jones Industrial Average                              | N/A                                    | N                             | N/A                                                        | Daily                    | Aggregation (Annual average)          |
| 12               | Commercial Real Estate Prices                             | N/A                                    | N                             | N/A                                                        | Varies (Quarterly)      | Aggregation (Annual average)          |
| 13               | Residential Real Estate Prices                            | N/A                                    | N                             | N/A                                                        | Varies (Quarterly)      | Aggregation (Annual average)          |
| 14               | Corporate Bond Yield (BAA)                               | N/A                                    | N                             | N/A                                                        | Daily                    | Aggregation (Annual average)          |
| 15               | Corporate Bond Yield (AAA)                               | N/A                                    | N                             | N/A                                                        | Daily                    | Aggregation (Annual average)          |
| 16               | 30-Year Fixed Mortgage Rate (MORTGAGE30US)              | N/A                                    | N                             | N/A                                                        | Weekly                   | Aggregation (Annual average)          |
| 17               | Housing Starts (HOUST)                                   | N/A                                    | N                             | N/A                                                        | Monthly                  | Aggregation (Annual average)          |
| 18               | Existing Home Sales (EXHOSLUS)                           | N/A                                    | N                             | N/A                                                        | Monthly                  | Aggregation (Annual average)          |
| 19               | New Home Sales (HSN1F)                                   | N/A                                    | N                             | N/A                                                        | Monthly                  | Aggregation (Annual average)          |
| 20               | Foreign Exchange Rates (e.g., USD to EUR)               | N/A                                    | N                             | N/A                                                        | Daily                    | Aggregation (Annual average)          |
| 21               | Global Economic Growth Rate                               | N/A                                    | N                             | N/A                                                        | Varies                   | Extrapolation or Aggregation needed   |
| 22               | International Trade Volumes                              | N/A                                    | N                             | N/A                                                        | Varies                   | Extrapolation or Aggregation needed   |
| 23               | Emerging Market Economic Indicators                       | N/A                                    | N                             | N/A                                                        | Varies                   | Extrapolation or Aggregation needed   |
| 24               | Central Bank Balance Sheet Size (TGD)                    | N/A                                    | N                             | N/A                                                        | Weekly                   | Aggregation (Annual average)          |
| 25               | Money Supply (M2SL)                                     | N/A                                    | N                             | N/A                                                        | Monthly                  | Aggregation (Annual average)          |
| 26               | Reserve Requirements                                      | N/A                                    | N                             | N/A                                                        | Not typically available   | N/A                                   |


# Explanation of the Code

This Python code demonstrates how to pull econometric data from the Federal Reserve Economic Data (FRED) API using the `fredapi` library. Below is a breakdown of its functionality:

1. **Import Libraries**:
   - The code imports the `fredapi` library to interact with the FRED API and `pandas` for data manipulation and analysis.

2. **Set API Key**:
   - An API key is set to authenticate the connection to the FRED API.

3. **Define Variables and Parameters**:
   - A dictionary called `variables` is defined, containing keys for specific economic indicators (e.g., Central Bank Balance Sheet Size and Money Supply (M2)) along with their descriptions.
   - The `start_date` and `end_date` variables specify the date range for the data extraction.

4. **Initialize Dictionary for DataFrames**:
   - An empty dictionary named `dfs` is initialized to store the data frames for each variable.

5. **Data Pulling Loop**:
   - The code iterates over the `variables` dictionary. For each variable:
     - It uses `fred.get_series` to retrieve the time series data from FRED for the specified variable and date range.
     - The data is converted into a Pandas DataFrame with the appropriate description as the column name.
     - Each DataFrame is stored in the `dfs` dictionary.

6. **Combine DataFrames**:
   - The individual DataFrames are concatenated into a single DataFrame called `combined_df`, aligning them by date.

7. **Print Combined Data**:
   - The first 20 rows of the combined data are printed to the console.

8. **Resampling Data**:
   - The combined DataFrame is resampled to an annual frequency, calculating the mean for each variable.

9. **Print Resampled Data**:
   - The first 10 rows of the resampled annual data are printed to the console.

This code serves as a foundational example for retrieving and processing economic data from the FRED API, demonstrating key steps such as data extraction, DataFrame creation, and resampling.


