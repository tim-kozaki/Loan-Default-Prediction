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
| Training  | 0.786  |
| Test  | 0.751  |
| Specificity  | 0.752  |
| Precision  | 0.376  |
| Recall  | 0.745  |
| Accuracy  | 0.751  |
| F1  | 0.500  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_1_roc.png)
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_1.png)     

| Baseline  | 0.50  |
| ------------- | ------------- |
| ROC AUC  | 0.819  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_1_nodes.png)        
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_1_auc_roc.png)     
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_1_tree.png)     

<details><summary>DecisionTree Details</summary>
<p>|--- Tenor <= 5.50      
<p>|   |--- Year <= 2021.50        
<p>|   |   |--- Interest Rate <= 0.53        
<p>|   |   |   |--- Interest Rate <= 0.47        
<p>|   |   |   |   |--- Insured <= 0.50        
<p>|   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |--- Insured >  0.50        
<p>|   |   |   |   |   |--- Year <= 2019.50        
<p>|   |   |   |   |   |   |--- Month <= 6.50        
<p>|   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |--- Month >  6.50        
<p>|   |   |   |   |   |   |   |--- Disbursal Amount <= 1845.05        
<p>|   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |--- Disbursal Amount >  1845.05        
<p>|   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |--- Year >  2019.50        
<p>|   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |--- Interest Rate >  0.47        
<p>|   |   |   |   |--- Day <= 22.50        
<p>|   |   |   |   |   |--- Payment Amount <= 26650.00        
<p>|   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |--- Payment Amount >  26650.00        
<p>|   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |--- Day >  22.50        
<p>|   |   |   |   |   |--- class: 0        
<p>|   |   |--- Interest Rate >  0.53        
<p>|   |   |   |--- Year <= 2020.50        
<p>|   |   |   |   |--- Tenor <= 4.50        
<p>|   |   |   |   |   |--- Tenor <= 3.50        
<p>|   |   |   |   |   |   |--- Interest Rate <= 1.11        
<p>|   |   |   |   |   |   |   |--- Disbursal Amount <= 6356.48        
<p>|   |   |   |   |   |   |   |   |--- Month <= 4.50        
<p>|   |   |   |   |   |   |   |   |   |--- Amount <= 1550.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |--- Amount >  1550.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 4.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  4.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |--- Month >  4.50        
<p>|   |   |   |   |   |   |   |   |   |--- Product <= 4.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 2.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3        
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  2.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 7        
<p>|   |   |   |   |   |   |   |   |   |--- Product >  4.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |--- Disbursal Amount >  6356.48        
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 45105.50        
<p>|   |   |   |   |   |   |   |   |   |--- Year <= 2017.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 16.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  16.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |--- Year >  2017.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 6.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6        
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  6.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4        
<p>|   |   |   |   |   |   |   |   |--- SSIC >  45105.50        
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate <= 0.69                
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 21.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  21.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate >  0.69        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 18.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  18.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3        
<p>|   |   |   |   |   |   |--- Interest Rate >  1.11        
<p>|   |   |   |   |   |   |   |--- Product <= 2.50        
<p>|   |   |   |   |   |   |   |   |--- Interest Rate <= 1.45        
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.32        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 31509.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  31509.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6        
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.32        
<p>|   |   |   |   |   |   |   |   |   |   |--- Insured <= 0.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4        
<p>|   |   |   |   |   |   |   |   |   |   |--- Insured >  0.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3        
<p>|   |   |   |   |   |   |   |   |--- Interest Rate >  1.45        
<p>|   |   |   |   |   |   |   |   |   |--- Payment Amount <= 1470.35        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 16.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  16.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |--- Payment Amount >  1470.35        
<p>|   |   |   |   |   |   |   |   |   |   |--- Year <= 2019.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 11                
<p>|   |   |   |   |   |   |   |   |   |   |--- Year >  2019.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6        
<p>|   |   |   |   |   |   |   |--- Product >  2.50        
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 17209.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |--- SSIC >  17209.50        
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 6.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 29.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 7        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  29.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  6.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |--- Tenor >  3.50        
<p>|   |   |   |   |   |   |--- SSIC <= 79658.00        
<p>|   |   |   |   |   |   |   |--- Interest Rate <= 1.27        
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 45226.50        
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 3.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 2.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  2.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  3.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 3.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4        
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  3.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3        
<p>|   |   |   |   |   |   |   |   |--- SSIC >  45226.50        
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 6.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 74617.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  74617.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |--- Month >  6.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |--- Interest Rate >  1.27        
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 54459.50        
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.77        
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 35515.87        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3        
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  35515.87        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.77        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |--- SSIC >  54459.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |--- SSIC >  79658.00        
<p>|   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |--- Tenor >  4.50        
<p>|   |   |   |   |   |--- Interest Rate <= 0.65        
<p>|   |   |   |   |   |   |--- Month <= 8.50        
<p>|   |   |   |   |   |   |   |--- SSIC <= 29204.50        
<p>|   |   |   |   |   |   |   |   |--- Month <= 6.50        
<p>|   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 20175.80        
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 5.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  5.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  20175.80        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |--- Month >  6.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |--- SSIC >  29204.50        
<p>|   |   |   |   |   |   |   |   |--- Month <= 2.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |--- Month >  2.50        
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 12.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 4.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  4.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |--- Day >  12.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount <= 42450.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4        
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount >  42450.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |--- Month >  8.50                
<p>|   |   |   |   |   |   |   |--- Weekday <= 3.50        
<p>|   |   |   |   |   |   |   |   |--- Month <= 9.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |--- Month >  9.50        
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 11.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 11960.04        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  11960.04        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |--- Month >  11.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |--- Weekday >  3.50        
<p>|   |   |   |   |   |   |   |   |--- Day <= 19.50        
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 5.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  5.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |--- Day >  19.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |--- Interest Rate >  0.65        
<p>|   |   |   |   |   |   |--- SSIC <= 79658.00        
<p>|   |   |   |   |   |   |   |--- Payment Amount <= 5117.08        
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 76148.50        
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 11.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 2.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 11        
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  2.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 12        
<p>|   |   |   |   |   |   |   |   |   |--- Month >  11.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 35555.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  35555.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |--- SSIC >  76148.50                
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 5.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |--- Month >  5.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 2528.17        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  2528.17        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |--- Payment Amount >  5117.08        
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 28207.00        
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 26512.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 27897.72        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4        
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  27897.72        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  26512.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 9739.95        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  9739.95        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5        
<p>|   |   |   |   |   |   |   |   |--- SSIC >  28207.00        
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 29205.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 16.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  16.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3        
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  29205.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 71127.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 18        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  71127.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5        
<p>|   |   |   |   |   |   |--- SSIC >  79658.00        
<p>|   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |--- Year >  2020.50        
<p>|   |   |   |   |--- Month <= 11.50        
<p>|   |   |   |   |   |--- SSIC <= 30556.50        
<p>|   |   |   |   |   |   |--- Interest Rate <= 0.65        
<p>|   |   |   |   |   |   |   |--- Day <= 25.50        
<p>|   |   |   |   |   |   |   |   |--- Month <= 3.50        
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 19.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 0.57        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  0.57        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |--- Day >  19.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |--- Month >  3.50        
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 9.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 8.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4        
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  8.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |--- Month >  9.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 0.56        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  0.56        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |--- Day >  25.50        
<p>|   |   |   |   |   |   |   |   |--- Month <= 8.50        
<p>|   |   |   |   |   |   |   |   |   |--- Amount <= 5650.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |--- Amount >  5650.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 29204.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  29204.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |--- Month >  8.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |--- Interest Rate >  0.65        
<p>|   |   |   |   |   |   |   |--- Product <= 2.50        
<p>|   |   |   |   |   |   |   |   |--- Day <= 24.50        
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 28206.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.62        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.62        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  28206.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 7.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5        
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  7.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |--- Day >  24.50        
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 4.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 37024.19        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  37024.19        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |--- Month >  4.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.77        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4        
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.77        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |--- Product >  2.50        
<p>|   |   |   |   |   |   |   |   |--- Interest Rate <= 0.90        
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 12.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 1.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  1.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 8        
<p>|   |   |   |   |   |   |   |   |   |--- Day >  12.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 5348.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 9        
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  5348.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 10        
<p>|   |   |   |   |   |   |   |   |--- Interest Rate >  0.90        
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.62        
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 9199.94        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  9199.94        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.62        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |--- SSIC >  30556.50        
<p>|   |   |   |   |   |   |--- Interest Rate <= 1.05        
<p>|   |   |   |   |   |   |   |--- SSIC <= 57156.00        
<p>|   |   |   |   |   |   |   |   |--- Month <= 1.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |--- Month >  1.50        
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 43605.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 10.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  10.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5        
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  43605.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 17931.23        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  17931.23        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3        
<p>|   |   |   |   |   |   |   |--- SSIC >  57156.00        
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 79658.00        
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 8.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 27.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  27.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |--- Month >  8.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 21.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3                
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  21.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |--- SSIC >  79658.00        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |--- Interest Rate >  1.05        
<p>|   |   |   |   |   |   |   |--- SSIC <= 46759.50        
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 45105.50        
<p>|   |   |   |   |   |   |   |   |   |--- Tenor <= 3.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 86106.89        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  86106.89        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |--- Tenor >  3.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount <= 76300.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount >  76300.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |--- SSIC >  45105.50        
<p>|   |   |   |   |   |   |   |   |   |--- Payment Amount <= 42498.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount <= 2650.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount >  2650.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |--- Payment Amount >  42498.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |--- SSIC >  46759.50        
<p>|   |   |   |   |   |   |   |   |--- Month <= 8.50        
<p>|   |   |   |   |   |   |   |   |   |--- Payment Amount <= 5383.05        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |--- Payment Amount >  5383.05        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 70201.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  70201.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3        
<p>|   |   |   |   |   |   |   |   |--- Month >  8.50        
<p>|   |   |   |   |   |   |   |   |   |--- Amount <= 10350.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 8.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  8.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |   |   |--- Amount >  10350.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- Tenor <= 3.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |   |--- Tenor >  3.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |--- Month >  11.50        
<p>|   |   |   |   |   |--- Day <= 5.50        
<p>|   |   |   |   |   |   |--- Product <= 2.50        
<p>|   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |--- Product >  2.50        
<p>|   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |--- Day >  5.50        
<p>|   |   |   |   |   |   |--- class: 0        
<p>|   |--- Year >  2021.50        
<p>|   |   |--- class: 0        
<p>|--- Tenor >  5.50        
<p>|   |--- Year <= 2021.50        
<p>|   |   |--- Tenor <= 10.50        
<p>|   |   |   |--- Payment Amount <= 14297.44        
<p>|   |   |   |   |--- Year <= 2019.50        
<p>|   |   |   |   |   |--- SSIC <= 63200.50        
<p>|   |   |   |   |   |   |--- Weekday <= 3.50        
<p>|   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |--- Weekday >  3.50        
<p>|   |   |   |   |   |   |   |--- Weekday <= 5.50        
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 45004.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |--- SSIC >  45004.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |--- Weekday >  5.50        
<p>|   |   |   |   |   |   |   |   |--- Payment Amount <= 5423.77        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |--- Payment Amount >  5423.77        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |--- SSIC >  63200.50        
<p>|   |   |   |   |   |   |--- Day <= 16.50        
<p>|   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |--- Day >  16.50        
<p>|   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |--- Year >  2019.50        
<p>|   |   |   |   |   |--- Disbursal Amount <= 28876.50        
<p>|   |   |   |   |   |   |--- Weekday <= 4.50        
<p>|   |   |   |   |   |   |   |--- Payment Amount <= 3615.85        
<p>|   |   |   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |   |   |--- Payment Amount >  3615.85        
<p>|   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |--- Weekday >  4.50        
<p>|   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |--- Disbursal Amount >  28876.50        
<p>|   |   |   |   |   |   |--- Month <= 5.50        
<p>|   |   |   |   |   |   |   |--- Disbursal Amount <= 38502.00        
<p>|   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |--- Disbursal Amount >  38502.00        
<p>|   |   |   |   |   |   |   |   |--- Day <= 18.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |--- Day >  18.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |--- Month >  5.50                
<p>|   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |--- Payment Amount >  14297.44        
<p>|   |   |   |   |--- Weekday <= 4.50        
<p>|   |   |   |   |   |--- Year <= 2018.50        
<p>|   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |   |--- Year >  2018.50        
<p>|   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |--- Weekday >  4.50        
<p>|   |   |   |   |   |--- Weekday <= 6.50        
<p>|   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |--- Weekday >  6.50        
<p>|   |   |   |   |   |   |--- class: 0        
<p>|   |   |--- Tenor >  10.50        
<p>|   |   |   |--- Payment Amount <= 9392.33        
<p>|   |   |   |   |--- Disbursal Amount <= 98395.00        
<p>|   |   |   |   |   |--- Interest Rate <= 1.88        
<p>|   |   |   |   |   |   |--- Disbursal Amount <= 47592.50        
<p>|   |   |   |   |   |   |   |--- SSIC <= 56651.00        
<p>|   |   |   |   |   |   |   |   |--- Disbursal Amount <= 18079.80        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |--- Disbursal Amount >  18079.80        
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 3.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 43561.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  43561.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  3.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount <= 27500.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount >  27500.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |--- SSIC >  56651.00        
<p>|   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |--- Disbursal Amount >  47592.50        
<p>|   |   |   |   |   |   |   |--- Payment Amount <= 4548.46        
<p>|   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |--- Payment Amount >  4548.46        
<p>|   |   |   |   |   |   |   |   |--- Month <= 10.50        
<p>|   |   |   |   |   |   |   |   |   |--- Year <= 2020.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |--- Year >  2020.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |--- Month >  10.50        
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 23.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 35555.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  35555.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |--- Day >  23.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 11.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  11.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |--- Interest Rate >  1.88        
<p>|   |   |   |   |   |   |--- Month <= 1.50        
<p>|   |   |   |   |   |   |   |--- Day <= 13.50        
<p>|   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |--- Day >  13.50        
<p>|   |   |   |   |   |   |   |   |--- Year <= 2020.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |--- Year >  2020.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |--- Month >  1.50        
<p>|   |   |   |   |   |   |   |--- Payment Amount <= 3298.74        
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 46493.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |--- SSIC >  46493.50        
<p>|   |   |   |   |   |   |   |   |   |--- Year <= 2019.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 2.12        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  2.12        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |--- Year >  2019.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 23.00                
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4        
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  23.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |--- Payment Amount >  3298.74        
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 47526.50        
<p>|   |   |   |   |   |   |   |   |   |--- Amount <= 49883.79        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |--- Amount >  49883.79        
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 3.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3        
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  3.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6        
<p>|   |   |   |   |   |   |   |   |--- SSIC >  47526.50        
<p>|   |   |   |   |   |   |   |   |   |--- Amount <= 92000.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |--- Amount >  92000.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |--- Disbursal Amount >  98395.00        
<p>|   |   |   |   |   |--- Month <= 9.50        
<p>|   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |--- Month >  9.50        
<p>|   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |--- Payment Amount >  9392.33        
<p>|   |   |   |   |--- Payment Amount <= 9586.31        
<p>|   |   |   |   |   |--- Month <= 10.50        
<p>|   |   |   |   |   |   |--- Disbursal Amount <= 95185.00        
<p>|   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |--- Disbursal Amount >  95185.00        
<p>|   |   |   |   |   |   |   |--- Weekday <= 4.50        
<p>|   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |--- Weekday >  4.50        
<p>|   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |--- Month >  10.50        
<p>|   |   |   |   |   |   |--- class: 1        
<p>|   |   |   |   |--- Payment Amount >  9586.31        
<p>|   |   |   |   |   |--- Year <= 2016.50        
<p>|   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |--- Year >  2016.50        
<p>|   |   |   |   |   |   |--- Interest Rate <= 1.38        
<p>|   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |--- Interest Rate >  1.38        
<p>|   |   |   |   |   |   |   |--- Day <= 8.50        
<p>|   |   |   |   |   |   |   |   |--- Year <= 2018.50        
<p>|   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |--- Year >  2018.50        
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 7.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 4.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  4.50        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |--- Month >  7.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |--- Day >  8.50        
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 47421.00        
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 46492.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 44858.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4        
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  44858.00        
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  46492.00        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |--- SSIC >  47421.00      
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 8.50      
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 2.50       
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  2.50       
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2        
<p>|   |   |   |   |   |   |   |   |   |--- Month >  8.50        
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0        
<p>|   |--- Year >  2021.50         
<p>|   |   |--- class: 0       
</details>

