# Classification Project - Predicting the Possibility of subscribing term deposit
Calvin Yu

## Abstract
The goal of this project is to create a classification model for the Portuguese banking institution that can predict the possibility of the customer subscribing term deposit in order to help the marketing team to prioritize which customer should they reach out to first. The dataset that I used contains forty thousand data points with twenty features given the last feature is the target variable of whether or not the customer subscribed term deposit. The period for this data set is from May 2008 to November 2010. I have used multiple algorithms to train the dataset including Logistic Regression, KNeighbors Classifier, Decision Tree Classifier, Random Forest Classifier, and gradient boost/ XGB Classifier. I used ROC AUC to compare the performance of each algorithm. After tuning the hyperparameters and applying oversampling on some of the algorithms, I chose the best one.

## Design
A Portuguese banking institution put thousands of money on a direct marketing campaign to promote term deposit. The marketing team from this institution wants to know who has a higher probability of subscribing to the term deposit so they save time and reach out to those that are likely to subscribe to the term deposit. So the business question for the marketing team is how to implement their time wisely and efficiently to get more term deposit subscriptions. The model that I create will answer this question by ranking the possibility of each customer and sort them from the highest to the lowest.

## Data
### Bank Marketing Data set
- From May 2008 to November 2010
- 41188 rows with 17 features (dropped three features due to redenducy and model fairness)and 1 target variable(y/n)
- feature highlights :
age , job , education, contact, loan,euribor3m,nr.employed

## Algorithms 
1. Use Python to read the dataset and clean the dataset by checking to see if there is any missing values
2. Perform Exploratory Data analysis, plotting each features grouping by the target variable, also check the heatmap to drop any highly correlated features (dropped euribor3m and emp.var.rate because they highly correlate with nr.employed)
3. Use Dictionary and LabelEncoding to turn the categorical column into interger
4. Check the distribution of the target variable 
5. Split the dataset into test,train,validation and stratify it with y because the distribution of y is extremely imbalanced and we do not want the dataset to split into a set with no one subscribing term deposit
6. The entire dataset has been splited into 60/20/20 train vs validation vs test. 
7. Use the training set to train each model and use the validation set to evaluate the performance of the algorithm
8. Tuning the hyperparameters for the algorithms that are overfitting
9. Compare the ROC AUC score for each hyperparameters within an algorithm, choose the best hyperparameter that doesn't overfit on the training set and has the highest ROC_AUC score 
10. Perform the same task above to get the best ones for each algorithm
11. Graph the ROC AUC curve for all the algorithms with the best hyperparameters

![Roc_auc](https://user-images.githubusercontent.com/63031028/118230461-92e11d80-b442-11eb-8591-05281d79a264.png)

- ROC AUC score for Logistic Regression =  0.7709702550827869
- ROC AUC score for KNN =  0.7795373602528421
- ROC AUC score for Decision Tree =  0.7664935551205246
- ROC AUC score for Random Forest =  0.7839620972687391
- ROC AUC score for XGboost/Gradient Boosting =  0.7919172189725932
- ROC AUC score for Naive Bayes =  0.6718804542667106



12. Decide to use XGboost because it has the highest score among the models, and use shap to evaluate the feature importance

13. Use the model to train the test set and the ROC_AUC score is 0.802 

## Tools
- Python Numpy, Pandas - data cleaning,data manipulation
- Scikit learn for modeling and metrics
- Matplotlib, seaborn ,and shap for data visualization

## Communication
![feature importance](https://user-images.githubusercontent.com/63031028/118231451-03d50500-b444-11eb-8e16-7302cb8ec09b.png)

As we can see that number employers for the bank is a really important feature. So I checked the boxplot to see the correlation between subscribing the term and deposit and the number of employers and here is the results: 

![boxplot](https://user-images.githubusercontent.com/63031028/118231877-8e1d6900-b444-11eb-907d-36d625bfcdb8.png)

The result is really strange and counter my hypothesis that more employers will lead to more subscriptions because the bank can reach out the more people. This feature needs to be further investigate but my assumption is just that only the total of the employers in the marketing team matters

Another important feature is contact and here is the result: 

![contactbox](https://user-images.githubusercontent.com/63031028/118232327-3a5f4f80-b445-11eb-88a3-764c45be2d90.png)

This feature is much more easier to interpret as the successful rate tends to be higher when customers are contacted by cell phone

The month feature is also important, but there is lack of information of why it is important, so I can only assume that people tend to subscribe on certain months. I definitely need to investigate on that.

## Future steps
1. Try more hyperparameters on the models 
2. Acquire a larger data set with longer time span 
3. investigate on the important features 