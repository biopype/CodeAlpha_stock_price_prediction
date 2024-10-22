# Code Alpha Project 01: Stock Price Prediction of Moderna using LSTM

In this project, we will predict Moderna’s stock prices using the Long Short-Term Memory (LSTM) Regressor. We will visualize the results and evaluate the performance metrics of our model.  

This project is assignment 01 of the data science internship with [Code Alpha](https://www.codealpha.tech/).

## Introduction:

A stock price is the amount of money the public is willing to pay to buy the shares of a company. Stock price prediction is important to make investment decisions, and assess risks of investment, etc.

### Moderna:

The company whose stock prices we will be predicting is Moderna. Moderna is a US-based healthcare and biotechnological company, that is a major driver in RNA-based therapeutics worldwide. Understanding and predicting the stock prices of a biotechnological company is important for early career research scientists and healthcare professionals to understand where the healthcare market is heading to and what potential innovative business areas in healthcare biotechnology (or related fields) need to be targeted for a career in healthcare business.

### Long Short-Term Memory (LSTM):

LSTM is a recurrent neural network (RNN) that learns general trends over time. Sudden changes in the historical data, irrelevant to the main trend over time, are disregarded and sequential data is modeled. The final output is a result of a normal trend that is learned over time. This model is effective for time series predictions where predictions are made by learning patterns over time.

## Steps in model development:

The code can be accessed at [Code Alpha Task 1](/code.ipynb)

1. The historical data between 10-12-2018 and 03-10-2018 was retrieved from [Yahoo Finance](https://finance.yahoo.com/).
2. Only the closing prices were selected because they are reliable and the final price of the daily stock share.
3. The values were pre-processed and normalized between the 0-1 range, so they don’t cause hindrance during model development.
4. This data was split into 80% training and 20% testing.
5. Past 60 days' stock prices were used to predict the next day’s closing price.
6. The model was structured by adjusting the number of layers and units (neurons).
7. Predictions were made by training the model.
8. Model evaluation was done through performance metrics.

## Model Structure:

![Model Structure](https://github.com/user-attachments/assets/61a8ae10-c680-40cb-94c8-97d2ac34926a)


### 1. First LSTM layer:

Processes the sequence of 60 days of data using 50 neurons. Information is passed from each day (60 days) to the next layer.

### 2. Second LSTM layer:

50 memory cells are used to process the information. Only the final output of the last day is passed onto the next layer – the most relevant prediction.

### 3. Dense layers:

These layers are the final decision-making step.

- The first layer learns complex patterns in data using 25 neurons.
- The second layer produces the final prediction using only 1 neuron.

## Result:

The results can are available at [actual vs. predicted prices](/actual_vs._predicted_prices.csv)

The actual and predicted prices for 5 entries are shown below.

| Actual | Predicted |
|--------|-----------|
| 74.069 | 76.746    |
| 75.959 | 78.746    |
| 76.199 | 80.197    |
| 71.230 | 80.585    |
| 77.529 | 76.092    |

## Visualization:

![visualization](/results.png)


The results show moderate differences between the actual and predicted prices of the company. The red line represents the predicted price, while the actual price is represented by the blue line.

## Performance Metrics:

The model evaluation was done through three metrics.

| Metric                          | Value    |
|----------------------------------|----------|
| Root Mean Squared Error (RMSE)   | 7.357753 |
| Mean Absolute Error (MAE)        | 6.304151 |
| Coefficient of Determination (R²) | 0.898834 |

1. **Root Mean Squared Error (RMSE):** RMSE measures the average difference between values. RMSE of 7.35 suggests that the predicted values are 7.35 units away from the actual values.
2. **Mean Absolute Error (MAE):** MAE describes the absolute difference between predicted and actual values. 6.3 suggests that the predicted prices are 6.35 units off.
3. **Coefficient of Determination (R²):** R² describes how much variance between the actual and predicted values is explained by the model. Approximately 90% of the variance is explained by our model.

## Conclusion:

We were successfully able to develop a long short-term memory model to predict the stock prices of Moderna. An R² score of 0.89 indicates that the model is a good fit and is able to explain a significant amount of difference between actual and predicted prices.
