# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Capstone: Loan Default Prediction

## Overview

- The main objective of this project is to predict whether a loan will be defaulted in the period of repayment by a company. 

## Problem Statement

- This project aims to develop a classification model to identify whether a loan will be defaulted during the tenor of the loan repayment by a company. 
-----

## About the Data

- Real loan information is extracted from a company that offers SME financing across Southeast Asia. 
- For confidentiality reasons, the company are not revealed. 
- Company names are masked with unique identifiers and additional information was limited. 
- Singapore Standard Industrial Classification are used to identify the companies industry. 
- Loan information consisted of product types, amount, insurance, date, tenor period, status, and delinquency of payments.
- Data imbalance existed where the target value only made up 16% of the data set. 

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/imbalance.png)

## Data Preparation

- Null values in the data set were removed or filled using external data collected through web scraping.
- Date values were reconfigured into individual features into Weekday | Day | Month | Year
- Imbalance issue was resolved using over sampling, under sampling, and a mix of both over & under sampling.


## Key Features
 - SSIC
 - Product
 - Weekday
 - Day
 - Month
 - Year
 - Tenor
 - Interest Rate
 - Loan Amount
 - Disbursal Amount
 - Monthly Payment Amount
 - Payment Amount
 - Insured
 - Defaulted

------

## Modelling & Evaluation
 
--------
## Logistic Regression
     
| -  | Score |
| ------------- | ------------- |
| Training  | 0.363  |
| Test  | 0.367  |
| Specificity  | 0.255  |
| Precision  | 0.200  |
| Recall  | 0.925  |
| Accuracy  | 0.367  |
| F1  | 0.328  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/lr_1_roc.png)
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/lr_1.png)      

| Baseline  | 0.50 |
| ------------- | ------------- |
| ROC AUC  | 0.621  |

-----------
## Logistic Regression with Over-sampling     
| -  | Score |
| ------------- | ------------- |
| Training  | 0.595  |
| Test  | 0.598  |
| Specificity  | 0.280  |
| Precision  | 0.556  |
| Recall  | 0.923  |
| Accuracy  | 0.598  |
| F1  | 0.694  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/lr_2_roc.png)
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/lr_2.png)     

| Baseline  | 0.50  |
| ------------- | ------------- |
| ROC AUC  | 0.640  |
------------
## Logistic Regression with Under-sampling     
| -  | Score |
| ------------- | ------------- |
| Training  | 0.597  |
| Test  | 0.585  |
| Specificity  | 0.286  |
| Precision  | 0.545  |
| Recall  | 0.901  |
| Accuracy  | 0.585  |
| F1  | 0.679  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/lr_3_roc.png)
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/lr_3.png)     

| Baseline  | 0.50  |
| ------------- | ------------- |
| ROC AUC  | 0.620  |
------------
## Logistic Regression with Mixed-sampling
| -  | Score |
| ------------- | ------------- |
| Training  | 0.594  |
| Test  | 0.599  |
| Specificity  | 0.269  |
| Precision  | 0.561  |
| Recall  | 0.926  |
| Accuracy  | 0.599  |
| F1  | 0.698  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/lr_4_roc.png)
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/lr_4.png)     

| Baseline  | 0.50  |
| ------------- | ------------- |
| ROC AUC  | 0.625  |
------------

## DecisionTreeClassifier
| -  | Score |
| ------------- | ------------- |
| Training  | 0.594  |
| Test  | 0.599  |
| Specificity  | 0.269  |
| Precision  | 0.561  |
| Recall  | 0.926  |
| Accuracy  | 0.599  |
| F1  | 0.698  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/lr_4_roc.png)
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/lr_4.png)     

| Baseline  | 0.50  |
| ------------- | ------------- |
| ROC AUC  | 0.625  |
------------










--------
**AdaBoostClassifier**   

**Best Score:** 0.825     
**Best Paramters:** 'base_estimator__max_depth': 7, 'learning_rate': 0.9, 'n_estimators': 100   

**Training Score:** 0.894   
**Test Score:**     0.824   

**Specificity:**     0.945  
**Precision:**       0.644   
**Recall:**          0.369  
**Accuracy Score:**  0.824   
**F1:**              0.469     

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/ada_matrix.png)

--------
- GradientBoostingClassifier
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/gb_matrix.png)

--------
**VotingClassifier**

The VotingClassifer used DecisionTreeClassifier(), AdaBoostClassifier(), GradientBoostingClassifer() and used a GridSearchCV() to find the best score and parameters. 
The scores were good and slightly overfitted, but failed to predict the attended target. 

**Best Score:** 0.814    
**Best Paramters:** 'ada__n_estimators': 175, 'gb__n_estimators': 200, 'tree__max_depth': None

**Training Score:** 0.851   
**Test Score:**     0.819   

**Specificity:**     0.965  
**Precision:**       0.678   
**Recall:**          0.273   
**Accuracy Score:**  0.819   
**F1:**              0.39    

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/vc_matrix.png)
 -------
 
 ### Future Improvements
 
- Extracting additional information on the companies such as their annual financial reports, credit information from ACRA & BRC reports. 
- Further model explorations with RandomForests, XGBoost. 
- Implement model into a web application, and connect the results into a dashboard for visualizations. 
