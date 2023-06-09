# Dataset-For-final-project

https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques/data

# House Prediction 
The purpose of this project is to predict the house prices based on some features.It is a regression problem. The data is for kaggle competition.
I chose this dataset because my sister and I are in the process of buying a house and it would be interesting to see which features are more correlated and to see if we can predict the house price based on some features.

-------------------------------------------------
## Data Description
A competition hosted by Kaggle
The train  and test data that is given contains 1460  observations containing 80 features including categorical, ordinal and numerical features .

<img src="https://user-images.githubusercontent.com/15922299/232814240-3a0984e2-e82a-43ee-a3f2-163f0776dfda.png" width=800 />

you can see data_description.txt file for more information about features.

<img src="https://user-images.githubusercontent.com/15922299/232815125-204d895c-58e7-4f35-9fcc-4432ba3f7da4.png" width=400 />
<img src="https://user-images.githubusercontent.com/15922299/232814936-bfcd3161-3e36-4ffa-b6a3-4ed081bbfd29.png" width=500/>

## let us take a look at how the house prices are distributed.

<img src="https://user-images.githubusercontent.com/15922299/232815578-cc5236ae-66ff-450d-8561-2edac5da44c3.png" width=500/>

<img src="https://user-images.githubusercontent.com/15922299/232816311-203fd4da-d9bb-40c7-baf5-da9015a73386.png" width=300/>

## Numerical data distribution

We will now take a look at how the numerical features are distributed. In order to do this, let us first list all the types of data from our dataset and select only the numerical ones.

