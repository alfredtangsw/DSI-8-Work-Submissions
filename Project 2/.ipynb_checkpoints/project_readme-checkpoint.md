# Project 2

Task: Create a regression model based on Ames Housing Dataset to predict the price of a house at sale.

<span style="color:red"> Roadblocks:</span> There are more than 70 columns of different types of data related to houses. 


## Problem Statement
**Key questions:**
1. What variables are most important for predicting the price of a house at sale?
2. On what basis will we select our features?

## Executive Summary
1. Conventional wisdom has it that location heavily influences house prices.

2. The model finds this to be true, but several other factors also have significant influence. 
    
3. The model generalises well to new data. Lasso Regression was selected as the preferred regression model, because it generates the best R-squared and RMSE between OLS, Lasso, and Ridge models.

4. The model is able to generate predictions for house prices with an RMSE score of 34,000 (Kaggle comparison). This is significant variation, but RMSE is only one measure of success.

5. The model adequately answers the data science problem. These features are the answer to the problem statement, in order of priority (greater is better unless specified otherwise):
    - Overall Quality
    - 1st Floor Square Footage
    - Above-Grade Living Area
    - Number of Fireplaces
    - Garage size
    - Age of house (Fewer years, higher price)
    - Years since last remodelling (Fewer years, higher price)
    - Type of house (MS SubClass - various configurations of housing)
        - SubClass 20, 60
    - Neighbourhood
        - Crawford, Green Hills, Northridge, Northridge Heights, Stone Brook
    - Garage Type 
        - None
        - (Retained because it remained in list after Recursive Feature Elimination from 20 to 15 features)
        - Possibly apartments/townhouses

**Business Recommendation:** House buyers looking to invest in housing should look for houses in the neighbourhoods of Crawford,Green Hills, Northridge, Northridge Heights, Stone Brook, below their median prices. 

If their other features such as Overall Quality and 1st Floor Square Footage are above the mode or median for their respective categories, they could make a profit over time if the house is maintained well/remodelled regularly.

|Neighborhood|Median Price|
|----|----|
|Crawford|199500 |
|Green Hills| 280000|
|Northridge|290500|
|Northridge Heights|274900|
|Stone Brook|302950|

|Model|No. of Features|R-Squared|RMSE|Remarks|
|---|---|---|---|---|
|OLS Baseline|	75|	-1497787013710829232062464....| 84593790781937488.00000|Overfit|
|LassoCV Baseline	|75|	0.84934	|26956.10|
|RidgeCV Baseline	|75|	0.84992	|27343.10|
|Ridge Pre-RFE|	75	|0.86597	|25819.12|
|Lasso Pre-RFE|	75	|0.86576	|25840.14|
|OLS Baseline Post-RFE|	15|	0.83226|	28512.95|
|LassoCV Baseline Post-RFE|	15	|0.83227|	28513.48|
|RidgeCV Baseline Post-RFE|	15	|0.83258|	28497.40|
|Ridge Post-RFE|	15|	0.84375|	27877.49|
|Lasso Post-RFE|	15|	0.84384|	27869.30|



## Data Dictionary

|Feature|Type|Description|Range of Values|
|---|---|---|---|
|Overall Qual|ordinal integer|Rates the overall material and finish of the house|0 - 10|
|1st Flr SF| continuous float|First Floor square footage|0.00 - infinity|
|Gr Liv Area|continuous float| a |0.00 - infinity|
|Fireplaces| discrete integer|Number of fireplaces|0 - infinity|
|Garage Size| continuous float| a |0.00 - infinity|
|Age of house| discrete integer| Age of house at time of sale, in years | 0 - infinity|
|Remod Age|discrete integer| Years since last remodelling|0-infinity|
|MS SubClass|nominal categorical|Type of house|020,030,040,045,050,060,070,075,080,085,090,120,150,160,180,190|
|Neighbourhood|nominal categorical|Location of house in the city, by neighbourhood| Blmngtn, Blueste, BrDale, BrkSide, ClearCr, CollgCr, Crawfor, Edwards, Gilbert, Greens, GrnHill, IDOTRR, Landmrk, MeadowV, Mitchel, Names, NoRidge, NPkVill,NridgHt, NWAmes, OldTown, SWISU, Sawyer, SawyerW, Somerst,StoneBr, Timber, Veenker |
|GarageType| nominal categorical| Presence of garage|2Types,Attchd,Basment,BuiltIn,CarPort,Detchd,None|

## References
1. https://support.sas.com/resources/papers/proceedings/proceedings/sugi30/113-30.pdf
1. 

## Notes for future improvement
1. Split notebook into multiple parts to reduce computation time and dependency on previous cells
2. Review the dropped rows -- perhaps impute values instead of deleting the whole outlier row altogether?