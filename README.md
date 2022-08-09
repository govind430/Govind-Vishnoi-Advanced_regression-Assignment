# House Price Prediction
A US-based housing company named Surprise Housing has decided to enter the Australian market. The company uses data analytics to purchase houses at a price below their actual values and flip them on at a higher price. For the same purpose, the company has collected a data set from the sale of houses in Australia.


## General Information
The company is looking at prospective properties to buy to enter the market. You are required to build a regression model using regularisation in order to predict the actual value of the prospective properties and decide whether to invest in them or not.

 

The company wants to know:

Which variables are significant in predicting the price of a house, and

How well those variables describe the price of a house.

## Approach Explaination

### EDA Findings:
1. Data is having both numeric and categorical data
2. Size of data is 1460 datapoints
3. Checked missing values percentage in whole data and dropped those features where missing values is greater than 80%. 
4. Numeric data is having lots of outlier and very skewed. To introduce some linearity I did log transformation which will de-emphasize on outliers also.
5. I plotted correlation heatmap of all the numeric variable. We can see that some numeric features are not having strong relationship with target varibale.
6. For categorical data, firstly I checked the distribution of categories in the respective features. We saw some features are having 95%+ of data belonging to one category.
7. We have seen the data distribution of categorical varibale with target varibale using boxplot.

### Why I have not performed feature selection in EDA?
We have seen that in numeric varibale some varibales are having lots of 0 or some varibales are having very low correlation with target varibale. Similarly in categorical varibale we have seen some varibales are having 95%+ times one category. 
Why I have not dropped those features because I want Lasso and Ridge or RFE to perform this operation. If any feature is not important they will make the coefficient 0 or very close to 0 in case of ridge. And I think that's what we have to perform in this assignment.

### Model Explaination
1. As we can see linear regression model with all feature is getting overfitted. Train R2 score and RMSE value is good but when it coming to test its performing very bad. Error terms are not normally distributed on test data.
2. In RFE, we used cross validation to find best params in this case number of features. We got 15 as best param. Trained the model and we can see that its performing very good compare to linear regression. But RMSE value is still high in RFE. 
3. In Ridge, we used all the features and performed cross validation to get best lambda value. Trained model using best params and we can see its performing good in terms of R2 score and RMSE value than RFE model. Error terms are also normally distributed and we dont see any pattern in errors also.
4. In Lasso, again we used all the features and performed cross validation to get best lambda value. Trained model using best params and we can see that the difference in R2 score and RMSE of train and test is reduced as compare to Ridge. Error terms are also normally distributed and we dont see any pattern in errors also. 

<b> Best Model</b>
Lasso is performing best so far in terms of R2 score and RMSE value. 

### Next Steps 
1. As part of next step we can check the multicollinear feature in lasso model and we can remove those also to make it more interpretable.
2. Check the p-value of of all the coefficient to confirm if those coefficient values are reliable or not.

## Technologies Used
- Numpy
- Pandas
- SkLearn
- MatplotLib
- Seaborn
- Python

## Contact
Created by [@govind430] - feel free to contact me!