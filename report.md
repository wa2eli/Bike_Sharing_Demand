# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### NAME HERE

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
There were no negative numbers in the predictions, despite the fact that they were not exactly as predicted. Given that count is always higher than or equal to zero, this makes logical. As a consequence, when I attempted to submit my predictions, no errors were produced.

### What was the top ranked model that performed?
The top ranked model performed is WeightedEnsemble_L3.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
The dataset's produced histograms showed the following:
1. Seasons fall into four types. 
2. There are three types of weather. 
It became clear that some category characteristics represent object types (str types) in the dataset by describing the train and test datasets. This could in some way affect the model's judgments. 
Season and weather characteristics, for example, were changed to the categorical feature type.
The hour, day, month, and year were retrieved as new characteristics and put to the dataframe. 
### How much better did your model preform after adding additional features and why do you think that is?
The model's score value increased significantly to a value of 0.63630. The addition of additional features including day, time, month, and year as well as the conversion of categorical datatypes to the proper type are responsible for the improved score. This has improved the model's capability for prediction.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
I have to admit that I was astonished by how the score value increased even more with the addition of certain new hyperparameters. The score dropped to 0.57065. which was lower than ever before, an improvement from the prior model. 

### If you were given more time with this dataset, where do you think you would spend more time?
If I had more time, I might think about feature engineering more data columns, such as temperature, ambient temperature, humidity, and others.  

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|eval_metric="root_mean_squared_error"|-|-|1.80836|
|add_features|eval_metric="root_mean_squared_error"|problem_type = "regression"|-|0.63630|
|hpo|eval_metric="root_mean_squared_error"|hyperparameter_tune_kwargs={'scheduler' : 'local','searcher': search_strategy}|hyperparameters={'GBM': gbm_options,'NN': nn_options}|0.56609|
### Create a line plot showing the top model score for the three (or more) training runs during the project.


![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.


![model_test_score.png](img/model_test_score.png)

## Summary
utilizing AutoGluon, a regression model was created utilizing the Kaggle bike sharing demand data. It turns out that feature engineering and hyperparameter tweaking significantly increased the models' performance. 
