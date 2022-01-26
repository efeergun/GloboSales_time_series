# GloboSales_time_series
This repository is created for imaginary sales portal company called GloboSales. It simply is a tool to predict future transactions or sales for each individual E-Store on the Portal   

# Table of Contents
* Introduction
* QuickStart
* Detailed Explanation of the Work

# Introduction

I made a Trend predictor for E-Stores, for our client GloboSales. 
This predictor can either be used for predicting the total amount of transactions on the next day (Because our client charges Estores on per transaction basis)
Or for predicting the total amount of sales revenue on the next day (For additional use cases such as estimating the possible comission rate on each store OR For EStores to estimate themselves for future dates).
This ReadME file is mainly designed for those with basic level of Data Science knowledge.

# QuickStart For Data Scientists/Engineers

The entire project is prepared to be run on google collab, doesn't require any installations or configuration.

To run it on your end:
0. Clone this repo
1. Go to google collab
2. Upload the Notebook named POC_time_series_transaction_prediction.ipynb from the repo
3. Open the related Notebook and run first 2 cells
4. Choose the 'ecommerce_data.csv' file once Notebook asks you after running the Second cell (insert image here.)
5. Confirm both of the selections on the third cell (1 is for prediction of sales, 0 is for predicting the total amount of transactions)
6. Run the rest of the cells.
7. Prediction graph is displayed on the last cell as output. (The same graph can be used in the eStore portal.)


# Detailed Explanation of the Work/Process

To begin with, this part of the ReadMe file is for ones who already read/run the Notebook but did not fully understand Why/How a thing happens. 

- Empty the quantity fields are filled with 1. As there can't be 0 amount of bread purchase registered by a valid Customer. (Critical for second use case of the notebook)
- All the purchase has been grouped by the Day it happened. So, the timeline does have an easy to understand/work order.
- Days without any records has been generated to have constant 1 day as step size.
- Rolling mean is used to reduce complexity of the data. To make the lines smoother, easier on the prediction work.
- In order to use historical data to predict future data, training data has been reshaped. (Earlier day's values saved under lag_n columns)
- Each E-Store's data can be separately trained / predicted. **Because** the characteristics of trends are different between each store. (e.g. Christmas Tree seller != Bread Seller)
- Simple RandomForestRegressor is utilized. Because it is easy to utilize, quick, doesn't requires BIG datasets to train.
- 80/20 train test split applied.
- Mean Absolute Error (MAE) metric has been used for evaluating the results.
- As the model requires only 15 data points prior to the prediction. Any EStore on the platform that is older than 1 month can easily utilize it.
- Additionally, for further predictions, we can use iteration method. So, after the prediction happens, it can be registered as data point for next predictions. 
(Not the best ofc. but it doesn't requires to create multi output models or multiple single output models.)
- Client could see the predictions for later days on the portal as a graph. (Example presented on the last cell of the Notebook.) 
- The computation is very light, it can be done on server or client side easily.
- Additionally we can provide the LinearRegression line graph for a simpler trend prediction on the same graph.
- One size fits all design applied specifically for the future functionalities.
- It is not so easy to evaluate the overall success of this model/effort. However, the final graph shows promise.
