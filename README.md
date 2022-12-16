# VRFB-Temp-Prediction
Predicted variation of Vanadium Redox Flow Battery stack temperature with time using Polynomial Regression and LSTM.

## Abstract
Redox Flow Batteries have risen in popularity in recent years as a large-scale energy storage solution. Efficiency of the battery storage system relies on minimizing power loss, which in turn is dependent on predicting VRFB stack temperature and keeping it within a safe limit so as to prevent thermal precipitation. We have predicted variation of stack temperature with time duration of a practical 1kW 6kWh VRFB system dataset under four different operating current levels (40, 45, 50, and 60A) keeping a constant electrolyte flow rate of 180 ml/sec. Here, we have used both Polynomial Regression and LSTM methods to accurately predict the stack temperature of the battery during charging and discharging profiles. The prediction accuracy of the algorithm was tested using regression metrics such as Root Mean Square Error (RMSE), Mean Absolute Error (MAE) and Correlation Coefficient (R2). The algorithm performance and the parameter performance graphs were plotted for visualization of results.

## Polynomial Regression
We created polynomial regression models for degrees 0-9 and implemented it on the dataset. We used gradient descent to update the weights at each iteration. <br />
<br />
The MSE error was calculated every 5000 iterations and the model was run for a total of 50000 iterations. <br />
<br />
The final MAE, RMSE and R2 errors were calculated and tabulated for each of the polynomial functions of degrees 0-9. <br />
<br />
The code for this can be found in [Poly_regression for Temp Prediction.ipynb](https://github.com/VSARG-dev/VRFB-Temp-Prediction/blob/main/Poly_regression%20for%20Temp%20Prediction.ipynb)

## LSTM
We used the ‘train_test_split’ function within Scikit-learn to split the dataset 70:30 for training and testing respectively. We did not shuffle the data in this case as LSTM’s need sequential data for performing time series prediction. <br />
<br />
We reshaped the training and testing temperature data and performed Min-Max scaling using the ‘MinMaxScaler’ function within Scikit-learn so as to bring all temperature values within the range [0,1]. Min-Max scaling is performed when it is required to capture small variance in features and also for sparse data where the zero value needs to be preserved. <br />
<br />
We then used the ‘TimeseriesGenerator’ module within Tensorflow to generate a time series with number of features as 1 and number of inputs as 5. Essentially this means that the model will use 5 values from the data to predict the 6th value in the data. <br />
<br />
We then created an LSTM model having 100 hidden layers which takes an input of shape (5,1) and uses a ReLU activation function at the output layer finally giving an output of size 1. The Adam optimizer with a learning rate of 0.001,  β1 = 0.9, β2 = 0.999,  ϵ = 10-8 was used with no weight decay. MSE error was used as the loss function. <br />
<br />
The model was then trained on the training dataset for 50 epochs and the loss per epoch was plotted. 
We then used the model for prediction over the length of the entire dataset and the predicted values were stored in an array before being rescaled to the original size. The array was added later as an extra column within the dataset. <br />
<br />
The code for this can be found in [LSTM Implementation for Temp Prediction.ipynb](https://github.com/VSARG-dev/VRFB-Temp-Prediction/blob/main/LSTM%20Implementation%20for%20Temp%20Prediction.ipynb)

