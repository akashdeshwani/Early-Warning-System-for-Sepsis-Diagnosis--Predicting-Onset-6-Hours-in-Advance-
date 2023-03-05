# Early Warning System for Sepsis Diagnosis: Predicting Onset 6 Hours in Advance:

## Problem statement 
We build a model that predicts non-sepsis and sepsis patients 6 hr ahead of clinical onset time. This project was a challenge proposed by PhysioNet in 2019 as a cardiology challenge ( PhysioNet supports open challenge which invite participants to tackle clinical data.). The clinical data of ICU from two hospital provided by Physionet. Each patient file represented single Hours’ worth for measurement within stay of hospital. 

This project was one of the project assigned by Prof Shailesh during ML course. And the key point for this project was we were not allowed to use DL Models.Before start of this project we understood that Intensive care units (ICU) are the part of hospitals where decision making is very important, complex and critical at the same time. Deciding correctly and at the right time who is the patient who needs critical care, ensuring good management and allocation of resources which are both limited and very expensive. This good management will guarantee a considerable saving in costs by reducing them considerably.

To work of this project we used Knowledge Discovery in Databases (KDD) process. KDD is a process of discovering useful information from large amount of data. This process consists of following steps:

1. Selecting and extracting data set from the database.
2. Pre-processed and cleaned up into a tidy dataset by exploring the data, handling missing data, and removing noise / outliers.
3. Building a predictive model allowing to associate biomedical measurements with a real-time severity indicator (probability of mortality) by implementing several machine learning algorithms.
4. Evaluation and validation. The use of two databases provides an opportunity to validate the different predictive models that will be produced.

## Flow and Explanation of the code

At first we create functionality to read the data from the given files. We had psv files which were pipe separated files. We used pandas to read the data.We had to merge each patient file into a single CSV files and valiate it. After looking at the data we found its very imbalanced dataset that has only 2.2 percent of Sepsis patients. 

As no one in our group had healthcare background, So to understand the data we first read multiple research papers check what others have done. We gained knowledge about multiple features and their importance like SofA score. The SOFA score is calculated by adding the scores of 6 parameters: respiratory rate, blood pressure, Glasgow Coma Scale, serum sodium, serum bilirubin, and platelet count. The SOFA score ranges from 0 to 24, with higher scores indicating more severe illness.

Before moving forward we decided to use tree based models as they are robust to missing data. also we fixed our evaluation matrix F1 score and ROC AUC graph was one of the most important evaluation metric for this challenge. 

So now when we did feature Transformation based on tree type models e.g. Age divided into 5 bins Infant child adult and old. Similarly we did for many other features.
and we also create derived features like Blood pressure ratio, Septic shock, and many more.

Missing data is a common problem in real-world data. So we tried multiple ways to handle missing data. Interpolation | forward fill | backward fill | mean, we found that interpolation is the best way to handle missing data as it does not change the distribution of the data. We also used forward fill and backward fill but it changes the distribution of the data 

We used 6 different models to predict the sepsis. We used Decision tree, Random forest, Xgboost, LGBM. We used 5 fold cross validation to validate the model. We used accuracy, precision, recall, f1 score, and AUC score to evaluate the model. We also used confusion matrix to evaluate the model. We also used hyperparameter tuning to improve the model. We used grid search to tune the hyperparameters. 

## Results 

Best model was Xgboost with 0.9 AUC score and 0.8 F1 score. We found that the most important features were Age, Heart rate, and Blood pressure ratio.

## Conclusion

What made the challenge too hard was the presence of a lot of missing data, At first we had to add 8 new features to compensate for the missing data 
We got a result with the Decision tree algorithm and Xgboost that partially classify sepsis. The quest to find the best model led us to consider all the dataset and eliminate theunbalanced data. The choice for the 6 models to compare was already inspired by the success of these algorithms in similar problems.


## Future Scope

In a future work, we will use the time component approach and consider the problem as being the classification of a multivariate time series with two classes. 
We will focus on a complete set of data,so we have to deal with the interpolation of the missing value. We will try to get a more concise way of learning distribution from other equivalent problems and measure. The sepsis challenge prediction with time series approach depend on the study of the relationship between observed data at different times, and the number of lag observations provided as input must be checked and specified.