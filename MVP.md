## MVP

The goal of this project is to see which customer will have a higher probability of subscribing the term deposit 

Since the target variable (people who subscribed term deposit) is extermely imbalanced, I will apply oversampling ,and SMOTE method to deal with this problem 

```

Simple Logistic Regression; Test AUC: 0.803
Logistic Regression on Oversampled Train Data ratio 2; TTest AUC: 0.848
Logistic Regression on Oversampled Train Data ratio 3;  Test AUC: 0.818
Logistic Regression on Oversampled Train Data ratio 4;  Test AUC: 0.848
Logistic Regression on Oversampled Train Data ratio 5;  Test AUC: 0.833
Logistic Regression on Oversampled Train Data ratio 6; Test AUC: 0.803
Logistic Regression on Oversampled Train Data ratio 7;  Test AUC: 0.788
Logistic Regression on Oversampled Train Data ratio 8 ;  Test AUC: 0.848
Logistic Regression on SMOTE Train Data ratio 2;  Test AUC: 0.818
Logistic Regression on SMOTE Train Data ratio 3; Test AUC: 0.818
Logistic Regression on SMOTE Train Data ratio 4; Test AUC: 0.848
Logistic Regression on SMOTE Train Data ratio 5;  Test AUC: 0.879
Logistic Regression on SMOTE Train Data ratio 6; Test AUC: 0.864
Logistic Regression on SMOTE Train Data ratio 7;  Test AUC: 0.879
Logistic Regression on SMOTE Train Data ratio 8; Test AUC: 0.879

```

I multiply the target variable with different ratio, and using the SMOTE method on the ratio of 5 is the best 

![mvproc](https://user-images.githubusercontent.com/63031028/117887683-f2360680-b265-11eb-87c8-08e89949dd21.png)

I use ROC/AUC metrics to measure to performance is because I would like to predict all the True positive value correctly, in my case, it is the customer that will likely to subscribe term deposit 

Logistic Regression on SMOTE Train Data ratio 5;  Test AUC: 0.879

The next step I will do is to try out different models

