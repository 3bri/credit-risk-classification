# credit-risk-classification

Brian Guenther

The purpose of this analysis is to build and evaluate two Logistic Regression model approaches for identifying and predicting the creditworthiness of borrowers.  

This data set utilized was composed of over 77,000 entries and included the following information:  loan_size, interest_rate, borrower_income, debt_to_income, num_of_accounts, derogatory_marks, total_debt, and loan_status.  A loan status of zero indicated a healthy loan, whereas a value of one indicated a high risk of default.  Loan status is our dependent variable, so this information was separated from the independent variables.  The balance of the target values (loan status) was displayed and consisted of 75,036 healthy and 2500 high-risk.  This was done to identify if the data was skewed or not and indicated that the data was imbalanced.  This is a concern since the output may be biased to the class which has a higher number of examples (healthy loans).  This is a problem since identification of the minority result (high risk loans) is the desired outcome.

The data was then split 70:30 into training and test data sets.  A logistic regression model was built and fit to the training data set.  This model was then run on the test data set and the predictive powers of the model were assessed with an accuracy score, confusion matrix, and a classification report.  To evaluate the bias created by the skewed original data set, the random oversampling function was run on the training data set.  Using the “sampling_strategy=’minority’” setting, the high risk loan data points are randomly selected, copied, and added until the number of input rows is equal to that of the majority class.  This oversampled generation was confirmed by a value_count after running the random oversampling function.  The logistic regression model was then fit to the oversampled data set.  The predictive powers of the model after training on the oversampled data were then also assessed with an accuracy score, confusion matrix, and a classification report.  

The results for the two models are as follows:
                For original data logistic regression	    For oversampled data logistic regression
Balanced accuracy score: 	      0.944					                  0.996
True Positives:			            18679					                  18668
False Positives:			          67					                    2
False Negatives:		            80					                    91
True Negatives:			            558					                    623
Precision for class 0:		      1.00					                  1.00
Precision for class 1:		      0.87					                  0.87
Recall for class 0:		          1.00					                  1.00
Recall for class 1: 		        0.89					                  1.00

Accuracy is a measure of the fraction of predictions that were correct.  Balanced accuracy measures this value within each class and then averages the result.  Recall represents the ability to correctly identify all positive occurrences.  Precision represents the ability to not label a positive result as a negative.

Summary of the results:
The large sample size of class 0 dominated the accuracy calculation for the model as well as the precision and recall values for class 0.  However, the bank was desiring to identify high risk loans, so metrics indicative of class 1 were most important for evaluating the two models.  There is a clear difference between training the logistic regression model on the original data and the oversampled data in this regard.  Training on the original data resulted in 67 false positives (high risk loans that were identified as healthy loans) and 80 false negatives (healthy loans that were identified as high risk).   Training on the oversampled data resulted in 2 false positives (high risk loans that were identified as healthy loans) and 91 false negatives (healthy loans that were identified as high risk).  Using the oversampled data to train the logistic regression identified 65 more high risk loans than training on the original data.  This benefit is slightly offset by the addition of 11 healthy loans being incorrectly identified as high risk.  This difference is also captured in the change in recall value for class 1 in the classification report.  

I would recommend using the oversampled data to train the logistic regression predictive model to the bank.  The goal is to identify high risk loans.  The oversampled model correctly identifies 99.7% of these, whereas the original data model only identifies 89.3% of the high risk loans.  

Aid in this project:
Other than the class activities, I found the following blog post by Jason Brownlee to be very helpful.  
https://machinelearningmastery.com/random-oversampling-and-undersampling-for-imbalanced-classification/  
Additionally, time with tutor Matthew Werth was very helpful for clarification of principles underlying this project.
