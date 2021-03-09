## Colin Mondi - Kaggle Competition – Ames, Iowa Housing Prices

### Problem Statement

Iowa State University, located in Ames Iowa, is interested in expanding their campus. Due to most of the surrounding land not being up for sale, the University must determine the predicted sales price in order to provide the best offers for property owners.

### Findings

##### High-Level

- Data-specific statistics:
    - ~80 columns, ~2,000 rows
    - Majority of data present; minimal or no instances of NULLs across columns
    - Mix of integer and object data types
- The average house price is ~180,000 dollars
- 100+ years of sales prices available for homes
- Neighborhoods including Brookside and Old Town have the lowest average housing prices
- Neighborhoods including Northridge Heights and Northridge have the highest average housing prices

##### Variable-Specific
- The first-floor square footage of a property building has a bigger impact on sales price in comparison to the square footage of the entire lot
- The overall quality is heavily correlated with sales price while the overall condition shows almost no relationship with sales price
- Both the garage area and garage finish show a linear relationship with sales price, but there are some potential outliers at play here for garage area
- There’s an expected increase in the change in average housing price YoY in recent years, but prior to ~1940 this wasn’t necessarily the case


### Cleansing
- Removed columns with 1,000+ NULL values; 5 total
- Replaced remaining NULL values with either 1) mean of column values or 2) 0
- Removed outliers for key model variables; 7 total
- Added two new categorical columns for groupings; lot size & year built
- One-Hot Encoded ordinal-type columns; 18 total

### Modeling 

##### Pre-Processing
- Multiple iterations of feature list established throughout the model testing process
    - Before testing, I started with all variables positively correlated with sales price and modified the list from there
- Standardized data
- Created dummy columns
    - 20 object-type variables

##### Model Testing Process
- Applied the same data cleansing & pre-processing actions to the test data that was originally made in the train data
- Tested 4 different model types; Linear Regression, Ridge, Lasso, Elastic Net
- Utilized GridSearch to view how each individual variable was performing; adjusted feature list (completed in ‘Pre-Processing Actions’ above) using the results

### Conclusions and Recommendations

Recommendation: After cleansing, pre-processing, and prepping all 4 models, the ridge model is the best predictor of housing prices for Ames, Iowa.

Although lasso and ridge had very similar R² & RSME values, the ridge model will generally perform better when the prediction is a function of multiple variables.