------------      

## DecisionTreeClassifier with Over-sampling    

| -  | Score |
| ------------- | ------------- |
| Training  | 0.856  |
| Test  | 0.817  |
| Specificity  | 0.785  |
| Precision  | 0.794  |
| Recall  | 0.850  |
| Accuracy  | 0.817  |
| F1  | 0.821  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_2_roc.png)
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_2.png)     

| Baseline  | 0.50  |
| ------------- | ------------- |
| ROC AUC  | 0.907  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_2_nodes.png)        
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_2_auc_roc.png)     
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_2_tree.png)     

<details><summary>DecisionTree Details</summary>
<p>|--- Tenor <= 5.50
<p>|   |--- Year <= 2021.50
<p>|   |   |--- Interest Rate <= 0.53
<p>|   |   |   |--- Year <= 2019.50
<p>|   |   |   |   |--- Month <= 6.50
<p>|   |   |   |   |   |--- SSIC <= 33503.00
<p>|   |   |   |   |   |   |--- Day <= 29.00
<p>|   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |--- Day >  29.00
<p>|   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |--- SSIC >  33503.00
<p>|   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- Month >  6.50
<p>|   |   |   |   |   |--- Interest Rate <= 0.45
<p>|   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Interest Rate >  0.45
<p>|   |   |   |   |   |   |--- class: 0
<p>|   |   |   |--- Year >  2019.50
<p>|   |   |   |   |--- Insured <= 0.50
<p>|   |   |   |   |   |--- Month <= 3.50
<p>|   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |--- Month >  3.50
<p>|   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- Insured >  0.50
<p>|   |   |   |   |   |--- Interest Rate <= 0.48
<p>|   |   |   |   |   |   |--- Month <= 1.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Month >  1.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Interest Rate >  0.48
<p>|   |   |   |   |   |   |--- Month <= 8.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Month >  8.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |--- Interest Rate >  0.53
<p>|   |   |   |--- Year <= 2020.50
<p>|   |   |   |   |--- Tenor <= 4.50
<p>|   |   |   |   |   |--- Tenor <= 3.50
<p>|   |   |   |   |   |   |--- Interest Rate <= 1.11
<p>|   |   |   |   |   |   |   |--- Payment Amount <= 6447.04
<p>|   |   |   |   |   |   |   |   |--- Insured <= 0.50
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate <= 0.76
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 1780.74
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  1780.74
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate >  0.76
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 11.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  11.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Insured >  0.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 7.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 55620.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  55620.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Month >  7.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 3.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  3.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |--- Payment Amount >  6447.04
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 45105.50
<p>|   |   |   |   |   |   |   |   |   |--- Year <= 2017.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Tenor <= 1.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Tenor >  1.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Year >  2017.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 6.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  6.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 7
<p>|   |   |   |   |   |   |   |   |--- SSIC >  45105.50
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate <= 0.69
<p>|   |   |   |   |   |   |   |   |   |   |--- Year <= 2018.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Year >  2018.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate >  0.69
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 15.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  15.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |--- Interest Rate >  1.11
<p>|   |   |   |   |   |   |   |--- SSIC <= 10410.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- SSIC >  10410.50
<p>|   |   |   |   |   |   |   |   |--- Product <= 2.50
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.45
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.32
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 9
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.32
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.45
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 46780.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 13
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  46780.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 12
<p>|   |   |   |   |   |   |   |   |--- Product >  2.50
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 6.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Tenor <= 2.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- Tenor >  2.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 12
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  6.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Tenor >  3.50
<p>|   |   |   |   |   |   |--- Interest Rate <= 1.35
<p>|   |   |   |   |   |   |   |--- SSIC <= 79658.00
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 45226.50
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 4.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  4.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 3.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 10
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  3.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 7
<p>|   |   |   |   |   |   |   |   |--- SSIC >  45226.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 6.00
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 61710.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  61710.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |--- Month >  6.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 11.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  11.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- SSIC >  79658.00
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Interest Rate >  1.35
<p>|   |   |   |   |   |   |   |--- SSIC <= 54459.50
<p>|   |   |   |   |   |   |   |   |--- Payment Amount <= 30331.00
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 19.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 8.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  8.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Day >  19.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 15984.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  15984.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Payment Amount >  30331.00
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 13.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 62920.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  62920.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Day >  13.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 4.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  4.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- SSIC >  54459.50
<p>|   |   |   |   |   |   |   |   |--- Disbursal Amount <= 64159.47
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 6.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount <= 25000.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount >  25000.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  6.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount <= 15950.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount >  15950.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Disbursal Amount >  64159.47
<p>|   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |--- Tenor >  4.50
<p>|   |   |   |   |   |--- Interest Rate <= 0.65
<p>|   |   |   |   |   |   |--- SSIC <= 29204.50
<p>|   |   |   |   |   |   |   |--- Month <= 6.50
<p>|   |   |   |   |   |   |   |   |--- Month <= 3.50
<p>|   |   |   |   |   |   |   |   |   |--- Amount <= 15450.00
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Amount >  15450.00
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Month >  3.50
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 2.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  2.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 6.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  6.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- Month >  6.50
<p>|   |   |   |   |   |   |   |   |--- Day <= 7.50
<p>|   |   |   |   |   |   |   |   |   |--- Year <= 2019.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount <= 27150.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount >  27150.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Year >  2019.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 5.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  5.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Day >  7.50
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 16.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Day >  16.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- SSIC >  29204.50
<p>|   |   |   |   |   |   |   |--- SSIC <= 42109.50
<p>|   |   |   |   |   |   |   |   |--- Month <= 2.50
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 2.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  2.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Month >  2.50
<p>|   |   |   |   |   |   |   |   |   |--- Year <= 2019.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 8.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  8.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |--- Year >  2019.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 12.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  12.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |--- SSIC >  42109.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Interest Rate >  0.65
<p>|   |   |   |   |   |   |--- SSIC <= 79658.00
<p>|   |   |   |   |   |   |   |--- Payment Amount <= 5117.08
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 76148.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 11.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 2.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 13
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  2.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 16
<p>|   |   |   |   |   |   |   |   |   |--- Month >  11.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 35555.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 7
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  35555.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- SSIC >  76148.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 5.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 1437.59
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  1437.59
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |--- Month >  5.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 6.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  6.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |--- Payment Amount >  5117.08
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 71127.00
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 49966.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.27
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 18
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.27
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 12
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  49966.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 0.74
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  0.74
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |--- SSIC >  71127.00
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 9478.47
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  9478.47
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |--- Month >  3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 23103.76
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 7
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  23103.76
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |--- SSIC >  79658.00
<p>|   |   |   |   |   |   |   |--- Month <= 4.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Month >  4.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |--- Year >  2020.50
<p>|   |   |   |   |--- Month <= 11.50
<p>|   |   |   |   |   |--- SSIC <= 30556.50
<p>|   |   |   |   |   |   |--- Product <= 2.50
<p>|   |   |   |   |   |   |   |--- Day <= 23.50
<p>|   |   |   |   |   |   |   |   |--- Interest Rate <= 0.65
<p>|   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Interest Rate >  0.65
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 26116.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.62
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.62
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  26116.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.12
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.12
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |--- Day >  23.50
<p>|   |   |   |   |   |   |   |   |--- Interest Rate <= 1.77
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 5.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 1.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  1.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  5.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount <= 13350.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount >  13350.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Interest Rate >  1.77
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 5.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Month >  5.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Product >  2.50
<p>|   |   |   |   |   |   |   |--- Interest Rate <= 0.65
<p>|   |   |   |   |   |   |   |   |--- Day <= 25.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 29204.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  29204.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |   |--- Month >  3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 5.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 8
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  5.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |--- Day >  25.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 8.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 4461.48
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  4461.48
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |   |--- Month >  8.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Interest Rate >  0.65
<p>|   |   |   |   |   |   |   |   |--- Product <= 3.50
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 27207.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  27207.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount <= 9200.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount >  9200.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |--- Product >  3.50
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 12.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 1.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  1.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 10
<p>|   |   |   |   |   |   |   |   |   |--- Day >  12.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 5441.15
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 10
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  5441.15
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 13
<p>|   |   |   |   |   |--- SSIC >  30556.50
<p>|   |   |   |   |   |   |--- Interest Rate <= 1.05
<p>|   |   |   |   |   |   |   |--- Tenor <= 1.50
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- Tenor >  1.50
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 57156.00
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 43605.00
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 43215.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  43215.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  43605.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 17931.23
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  17931.23
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |--- SSIC >  57156.00
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 79658.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 8.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  8.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  79658.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 4.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  4.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Interest Rate >  1.05
<p>|   |   |   |   |   |   |   |--- SSIC <= 46759.50
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 45105.50
<p>|   |   |   |   |   |   |   |   |   |--- Tenor <= 3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 94870.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  94870.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |--- Tenor >  3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 74971.59
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  74971.59
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |--- SSIC >  45105.50
<p>|   |   |   |   |   |   |   |   |   |--- Payment Amount <= 42498.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Payment Amount >  42498.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- SSIC >  46759.50
<p>|   |   |   |   |   |   |   |   |--- Month <= 8.50
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 70201.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 49877.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  49877.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  70201.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 5.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  5.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |--- Month >  8.50
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 6.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Day >  6.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 26222.27
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  26222.27
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |--- Month >  11.50
<p>|   |   |   |   |   |--- Day <= 5.50
<p>|   |   |   |   |   |   |--- Product <= 2.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Product >  2.50
<p>|   |   |   |   |   |   |   |--- SSIC <= 29204.50
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- SSIC >  29204.50
<p>|   |   |   |   |   |   |   |   |--- Payment Amount <= 15257.70
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Payment Amount >  15257.70
<p>|   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |--- Day >  5.50
<p>|   |   |   |   |   |   |--- Amount <= 1450.00
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Amount >  1450.00
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |--- Year >  2021.50
<p>|   |   |--- class: 0
<p>|--- Tenor >  5.50
<p>|   |--- Year <= 2021.50
<p>|   |   |--- Tenor <= 10.50
<p>|   |   |   |--- Month <= 6.50
<p>|   |   |   |   |--- Day <= 22.50
<p>|   |   |   |   |   |--- Month <= 1.50
<p>|   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Month >  1.50
<p>|   |   |   |   |   |   |--- Weekday <= 1.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Weekday >  1.50
<p>|   |   |   |   |   |   |   |--- SSIC <= 70205.00
<p>|   |   |   |   |   |   |   |   |--- Payment Amount <= 4429.04
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Payment Amount >  4429.04
<p>|   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 48127.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  48127.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount <= 90000.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount >  90000.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- SSIC >  70205.00
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- Day >  22.50
<p>|   |   |   |   |   |--- SSIC <= 56111.50
<p>|   |   |   |   |   |   |--- Year <= 2020.50
<p>|   |   |   |   |   |   |   |--- Month <= 2.50
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- Month >  2.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Year >  2020.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- SSIC >  56111.50
<p>|   |   |   |   |   |   |--- Day <= 23.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Day >  23.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |--- Month >  6.50
<p>|   |   |   |   |--- Year <= 2018.50
<p>|   |   |   |   |   |--- Weekday <= 4.50
<p>|   |   |   |   |   |   |--- Month <= 10.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Month >  10.50
<p>|   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |--- Weekday >  4.50
<p>|   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- Year >  2018.50
<p>|   |   |   |   |   |--- Disbursal Amount <= 19144.00
<p>|   |   |   |   |   |   |--- Day <= 24.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Day >  24.50
<p>|   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |--- Disbursal Amount >  19144.00
<p>|   |   |   |   |   |   |--- Payment Amount <= 5423.77
<p>|   |   |   |   |   |   |   |--- Disbursal Amount <= 28475.25
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Disbursal Amount >  28475.25
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Payment Amount >  5423.77
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |--- Tenor >  10.50
<p>|   |   |   |--- Payment Amount <= 9392.33
<p>|   |   |   |   |--- Month <= 1.50
<p>|   |   |   |   |   |--- Weekday <= 3.50
<p>|   |   |   |   |   |   |--- SSIC <= 66145.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- SSIC >  66145.50
<p>|   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |--- Weekday >  3.50
<p>|   |   |   |   |   |   |--- Interest Rate <= 2.38
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Interest Rate >  2.38
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- Month >  1.50
<p>|   |   |   |   |   |--- Disbursal Amount <= 9572.00
<p>|   |   |   |   |   |   |--- Month <= 6.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Month >  6.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Disbursal Amount >  9572.00
<p>|   |   |   |   |   |   |--- SSIC <= 47711.50
<p>|   |   |   |   |   |   |   |--- Day <= 9.50
<p>|   |   |   |   |   |   |   |   |--- Weekday <= 5.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Weekday >  5.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 9.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Month >  9.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Day >  9.50
<p>|   |   |   |   |   |   |   |   |--- Month <= 11.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 10.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 94917.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 8
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  94917.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |--- Month >  10.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Year <= 2020.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Year >  2020.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |--- Month >  11.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- SSIC >  47711.50
<p>|   |   |   |   |   |   |   |--- Payment Amount <= 3298.74
<p>|   |   |   |   |   |   |   |   |--- Payment Amount <= 2902.57
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 58566.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 4.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  4.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  58566.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 2.12
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  2.12
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |--- Payment Amount >  2902.57
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 4.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  4.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- Payment Amount >  3298.74
<p>|   |   |   |   |   |   |   |   |--- Disbursal Amount <= 97860.00
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.60
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 76576.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  76576.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.60
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 87240.24
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  87240.24
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |--- Disbursal Amount >  97860.00
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |--- Payment Amount >  9392.33
<p>|   |   |   |   |--- Year <= 2016.50
<p>|   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- Year >  2016.50
<p>|   |   |   |   |   |--- Payment Amount <= 9586.31
<p>|   |   |   |   |   |   |--- Month <= 10.50
<p>|   |   |   |   |   |   |   |--- Disbursal Amount <= 95987.50
<p>|   |   |   |   |   |   |   |   |--- Month <= 6.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 4.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Month >  4.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Month >  6.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Disbursal Amount >  95987.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Month >  10.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Payment Amount >  9586.31
<p>|   |   |   |   |   |   |--- Day <= 8.50
<p>|   |   |   |   |   |   |   |--- Year <= 2018.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Year >  2018.50
<p>|   |   |   |   |   |   |   |   |--- Weekday <= 1.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Weekday >  1.50
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 4.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 46726.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  46726.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  4.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 4.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  4.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Day >  8.50
<p>|   |   |   |   |   |   |   |--- SSIC <= 47421.00
<p>|   |   |   |   |   |   |   |   |--- Month <= 7.50
<p>|   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 486625.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 12.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  12.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  486625.00
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Month >  7.50
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 18.00
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Day >  18.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 2.12
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  2.12
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |--- SSIC >  47421.00
<p>|   |   |   |   |   |   |   |   |--- Month <= 7.50
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate <= 2.12
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 168580.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  168580.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate >  2.12
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 9675.23
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  9675.23
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |--- Month >  7.50
<p>|   |   |   |   |   |   |   |   |   |--- Year <= 2018.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Year >  2018.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |--- Year >  2021.50
<p>|   |   |--- class: 0

