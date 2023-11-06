# Data_Mining

## Introduction
This project was inspired to make future planning easier and more appealing for the new generation of young adults in Singapore when it comes to buying a property. With an accurate prediction of property prices, particularly resale HDBs, young adults will find it easier to plan ahead of time and work towards their dream homes. Additionally, we also want to equip customers with the knowledge to determine if they are getting a fair price for the property they are interested in. For this project, we evaluated a number of models that could be used to help predict resale HDB prices. 

## Dataset
We used the dataset “HDB Resale Flat Prices from 1990 to 2021 March” from Kaggle. This dataset contains a total of 28 columns and 840918 rows and provides an overview of the HDB resale market in Singapore. The dataset is fully complete with no null values for each attribute. The data types include object, integer, and float. Each record in the dataset represents a specific flat and its resale price, along with the other attributes like flat type. Some important attributes included resale_price, price_psm, year_gini, area_sqm, flat_model, storey that could help predict resale HDB prices. 

## Precusor Steps

### i. Data Pre-Processing
Before jumping into our analysis, we conducted some data pre-processing. Some techniques applied included applying log transformation to remove skewness are performed, and filtering important attributes to derive relevant information from the dataset such as area_sqm and flat_model.

Additionally, we also did some encoding for our data to transform categorical variables into numerical values that can be used by machine learning algorithms. We primarily used 2 methods namely Label Encoding and Target Encoding. Both methods have their pros and cons and we wanted to see if either methods had an adverse impact on our analysis later on. 

### ii. Exploratory Data Analysis
Then, EDA was conducted to better understand the dataset and HDB resale trends. Some interesting insights were that the majority of the home buyers tend to choose 3 room and 4 room flats, and that the demand for multi generation flats remained relatively low over the years likely due to the skyrocketing prices of such properties. 

## Model Evaluation

We evaluated our models based on 2 evaluation metrics. The R² value shows how well the data fits in a regression model whereas the Root Mean Square Error (RMSE) value indicates how spread out the data is around the regression line. In this case, we want our model to have high R² and low RMSE values.

We began preparing the data for modelling by splitting the dataset into a matrix of input variables and output variables. In this case, the input variables were the town_dummy, flat_type, flat_model, storey, area_size in square metres, years_remaining on the lease, and the year_gini, while the output variable was the resale_price. The dataset was split into two random subsets of 80% for training and 20% for  testing.

### i. Models Used
For our evaluation, we used the following models: Linear Regression, Decision Tree, Random Forest, Neural Network, Gradient Boosting, Ada Boosting, XG Boost, Bagging Regression, Linear Support Vector Regression, Ridge Regression, Lasso Regression, KNN-Regression. 

### ii. Results
For evaluation, we compared the R² and RMSE values produced by each model to determine the best performing regression algorithm.

In our Label Encoded Dataset (DS_TEST), our top three performing models are the Random Forest, Bagging Regression and the Adaboost algorithms. The best performing model, the Random Forest algorithm, was able to return us the highest R² value of 0.96093 and the lowest RMSE of 29814 amongst all other algorithms.

In our Target Encoded Dataset (DS_TEST2), while both the Random Forest and Bagging Regression algorithm yielded us the highest R² value of 0.95875, the former produced the lowest RMSE of 30534 compared to all other algorithm models we have run the dataset on.

### iii. Conclusion
We believed that the Random Forest algorithm was able to produce the best results as compared to the other models due to the fact that the results from a Random Forest algorithm are produced by combining multiple random decision trees. With the aggregation of multiple results from multiple random decision trees, this helps reduce the weightage bias of the associated attributes in the dataset.

Our worst performing model was the Linear Support Vector Regression, with a R2 value of 0.63193 and RMSE 91624 for the DS_TEST, and of R2 value of -0.40194 and RMSE 178600 for the DS_TEST2. The goal of the Linear Support Vector Regression is to fit the best line within the threshold value, but HDB resale prices are evidently not lined up in a straight line, combining the effects of the associated attributes. This is bound to create a model that produces a high squared error, which will also lead to a high RMSE and R2 value.

Other well performing models include Decision Tree, K-NN Regression and XGBoost Regression algorithm with R2 values well over 0.9.  These models fared well against the top 3 models identified from our findings and there is definitely space for improvement in terms of fine-tuning the parameters of each algorithm.

## Feature Selection
After running the models and choosing the best performing ones (random forest, adaboost and bagging regression), we conducted a feature importance analysis to decide which factors were most critical to consider when predicting HDB resale prices. Using feature_importances_, we plotted the graph of the feature importance scores. 

From our results, year_gini was the most important factor in predicting HDB prices followed by area_sqm, flat_type, town (location), lease_remaining, storey, and lastly flat_model. With inflation and rising prices due to economic factors, it is no surprise that year_gini is the most significant factor. Furthermore, with flat_area, type and town being the other significant factors, this indeed corroborates with the common valuation factors that are widely employed to determine a property’s worth.   



