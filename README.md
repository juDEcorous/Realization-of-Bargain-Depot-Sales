# Realization of Bargain Depot Sales

<p align="center">
<img src = 'https://user-images.githubusercontent.com/125017784/229952353-671d148a-6895-402f-9aee-de7ca0540f30.jpg'>
</p>

# Investigation of Outlet Sales
Jude Maico Jr.

#### There's a lot of things to consider when starting a Grocery Outlet: Which Outlet makes more profit? What type of Outlet to consider? Where should this Outlet be located? How will this Outlet compete with the existing Grocery Outlets? With this in mind, We need to have an idea on how things are going in Outlet Stores to make a firm decision.

# Data Source:
Big Mart Sales Prediction:
https://datahack.analyticsvidhya.com/contest/practice-problem-big-mart-sales-iii/

# Data Dictionary:
![Screenshot 2023-04-04 174607](https://user-images.githubusercontent.com/125017784/229956145-9eedfd9f-7e29-43be-9605-dc67bb95f912.png)

#### This data was cleaned: Duplicates has been removed and Missing values has been inputed. Finally graph has been made for data analysis.

# Data Visualisation:  

## Linear Regression Coefficients

<p align="center">
<img src = 'Linear Regression Coefficients.jpg'>
</p>

- According to the Linear Regression Model the Top 3 most important features are:
    1. Item_MRP: The retail price of the item will increase the outlet sales by 987.91.
    2. Outlet_Type: Being in a category of which the product belongs will increase the sales by 843.257
    3. Outlet_Location_Type_Tier2: Being a Tier 2 for Location Type will Increase the sales by 477.208.

## Random Forest Model Importances and Bar SHAP

<p align="center">
<img src = 'Random Forest Importances.jpg'>
</p>

- According to the Random Forest the top 5 most important features are:
    1. Item_MRP
    2. Outlet_Type
    3. Item_Visibility
    4. Item_Weight
    5. Outlet_Establishment_Year
- However, Permutation Importance only shows 3 as the most important features. All of which are also seen in the Feature Importance Top 5. These Features are:
    1. Item_MRP
    2. Outlet_Type
    3. Outlet_Establishment_Year

<p align="center">
<img src = 'Random Forest Shap Values Bar.jpg'>
</p>

- Shap Values and Feature Importance have the same top 5 most important features. However, three of them are not in the same place. 
    1. Outlet_Establishment_Year is placed 3rd on Shap but for feature importance it is placed 5th.
    2. Item_Visibility is placed 4th on Shap but for feature importance it is placed 3rd.
    3. Item_weight is placed 5th on Shap but for feature importance it is placed 4th. 
    
- Shap values and Permutation Importance have the same top 3 most important features:
    1. Item_MRP
    2. Outlet_type
    3. Outlet_Establishment_year

## Tuned Random Forest Model Importances and Bar SHAP

<p align="center">
<img src = 'Tuned Forest Importances.jpg'>
</p>

- Tuned Random Forest Only shows top 3 most important features. This is true for both Feature Importance and Permutation Importance. These Features are:
    1. Item_MRP
    2. Outlet_Type
    3. Outlet_Establishment_Year
- Notice that these 3 important features (According to Tuned Random Forest Model) are the same results we get on the Defaulted model under Permutation Importance.

<p align="center">
<img src = 'Tuned Random Forest Shap Values Bar.jpg'>
</p>

- Shap values, Feature importance and Permutaton Importance for the Tuned Random Forest, all have the same top 3 most important values.
    1. Item_MRP
    2. Putlet_Type
    3. Outlet_Establishment_Year
    
### SHAP Model Explainer
#### NOTE: Defaulted Random Forest and Tuned Random Forest have the same top 5 values.

<p align="center">
<img src = 'Random Forest Shap Values Dot.jpg'>
</p>
 
1. Item_MRP has the largest effect on Random Forest Model.
    - The higher the retail price of the product, the higher the outlet sales the store will have.
2. Outlet_type has the second largest effect on the model.
    - A product being in a higher category(type), the higher the outlet sales the store will have.
3. Outlet_Establishment_Year
    - The red values (newly established) are leaning more on the left (negative) side. Newly Established outlets have lower sales than the Older Established outlets. 

# Exploratory Data Analysis:
- Count Plot was used to graph Categorical Columns
- Histogram was used to graph Numerical Columns
- Regplot was used to plot the data and draw the linear Regression fit
- Heatmap was used to see the Initial Correlation of Numerical Columns, which only shows a moderate correlation between Item_MRP and Item_Outlet_Sales.

![Screenshot 2023-04-04 182238](https://user-images.githubusercontent.com/125017784/229959887-9438b406-e014-4d43-ac7d-adfd45e2a774.png)

This histoplot shows that the average Outlet Sales is 2181.29. 

- Barplot was used in analysing the data.

![Screenshot 2023-04-04 183753](https://user-images.githubusercontent.com/125017784/229960759-b344f6e6-a3d9-4792-b03e-495b9a6daee9.png)
### Which Outlet Size has the most sales?
* **Top** earning Outlet Size
  - **Medium Size Outlet: 2681.60**
* 2nd earning Outlet Size
  - **High Size Outlet: 2298.99**
* 3rd earning outlet Size
  - **Small Size Outlet: 1912.14**
* Lowest earning Outlet Size
  - **Unknown Size Outlet: 1822.62**
  
![Screenshot 2023-04-04 183800](https://user-images.githubusercontent.com/125017784/229960978-20a07227-deaf-44bf-91ec-d9fbfc694f6b.png)
### Which Location Type makes the highest sales?
- **Top** earning per location type
  - **Tier 2: 2323.99**
- 2nd place earning per location type
  - **Tier 3: 2279.62**
- Lowest earning per location type
  - **Tier 1: 1876.90**

![Screenshot 2023-04-04 182307](https://user-images.githubusercontent.com/125017784/229961080-82f78cae-5600-4498-bc43-5817231a786a.png)
### Which Item Sales most?
- Top 3 Item that sales most are:
  1. Starchy Foods: **2374.33**
  2. Seafood: **2326.06**
  3. Fruits and Vegetables: **2289.00**
  
![Screenshot 2023-04-04 183824](https://user-images.githubusercontent.com/125017784/229961250-1d212c8c-e3b6-482c-b14b-329eab3a9f9a.png)
### Additional Graph
The previous graphs shows that the top earning for Outlet Size is the Medium Size, and the top earning Outlet Location is the Tier 2. This graph shows that we cannot see any Tier 2 in our Middle-Sized Outlets. We need to investifate the Unknown Values in this regard. 


# Machine Learning

## Models Used:
1. Linear Regression Model
2. Decision Tree Regression Model
3. Bagged Tree Regression Model
4. Random Tree Regression Model
5. K-Nearest Neighbors Model

## Models were evaluated and Results:
Linear Regression Test Scores:
- R^2: 0.567 
- MAE: 804.177 
- MSE: 1194454.943 
- RMSE: 1092.911 

Decision Tree Test Scores:
- R^2: 0.183 
- MAE: 1044.079 
- MSE: 2252983.394 
- RMSE: 1500.994 

Tuned Decision Tree Test Scores:
- R^2: 0.582 
- MAE: 742.572 
- MSE: 1152549.335 
- RMSE: 1073.569 

Bagged Tree Test Scores:
-  R^2: 0.522 
- MAE: 796.362 
- MSE: 1318765.376 
- RMSE: 1148.375 

Random Forest Test Scores:
- R^2: 0.554 
- MAE: 769.215 
- MSE: 1229700.289 
- MSE: 1108.919 

K-Neighbors Test Scores:
- R^2: 0.493 
- MAE: 839.764 
- MSE: 1399274.266 
- RMSE: 1182.909 

### Model Performance:

- Decision Tree tuned at 6 max depth have a little bias on it and it out-perform other models.
- For the testing set on the model, 58.2% of the variance in y was explained by x. 
- It has the lowest Testing Mean Absolute Error at 742.572.
- It has the lowest Mean Squared Error at 1138939.058.
- It has the lowset Testing Mean Squared Error at 1073.569.

We can use Decision Tree Model (Tuned max depth to 6) to make predictions about: Which Outlet makes more profit? What type of Outlet to consider? Where should this Outlet be located? 


# Recommendation
### Even if our data doesn't show Medium-Sized Outlet in Tier 2 Location. Entrepreneurs should still consider having a Medium Sized Outlet on Tier 2 Locations as these makes the most profits. Starchy Foods, Seafoods, Fruit and Vegetables are amongst the highest sales on our Item list. 

# Limitations & Next Steps
Entrepreneurs should be able to use the insights on how things are going in Outlet stores using the visuals and have a firm decision on which Outlet is the better choice.  

**“Good business leaders create a vision, articulate the vision, passionately own the vision, and relentlessly drive it to completion.”** </br>
-Jack Welch


# For Further Information:
Jude Maico Jr. (Future Data Scientist) </br>
j29maico@gmail.com
