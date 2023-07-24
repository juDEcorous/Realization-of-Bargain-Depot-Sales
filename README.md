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


# Exploratory Data Analysis:
- Count Plot was used to graph Categorical Columns
- Histogram was used to graph Numerical Columns
- Regplot was used to plot the data and draw the linear Regression fit
- Heatmap was used to see the Initial Correlation of Numerical Columns, which only shows a moderate correlation between Item_MRP and Item_Outlet_Sales.

<p align="center">
<img src = 'Graph/average sales of all outlet stores.jpg'>
</p>

This histoplot shows that the average Outlet Sales is 2181.29. 

- Barplot was used in analysing the data.

<p align="center">
<img src = 'Graph/average sales of outlet stores b y outlet size.jpg'>
</p>

### Which Outlet Size has the most sales?
* **Top** earning Outlet Size
  - **Medium Size Outlet: 2681.60**
* 2nd earning Outlet Size
  - **High Size Outlet: 2298.99**
* 3rd earning outlet Size
  - **Small Size Outlet: 1912.14**
* Lowest earning Outlet Size
  - **Unknown Size Outlet: 1822.62**
  
<p align="center">
<img src = 'Graph/average sales of outlet stores by outlet type.jpg'>
</p>

### Which Location Type makes the highest sales?
- **Top** earning per location type
  - **Tier 2: 2323.99**
- 2nd place earning per location type
  - **Tier 3: 2279.62**
- Lowest earning per location type
  - **Tier 1: 1876.90**

<p align="center">
<img src = 'Graph/average sales of outlet stores by outlet type.jpg'>
</p>

### Which Item Sales most?
- Top 3 Item that sales most are:
  1. Starchy Foods: **2374.33**
  2. Seafood: **2326.06**
  3. Fruits and Vegetables: **2289.00**
  
<p align="center">
<img src = 'Graph/item on outlet with most sales.jpg'>
</p>

# Machine Learning

## Models Used:
1. Linear Regression Model
2. Decision Tree Regression Model
3. Bagged Tree Regression Model
4. Random Tree Regression Model
5. K-Nearest Neighbors Model

## Models were evaluated and Results:

<p align="center">
<img src = 'Graph/model results.png'>
</p>

### Model Performance:

- Decision Tree tuned at 6 max depth have a little bias on it and it out-perform other models.
- For the testing set on the model, 58.2% of the variance in y was explained by x. 
- Tuned Decision Tree has the lowest Testing MAE at 747.58.
- Tuned Decision Tree has the lowest Testing MSE at 1152549.33.
- Tuned Decision Tree has the lowest Testing RMSE at 1073.57.


# Data Visualisation:  

## Linear Regression Coefficients

<p align="center">
<img src = 'Graph/Linear Regression Coefficients.jpg'>
</p>

- According to the Linear Regression Model the Top 3 most important features are:
  1. Outlet_Location_Type_3: A Supermarket Type 3 will increase the sales by ₹2,163.73.
  2. Item_MRP: The supply planning method will efficiently increase the sales by ₹984.64.
  3. Outlet_Size_Big: Having a big Outlet seems to increase the sales by ₹553.40.
    
<p align="center">
<img src = 'Graph/Linear Regression Shap Values Bar.jpg'>
</p>

- Item_MRP, Outlet_Type_Supermarket_Type3, Outlet_Establishment_Year are seen on the top 5 most important feature for both Coefficients and SHAP. However, they are all in different order.
- For the other two features. We notice that the Coefficient relied more on Outlet_Size_Big and Item_Type_Seafood features while the SHAP relied more on Outlet_Size_Medium and Outlet_type_Grocery_Store.


## Random Forest Model Importances and Bar SHAP
#### We tuned this model as High Variance is seen on the defaulted model.

<p align="center">
<img src = 'Graph/Tuned Forest Importances.jpg'>
</p>