</details>

------------      

## DecisionTreeClassifier with Under-sampling    

| -  | Score |
| ------------- | ------------- |
| Training  | 0.766  |
| Test  | 0.732  |
| Specificity  | 0.727  |
| Precision  | 0.357  |
| Recall  | 0.755  |
| Accuracy  | 0.732  |
| F1  | 0.485  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_3_roc.png)
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_3.png)     

| Baseline  | 0.50  |
| ------------- | ------------- |
| ROC AUC  | 0.822  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_3_nodes.png)        
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_3_auc_roc.png)     
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_3_tree.png)     

<details><summary>DecisionTree Details</summary>
<p>|--- Tenor <= 5.50
<p>|   |--- Year <= 2021.50
<p>|   |   |--- Interest Rate <= 0.53
<p>|   |   |   |--- Weekday <= 4.50
<p>|   |   |   |   |--- Day <= 22.50
<p>|   |   |   |   |   |--- Disbursal Amount <= 19973.25
<p>|   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Disbursal Amount >  19973.25
<p>|   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- Day >  22.50
<p>|   |   |   |   |   |--- class: 0
<p>|   |   |   |--- Weekday >  4.50
<p>|   |   |   |   |--- class: 0
<p>|   |   |--- Interest Rate >  0.53
<p>|   |   |   |--- Year <= 2019.50
<p>|   |   |   |   |--- Month <= 8.50
<p>|   |   |   |   |   |--- Tenor <= 2.50
<p>|   |   |   |   |   |   |--- Interest Rate <= 1.58
<p>|   |   |   |   |   |   |   |--- Day <= 12.50
<p>|   |   |   |   |   |   |   |   |--- Disbursal Amount <= 19826.59
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Disbursal Amount >  19826.59
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Day >  12.50
<p>|   |   |   |   |   |   |   |   |--- Weekday <= 4.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Weekday >  4.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |--- Interest Rate >  1.58
<p>|   |   |   |   |   |   |   |--- SSIC <= 42700.00
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- SSIC >  42700.00
<p>|   |   |   |   |   |   |   |   |--- Day <= 21.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Day >  21.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |--- Tenor >  2.50
<p>|   |   |   |   |   |   |--- SSIC <= 28295.00
<p>|   |   |   |   |   |   |   |--- SSIC <= 27311.50
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- SSIC >  27311.50
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |--- SSIC >  28295.00
<p>|   |   |   |   |   |   |   |--- Tenor <= 4.50
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 45105.50
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 43297.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.43
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.43
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  43297.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 17238.84
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  17238.84
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- SSIC >  45105.50
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 71123.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Insured <= 0.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Insured >  0.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  71123.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 7.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  7.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |--- Tenor >  4.50
<p>|   |   |   |   |   |   |   |   |--- Interest Rate <= 1.12
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 16370.60
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  16370.60
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Interest Rate >  1.12
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- Month >  8.50
<p>|   |   |   |   |   |--- SSIC <= 79053.50
<p>|   |   |   |   |   |   |--- Year <= 2018.50
<p>|   |   |   |   |   |   |   |--- Interest Rate <= 0.72
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- Interest Rate >  0.72
<p>|   |   |   |   |   |   |   |   |--- Interest Rate <= 1.45
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 39651.00
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  39651.00
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Interest Rate >  1.45
<p>|   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 9417.54
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  9417.54
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 11.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  11.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |--- Year >  2018.50
<p>|   |   |   |   |   |   |   |--- Payment Amount <= 3722.70
<p>|   |   |   |   |   |   |   |   |--- Month <= 11.50
<p>|   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 2083.68
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  2083.68
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Month >  11.50
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 16.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Day >  16.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- Payment Amount >  3722.70
<p>|   |   |   |   |   |   |   |   |--- Disbursal Amount <= 9423.76
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 11.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 22.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  22.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Month >  11.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 2.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  2.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Disbursal Amount >  9423.76
<p>|   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 11358.08
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  11358.08
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 48056.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  48056.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- SSIC >  79053.50
<p>|   |   |   |   |   |   |--- Weekday <= 3.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Weekday >  3.50
<p>|   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |--- Year >  2019.50
<p>|   |   |   |   |--- Interest Rate <= 0.56
<p>|   |   |   |   |   |--- SSIC <= 29204.50
<p>|   |   |   |   |   |   |--- Weekday <= 4.50
<p>|   |   |   |   |   |   |   |--- Year <= 2020.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Year >  2020.50
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |--- Weekday >  4.50
<p>|   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |--- SSIC >  29204.50
<p>|   |   |   |   |   |   |--- Day <= 12.00
<p>|   |   |   |   |   |   |   |--- Month <= 5.50
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- Month >  5.50
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |--- Day >  12.00
<p>|   |   |   |   |   |   |   |--- Month <= 6.50
<p>|   |   |   |   |   |   |   |   |--- Weekday <= 3.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Weekday >  3.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- Month >  6.50
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |--- Interest Rate >  0.56
<p>|   |   |   |   |   |--- Month <= 4.50
<p>|   |   |   |   |   |   |--- SSIC <= 81255.50
<p>|   |   |   |   |   |   |   |--- Interest Rate <= 1.56
<p>|   |   |   |   |   |   |   |   |--- Product <= 2.50
<p>|   |   |   |   |   |   |   |   |   |--- Amount <= 25000.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.32
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.32
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Amount >  25000.00
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 35605.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  35605.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Product >  2.50
<p>|   |   |   |   |   |   |   |   |   |--- Product <= 3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Product >  3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 41005.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 12
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  41005.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |--- Interest Rate >  1.56
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 46551.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 2.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Month >  2.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- SSIC >  46551.50
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 46585.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  46585.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |--- SSIC >  81255.50
<p>|   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |--- Month >  4.50
<p>|   |   |   |   |   |   |--- SSIC <= 39651.00
<p>|   |   |   |   |   |   |   |--- Month <= 11.50
<p>|   |   |   |   |   |   |   |   |--- Amount <= 11850.00
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 7.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 0.72
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  0.72
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |--- Month >  7.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 0.69
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  0.69
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |--- Amount >  11850.00
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 11.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 21493.05
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  21493.05
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |--- Day >  11.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 84120.10
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  84120.10
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |--- Month >  11.50
<p>|   |   |   |   |   |   |   |   |--- Day <= 15.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Day >  15.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- SSIC >  39651.00
<p>|   |   |   |   |   |   |   |--- Interest Rate <= 1.05
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 57156.00
<p>|   |   |   |   |   |   |   |   |   |--- Year <= 2020.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 0.69
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  0.69
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Year >  2020.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 43607.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  43607.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |--- SSIC >  57156.00
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 79658.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 8.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  8.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  79658.00
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Interest Rate >  1.05
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 46640.00
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 45180.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 58026.68
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  58026.68
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  45180.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 9806.38
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  9806.38
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- SSIC >  46640.00
<p>|   |   |   |   |   |   |   |   |   |--- Tenor <= 4.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 50751.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  50751.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |--- Tenor >  4.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |--- Year >  2021.50
<p>|   |   |--- SSIC <= 29205.00
<p>|   |   |   |--- class: 0
<p>|   |   |--- SSIC >  29205.00
<p>|   |   |   |--- class: 0
<p>|--- Tenor >  5.50
<p>|   |--- Tenor <= 10.50
<p>|   |   |--- Month <= 6.50
<p>|   |   |   |--- SSIC <= 46725.50
<p>|   |   |   |   |--- class: 0
<p>|   |   |   |--- SSIC >  46725.50
<p>|   |   |   |   |--- class: 0
<p>|   |   |--- Month >  6.50
<p>|   |   |   |--- SSIC <= 47106.50
<p>|   |   |   |   |--- class: 0
<p>|   |   |   |--- SSIC >  47106.50
<p>|   |   |   |   |--- class: 0
<p>|   |--- Tenor >  10.50
<p>|   |   |--- Year <= 2021.50
<p>|   |   |   |--- Month <= 11.50
<p>|   |   |   |   |--- Month <= 10.50
<p>|   |   |   |   |   |--- Payment Amount <= 9586.31
<p>|   |   |   |   |   |   |--- Disbursal Amount <= 28447.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Disbursal Amount >  28447.50
<p>|   |   |   |   |   |   |   |--- Month <= 6.50
<p>|   |   |   |   |   |   |   |   |--- Day <= 11.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Day >  11.50
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.88
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.88
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 46592.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  46592.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Month >  6.50
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 47421.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 8.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Month >  8.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- SSIC >  47421.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Payment Amount >  9586.31
<p>|   |   |   |   |   |   |--- Weekday <= 4.50
<p>|   |   |   |   |   |   |   |--- SSIC <= 47105.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- SSIC >  47105.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Weekday >  4.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- Month >  10.50
<p>|   |   |   |   |   |--- Year <= 2020.50
<p>|   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Year >  2020.50
<p>|   |   |   |   |   |   |--- class: 0
<p>|   |   |   |--- Month >  11.50
<p>|   |   |   |   |--- SSIC <= 46722.00
<p>|   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- SSIC >  46722.00
<p>|   |   |   |   |   |--- class: 0
<p>|   |   |--- Year >  2021.50
<p>|   |   |   |--- class: 0

