# Food Sales Predictions
## Analyzing Properties of Products and Outlets To Predict Sales of Food Items Sold At Various Stores

**Author**: Brooke Eagan

### Business problem:

With the lack of data allowing us to see what to expect in sales we have a problem of not being able to make the necessary adjustments that would be needed to handle variations in sales volume.


### Data:

Big Mart Sales Prediction https://datahack.analyticsvidhya.com/contest/practice-problem-big-mart-sales-iii/

For this dataset, there were 8523 rows and 12 columns.

### Data Dictionary

<p align = "center"> 
  <img src = "https://raw.githubusercontent.com/Beagan19/food-sales-predictions/main/data_dictionary.png">
</p>

## Methods
- To prepare this data, the data was cleaned, and the following processes were performed:
  - Column names and datatypes were inspected and corrected 
  - Values and value datatypes were inspected and corrected
  - The dataset was split into training and test sets for regession models

## Exploratoy Data Analysis
- During the exploratory data analysis, a boxplot for item weight and histogram for outlet item sales were visualized. 
- Also, a count plot was visualized for item type. 

<p align = "center"> 
  <img src = "https://raw.githubusercontent.com/Beagan19/food-sales-predictions/main/item outlet sales histogram.png">
</p>

The most item outlet sales are between 0 and 200.

## Explanatory Data Analysis

#### Does Outlet parameters affect Item Outlet Sales?
<p align = "center"> 
  <img src = "https://raw.githubusercontent.com/Beagan19/food-sales-predictions/main/Sales based on outlet parameters.png">
</p>

Based on three different outlet parameters, medium outlet size, supermarket type 3, and outlet location type tier 2 have the highest item outlet sales.

#### Does Item MRP affect Item Outlet Sales?
<p align = "center"> 
  <img src = "https://raw.githubusercontent.com/Beagan19/food-sales-predictions/main/item mrp vs item outlet sales.png">
</p>

There is a moderate positive correlation between item maximum retail price and item outlet sales.


## Models Evaluated & Results

- Linear Regression Model (Testing Set):
  - MAE: 804.1187 
  - MSE: 1,194,345.9381 
  - RMSE: 1,092.8614 
  - R2: 0.5671
  



    
    
- Random Forest Regressor Model (Testing Set):
  - MAE: 773.6878 
  - MSE: 1,241,023.4240 
  - RMSE: 1,114.0123 
  - R2: 0.5502

- Tuned Random Forest Regressor Model (Testing Set):
  - MAE: 728.3530 
  - MSE: 1,096,354.0177 
  - RMSE: 1,047.0693 
  - R2: 0.6026
  
The Final Model Chosen was a Random Forest Regressor Model with the n_estimators tuned to 5.

For the testing set on the model, 60.26% of the variance in y was explained by x.

The Mean Absolute Error was off by about ₹728.35

The Mean Squared Error was ₹1,096,354.02.

The Root Mean Squared Error had a calculation of ₹1,047.07.

Using this model to make predictions about item outlet sales would not be a very reliable. Considering the previous regression metrics from how the model performed, there is a disparity between the R^2 score and also the Root Mean Squared Error that cannot be ignored.  

<p align = "center"> 
  <img src = "https://github.com/Beagan19/food-sales-predictions/blob/main/Top%2015%20Coefficients.png">
</p>

- Top 3 Postive Coefficients:
    - Outlet Identifier OUT010
    - Outlet Identifier OUT018
    - Outlet Identifier OUT027
 
- Top 3 Negative Coefficients:
    - Outlet Type Grocery Store
    - Outlet Identifier OUT046
    - Outlet Location Type Tier 3
  
<p align = "center"> 
  <img src = "https://github.com/Beagan19/food-sales-predictions/blob/main/Feature_Importance_Decision_Tree_Regressor.png">
</p>

- Top 5 Important Features (used repeatedly by the model during the training process and does not indicate positive or negative impact)
    - Item MRP
    - Outlet Type Grocery Store
    - Item Visibility
    - Outet Identifier OUT027
    - Item Weight

**Global Explanation**

<p align = "center"> 
  <img src = "https://github.com/Beagan19/food-sales-predictions/blob/main/global_bar_plot.png">
</p>

- Three of five top features are listed in both the feature importance plot and the global shap summary plot.

<p align = "center"> 
  <img src = "https://github.com/Beagan19/food-sales-predictions/blob/main/global_summary.png">
</p>

- Top 3 Important Features:
    - Item MRP
        - The higher item MRP the more likely the model will predict a higher Item Outlet Sale
    - Outlet Type Grocery Store
        - Being classified as Outlet type grocery store decreased the likelihood the model will predict a higher Item Outlet Sale.
    - Outlet Identifier OUT027
        - Outlet identifier OUT027 indicates that the model will predict a higher Item Outlet Sale.

**Local Explanation**

- Item_MRP is a moderate postive correlation with Item_Outlet_Sale so I chose the highest and lowest Item_MRP data points to analyze.

<p align = "center"> 
  <img src = "https://github.com/Beagan19/food-sales-predictions/blob/main/high_force_plot.png">
</p>

- There are more features that have a positive impact on the model increasing the predicted item outlet sale.

<p align = "center"> 
  <img src = "https://github.com/Beagan19/food-sales-predictions/blob/main/high_tabular_plot.png">
</p>

- There are multiple features that had a negative impact on the item outlet sale, but there four features that had a stronger positive impact on the predicted item outlet sale.

<p align = "center"> 
  <img src = "https://github.com/Beagan19/food-sales-predictions/blob/main/low_force_plot.png">
</p>

- Item_MRP had a more negative impact on the model decreasing the predicted item outlet sale.

<p align = "center"> 
  <img src = "https://github.com/Beagan19/food-sales-predictions/blob/main/low_tabular_plot.png">
</p>

- There are several factors that have a positive impact on the predicted item outlet sale, but there are several factors that have a stronger negative impact to decrease the predicted item outlet sale.


### Model Performance

Overall, the best model is definitely the tuned Random Forest Regressor Model. There was still some bias in the model, but by far it outperformed the linear regression model.


## For Further Information

For any additional questions, please contact:

Brooke Eagan
brooke.eagan4@gmail.com