- Tuned Random Forest only shows top 4 most important features. This is true for both Feature Importance and Permutation Importance. These Features are:
    1. Item_MRP
    2. Outlet_Type_Grocery_Store
    3. Outlet_Type_Supermarket_Type3
    4. Outlet_Establishment_Year


<p align="center">
<img src = 'Graph/Tuned Random Forest Shap Values Bar.jpg'>
</p>

- Shap values, Feature importance and Permutaton Importance for the Tuned Random Forest, all have the same top 4 most important values.
    1. Item_MRP
    2. Outlet_Type_Grocery_Store
    3. Outlet_Type_Supermarket_Type3
    4. Outlet_Establishment_Year
- Shap values and Feature importance have same 5th place which is Item_Visibility. While Permutaion Importance suggest that Outlet_Type_Supermarket_Type3 is more important.

    
## SHAP Dot Models

#### We are going to compare Linear Regression model vs Random Forest Model with regards to beeswarm graph

## Linear Regression SHAP Dot

<p align="center">
<img src = 'Graph/Linear Regression Shap Values Dot.jpg'>
</p>

1. Item_MRP has the largest effect on Linear Regression Model.
    - The green and yellow values are mostly seen on the right (positive) side. The higher the retail price of the product, the higher the outlet sales the store will have.
2. Outlet_Type_Supermarket_Type3
    - The yellow values are leaning more on the right (negative) side. Supermarket_Type3 will make much more profit than the other outlet types.
3. Outlet_Type_Grocery_Store
    - The Yellow values are at the left (negative) side. The Grocery Stores will not make as much sales as the other type.
4. Outlet_Establishment_Year
    - The yellow and green values (newly established) are more on the right (positive) side. Newly Established outlets makes more sale than the Older Established outlets.

## Random Forest SHAP Dot

<p align="center">
<img src = 'Graph/Tuned Random Forest Shap Values Dot.jpg'>
</p>

1. Item_MRP has the largest effect on Random Forest Model.
    - The green and yellow values are mostly seen on the right (positive) side. The higher the retail price of the product, the higher the outlet sales the store will have.
2. Outlet_Type_Grocery_Store has the second largest effect on the model.
    - The Yellow values are at the left (negative) side. This suggest that the Grocery Stores will not make as much high sales as the other type.
3. Outlet_Type_Supermarket_Type3
    - The yellow values are leaning more on the right (positive) side. Unlike the Grocery Stores, Supermarket_Type3 will make much more profit.
4. Outlet_Establishment_Year
    - The yellow and green values (newly established) are leaning more on the left (negative) side. Newly Established outlets have lower sales than the Older Established outlets.

#### Both Linear Regression and Random Forest have the same top 4 features with regards to largest effect. The only difference is Outlet_Type_Grocery_Store is seen on the negative side for Linear Regression but is on positive side for Random Forest. Another thing to note is Outlet_Establishment_Year is seen on positive side for Linear Regression but is on the negative side for Random Forest.

## Local Explanation
- We are going to compare the Top 3 samples with the highest sales.
    - [!]Lime and Forceplot predicted exactly the same output for all these sample.

## Top 1 Highest Sales

