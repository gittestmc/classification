# Module 17 Practical Application. Comparing Classifers

### Please note : all the code is in prompt_III.ipynb . also notebook is exported to prompt_III.pdf. if any trouble in viewing please use PDF to view.


 In this practical application, the goal is to compare the performance of the classifiers, namely K Nearest Neighbor, Logistic Regression, Decision Trees, and <br /> Support Vector Machines. A dataset related to marketing bank products over the telephone was used. <br />
 
 The provided dataset contains information on 411K results of marketing campaign and the goal is to help provide features that will help the client a bank improve their efficency of markerting campaigns. This is to done by building an accurate model <br />

The data set had 21 columns of which 10 were numerical and rest categorical. <br />
<p>&nbsp;</p>

#### Accuracy metric used for this analysis <br />
As the data was imbalanced , area under the roc_curve was used as a metric for comparing the different models. High AUC for ROC curve <br />
implies both high TPR and low FPR which is what is needed with the imbalanced classification case. All models were checked with probabilites as a measure as<br />
as the thresholds may be changed to impact the predictions.

Analysis was done in two parts:<br />
a)Part 1: using columns 1-7 <br />
b)Part2: using all columns <br />


#### Part 1: 
Following 7 columns were used:
'age', 'job', 'marital', 'education', 'default', 'housing', 'loan' <br />
Age was the only numerical columnn - all others were categorical data <br />
Following methodology was used for analyzing the data: <br />
1)All the categorcial data was split into two buckets per whether they were giving above or below mean subscribers. <br />
2)Age was used as numerical column without an processing <br />
Models :
Five models were ran and ran their default settings. They were Naive-Bayes,Logistic Regression,KNN,Decision Tree and Support Vector Machine.<br />
                                   
Results:.<br />
1)In terms of AUC terms,Logistic regression was the only model performing better than the baseline Naive bayes model<br />
 2)In prediction terms SVM was doing the best as it give 42% accuracy for class 1<br />


#### Part2: Improving the model <br />

All columns in the dataset were used. Remaining Categorical columns were  grouped into two buckets for the purpose of analysis. <br />
The reduction in number of categories was done to reduce the curse of dimensionality <br />
Numerical column Age - was Sliced into 5 buckets and as was seen from a bar plot that age group below 20 years and greater than 60 years have a higher mean than other age groups so were grouped togehter<br />

Models
Six Different models were ran with grid serach to find the optimal parameter. Other aspects are given below <br /> 

1)One model was run for Logistic Regression with columns checked and addressed for multicollinearity. Logisitic regression gets impacted by mulitcollinearity so this model was run to check the impact of multicollinearity<br />
2)Another Logistic Regression model with Grid search and regularization for multicollinearity was run( no external checking and column removal done for multicollinearity was done for this model) <br />
3)KNN mode with  no external checking and column removal done for multicollinearity. As expected KNN model took the longest to run.<br />
4)Decision Tree model. Decision Tree models are not impacted by mulicollinearity)<br />
5)Support Vector Machine model. Again SVM is not impacted by mulicollinearity. Had to run HalvingGridSearchCV as normal grid searches were running for ever. <br />
6)Finally a Logistic Regression mode with SMOTE was run to check on the effectiveness of minoritty oversampling. <br />


Following plots were used to shown results: <br />
1)PLot -1: ROC curve-AUC to compare the models performance against baseline NB Model and absolute baseline<br />
2)PLot -2 : AUC using SKLPT to show the macro and micro AUC for different classes <br />
3)Plot-3 : Confusion Matrix- for test data<br />
4)Plot-4:Classification report showing all major metrics (f1,precision,recall, accuracy)<br />
5)Plot 5: Lift curve showing the deciles to be used by marketing to decide how many contacts to make and compare with other models<br />
6)Coefficients on a horizontal plot showing feature importances (this was done only on logistic regression models)<br />
7)Variability of coefficients using K-fold cross validation(this was done only on regression model)<br />
8) Variability of model coefficients using permuation feature <br />

Following were the observations:
1)Features to assist marketing with an efficient contact were got out of only Logistic Regression and not others. SVM support features only with linear Kernel, KNN does not have any functionality as such while Random forrest gives feature importance but was not used here.<br />
2)Important features were( these were selected per their absolute values)<br />
a)duration
b) month
c)nr.employed
d)ontact_cellular
e)emp.var.rate
3) In case coefficients vary significantly when changing the input dataset their robustness <br />
is not guaranteed, and they should probably be interpreted with caution and so a variability test was also done to show the variability among feature <br />
 coefficients<br />
4) All models gave a >0.9 AUC with test data but with much shorter running time and ease to take out features logistic regression come out to top for this dataset.
A summary dataframe and plots are shown at the end which will provide a good snapshot of performance  <br />

                            
                                   
                                   
                                   
