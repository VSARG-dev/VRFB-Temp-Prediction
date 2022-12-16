# VRFB-Temp-Prediction
Predicted variation of Vanadium Redox Flow Battery stack temperature with time using Polynomial Regression and LSTM.

## Abstract
Redox Flow Batteries have risen in popularity in recent years as a large-scale energy storage solution. Efficiency of the battery storage system relies on minimizing power loss, which in turn is dependent on predicting VRFB stack temperature and keeping it within a safe limit so as to prevent thermal precipitation. We have predicted variation of stack temperature with time duration of a practical 1kW 6kWh VRFB system dataset under four different operating current levels (40, 45, 50, and 60A) keeping a constant electrolyte flow rate of 180 ml/sec. Here, we have used both Polynomial Regression and LSTM methods to accurately predict the stack temperature of the battery during charging and discharging profiles. The prediction accuracy of the algorithm was tested using regression metrics such as Root Mean Square Error (RMSE), Mean Absolute Error (MAE) and Correlation Coefficient (R2). The algorithm performance and the parameter performance graphs were plotted for visualization of results.

## Polynomial Regression
We created polynomial regression models for degrees 0-9 and implemented it on the dataset. We used gradient descent to update the weights at each iteration. <br />
The MSE error was calculated every 5000 iterations and the model was run for a total of 50000 iterations. <br />
The final MAE, RMSE and R2 errors were calculated and tabulated for each of the polynomial functions of degrees 0-9. <br />
The code for this can be found in [Poly_regression for Temp Prediction.ipynb](https://github.com/VSARG-dev/VRFB-Temp-Prediction/blob/main/Poly_regression%20for%20Temp%20Prediction.ipynb)
