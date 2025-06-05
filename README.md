# Sales-Forecasting-Python-

About Dataset:

There are 5 files:
1. train.csv contains information on sales of every product family across all stores, it also contains additional 
    information on the number of products in each family that were on promotion.
2. stores.csv is metadata about each store, consisting of location details like city and state.
3. oil.csv lists the oil price over the available date range.
4. holiday.csv contains a calendar of holidays along with their respective types.
5. transaction.csv contains total number of transactions made by a store on each date.

Aim of this project:

The aim of this project is to forecast daily sales for each store over a 16-day period following the last date in the training dataset.

Overview of the approach:

1. Exploratory Data Analysis was done with the aim of identifying missing dates, learn about the distribution of sales for each family,
    and to understand the effect of each type of holiday on the sales.
2. Merging the files on appropriate columns.
3. Selecting and creating new features, including date-related features, lag variables, exponentially weighted moving averages,
    and holiday-related features grouped by type or description.   
4. Each exponentially weighted moving average was calculated using different shift and span values. To be specific, span values were 4 and 30, and for 
    each span value shift values were 1, 16 and 365. Same XGBoost model was fitted separately with data containing only one type of shift values in 
    addition to other non-lag features. The three outputs from the three distinct fitted models, then, were combined with varying weights depending on 
    the number of days since the first test date.
5. Date based weights were used, for the XGBoost models, to assign higher weight to recent data points.
6. A sliding window validation was created to assess model performance. Root mean squared logarithmic error was used to measure error. 
