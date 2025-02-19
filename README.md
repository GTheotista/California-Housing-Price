# **California Housing Price**

**Tools:** Python <br>
**Visualizations:** Python (Matplotlib/Seaborn)<br>
**Dataset:** [California Housing Price](https://github.com/GTheotista/Purwadhika-Capstone3/blob/main/data_california_house.csv)

**Table of Contents:**

- [**Supermarket Customers Analysis**](#California-Housing-Price)
- [**Step 0: Business Problem Understanding**](#Step-0-Business-Problem-Understanding)
- [**Step 1: Data Understanding**](#Step-1-Data-Understanding)
- [**Step 2: Data Preprocessing**](#Step-2-Data-Preprocessing)
- [**Step 3: Modeling**](#Step-3-Modeling)
- [**Step 4: Conclusion And Recommendations**](#Step-4-Conclusion-And-Recommendations)
- [**Step 5: Save Model**](#Step-5-Save-Model)

---

# **Step 0: Business Problem Understanding**

---
In the complex dynamics of the housing market, consumers strive to get the best value for their investments, while real estate entrepreneurs aim to maintain profitability and business growth. Overpricing can damage consumer trust, while underpricing can hinder business growth and lead to financial losses.

**Problem Statement**
- **Consumer Perspective:** Consumers often face uncertainty in assessing whether a property's price reflects its actual value. Avoiding overpriced purchases is a key challenge in decision-making.
- **Business Perspective:** Real estate entrepreneurs struggle to set balanced prices. Overpricing can hinder sales and damage reputation, while underpricing can cause financial losses and limit business growth.

**Goals**
- **Consumer Empowerment:** Provide consumers with accurate and transparent information about factors influencing property prices, enabling them to make informed purchasing decisions.
- **Business Sustainability:** Assist real estate entrepreneurs in setting balanced prices, reducing the risks of overpricing and underpricing, and fostering sustainable relationships with consumers.

**Analytics Approach**
- **Machine Learning Regression Model:** Build a regression model to predict property prices based on factors such as geographic location, population, number of rooms, and more.
- **Feature Importance Analysis:** Analyze the significant factors affecting property prices, helping consumers better understand price determinants.
- **Price Strategy Optimization:** Use the model to help entrepreneurs optimize pricing strategies, ensuring that offered prices reflect actual property value without overpricing or underpricing.

---

# **Step 1: Data Understanding**

---

**Feature Explanation**
Explaining the meaning and significance of each feature:
- **Longitude:** Geographic coordinate indicating east-west location.
- **Latitude:** Geographic coordinate indicating north-south location.
- **Housing Median Age:** Average age of houses in the area (years).
- **Total Rooms:** Total number of rooms in all houses in the area.
- **Total Bedrooms:** Total number of bedrooms in all houses in the area.
- **Population:** Total number of residents in the area.
- **Households:** Number of households in the area.
- **Median Income:** Median household income in the area.
- **Ocean Proximity:** Information on how close a house is to the ocean (e.g., "Near Ocean," "Inland," etc.).
- **Median House Value (Target Feature):** Median house value in the area.

From the target feature explanation, this problem can be solved using a regression model.

**Checking Unique Values in 'Ocean Proximity' Column**
Examining unique values in the categorical column 'ocean_proximity' to gain insight into proximity-to-ocean category distribution.

**Data Correlation and Distribution**
Checking the correlation between features and the target variable, visualizing data distribution through pair plots and heatmaps. It is found that 'median_income' strongly correlates with 'median_house_value.'

---

# **Step 2: Data Preprocessing**

---

**Missing Value Handling**
Confirming missing values in the dataset, handling missing values using median imputation due to data non-normality.

**Outlier Handling**
Handling outliers for various features such as 'median_house_value,' 'total_rooms,' 'population,' 'households,' and 'median_income.'

---

# **Step 3: Modeling**

---

**Defining Variables (X) and Target Variable (y)**
For model development, the independent variables (X) include geographic coordinates, median housing age, number of rooms, population, number of households, median income, and ocean proximity information. The dependent variable (y) is the median house value ('median_house_value').

**Encoding**
Applying one-hot encoding to process categorical data, particularly the 'ocean_proximity' column, allowing the model to understand and utilize this information in learning.

**Data Splitting**
Splitting data into training and testing sets, with the training set used for model training and the test set for evaluation.

**Benchmark Model Selection**
Selecting multiple regression models as benchmarks to establish a baseline before improvement:
- Linear Regression
- K-Nearest Neighbors (KNN)
- Decision Tree
- Random Forest
- XGBoost

**Scaling**
Applying feature scaling before training, choosing between Min-Max Scaler and Standard Scaler based on model performance evaluation.

**Best Model Selection**
Evaluating each model using metrics such as Root Mean Squared Error (RMSE), Mean Absolute Error (MAE), and Mean Absolute Percentage Error (MAPE). The best model selected is XGBoost Regressor.

**Hyperparameter Tuning for XGBoost**
Performing hyperparameter tuning using GridSearchCV to find the best parameter combinations for performance improvement.

**Post-Tuning Model Evaluation**
Comparing the performance of XGBoost before and after tuning using RMSE, MAE, and MAPE, concluding that tuning improves model performance.

---

# **Step 4: Conclusion And Recommendations**

---

**Conclusion**
- The model effectively predicts house prices within specified feature boundaries.
- RMSE and MAE are large but acceptable due to the wide target variable range.
- MAPE of 17% indicates the model's high accuracy in predicting house prices.
- Feature importance analysis identifies 'Median Income' and 'Ocean Proximity' as key factors.

**Recommendations**
1. Adding additional features like bedroom-to-room ratio, building area per land area, nearby public facilities, economic growth indicators, distance to city center, and life quality index could enhance model performance.
2. Investigate high-error predictions by analyzing overestimation and underestimation groups.
3. Consider collecting more data and exploring advanced models like RNNs if sufficient data is available.

---

# **Step 5: Save Model**

---
After completing the model, it is saved using the pickle module in a reusable format.