</details>

------------      

## DecisionTreeClassifier with Mixed-sampling    

| -  | Score |
| ------------- | ------------- |
| Training  | 0.856  |
| Test  | 0.816  |
| Specificity  | 0.780  |
| Precision  | 0.796  |
| Recall  | 0.852  |
| Accuracy  | 0.816  |
| F1  | 0.823  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_4_roc.png)
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_4.png)     

| Baseline  | 0.50  |
| ------------- | ------------- |
| ROC AUC  | 0.900  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_4_nodes.png)        
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_4_auc_roc.png)     
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_4_tree.png)     

<details><summary>DecisionTree Details</summary>
<p>|--- Tenor <= 5.50
<p>|   |--- Year <= 2021.50
<p>|   |   |--- Interest Rate <= 0.53
<p>|   |   |   |--- Weekday <= 5.50
<p>|   |   |   |   |--- Amount <= 247600.00
<p>|   |   |   |   |   |--- Interest Rate <= 0.47
<p>|   |   |   |   |   |   |--- Year <= 2019.50
<p>|   |   |   |   |   |   |   |--- Month <= 8.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Month >  8.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Year >  2019.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Interest Rate >  0.47
<p>|   |   |   |   |   |   |--- Day <= 22.50
<p>|   |   |   |   |   |   |   |--- Payment Amount <= 7790.00
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Payment Amount >  7790.00
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Day >  22.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- Amount >  247600.00
<p>|   |   |   |   |   |--- class: 0
<p>|   |   |   |--- Weekday >  5.50
<p>|   |   |   |   |--- Day <= 29.50
<p>|   |   |   |   |   |--- Insured <= 0.50
<p>|   |   |   |   |   |   |--- SSIC <= 46276.00
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- SSIC >  46276.00
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Insured >  0.50
<p>|   |   |   |   |   |   |--- Year <= 2019.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Year >  2019.50
<p>|   |   |   |   |   |   |   |--- SSIC <= 36048.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- SSIC >  36048.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- Day >  29.50
<p>|   |   |   |   |   |--- class: 1
<p>|   |   |--- Interest Rate >  0.53
<p>|   |   |   |--- Year <= 2020.50
<p>|   |   |   |   |--- Tenor <= 4.50
<p>|   |   |   |   |   |--- Tenor <= 3.50
<p>|   |   |   |   |   |   |--- Interest Rate <= 1.11
<p>|   |   |   |   |   |   |   |--- Payment Amount <= 6195.17
<p>|   |   |   |   |   |   |   |   |--- Product <= 4.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 7.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 1812.06
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  1812.06
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |   |--- Month >  7.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 3.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  3.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |--- Product >  4.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 11.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 3174.26
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  3174.26
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |--- Month >  11.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- Payment Amount >  6195.17
<p>|   |   |   |   |   |   |   |   |--- Year <= 2018.50
<p>|   |   |   |   |   |   |   |   |   |--- Tenor <= 2.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 39651.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  39651.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |   |--- Tenor >  2.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 0.84
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  0.84
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |--- Year >  2018.50
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate <= 0.69
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 8.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  8.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate >  0.69
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 6.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  6.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |--- Interest Rate >  1.11
<p>|   |   |   |   |   |   |   |--- SSIC <= 10410.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- SSIC >  10410.50
<p>|   |   |   |   |   |   |   |   |--- Product <= 2.50
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.45
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.32
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 9
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.32
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.45
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 1470.35
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  1470.35
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 18
<p>|   |   |   |   |   |   |   |   |--- Product >  2.50
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 6.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 29.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 14
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  29.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  6.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Tenor >  3.50
<p>|   |   |   |   |   |   |--- SSIC <= 79658.00
<p>|   |   |   |   |   |   |   |--- Interest Rate <= 1.35
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 45226.50
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 4.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  4.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 3.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 7
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  3.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 7
<p>|   |   |   |   |   |   |   |   |--- SSIC >  45226.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 6.00
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 61710.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  61710.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |--- Month >  6.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 11.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  11.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- Interest Rate >  1.35
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 54459.50
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.77
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 3.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  3.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.77
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 17290.80
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  17290.80
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- SSIC >  54459.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 6.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 6.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  6.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Month >  6.00
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |--- SSIC >  79658.00
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- Tenor >  4.50
<p>|   |   |   |   |   |--- Interest Rate <= 0.61
<p>|   |   |   |   |   |   |--- Month <= 8.50
<p>|   |   |   |   |   |   |   |--- Month <= 2.50
<p>|   |   |   |   |   |   |   |   |--- Day <= 7.00
<p>|   |   |   |   |   |   |   |   |   |--- Payment Amount <= 22628.77
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Payment Amount >  22628.77
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Day >  7.00
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Month >  2.50
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 29204.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 6.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 2.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  2.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |   |--- Month >  6.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- SSIC >  29204.50
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 35559.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 12.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 8
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  12.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  35559.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 6.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  6.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |--- Month >  8.50
<p>|   |   |   |   |   |   |   |--- Weekday <= 3.50
<p>|   |   |   |   |   |   |   |   |--- Year <= 2019.50
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 2.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 28.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  28.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  2.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 24888.90
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  24888.90
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Year >  2019.50
<p>|   |   |   |   |   |   |   |   |   |--- Amount <= 44300.00
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Amount >  44300.00
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- Weekday >  3.50
<p>|   |   |   |   |   |   |   |   |--- Amount <= 4750.00
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Amount >  4750.00
<p>|   |   |   |   |   |   |   |   |   |--- Amount <= 20100.00
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Amount >  20100.00
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Interest Rate >  0.61
<p>|   |   |   |   |   |   |--- SSIC <= 79658.00
<p>|   |   |   |   |   |   |   |--- Payment Amount <= 5117.08
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 76148.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 11.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 35555.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 12
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  35555.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |--- Month >  11.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount <= 3050.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount >  3050.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |--- SSIC >  76148.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 4.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 21.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  21.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Month >  4.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 2754.27
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  2754.27
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |--- Payment Amount >  5117.08
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 28207.00
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 26512.00
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 22666.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  22666.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  26512.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 5.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  5.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 8
<p>|   |   |   |   |   |   |   |   |--- SSIC >  28207.00
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 29205.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 8.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  8.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  29205.00
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 71127.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 18
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  71127.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 9
<p>|   |   |   |   |   |   |--- SSIC >  79658.00
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |--- Year >  2020.50
<p>|   |   |   |   |--- Month <= 11.50
<p>|   |   |   |   |   |--- SSIC <= 30556.50
<p>|   |   |   |   |   |   |--- Product <= 2.50
<p>|   |   |   |   |   |   |   |--- Interest Rate <= 1.55
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 28206.00
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 9.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 52420.55
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  52420.55
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |--- Month >  9.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 27.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  27.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- SSIC >  28206.00
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 24.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 0.65
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  0.65
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |--- Day >  24.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 1.43
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  1.43
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Interest Rate >  1.55
<p>|   |   |   |   |   |   |   |   |--- Disbursal Amount <= 58397.44
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 15.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Day >  15.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Disbursal Amount >  58397.44
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Product >  2.50
<p>|   |   |   |   |   |   |   |--- Interest Rate <= 0.65
<p>|   |   |   |   |   |   |   |   |--- Day <= 25.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 29204.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  29204.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |--- Month >  3.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 9.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 7
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  9.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |--- Day >  25.50
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 8.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 29204.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  29204.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |--- Month >  8.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Interest Rate >  0.65
<p>|   |   |   |   |   |   |   |   |--- Product <= 3.50
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 27207.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  27207.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount <= 4600.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount >  4600.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |--- Product >  3.50
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 12.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 8.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 9
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  8.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |--- Day >  12.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 5348.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 10
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  5348.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 11
<p>|   |   |   |   |   |--- SSIC >  30556.50
<p>|   |   |   |   |   |   |--- Interest Rate <= 1.05
<p>|   |   |   |   |   |   |   |--- SSIC <= 57156.00
<p>|   |   |   |   |   |   |   |   |--- Tenor <= 1.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Tenor >  1.50
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 46760.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 33659.39
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  33659.39
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  46760.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 17931.23
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  17931.23
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |--- SSIC >  57156.00
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 79658.00
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 8.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 0.69
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  0.69
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |   |--- Month >  8.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 71125.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  71125.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- SSIC >  79658.00
<p>|   |   |   |   |   |   |   |   |   |--- Weekday <= 4.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 28134.32
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  28134.32
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Weekday >  4.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Interest Rate >  1.05
<p>|   |   |   |   |   |   |   |--- Interest Rate <= 1.77
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 46556.00
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 45105.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Product <= 2.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |   |   |--- Product >  2.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  45105.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 4.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  4.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- SSIC >  46556.00
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 8.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 4990.19
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  4990.19
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |--- Month >  8.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 70202.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  70202.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Interest Rate >  1.77
<p>|   |   |   |   |   |   |   |   |--- Month <= 2.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Month >  2.50
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 10.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- Day >  10.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 5.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  5.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |--- Month >  11.50
<p>|   |   |   |   |   |--- Day <= 5.50
<p>|   |   |   |   |   |   |--- Amount <= 5250.00
<p>|   |   |   |   |   |   |   |--- Interest Rate <= 0.61
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- Interest Rate >  0.61
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |--- Amount >  5250.00
<p>|   |   |   |   |   |   |   |--- Disbursal Amount <= 15585.46
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Disbursal Amount >  15585.46
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 39610.00
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- SSIC >  39610.00
<p>|   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |--- Day >  5.50
<p>|   |   |   |   |   |   |--- Payment Amount <= 1437.52
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Payment Amount >  1437.52
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |--- Year >  2021.50
<p>|   |   |--- Payment Amount <= 1351.03
<p>|   |   |   |--- class: 0
<p>|   |   |--- Payment Amount >  1351.03
<p>|   |   |   |--- class: 0
<p>|--- Tenor >  5.50
<p>|   |--- Year <= 2021.50
<p>|   |   |--- Tenor <= 10.50
<p>|   |   |   |--- Year <= 2018.50
<p>|   |   |   |   |--- SSIC <= 72656.00
<p>|   |   |   |   |   |--- Weekday <= 4.50
<p>|   |   |   |   |   |   |--- Month <= 10.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Month >  10.50
<p>|   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |--- Weekday >  4.50
<p>|   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- SSIC >  72656.00
<p>|   |   |   |   |   |--- class: 0
<p>|   |   |   |--- Year >  2018.50
<p>|   |   |   |   |--- Month <= 6.50
<p>|   |   |   |   |   |--- Weekday <= 4.50
<p>|   |   |   |   |   |   |--- Year <= 2019.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Year >  2019.50
<p>|   |   |   |   |   |   |   |--- Disbursal Amount <= 14438.25
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- Disbursal Amount >  14438.25
<p>|   |   |   |   |   |   |   |   |--- Day <= 9.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Day >  9.50
<p>|   |   |   |   |   |   |   |   |   |--- Year <= 2020.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 2.38
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  2.38
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Year >  2020.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Weekday >  4.50
<p>|   |   |   |   |   |   |--- Payment Amount <= 8964.02
<p>|   |   |   |   |   |   |   |--- SSIC <= 47677.00
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- SSIC >  47677.00
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Payment Amount >  8964.02
<p>|   |   |   |   |   |   |   |--- Weekday <= 6.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Weekday >  6.50
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |--- Month >  6.50
<p>|   |   |   |   |   |--- Payment Amount <= 5423.77
<p>|   |   |   |   |   |   |--- SSIC <= 44700.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- SSIC >  44700.50
<p>|   |   |   |   |   |   |   |--- SSIC <= 47106.50
<p>|   |   |   |   |   |   |   |   |--- Amount <= 22500.00
<p>|   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Amount >  22500.00
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- SSIC >  47106.50
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 72196.00
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- SSIC >  72196.00
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Payment Amount >  5423.77
<p>|   |   |   |   |   |   |--- class: 0
<p>|   |   |--- Tenor >  10.50
<p>|   |   |   |--- Month <= 11.50
<p>|   |   |   |   |--- Month <= 10.50
<p>|   |   |   |   |   |--- Day <= 2.50
<p>|   |   |   |   |   |   |--- Weekday <= 5.50
<p>|   |   |   |   |   |   |   |--- Month <= 4.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Month >  4.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Weekday >  5.50
<p>|   |   |   |   |   |   |   |--- SSIC <= 47001.00
<p>|   |   |   |   |   |   |   |   |--- Month <= 7.00
<p>|   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Month >  7.00
<p>|   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- SSIC >  47001.00
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Day >  2.50
<p>|   |   |   |   |   |   |--- Interest Rate <= 1.93
<p>|   |   |   |   |   |   |   |--- Year <= 2019.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Year >  2019.50
<p>|   |   |   |   |   |   |   |   |--- SSIC <= 43905.50
<p>|   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 95185.00
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 24.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  24.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  95185.00
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 35559.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  35559.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- SSIC >  43905.50
<p>|   |   |   |   |   |   |   |   |   |--- Payment Amount <= 13007.85
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount <= 23796.25
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |   |--- Disbursal Amount >  23796.25
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |--- Payment Amount >  13007.85
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Interest Rate >  1.93
<p>|   |   |   |   |   |   |   |--- Year <= 2020.50
<p>|   |   |   |   |   |   |   |   |--- Interest Rate <= 2.38
<p>|   |   |   |   |   |   |   |   |   |--- Day <= 24.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount <= 90000.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- Amount >  90000.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |   |   |--- Day >  24.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Month <= 9.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 5
<p>|   |   |   |   |   |   |   |   |   |   |--- Month >  9.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |--- Interest Rate >  2.38
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 31006.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday <= 3.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Weekday >  3.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  31006.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 47262.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  47262.00
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 4
<p>|   |   |   |   |   |   |   |--- Year >  2020.50
<p>|   |   |   |   |   |   |   |   |--- Payment Amount <= 7828.10
<p>|   |   |   |   |   |   |   |   |   |--- Amount <= 66087.62
<p>|   |   |   |   |   |   |   |   |   |   |--- Day <= 28.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 6
<p>|   |   |   |   |   |   |   |   |   |   |--- Day >  28.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |--- Amount >  66087.62
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount <= 6695.72
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- Payment Amount >  6695.72
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Payment Amount >  7828.10
<p>|   |   |   |   |   |   |   |   |   |--- Month <= 7.50
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate <= 2.38
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 3
<p>|   |   |   |   |   |   |   |   |   |   |--- Interest Rate >  2.38
<p>|   |   |   |   |   |   |   |   |   |   |   |--- truncated branch of depth 2
<p>|   |   |   |   |   |   |   |   |   |--- Month >  7.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- Month >  10.50
<p>|   |   |   |   |   |--- Disbursal Amount <= 98395.00
<p>|   |   |   |   |   |   |--- SSIC <= 47001.00
<p>|   |   |   |   |   |   |   |--- SSIC <= 38500.50
<p>|   |   |   |   |   |   |   |   |--- Disbursal Amount <= 48662.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Disbursal Amount >  48662.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- SSIC >  38500.50
<p>|   |   |   |   |   |   |   |   |--- Weekday <= 3.50
<p>|   |   |   |   |   |   |   |   |   |--- SSIC <= 42109.50
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |   |--- SSIC >  42109.50
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC <= 46450.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |   |--- SSIC >  46450.50
<p>|   |   |   |   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |   |--- Weekday >  3.50
<p>|   |   |   |   |   |   |   |   |   |--- Payment Amount <= 5718.03
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |   |--- Payment Amount >  5718.03
<p>|   |   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- SSIC >  47001.00
<p>|   |   |   |   |   |   |   |--- Day <= 23.50
<p>|   |   |   |   |   |   |   |   |--- Amount <= 31080.16
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Amount >  31080.16
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Day >  23.50
<p>|   |   |   |   |   |   |   |   |--- Day <= 26.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |   |--- Day >  26.50
<p>|   |   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Disbursal Amount >  98395.00
<p>|   |   |   |   |   |   |--- Year <= 2020.50
<p>|   |   |   |   |   |   |   |--- Day <= 20.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |   |--- Day >  20.50
<p>|   |   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Year >  2020.50
<p>|   |   |   |   |   |   |   |--- Day <= 29.50
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |   |   |   |   |--- Day >  29.50
<p>|   |   |   |   |   |   |   |   |--- class: 1
<p>|   |   |   |--- Month >  11.50
<p>|   |   |   |   |--- Disbursal Amount <= 19037.00
<p>|   |   |   |   |   |--- class: 0
<p>|   |   |   |   |--- Disbursal Amount >  19037.00
<p>|   |   |   |   |   |--- Weekday <= 1.50
<p>|   |   |   |   |   |   |--- Disbursal Amount <= 90399.00
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Disbursal Amount >  90399.00
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |--- Weekday >  1.50
<p>|   |   |   |   |   |   |--- Weekday <= 2.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |   |   |   |   |   |--- Weekday >  2.50
<p>|   |   |   |   |   |   |   |--- class: 0
<p>|   |--- Year >  2021.50
<p>|   |   |--- class: 0
 
