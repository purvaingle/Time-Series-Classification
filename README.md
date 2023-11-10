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

1. Used training set to classify bending from other activities, i.e. a binary classification problem. Depicted scatter plots of the features you specified in 1(c)iv extracted from time series 1, 2, and 6 of each instance, and use color to distinguish bending vs. other activities

2. Divided each time series in your training set into two (approximately) equal
length time series. Now instead of 6 time series for each of the training
instances, I had 12 time series for each training instance. Repeated 2(a)i, i.e depicted scatter plots of the features extracted from both parts of the time series 1,2, and 6.

3. I broke each time series in my training set into  l ∈ {1, 2, . . . , 20}  time series of approximately equal length. I used logistic regression to address the binary classification problem, focusing on time-domain features. It's important to note that breaking each time series didn't alter the number of instances; it only changed the number of features for each instance. Afterward, I calculated the p-values for the logistic regression parameters in each model associated with each value of l, and then re-fitted a logistic regression model using the pruned set of features.
   
Alternatively, I had the option to employ backward selection with tools like sklearn.feature selection. To determine the optimal value for the pair (l,p), where p represents the number of features used in recursive feature elimination, I utilized 5-fold cross-validation. It's crucial to understand the correct and incorrect ways to perform cross-validation in this context.

In case of class imbalance, which could result in some folds lacking any instances of the rare class, I implemented stratified cross-validation. This method ensures that each fold maintains a balanced representation of both classes.

4. I reported the confusion matrix and displayed the ROC curve along with the AUC score for my classifier on the training data. Additionally, I provided the parameters (\( \beta_i \)'s) of my logistic regression model, along with the associated p-values.

5. Next, I tested the classifier on the test set, making sure to break the time series in the test set into the same number of segments as I did in the training set. I used the features extracted from the test set for this evaluation. I compared the accuracy on the test set with the cross-validation accuracy I obtained earlier.

6. Upon examination, it appeared that the classes were well-separated, potentially leading to some instability in calculating the logistic regression parameters.

7. Upon inspecting the confusion matrices, I noticed imbalanced classes. In response, I built a logistic regression model based on case-control sampling and adjusted its parameters accordingly. I then reported the confusion matrix, ROC curve, and AUC score of the model.

(b) Binary Classification Using L1-penalized logistic regression:

1. I repeated 2(a)(3) using L1-penalized logistic regression. This involved replacing the use of p-values for variable selection with L1 regularization. I had to cross-validate for both (l), the number of time series into which I broke each of my instances, and (lambda), the weight of the L1 penalty in the logistic regression objective function (or C, the budget).

2. Compared the L1-penalized with variable selection using p-values.

3. To find the best l for building an L1-penalized multinomial regression model to classify all activities in the training set, I followed the same procedure as in 2(b)(1). After obtaining the best l, I reported the test error. 

4. I repeated 2(c)(1) using a Naïve Bayes' classifier, employing both Gaussian and Multinomial priors. I then compared the results obtained with each type of prior.

5. To determine which method is better for multi-class classification in this problem, I assessed the performance metrics, such as accuracy, precision, recall, and F1-score, for both the L1-penalized multinomial regression model and the Naïve Bayes' classifier with both Gaussian and Multinomial priors. Based on these metrics, I concluded which method provided better classification results for the specific problem at hand.





