# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Capstone: Loan Default Prediction

### Overview

- The main objective of this project is to predict whether a loan will be defaulted in the period of repayment by a company. 

### Problem Statement

- This project aims to develop a classification model to identify whether a loan will be defaulted during the tenor of the loan repayment by a company. 
-----

### About the Data

- Real loan information is extracted from a company that offers SME financing across Southeast Asia. 
- For confidentiality reasons, the company are not revealed. 
- Company names are masked with unique identifiers and additional information was limited. 
- Singapore Standard Industrial Classification are used to identify the companies industry. 
- Loan information consisted of product types, amount, insurance, date, tenor period, status, and delinquency of payments.
- Data imbalance existed where the target value only made up 16% of the data set. 

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/imbalance.png)

### Data Preparation

- Null values were found in the data set and were either removed or filled using external data collected through web scraping.
- Date values were reconfigured into individual features into Weekday | Day | Month | Year
- Imbalance issue was resolved using over sampling, under sampling, and a mix of both over & under sampling.


### Key Features
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

### Modelling & Evaluation
 
--------
**Logistic Regression**
- Over/Under Sampling Mix 

**Intercept:** 3.93104947e-09    
**Coefficient:**
1.00000235    
1.00000022    
1.00000017   
1.00000397  
0.99999681  
1.0000071 
0.99999652   
1.00000015   
0.9999377  
1.00004443     
1.00001859    
0.99999989   

**Training Score:** 0.586   
**Test Score:**     0.573    

**Specificity:**     0.188   
**Precision:**       0.539   
**Recall:**          0.966   
**Accuracy Score:**  0.573   
**F1:**              0.692 

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/lr_matrix_1.png)
------
**DecisionTreeClassifier**  

**Training Score:** 0.587    
**Test Score:**     0.573     

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_matrix.png)

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/dt_alpha.png)

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

**Best Score:** 0.814
**Best Paramters:** 'ada__n_estimators': 175, 'gb__n_estimators': 200, 'tree__max_depth': None

**Training Score:** 0.851
**Test Score:**     0.819

![](https://github.com/tim-kozaki/Loan-Default-Prediction/blob/main/image/vc_matrix.png)
 -------
 
 ### Future Improvements
 
- Extracting additional information on the companies such as their annual financial reports, credit information from ACRA & BRC reports. 
- Further model explorations with RandomForests, XGBoost. 
- Implement model into a web application, and connect the results into a Tableau dashboard for visualizations. 
