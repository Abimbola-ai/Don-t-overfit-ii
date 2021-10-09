# Don-t-overfit-ii

This is a solution to the second problem DON'T OVERFIT II, a kaggle competition.

# EDA
The train data set has 250 rows and 302 columns while the test dataset has a shape of (19750, 301).
The following were observed while exploring the train dataset:
* There are hardly any outliers present in the data
* Fraction of dataset contain total number of 0s: 36.0 %
* Fraction of dataset contain total number of 1s: 64.0 %
* The patterns in the targets (0s and 1s) when plotted were not totally seperable which makes harder to predict on the dataset.

# Feature Engineering
Feature engineering was performed on the dataset my creating additional variables using the following:
* mean: mean of the entire columns,
* std: standarad deviation of the entire column,
* mean_sin: mean of the sine,
* mean_cos: mean of the cosine,
* mean_tan: mean of the tangent,
* mean_sinh: mean of the sinh
* mean_cosh: mean of the cosh,
* mean_tanh: mean of the tanh,
* mean_exp: mean of the exponential
* mean_expm1: mean of exp(x)-1
* mean_exp2: mean of 2**x
* mean_x2: mean of x raise to power 2
* mean_x3: mean of x raise to power 3
* mean_x4: mean of x raise to power 4

# Modeling & Results
Models ran on the dataset includes  
+-----------------------------------------------+--------------------------+-------------------+
|                     Model                     |         Features         | LeaderBoard Score |
+-----------------------------------------------+--------------------------+-------------------+
|              Logistic Regression              |    All Data - scaled     |       0.737       |
|    Logistic Regression with hyperparameter    |    All Data - scaled     |       0.848       |
|    Logistic Regression with hyperparameter    | Forward selection-top 10 |       0.832       |
|            Random Forest Classifier           |    All Data - scaled     |       0.662       |
|  Random Forest Classifier with hyperparameter |    All Data - scaled     |       0.734       |
|  Random Forest Classifier with hyperparameter | Forward selection-top 10 |       0.779       |
| Support Vector Classifier with hyperparameter |    All Data - scaled     |       0.756       |
+-----------------------------------------------+--------------------------+-------------------+

+----------------------------------------------+-----------------------------+-------------------+
|                    Model                     |           Features          | LeaderBoard Score |
+----------------------------------------------+-----------------------------+-------------------+
|             Logistic Regression              | Feature Engineered - scaled |       0.738       |
|   Logistic Regression with hyperparameter    | Feature Engineered - scaled |       0.848       |
|           Random Forest Classifier           | Feature Engineered - scaled |       0.662       |
| Random Forest Classifier with hyperparameter | Feature Engineered - scaled |       0.734       |
+----------------------------------------------+-----------------------------+-------------------+

# Conclusion
Logistic regression model is known to perform better when the number of noise variables is less than or equal to the number of explanatory vaibles and Random Foresthas a higher true and false positive rateas the number of explanatory variables increase in the dataset. 

Random Forest is also said to be more accuracy focused and it performs better with more categorical data than numeric while logistic regression on the hand is a little confusing when it comes to categorical data. If the dataset has more categorical data and consists of outliers, it is better to use a Random Forest classification model.

# Aknowledgements
Many thanks to Sahil's article on medium for breaking the problem into more understandable parts