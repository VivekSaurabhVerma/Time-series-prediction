# Time-series-prediction

Prediction of time series over n steps using scipy and sklearn.
The series is decomposed into trend, seasonnal and noise, with randomForest. Best decomposition periods can be automatically determined. 
Seasonnalities and trend are then predicted n steps forward.
The solution won the Analytica Vidhya challenge "Time series forecasting"

Here are some examples of predictions generated by the program :

<img src=https://github.com/Prevost-Guillaume/Time-series-prediction/blob/main/images/Temperatures.png>
<img src=https://github.com/Prevost-Guillaume/Time-series-prediction/blob/main/images/Shampoo.png>
<img src=https://github.com/Prevost-Guillaume/Time-series-prediction/blob/main/images/Power.png>
<img src=https://github.com/Prevost-Guillaume/Time-series-prediction/blob/main/images/Transport.png>
This last example is actually the winning solution of the challenge.


## How does it works ? :thinking:
Let's take example on the beer sales time serie.
Here is the original serie :
<img src=https://github.com/Prevost-Guillaume/Time-series-prediction/blob/main/images/init.png>

First, the serie is normalized using a rolling mean and a rolling standard deviation. We get the following serie :
<img src=https://github.com/Prevost-Guillaume/Time-series-prediction/blob/main/images/Norm.png>

The mean and the std are forecasted with a scikit learn model :

<img src=https://github.com/Prevost-Guillaume/Time-series-prediction/blob/main/images/trend%20forecasting.png>
<img src=https://github.com/Prevost-Guillaume/Time-series-prediction/blob/main/images/Var%20forecasting.png>

Then, seasonnalities are extracted from the normalised serie. 
To do this, it is necessary to know the period of the different seasonality. For that, I have implemented a graphical tool that highlights the periodicities present in the signal.
<img src=https://github.com/Prevost-Guillaume/Time-series-prediction/blob/main/images/period_importance.png>
Here we can note a pericity of 6, a periodicity of 12 and one of 23. 

Seasonnalities are then extracted using a randomForestRegressor from scikit-learn.
<img src=https://github.com/Prevost-Guillaume/Time-series-prediction/blob/main/images/Periodicity%20forecasting.png>

Then, we just have to put everything together, and we get the following prediction
<img src=https://github.com/Prevost-Guillaume/Time-series-prediction/blob/main/images/Beer.png>