</details>
 
--------
## AdaBoostClassifier

| -  | Score |
| ------------- | ------------- |
| Training  | 0.887  |
| Test  | 0.860  |
| Specificity  | 0.979  |
| Precision  | 0.672  |
| Recall  | 0.232  |
| Accuracy  | 0.860  |
| F1  | 0.345  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/ada_roc.png)
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/ada.png)     

| Baseline  | 0.50  |
| ------------- | ------------- |
| ROC AUC  | 0.852  |

--------
## GradientBoostingClassifier

| -  | Score |
| ------------- | ------------- |
| Training     | 0.878  |
| Test         | 0.855  |
| Specificity  | 0.986  |
| Precision    | 0.743  |
| Recall       | 0.202  |
| Accuracy     | 0.855  |
| F1           | 0.318  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/gb_1_roc.png)
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/gb_1.png)     

| Baseline  | 0.50  |
| ------------- | ------------- |
| ROC AUC  | 0.830  |

--------
## GradientBoostingClassifier with Over-sampling

| -  | Score |
| ------------- | ------------- |
| Training     | 0.993  |
| Test         | 0.975  |
| Specificity  | 0.971  |
| Precision    | 0.872  |
| Recall       | 0.995  |
| Accuracy     | 0.975  |
| F1           | 0.929  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/gb_2_roc.png)
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/gb_2.png)     

