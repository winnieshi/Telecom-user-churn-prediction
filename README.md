# Telecom-user-churn-prediction
link: https://winnieshi.github.io/Telecom-user-churn-prediction/Telecom%20user%20churn%20prediction

The project includes four parts:
1. Telecom customer data collection, parsing and cleaning.  
2. Data analysis.  
3. Customer churn prediction with models.   

# 1. Data collection, parsing and cleaning.  
In this part:  
(1) converting all data to the proper data type,  
(2) checking and deleting missing values,  
(3) checking duplicate rows.  

# 2. Data analysis  
In this part:  
(1) Analyzing data from customer demographic view  
  Features: gender, SeniorCitizen, Partner, Dependents 

(2) Analyzing data from product services view  
  Basic features: PhoneService, InternetService  
  Adds-on service: MultipleLines, OnlineSecurity, OnlineBackup, DeviceProtection, TechSupport, StreamingTV, StreamingMovies   

(3) Analyzing data from customer behaviour view   
Customer behaviours has correlation with churning, it is not the reason of churning, instead, it can predict the possibility of churning.  
Features: tenure, contract(MonthlyCharges, TotalCharges), PaperlessBilling, PaymentMethod.  
Tenure, contract(MonthlyCharges, TotalCharges) can reflect a customer's loyalty to the company.  
PaperlessBilling and PaymentMethod reflect a customer's consumer attitude.  
Tenure and TotalCharges have high correlation at 0.83. So we only need to choose one feature from these two.  

**What I found**  
 - From customer demographic view  
   - From the hypothesis test result, I found that SeniorCitizen, Partner, Dependents have statistically significant effect on churning. 
   - Senior citizens have large churn rate, cannot exclude the reason of death. 
   - Customers who have partner or have dependents have less churn rate than those who don't have partner or dependents.  
 
 - From product services view   
   - Whether the customers have the internet service or have adds-on internet service, has some relation to the churning rate.  
    
 - From customer behaviour view   
   -  tenue and TotalCharges have high correlation at 0.83. So basically I only need to analyze the relation between tenue and churn. Customer who have longer tenue will have less probability of churn.
   - Customers who paid less on monthly have larger probability than those paid more. 
   - Customers who have contract of month-to-month have larger probability of churn compared to those who have long-term contract. 
   - Customers who choose paperless billing have larger probability than others. 
   - Customers who choose electric check have larger probability than others. 
 
#### Conclusions: ####
According to analysis above, we have 15 features that are related to churning, which are customer demographic (SeniorCitizen, Partner, Dependents), Product service (InternetService, MultipleLines, OnlineSecurity, OnlineBackup, DeviceProtection, TechSupport, StreamingTV, StreamingMovies), customer behavior (tenure, contract, MonthlyCharges, PaymentMethod and PaperlessBilling).

# 3. Customer churn prediction with models
(1) Feature engineering  
Adding a new feature, using label encoding and one-hot encoding to deal with categorical features, using min-max scaling to deal with numerical features.   
(2) Correlation analysis  
(3) Split train and test data  
(4) Build, train and test ML models-logistic regression model, random forest model, GBDT model, multilayer perceptron classifier model  

**Conclusion:**  
GDBT model performs best among the Logistic regression, random forest and multilayer perception models.   
The performances are: 
AUC: 0.76  
Precision: 0.75  
Recall: 0.80  
F1_Score: 0.78  
