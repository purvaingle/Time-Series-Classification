# Time-Series-Classification
An interesting task in machine learning is classification of time series. Here, I have classified the activities of humans based on time series obtained by a Wireless Sensor Network. 

## Dataset used:  
AReM data: https://archive.ics.uci.edu/datasets

## Tasks Performed: 
### Part 1:  Feature Creation/Extraction

1. Minor data cleaning
   
2. Extraction of time-domain features minimum, maximum, mean, median, stan-
dard deviation, first quartile, and third quartile for all of the 6 time series
in each instance.

3. Estimated the standard deviation of each of the time-domain features
extracted from the data. Then, used Python’s bootstrapped or any other
method to build a 90% bootsrap confidence interval for the standard deviation
of each feature.

4. Selected the three most important time-domain features

### Part 2: Binary and Multiclass Classification

(a) Binary Classification Using Logistic Regression
i. Used training set to classify bending from other activities, i.e. a binary classification problem. Depicted scatter plots of the features you specified in 1(c)iv extracted from time series 1, 2, and 6 of each instance, and use color to distinguish bending vs. other activities

ii. Divided each time series in your training set into two (approximately) equal
length time series. Now instead of 6 time series for each of the training
instances, I had 12 time series for each training instance. Repeated 2(a)i, i.e depicted scatter plots of the features extracted from both parts of the time series 1,2, and 6.

iii. I broke each time series in my training set into  l ∈ {1, 2, . . . , 20}  time series of approximately equal length. I used logistic regression to address the binary classification problem, focusing on time-domain features. It's important to note that breaking each time series didn't alter the number of instances; it only changed the number of features for each instance. Afterward, I calculated the p-values for the logistic regression parameters in each model associated with each value of l, and then re-fitted a logistic regression model using the pruned set of features.
Alternatively, I had the option to employ backward selection with tools like sklearn.feature selection. To determine the optimal value for the pair (l,p), where p represents the number of features used in recursive feature elimination, I utilized 5-fold cross-validation. It's crucial to understand the correct and incorrect ways to perform cross-validation in this context.
In case of class imbalance, which could result in some folds lacking any instances of the rare class, I implemented stratified cross-validation. This method ensures that each fold maintains a balanced representation of both classes.





