# Train Travel Demand Modelling using Python
## Context
Linear regression (LR) is one of the most popular and understandable ways to model demand. The coefficients on each variable in the fitted regression equation tell us exactly how much a change in each independent variable (X) will change the dependant variable (Y).

One of the key underlying assumptions LR relies on is exogeneity of the independent variables (X). This critical assumption states that changes in the dependent variable (Y) must be caused solely by X or some other unidentified variable. Crucially, changes in Y itself cannot cause X (reverse causation). 

Where this assumption does not hold for a variable X, X is said to be endogenous and linear regression coefficients will not accurate reflect the true change in Y for each unit of change in X.

In the context of train travel demand, ticket price (X) will be shown to be endogenous with respect to demand for train seats (Y) which distorts a plain linear regression model and must be adjusted for. 

## Objective
The objectives are thus as follows:

- Identify endogeneity issues in a linear demand model
- Correct for reverse causation using Python linearmodels 2-stage least squares regression (OLS in statsmodels, IV2SLS in linearmodels)
- Obtain a truer representation of the impact of each independant variable on train travel demand 


## Dataset
As the dataset is a subset of a proprietary real-world dataset, it cannot be released as part of this repository. However, adequate examples will be given in supporting notebooks on the dataset structure to enable easy reapplication to other scenarios.

This dataset is a csv file containing 1 target variable (*num_seats_total* i.e. total demand) and 9 features (ticket price, departure date, purchase date, train id, cumulative sales, cabin class, return to hub, one way journey and customer category).

## Steps

<b>Data Preprocessing & EDA</b>

- Data is formatted and outliers for key variables (demand & price) are dropped
- 3 useful are engineered: purchase lead time, day of week & month
- EDA is done via correlation matrices, barplots & countplots to determine which features may be important to demand & price models
- Demand & price columns are log-transformed
- Redundant columns are dropped & data is exported to CSV

<b>Demand Modelling</b>

Statsmodels OLS (Ordinary Least Squares, i.e. Simple Linear Regression)
- Demand is first modelled with OLS
- Price is then modelled with OLS using an additional instrumental variable.
- Price is re-forecasted and fed back into the Demand equation

Linearmodels
- IV2SLS is demonstrated to do the 3 steps above in 1 step
- Various robustness tests are applied to confirm endogeneity and overidentification

<b>Packages used</b>: pandas, numpy, seaborn, linearmodels, statsmodels

## Findings
<b> Importance of 2SLS</b>

Coefficient of ticket price is now an unbiased estimator following the IV2SLS which is critical for causal analysis and decision-making. Coefficient changed from -0.211 (simple OLS) to -0.342 (IV2SLS), suggesting that endogeneity problems would have caused significant errors in estimation with only Simple Linear Regression.

<b> Model Discussion</b>

Overall, after all proper adjustments have been made, this simple model allows us to quantify important and specific findings about demand for train travel. Importantly, this model can be used to directly forecast demand in the future and allows the train company to plan supply of trains accordingly. 

<b>Generalisable Observations</b>
1. Each 1% increase in price, results in a -0.3% decrease in demand, roughly 1/3rd the impact 
2. One way rides have slightly lower demand (-5%) compared to round trips 
3. With the baseline as Jan, December is the most popular (24% higher demand) while September is the least popular (-7% demand)


<b>Company-Specific Observations</b>
1. Commuters in Category B have 21% higher demand compared to Category A
2. Normal cabins, despite being the most sold & cheapest, are actually -14% less popular than premium ones (all else held constant)
3. With the baseline as Train A, Train B plys the most popular route (15% higher demand), while Train N operates the least popular route (-14% demand)

<b>Limitations</b>

The overall model fit remains low, with final reported R-squared being just 0.126 (a value closer to 1 would indicate a better fit). This strongly suggest that something more than a linear model may be needed to model this relationship better. 

## Files
- *01_Data_Preprocessing_and_EDA.ipynb*: Notebook for data pre-processing and preliminary exploration of dataset.
- *02_Demand_Modelling_with_2SLS.ipynb*: Linear regression model with checks for endogeneity and corrections made accordingly.

HTML versions of both files have also been included for convenience.

## Credits
This dataset was provided by the National University of Singapore.
This was co-authored with Gino Martelli Tiu (@ginosytiu).