![Screenshot 2023-06-30 044929](https://github.com/juDEcorous/Realization-of-Bargain-Depot-Sales/assets/125017784/79b2dc9d-3e0f-4b68-b6c4-b7852b483807)
- The predicted value of sale is ₹4,092.12
- The Random Forest Regression prediction is ₹3,770.59
- Positive influences are seen on features: Outlet_Type_Grocery Store, Item_MRP, Outlet_Establishment_Year, Item_Type_Breakfast
- Negative influences are seen on features: Outlet_Type_Supermarket Type3

![Screenshot 2023-06-30 044944](https://github.com/juDEcorous/Realization-of-Bargain-Depot-Sales/assets/125017784/887da9d9-2b34-4ebf-80d6-99b463026159)
- Predicted Sale Price: ₹4,092.13
- Push towards a higher price: Outlet_Type_Grocery Store, Item_MRP
- Push Towards a lower price: Outlet_Type_Supermarket Type3
- A Greater push towards a higher sale price is seen

## Top 2 Highest Sales

![Screenshot 2023-06-30 044951](https://github.com/juDEcorous/Realization-of-Bargain-Depot-Sales/assets/125017784/ce12eac3-3654-4b7a-bdf1-4033e258bbfb)

- The predicted value of sale is ₹6,417.38
- The Random Forest prediction is ₹4,730.68
- Positive influences are seen on features: Outlet_Type_Grocery Store, Item_MRP, Outlet_Establishment_Year, Outlet_Type_Supermarket Type3, Item_Type_Canned

![Screenshot 2023-06-30 044958](https://github.com/juDEcorous/Realization-of-Bargain-Depot-Sales/assets/125017784/916eb82a-de22-4b30-95ea-81a5d74c4549)

- Predicted Sale Price: ₹6,417.38
- Push towards a higher price: Outlet_Establishment_Year, Item_MRP, Outlet_Type_Supermarket Type3, Outlet_Type_Grocery Store
- Push Towards a lower price: No big impact as seen
- A Greater push towards a higher sale price is seen

## Top 3 Highest Sales

![Screenshot 2023-06-30 045008](https://github.com/juDEcorous/Realization-of-Bargain-Depot-Sales/assets/125017784/0847351f-6627-4e2a-8cd3-943c32018986)

- The predicted value of sale is ₹6,369.68
- The Random Forest prediction is ₹4,732.963
- Positive influences are seen on features: Outlet_Type_Grocery Store, Item_MRP, Outlet_Type_Supermarket Type3, Outlet_Establishment_Year,
- Negative influence: Item_Visibility

![Screenshot 2023-06-30 045013](https://github.com/juDEcorous/Realization-of-Bargain-Depot-Sales/assets/125017784/7782ee44-a0bd-4eda-8eb4-578893ca5109)

- Predicted Sale Price: ₹6,369.68
- Push towards a higher price: Outlet_Type_Grocery Store, Outlet_Establishment_Year, Item_MRP, Outlet_Type_Supermarket Type3
- Push Towards a lower price: No big impact as seen
- A Greater push towards a higher sale price is seen

### Local Explanation Findings:
- Outlet_Type_Grocery have the highest positive influence seen on all three samples. 
- Item_MRP is the second highest positive influence in all three samples.
- Predicted value of sale seems to be lower on our Top 1 Highest Sales that the other two.
- (Since they are amongst the Top 3 Highest Sales) Greater push towards a higher sale price is seen in all of them.
  

# Insights

- EDA shows that Medium Sized Outlet Stores have the highest mean sales of ₹2,681.60.
- EDA states that Tier 2 Locations are the best place to open a bussiness as the mean sales is about ₹2,323.99
- According to Linear Regression Coefficients Model, A Supermarket Type 3 will increase the sales by ₹2,163.73. The SHAP models then confirm this with an interpretation of "Supermarket_Type3 will make much more profit than the other outlet types," - This is true for both Linear Regression and Random Forest Models. 
- Upon further investigating the top 3 samples with the highest sales. It shows that Outlet_Type_Grocery Store have the highest positive influence on having a higher profit.
  
# Recommendation
### Entrepreneurs should consider having a Medium Sized Supermarket Type 3 on a Tier 2 Location as this makes the most profit. If Supermarket Type 3 is not to their liking or the budget won't afford it, Medium Sized Grocery Store on a Tier 2 Location could be an option. This Grocery Store could focus Starchy Foods, Seafoods, Fruit and Vegetables as these are amongst the highest sales on our Item list.

# Limitations & Next Steps
Entrepreneurs should be able to use the insights on how things are going in Outlet stores using the visuals and have a firm decision on which Outlet is the better choice.  

**“Good business leaders create a vision, articulate the vision, passionately own the vision, and relentlessly drive it to completion.”** </br>
-Jack Welch


# For Further Information:
Jude Maico Jr. (Future Data Scientist) </br>
j29maico@gmail.com
