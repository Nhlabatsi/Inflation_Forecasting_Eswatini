
INFLATION FORECASTING FOR ESWATINI
A Machine Learning Approach Using LASSO Regression
The dataset includes CPI sub-indices across major consumption categories:
•	Food Index - tracking prices of food and non-alcoholic beverages
•	Alcohol & Beverage Index - alcoholic drinks and tobacco
•	Clothing Index - apparel and footwear
•	Housing, Water & Utilities Index - rent, maintenance, utilities
•	Transport Index - vehicle purchases, fuel, public transport
•	Health Index - medical services and pharmaceuticals
•	Education Index - tuition fees and educational materials
•	Communications Index - telecommunication services

 Model Selection Rationale
LASSO (Least Absolute Shrinkage and Selection Operator) was selected for several key advantages in this forecasting context:
•	Automatic feature selection through L1 regularization
•	Prevention of overfitting with high-dimensional feature space (115+ features)
•	Interpretability through sparse coefficient vectors
•	Robustness to multicollinearity among related economic indicators


 Feature Categories
Original Indices (16 columns): Food, Alcohol & Bev., Clothing, Housing/Utilities, Furnishing, Health, Transport, Communications, Recreation, Education, Restaurants/Hotels, Other, plus Headline CPI, CPI_Index, Inflation_YoY
Engineered Features (99 columns): For each of 11 indices: _yoy, _lag1, _lag3, _lag6, _yoy_ma3, _yoy_std3, _yoy_ma6, _yoy_std6 (8 features × 11 indices + CPI_Index features)
Target Variable (1 column): target = Headline Inflation shifted -h months

Multi-Horizon Forecast Generation
Horizon-Specific Training
Each forecast horizon requires a dedicated model trained on appropriately aligned data. For h=2 (September forecast from July data), features at time t are paired with inflation at time t+2. For h=3 (October forecast), features at time t predict inflation at time t+3.