| Baseline  | 0.50  |
| ------------- | ------------- |
| ROC AUC  | 0.996  |

--------
## GradientBoostingClassifier with Under-sampling

| -  | Score |
| ------------- | ------------- |
| Training     | 0.747  |
| Test         | 0.714  |
| Specificity  | 0.599  |
| Precision    | 0.674  |
| Recall       | 0.830  |
| Accuracy     | 0.714  |
| F1           | 0.744  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/gb_3_roc.png)
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/gb_3.png)     

| Baseline  | 0.50  |
| ------------- | ------------- |
| ROC AUC  | 0.799  |

--------
## GradientBoostingClassifier with Mixed-sampling

| -  | Score |
| ------------- | ------------- |
| Training     | 0.882  |
| Test         | 0.842  |
| Specificity  | 0.833  |
| Precision    | 0.517  |
| Recall       | 0.892  |
| Accuracy     | 0.842  |
| F1           | 0.654  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/gb_4_roc.png)
![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/gb_4.png)     

| Baseline  | 0.50  |
| ------------- | ------------- |
| ROC AUC  | 0.942  |

----------------

## VotingClassifier

The VotingClassifer is set to use DecisionTreeClassifier(), AdaBoostClassifier(), GradientBoostingClassifer() and used a GridSearchCV() to find the best score and parameters. 

| -  | Score |
| ------------- | ------------- |
| Training     | 0.870  |
| Test         | 0.856  |
| Specificity  | 0.986  |
| Precision    | 0.695  |
| Recall       | 0.168  |
| Accuracy     | 0.856  |
| F1           | 0.271  |

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/vc.png)     

 -------
 
 ## Future Improvements
 
- Extracting additional features on the companies such as their annual financial reports, credit information from ACRA & BRC reports. 
- Further model explorations with RandomForests, XGBoost. 
- Implement model into a web application, and connect the results into a dashboard for visualizations. 
