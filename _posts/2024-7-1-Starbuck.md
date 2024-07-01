---
layout: post
title: Look into Starbucks Project
---

# Introduction
Starbucks mimics customer behavior on the Starbucks rewards mobile app. Once every few days, Starbucks sends out an offer to users of the mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount or BOGO (buy one get one free). Some users might not receive any offer during certain weeks. Not all users receive the same offer, and that is the challenge to solve with this data set.

![Starbucks](/images/Starbucks.jpeg)

# 1) Define:
###	Project Overview
Starbucks mimics customer behavior on the Starbucks rewards mobile app. Once every few days, Starbucks sends out an offer to users of the mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount or BOGO (buy one get one free). Some users might not receive any offer during certain weeks. Not all users receive the same offer, and that is the challenge to solve with this data set.
Dataset overview:
The program used to create the data simulates how people make purchasing decisions and how those decisions are influenced by promotional offers.
Each person in the simulation has some hidden traits that influence their purchasing patterns and are associated with their observable traits. People produce various events, including receiving offers, opening offers, and making purchases.
As a simplification, there are no explicit products to track. Only the amounts of each transaction or offer are recorded.
There are three types of offers that can be sent: buy-one-get-one (BOGO), discount, and informational. In a BOGO offer, a user needs to spend a certain amount to get a reward equal to that threshold amount. In a discount, a user gains a reward equal to a fraction of the amount spent. In an informational offer, there is no reward, but neither is there a requisite amount that the user is expected to spend. Offers can be delivered via multiple channels.
The basic task is to use the data to identify which groups of people are most responsive to each type of offer, and how best to present each type of offer.
Data Dictionary
profile.json
Rewards program users (17000 users x 5 fields)

gender: (categorical) M, F, O, or null
age: (numeric) missing value encoded as 118
id: (string/hash)
became_member_on: (date) format YYYYMMDD
income: (numeric)
portfolio.json
Offers sent during 30-day test period (10 offers x 6 fields)

reward: (numeric) money awarded for the amount spent
channels: (list) web, email, mobile, social
difficulty: (numeric) money required to be spent to receive reward
duration: (numeric) time for offer to be open, in days
offer_type: (string) bogo, discount, informational
id: (string/hash)
transcript.json
Event log (306648 events x 4 fields)

person: (string/hash)
event: (string) offer received, offer viewed, transaction, offer completed
value: (dictionary) different values depending on event type
offer id: (string/hash) not associated with any "transaction"
amount: (numeric) money spent in "transaction"
reward: (numeric) money gained from "offer completed"
time: (numeric) hours after start of test

###	Problem Statement
The target of this project is verifying the potential user who can consume the offer by
AI modeling. To begin with developing AI model, verify below question with EDA.
1. Is there any pattern or rules that people more likely to consume starbucks offers.
2. Which offer is most popular offer?
3. What is the feature importance due to AI modeling?

###	Metrics：

Based on the business overview and problem statement, it is typical binary problem, although there’s lots of metrics we can refer for binary problem including accuracy、precision、recall、f1_score. Etc. For this project I proposal precision is the most importance metrics to evaluate AI model performance. Whether the precision achieved 70% then it is acceptable for this project.


# 2) Analyze:
###	Data Exploration
First of all, I have combined all of the 3 datasets together for further exploration.
And also preprocessed for some columns, especially, split the value with offer_id and value, get the amount of transaction, convert the time to days, etc.

###	Exploratory Visualization
Explore the dataset and verify above pre-defined question with visualization:
Profile:  
![Profile_age](/images/profile_age.PNG)  
![Profile_gender](/images/profile_gender.PNG)  
![Profile_become1](/images/profile_become.PNG)  
![Profile_become2](/images/profile_become_proportion.PNG)  
   

Transcript & Profile & Portfolio combined dataset:
![ratio](/images/df_ratio.PNG)  
![df_gender](/images/df_gender.PNG)  
   

After sampling target dataset for AI modeling total 44K :
![df_label](/images/df_label.PNG)  
![df_info](/images/df_info.PNG)  
![df_become](/images/df_become.PNG)  
![df_offertype](/images/df_offertype.PNG)  

###	Algorithms and Techniques
For this binary project, I proposal LogisticRegression and RandomForest algorithms for further modeling.

###	Benchmark

Basically, I have trained LogisticRegression AI model on train dataset, the precision is 62%.
Additionally, I have iterated AI model with tree based RandomForest AI model with same train dataset. Based on the comparation with highlighted precision metrics, iterated AI model achieved 69% precision. I means RandomForest AI model got better performance. It means when AI model says it is positive samples, 69% is positive samples, the proportion of positive and negative is almost  1 : 1, so 69% precision is higher than the default.
LR
![lr_train](/images/lr_train.PNG)  

RandomForest
![rfc_train](/images/rfc_train.PNG)  

 
# 3) Implement
###	Data Preprocessing
I have completed to preprocess the dataset including, split offer id and value, get amount of transaction and verify the anomalous value for numeric columns age and income, onehot encoding for category columns: gender and offer type, and also labeling the target value with specific logic. 
![df_process](/images/df_process.PNG)  
![df_process](/images/df_process_v1.PNG)  
![df_age](/images/df_age.PNG)  
![df_income](/images/df_income.PNG)  


###	Implementation
I have trained AI model with LogisticRegression and RandomForest algorithm with same training datasets. And the completed hyperameter tuning for RandomForest algorithm, based on the quick exploration, n_estimators = 20 and max_depth = 6 is the best parameter. Retrain the RandomForest AI model with above best parameters.


###	Refinement
Based on the result exploration with LogisticRegression algorithm on training dataset the precision is 62%,  and iterate it with RandomForest and hyparameter tuning on same training datasets, the precision is achieved 69% .
![rfc_hyper](/images/rfc_hyper.PNG)  
	 
# 4) Results:

###	Model Evaluation and Validation
![df_score](/images/evaluation_score.PNG)  
![df_roc](/images/roc.PNG)  
![df_pr](/images/pr.PNG)  
![df_confusion](/images/evaluation_confusion.PNG)  
![df_feature](/images/feature_importance.PNG)  
  

###	Justificatiion
Benchmark AI Model:
![df_income](/images/lr_train.PNG)  
 
Iterated AI Model:
![df_income](/images/rfc_train.PNG)  

# 5) Conclusion
•	The customers that more completed profiles are more likely to consume starbucks
offers.
•	Woman are more likely to consume starbucks offer
•	The customers that became member after 2015 are more likely to consume
starbucks offers.
•	Discount offer is more popular offer
•	Based on the exploration with feature importances, 
became_member_year & difficulty & income are the top 3 important features.

