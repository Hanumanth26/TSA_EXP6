# Ex.No: 6               HOLT WINTERS METHOD
### Date: 
```
Developed by: vivek reddy
Reg No:212221240030
```

### AIM:
To implement the Holt Winters Method Model using Python.
### ALGORITHM:
1. You import the necessary libraries
2. You load a CSV file containing daily sales data into a DataFrame, parse the 'date' column as
datetime, and perform some initial data exploration
3. You group the data by date and resample it to a monthly frequency (beginning of the month
4. You plot the time series data
5. You import the necessary 'statsmodels' libraries for time series analysis
6. You decompose the time series data into its additive components and plot them:
7. You calculate the root mean squared error (RMSE) to evaluate the model's performance
8. You calculate the mean and standard deviation of the entire sales dataset, then fit a Holt-
Winters model to the entire dataset and make future predictions
9. You plot the original sales data and the predictions
### PROGRAM:
```python

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.holtwinters import ExponentialSmoothing
data=pd.read_csv("/content/AirPassengers.csv")
data
data['Month'] = pd.to_datetime(data['Month'])
data.set_index('Month', inplace=True)
model = ExponentialSmoothing(data, trend="add", seasonal="add", seasonal_periods=12)
fit = model.fit()
n_steps = 12  

forecast = fit.forecast(steps=n_steps)
forecast
plt.figure(figsize=(10, 6))
plt.plot(data.index, data, label='Original Data')
plt.plot(pd.date_range(start=data.index[-1], periods=n_steps+1, freq='M')[1:], forecast, label='Forecast')
plt.xlabel('Date')
plt.ylabel('Value')
plt.title('Holt-Winters Forecast')
plt.legend()
plt.show()
```

### OUTPUT:
![image](https://github.com/Vivekreddy8360/TSA_EXP6/assets/94525701/c6941dc2-ad9f-43f0-9411-fa8a94ffdd33)


### RESULT:
Thus the program run successfully based on the Holt Winters Method model.
