# Customer Churn Prediction (IBM Telco Dataset)

## Defining the Problem
In business, customer churn—the rate at which customers stop using a product or service—is a major challenge. Retaining existing customers is significantly cheaper than acquiring new ones, making churn prediction a critical business task.

This project builds a machine learning pipeline to predict whether a customer is likely to churn, using demographic information, service usage, and billing data. Beyond predictive performance, the goal is to identify the key drivers of churn and translate model results into actionable business insights.

---

## Dataset and Variables
**Source:** [IBM Telco Customer Churn Dataset (Kaggle)](https://www.kaggle.com/datasets/blastchar/telco-customer-churn/data)

**Target Variable:** `Churn` (Yes / No)

### Customer Demographics
*   **customerID** Unique customer identifier
*   **gender** Male or Female
*   **SeniorCitizen** Whether the customer is a senior citizen (0, 1)
*   **Partner** Whether the customer has a partner (Yes, No)
*   **Dependents** Whether the customer has dependents (Yes, No)

### Service Usage
*   **PhoneService** Phone service subscription
*   **MultipleLines** Multiple phone lines
*   **InternetService** DSL, Fiber optic, or No internet
*   **OnlineSecurity** Online security service
*   **OnlineBackup** Online backup service
*   **DeviceProtection** Device protection service
*   **TechSupport** Technical support service
*   **StreamingTV** Streaming TV service
*   **StreamingMovies** Streaming movies service

### Account Information
*   **tenure** Number of months the customer has stayed with the company
*   **Contract** Month-to-month, One year, or Two year
*   **PaperlessBilling** Paperless billing enabled
*   **PaymentMethod** Payment method used

### Charges
*   **MonthlyCharges** Monthly amount charged
*   **TotalCharges** Total amount charged

### Target
*   **Churn** Whether the customer churned (Yes or No)

---

## Approach

### Data Preprocessing
A `ColumnTransformer` and `Pipeline` was used to ensure clean and reproducible preprocessing:

*   **Numerical Features:** Median imputation and Standard scaling.
*   **Categorical Features:** Most-frequent imputation and One-hot encoding.
*   **Ordinal Feature:** Contract length encoded as:
    *   Month-to-month → 0
    *   One year → 1
    *   Two year → 2

This approach prevents data leakage and allows seamless model swapping.

### Model Evaluation
Models evaluated:
1. Logistic Regression
2. Random Forest
3. XGBoost

Cross-validation was used with **ROC-AUC** as the primary evaluation metric. **Logistic Regression** was selected as the final model due to:
*   Highest average ROC-AUC
*   Model stability
*   Strong interpretability

### Exploratory Data Analysis (EDA)
*   Categorical variables analyzed using normalized bar charts.
*   Numerical variables explored using histograms and box plots.
*   Binning was used only for visualization, not modeling.

EDA highlighted strong relationships between churn and **tenure**, **contract type**, and **internet service**.

---

## Results

### Model Performance
The final model achieved a **ROC-AUC of ~0.86**, indicating strong predictive performance.
> *Note: 0 → Not Churn, 1 → Churn*

### Key Insights
*   **Customer tenure is the strongest predictor of churn:**
    *   Median tenure (churned): 10 months
    *   Median tenure (retained): 38 months
*   Customers with **month-to-month contracts**, **fiber optic internet**, and **electronic check payments** are more likely to churn.
*   **Longer contracts**, **automatic payments**, and **technical support services** significantly reduce churn risk.

These findings suggest that early retention strategies and incentives for long-term commitments can meaningfully reduce churn.

---

## Tools & Technologies
*   **Python** (pandas, NumPy)
*   **scikit-learn** (Preprocessing, Pipelines, Models)
*   **XGBoost** (Model benchmarking)
*   **Matplotlib & Seaborn** (Visualization)
*   **Jupyter Notebook**

---

## Conclusion
This project demonstrates an end-to-end churn prediction workflow, combining exploratory data analysis, robust preprocessing pipelines, cross-validated model selection, and interpretable results. The analysis highlights the importance of customer tenure and contract structure in churn behavior and provides actionable insights for improving customer retention.

