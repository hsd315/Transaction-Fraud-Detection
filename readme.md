## Goal:
To create explainable model and generate business insights to predict fraud transactions in the future. The data is private, so cannot be shared.

## Feature Engineering 

### Some important features that has high correlation with fraud found: 
account age, the venue name is not posted, no social media information posted, certain type of payouts, transaction channels, the organization names are all in lower case or all cap, no previous payouts. 

Those features are selected after EDA from about 50+ features

## Modeling:
We started with logistic regression with only there features as a benchmark and use f1 score first as the metrics for evaluating model performance. We used cross validation to measure model performance and adding feature one after anonther to see whether there is a great boost in f1 score. We decided to use 6 features. Then we used those features to train on a random forest model and achieve a much better result. We used grid search to find the best parameters of 100 estimators and max depth of 5. We also compared with xgboost and SVM, but those models did not perform better. 

Thinking deeply about the business problem, we actually decided to design our own cost matrix in replace of f1 score since f1 score weighs the fp and fn error in the same scale. We decided that false negative should at least be penalized 10x greateer than false positive. But real ratio can be decided by people with more domain expertise.

## Web Application:
We then store the prediction in a mongodb and then publish in a web app 
