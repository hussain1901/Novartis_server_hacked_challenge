# Novartis Server Hacked Challenge

## Introduction
Novartis company conducted a Data Science hiring challenge in which they have given the dataset and asked to create a model to predict if the server will be hacked based on the features.

## Problem Statement
Predict if the server will be hacked based on the given features in the dataset.
This is binary classification problem.

## Data
The dataset has 23856 records with 18 features. Most of the features are kind of an encoded i.e. feature names are not directly given, instead it says X_1, X_2 etc.
All the features from X_1 to X_15 are continuous value features and apart from that there are features Incident_ID and Date.

The test data has 15903 records.

This is class imbalance problem as a particular class value has more than 95% records.

## IDE used
Jupyter Notebook

## Approach
### Data Cleaning
Data was loaded in dataframe and in the initial exploration it was found that feature X_12 has missing value, so it was filled using linear interpolation.
After that outlier detection was done using 3 Standard deviation away from mean method.
Features that contain outlier are : X_1, X_7, X_8, X_9, X_10, X_12, X_13, X_15
Treatment of those variable which contain outliers was done as below
1. Calculate the 10th and 90th percentile score of the features.
2. Replace the values that are beyond 10th and 90th with the 10th and 90th value respectively.

### Correlation
Now a correlation matrix was created to see relationship among the features.

### Feature selection
Using the SelectKBest function of feature_selection top important features were selected and used to create model.

### Model Development
Since this is a classification problem so below listed algorithm selected for model development.
- Logistics Regression
- KNN
- SVM
- Decision Tree
- Naive Bayes

Recall is metric used for model evaluation as accuracy could be misleading in this case.
Based on the recall score of all algorithm, KNN is selected for final model development.

K is selected as 3 based on the score of training and testing.

![Select K](https://github.com/hussain1901/Novartis_server_hacked_challenge/blob/master/KNN_select_K.png)

Now with K=3 a KNN model is build, tested on the unseen/test dataset.
Final recall score achieved was 0.906 after submission of the result on hiring challenge website.
![Result_submission](https://github.com/hussain1901/Novartis_server_hacked_challenge/blob/master/Result_submission.JPG)
