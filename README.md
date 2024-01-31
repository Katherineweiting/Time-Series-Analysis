## Store Sales - Time Series Forecasting 
### Main message: 
1.	Stage One - Explore time series concepts and models and provide a baseline model
2.	Stage Two - Apply different models to data subsets. Conduct adjustments according to dataset constraints and compare the performance/validation of different models.
3.	Stage Three - Expand by adding variables
### Application:
   We hope to give the store manager an idea of applying certain time series model based on their dataset characteristics to predict weekly sales

### Details:
#### 1.	Stage One
- Start with data exploration and visualization using decompose plots
- Explain the data constraints, e.g. dataset time span
- Baseline model: Focus on aggregated weekly sales of one store over 2010-02-05 to 2012-11-01
  * Dependent Variable: Store 1 sales aggregated over all departments, Date, and Weekly_Sales
  * Independent Variable: Time, lag of time
  * Train/Test: Split by timestamp: train 2 years data from 2010-02-05 to 2012-02-05, the rest is testing (73% / 27%)
  * Model: x days Moving Average y(t) = m(x)*ϵ(t-x) + ϵ(t)
  * Outcome: Prediction of weekly sales from 2012-02-06 to 2012-11-01 and calculate Mean Squared Error.

#### 2.  Stage Two
- Acknowledge the seasonal effect of the dataset, and conduct seasonal adjustments
- Apply modeling methods to store 1 weekly sales, store 2 weekly sales,... etc. Take store 1 to store 10 as an example, train and test different model methods and compare the model performances
  * Dependent Variable: Store X sales aggregated over all departments, Date, and Weekly_Sales
  * Independent Variable: Time, lag of time, lag of shock term
  * Train/Test: Split by timestamp: train 2 years data from 2010-02-05 to 2012-02-05, the rest is testing (73% / 27%)
  * Model: 
    * Moving Average
    * ARMA
    * ARMA-GARCH
    * Random Forest
    * Neural Network (NNET)
- Outcome - Table: Prediction of weekly sales from 2012-02-06 to 2012-11-01 and calculate Mean Squared Error. Compare the Mean Squared Error as the table below:
- Find out the reason of difference model on different stores’ performances


#### 3. Stage Three
a.	Add variables in addition to time and utilize panel linear model to predict sales for each store. For example, store, fuel price, temperature
- Dependent variable: Sales
- Independent variables: Store, Fuel Price, Temperature, CPI (Consumer Price Index), Unemployment Rate, and Time.
- Model: Salesit=α+β1Storei+β2Fuel Priceit+β3Temperatureit+β4CPIit+β5Unemployment Rateit+γi+δt+ϵit, Where:
     * Salesit is the sales for store i at time t
     * Storei is the categorical variable representing the store
     * Fuel Priceit, Temperatureit , CPIit and Unemployment Rateit are the independent variables for store i at time t.
     * γi is the store fixed effect.
     * δt is the time fixed effect.
     * ϵit is the error term.
- Estimation: Estimate the model using an appropriate method, such as OLS model,  Fixed Effects estimation or Random Effects estimation.
- Outcome: Prediction of weekly sales from 2012-02-06 to 2012-11-01 and calculate Mean Squared Error.
- Prediction: Use the estimated model with below coefficient to predict sales for future periods
