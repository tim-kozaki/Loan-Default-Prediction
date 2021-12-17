# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Capstone: Loan Default Prediction

### Overview

- The main objective of this project is to predict whether a loan will be defaulted in the period of repayment by a company. 

### Problem Statement

- This project aims to develop a classification model to identify whether a loan will be defaulted during the tenor of the loan repayment by a company. 
-----

### About the Data

- Real loan information is extracted from a company that offers SME financing across Southeast Asia. 
- For confidentiality reasons, the company will not be revealed. 
- Company names are masked with unique identifiers
- Singapore Standard Industrial Classification are used to identify the companies industry. 
- Loan information such as amount, insured, date, tenor period, status, and delinquency of payments.
- Data imbalance existed where the target value only made up 16% of the data set. 

<insert image>

### Data Preparation

- Null values were found in the data set and were either removed or filled using external data collected through web scraping.
- Title, Selftext, and Subreddit features were retained.
- Punctuations were removed using NLP & Regex.
- Genshin Impact encoded to 0.
- Honkai Impact encoded to 1.

### Key Features
 - subreddit (interger: 0 | 1)
 - title (String)

### Additional Features

Over 10,000 additional features derived from the word content in title & selftext, created by using CountVectorizer .

------

### Modelling & Evaluation
 
 Two pipelines were developed and used in the modelling:
 
 <b>First Pipeline:</b>
 - CountVectorizer
 - RandomForests
 
 ![](https://git.generalassemb.ly/tim-kozaki/dsif2_projects/blob/master/project_3/images/randomforests_results.png)
 ![](https://git.generalassemb.ly/tim-kozaki/dsif2_projects/blob/master/project_3/images/randomforests_matrix.png)
 
 <b>Evaluation Results:</b>
 5-fold Cross validation score: 0.74   
 Training score: 0.99    
 Testing score: 0.78    
 Grid Search (Best score): 0.74   
 Specificity: 0.74    
 Accuracy score: 0.78   
 ROC AUC: 0.87   
 
 <b>Second Pipeline:</b>
 - CountVectorizer
 - MultinomialNB
 
 ![](https://git.generalassemb.ly/tim-kozaki/dsif2_projects/blob/master/project_3/images/multinomialnb_results.png)
 ![](https://git.generalassemb.ly/tim-kozaki/dsif2_projects/blob/master/project_3/images/multinomialnb_matrix.png)
 
  <b>Evaluation Results:</b>
 5-fold Cross validation score: 0.78   
 Training score: 0.95    
 Testing score: 0.81    
 Grid Search (Best score): 0.78   
 Specificity: 0.82    
 Accuracy score: 0.81   
 ROC AUC: 0.90   


 -----
 
 ### Future Improvements
 
- Identify and develop keywords used uniquely for each subreddit. For example, unique character names in each game.
- Address overfitting of the models.
- Train and test the data with other models.
