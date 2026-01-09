# Customer Churn Prediction (IBM Telecom Dataset)
## Defining The Problem
In busineess, customer churn, the rate at which customers stop using a product, is a major challenge. It's much cheaper to retain customer than it is to get new ones, so customer churn is valulable for businessses. This project builds a machine learning pipeline to predict whether a client is likely to leave based on demographics, services used, and billing information from the dataset. The goal is not only to achieve a strong predictive performance, but also to identify key factors that drive churn and translate model results into actionable businesss insights.

#### Dataset and Variables
Source: [IBM Telecom Customer Churn Datsset](https://www.kaggle.com/datasets/blastchar/telco-customer-churn/data)
Target Variable: Churn (Yes/No)

**The dataset includes the following variables**
<br>**Customer Demographic**
1. customerID: a unique string given to each customer
2. gender: Whether customer is male or female
3. SeniorCitizen: Whether the customer is a senior citizen or not (1, 0)
4. Partner: Whether the customer has a partner or not (Yes, No)
5. Dependents: Whether the customer has dependents or not (Yes, No)
<br>**Service Usage** 
6. PhoneService: Whether the customer has a phone service or not (Yes, No)
7. MultipleLines: Whether the customer has multiple lines or not (Yes, No, No phone service)
8. InternetService: Customer’s internet service provider (DSL, Fiber optic, No)
9. OnlineSecurity: Whether the customer has online security or not (Yes, No, No internet service)
10. OnlineBackup: Whether the customer has online backup or not (Yes, No, No internet service)
11. DeviceProtection: Whether the customer has device protection or not (Yes, No, No internet service)
12. TechSupport: Whether the customer has tech support or not (Yes, No, No internet service)
13. StreamingTV: Whether the customer has streaming TV or not (Yes, No, No internet service)
14. StreamingMovies: Whether the customer has streaming movies or not (Yes, No, No internet service)
<br>**Account Information**
15. tenure: Number of months the customer has stayed with the company
16. Contract: The contract term of the customer (Month-to-month, One year, Two year)
17. PaperlessBilling: Whether the customer has paperless billing or not (Yes, No)
18. PaymentMethod: The customer’s payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic))
<br>**Charges**
19. MonthlyCharges: The amount charged to the customer monthly
20. TotalCharges: The total amount charged to the customer
<br>**Target Variable**
21. Churn: Whether the customer churned or not (Yes or No)


## The Approach
### Preprocessing
Utilized a ColumnTransfomer and Pipeline to ensure clean & reporducible processing of:
1. Numerical Features (median imputation, standard scaling)
2. Categorical Features (most-frequent imputation, one-hot encoding)
3. Ordinal Features (contract length encoded with [month-to-month, one year, two years] -> [0, 1, 2])
Prevented data leakage & allowed model swapping.

### Model Evaluation
Models Evaluated: Logistic Regression, Random Forrest, XGBoost
Cross-validation utilized for model selection
<img width="490" height="61" alt="Screenshot 2026-01-09 at 2 12 34 PM" src="https://github.com/user-attachments/assets/54cb3c1e-0fea-46a8-91d3-427f7a105003" />
Logistic Regression was chosen due to having the highest average ROC-AUC mean.

### Exploratory Data Analysis
Categorical features were compared to churn using bar charts, while numerical features used histograms and box plots.

## The Results
### Performance
<img width="482" height="189" alt="Screenshot 2026-01-09 at 2 23 41 PM" src="https://github.com/user-attachments/assets/2d018819-835e-413c-8d14-54d05f07f8f2" />
<br>[0 refers to Not Churn, while 1 refers to Churn]
### Key Insights
<img width="968" height="528" alt="image" src="https://github.com/user-attachments/assets/dc5885db-77ee-4e3f-bea6-39febca5a8af" />
<br>Features that increase churn risk include: utilizing fiber optic as an internet service and Electronic check as a payment method.
<br>In addition, according to the EDA, 
## Tools and Technologies
* Python
* Pandas, Numpy
* scikit-learn
* XGBoost
* matplotlib, seaborn
* Jupyter Notebook
## Conclusion

