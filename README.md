# A More Accurate Estimation of Train Travel Demand using Python linearmodels
## Context
Linear regression (LR) is one of the most popular and understandable ways to model the demand function. However, one of the key underlying assumptions LR relies on is exogeneity of the independent variables (X). 

This critical assumption states that changes in the dependent variable (Y) must be caused solely by X or some other unidentified variable. Crucially, changes in Y itself cannot cause X (reverse causation). Where this assumption does not hold for a variable X, that variable is said to be endogenous and linear regression coefficients will not accurate reflect the true change in Y given changes in X.

In the context of this case, price (X) will be shown to be endogenous with respect to demand for train seats (Y) which distorts a plain linear regression model. 

## Objective
Overall, getting a more reliable demand model enables us to plan train schedules more accurately in future time periods. The objectives are thus as follows:

- Identify endogeneity issues in linear demand modelling
- Correct for reverse causation using Python linearmodels
- Obtain a truer representation of the impact of each independant variable on train travel demand 


## Dataset
As the dataset is a subset of a proprietary real-world dataset, it cannot be released as part of this repository. However, adequate examples will be given on the dataset structure to enable easy reapplication to other scenarios.

This dataset is a csv file containing 10 features...

## Steps
- 
- 

## Findings
-
-

## Files
- *01_Data_Preprocessing_and_EDA.ipynb*: Notebook for data pre-processing and preliminary exploration of dataset.
- *02_Demand_Modelling_with_linearmodels.ipynb*: Linear regression model with checks for endogeneity and corrections made accordingly.

## Credits
This project was co-authored with Gino Martelli Tiu. This dataset was provided by the National University of Singapore.