![image](https://user-images.githubusercontent.com/15922299/232816408-1ec299c1-77af-4ef5-bc94-9f6a49910dd9.png)
![image](https://user-images.githubusercontent.com/15922299/232816443-392f01ad-e4b3-48e6-ac21-061074b141c3.png)

## Categorical data distribution

We will now take a look at how the categorical features are distributed. In order to do this, let us first list all the types of data from our dataset and select only the categorical ones.

<img src="https://user-images.githubusercontent.com/15922299/232816496-69dec857-a6e0-4ff7-93d9-2061b0c23f62.png" width=500 />

<img src="https://user-images.githubusercontent.com/15922299/232816512-cc6259ce-4c73-4e59-8860-802f716a0cbf.png" width=500 />

## Lets look at the correlation between features:
<img src="https://user-images.githubusercontent.com/15922299/232950993-ed90be9f-3618-4a67-8785-3c540376eec7.png" width=650 />

## And finally we try to see outliers:

<img src="https://user-images.githubusercontent.com/15922299/232823577-9e1ff988-950f-4c50-bbb6-f20fa01d649a.png" width=500/>

## Preprocessing/ Exploration with the Data

For the first step, I checked Nan values in the data:

<img src="https://user-images.githubusercontent.com/15922299/232965357-b72f0602-f0f6-4335-977b-d93166f8acb0.png" width=500/>

There is NA for some records that does not mean it is an empty record. Forexample in the picture below, it means there is no access to the alley. However, all of them converted to Nan values automatically. So as a first step, I replaced those NA, with NOT.

<img src="https://user-images.githubusercontent.com/15922299/232824585-caaf58ec-915b-4f06-be83-07232eb7f94f.png" width=300/>
<img src="https://user-images.githubusercontent.com/15922299/232965357-b72f0602-f0f6-4335-977b-d93166f8acb0.png" width=400 />
<img  src="https://user-images.githubusercontent.com/15922299/232825381-4dd8207f-8b98-48e6-adf8-f3007a4a1ebf.png" width=650/>

## Create a Transformer 
I created a transform function to categorical features to OneHotEncoder and ordinal features to OrdinalEncoder. Also to fill Empty values using SimpleImputer.

## Train-Test Split
## GridSearchCv Evaluation:
I used neg_mean_error for GridSearchCV evaluation
Scikit-learn considers by convention that a score follow the rule: 'higher values are better than lower values'. In this case a small MSE shows that your predictions are close to data so it follows the opposite rule. That's why sklearn consider the negative (actually opposite) MSE as score.
And MSE means minimum square error( y_real - y_predicted)
The R2 score is one of the performance evaluation measures for regression-based machine learning models. It is also known as the coefficient of determination. If you want to learn how to evaluate the performance of a machine learning model using the r squared score

## Model Evaluation
I used R2 Score and MSE and RMSE and MAE
MAE=The mean absolute error measures the average differences between predicted values and actual values
RMSE= Root Mean Squared Error (RMSE) is the square root of the mean squared error between the predicted and actual values.
in regression problems, the RMSE score is used as a metric to measure performance and the mean squared error (MSE) is used to evaluate the performance of a regression model.
R 2 (coefficient of determination) regression score function.Best possible score for R2 is 1.0 and it can be negative (because the model can be arbitrarily worse).

## The result of running Baseline gridsearch is as follows: 

<img  src="https://user-images.githubusercontent.com/15922299/232960550-f8aaf7ea-2c90-4834-9e56-7a13a0d87dc1.png" width=430  />

Based on the table,It seems GradientBoostingRegressor did better than two other algorithms both for train and test.
## After Experiment 1:
The Ridge performs poorly both for train and test. However GradientBoostingRegressor performed very well for train and test.
Svm get better only for train data but worse for the test data.

<img  src="https://user-images.githubusercontent.com/15922299/232960708-ba1b7717-71a5-4d99-93dc-99a923afc551.png" width=430/>


## After Experiment 2( adding Polynomial Feature):
adding polynomial feature usually should gives us better training result( even sometime overfitting) and sometimes better result for test data depends on the nature of features.

GradientBoostingRegressor get much better result both for train and test dataset.
SVM and Ridge seems to get overfitted because it has great result for training set but very poor result for the test set.

<img  src="https://user-images.githubusercontent.com/15922299/232960861-10e4c907-05e4-4cdd-9b0d-f3b28247cff0.png" width=430/>

## After Experiment 3 PCA transformation (Experiment 3):
The result get worse for Ridge.
a liitle change in GradientBoostingRegressor only in train set and it makes it worse.
For SVM results was significantly get worse.

<img  src="https://user-images.githubusercontent.com/15922299/232961021-55f89586-7076-464a-88c2-f81605561c80.png" width=430/>

## After Experiment 4 MinmaxScaling (Experiment 4):
MinMaxScaler rescales the data set such that all feature values are in the range [0, 1] as shown in the right panel below. However, this scaling compress all inliers in the narrow range [0, 0.005] for the transformed number of households.

It makes train data performance better for ridge but not for the test data. However it makes significantly increase in the performance of test data for GradientBoostingRegressor. And performance is geting worse for SVM

<img  src="https://user-images.githubusercontent.com/15922299/232961144-87fbfe44-24b2-4691-890c-c6bde7baef66.png" width=430/>

## After Adding random feature 1 (Experiment 5)

From the results, it seems after adding random feature all the models performance get worse which seems logical because it is irrelevant feature

<img  src="https://user-images.githubusercontent.com/15922299/232961378-198426f7-5f13-43d6-8108-4dfce139fa87.png" width=430/>

After performing the models we've determined KNN was the best model because of its accuracy rate with the testing data.

We can probably receive a better model if we are able to manipulate existing features 

Due to the fact that the dataset was large we couldn’t properly include every data point but there might be ways to work with big data that we don’t know at the moment

## After Adding random feature 2 (Discrete feature) (Experiment 5)

Lets see some record with our random discrete feature

<img  src="https://user-images.githubusercontent.com/15922299/232901223-a699a684-9353-4c1b-9a6b-56edff30d4c8.png" width=650/>

Ridge and SVM did not show any significant change. However GradientBoostingRegressor show slighlty better result.

<img  src="https://user-images.githubusercontent.com/15922299/232961508-9a4320ec-41a9-488e-be7f-f88df32ebf08.png" width=430/>

## Pipeline with the Best:
The final pipeline I created, used the imputer instead of filling Nan value by my approach and also use MinMaxScalor for numerical features and OnehotEncoder for categorical data and also OrdinalEncoder for ordinal features and polynomial degree 2 , with GradientBoostingRegressor. Here is the final result:

<img  src="https://user-images.githubusercontent.com/15922299/232950652-037800b3-9f38-42bd-a1c3-0401723e4427.png" width=300/>

You can see the comprehensive results of all experiments in the Experiment_Evaluation.xlsx.

