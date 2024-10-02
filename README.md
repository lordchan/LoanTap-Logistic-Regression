# LoanTap Creditworthiness Evaluation Model

## Overview
LoanTap is an innovative online platform that delivers customized loan products to millennials, focusing on instant, flexible loans with consumer-friendly terms. This project is part of LoanTap's initiative to enhance their underwriting processes by evaluating the creditworthiness of both MSMEs and individuals. Specifically, this case study concentrates on the underwriting process for Personal Loans.

## Problem Statement
The objective is to determine the creditworthiness of an individual based on a given set of attributes. The decision involves whether a credit line should be extended and under what repayment terms.

## Dataset
`LoanTapData.csv` is used, which includes various attributes such as loan amount, interest rates, employment details, and more, detailed in the data dictionary below.

## Data Dictionary
- `loan_amnt`: The amount of the loan applied for by the borrower.
- `term`: The loan term in months (36 or 60).
- `int_rate`: Interest rate on the loan.
- `installment`: Monthly payment owed if the loan originates.
- `grade`, `sub_grade`: LoanTap assigned loan grade and subgrade.
- `emp_title`: Job title supplied by the borrower.
- `emp_length`: Employment length in years.
- `home_ownership`: Home ownership status provided by the borrower.
- `annual_inc`: Self-reported annual income.
- `verification_status`: Indicates if income was verified by LoanTap.
- `issue_d`: The month the loan was funded.
- `loan_status`: Current status of the loan (target variable).
- `purpose`, `title`: Category and title provided by the borrower for the loan request.
- `dti`: Debt-to-income ratio.
- `earliest_cr_line`: Month the borrower's earliest reported credit line was opened.
- `open_acc`: Number of open credit lines in the borrower's credit file.
- `pub_rec`, `revol_bal`, `revol_util`, `total_acc`, `initial_list_status`, `application_type`, `mort_acc`, `pub_rec_bankruptcies`, `Address`: Various other financial and personal details.

## Steps
- **Exploratory Data Analysis (EDA)**: Statistical Analysis, Univariate, Bivariate Analysis, Data Wrangling, Imputing missing values using KNN imputer, encoding categoring to numeric data,
- **Feature Engineering**: Normalization, transforming skewed data using box-cox transformation, treating outliers using Guassian Mixture Models, evaluating the clusters with AIC/BIC scores, dropping duplicates, checking for multicollinearity using VIF scores and dropping unnecessary columns.
- **Oversampling and Undersampling using SMOTE**
- **Fitting Logistic Regression model**
- **Precision vs Recall Tradeoff**

## Key Insights & Business Recommendations
1. **EDA Findings**: The initial data exploration revealed significant insights into loan repayment trends based on employment title, home ownership status, and loan grades.
2. **Feature Importance**: Analysis indicated that employment title, verification status, DTI, and mortgage status are crucial in predicting loan repayment.
3. **Model Performance**: Evaluated using ROC AUC curve, precision-recall curve, and classification reports. The model aims to balance the trade-offs between predicting defaulters and minimizing false positives to reduce potential losses.

## Results Evaluation
- **ROC AUC Curve**: Helps in understanding the model's capability to distinguish between classes.
- **Precision Recall Curve**: Provides insights into the trade-off between precision and recall, important for making lending decisions.
- **Classification Report**: Summarizes the model accuracy, precision, recall, and F1 score.
- Base model: F1 score: 90%, Specificity: 40%, Recall: 94%
- Optimum Threshold model: F1 score: 90%, Specificity: 50%, Recall: 93% 
- Weight Balanced model: F1 score: 86%, Specificity: 76%, Recall: 80%, precision: 93%
  
## Tradeoff Questions and Answers
- **Detecting Real Defaulters**: Emphasis on precision to minimize false positives, enhancing profitability by reducing the chance of lending to non-repaying individuals.
- **Minimizing Non-Performing Assets (NPAs)**: Focus on conservative lending strategies to ensure loans are disbursed to applicants most likely to repay.

## Actionable Insights
1. The percentage of people paying back the amount is 80% and those who didn't pay back is 20%. Which is a pretty big number. The bank should reduce the money given to unpaid people.
2. People whose home ownership is NONE or RENT have low chances of paying back. Whereas those having Mortage or OTHER have relatively better chances of paying back. So the Bank should focus on such customers.
3. We see that there is a high correlation between the grade and payback. The Bank can prioritize on this parameter to decide whether to give or not.
4. Also once we determine the probabilty of a person paying back. Bank can then set the interest rate before disbursing the loan. Because higher interest rate is highly correlated with payback percentage. Low interest rate -> good candidate, high interest rate -> risky candidate.
5. The Parameters that dont have a significant impact to determine credit worthiness are - Grade (since subgrade already provides the info), address, Purpose/title (it is text data and not very useful for logistic regression model), rent_one_hot (because it can be determined by those who dont have mortage or own home), application_type,term (because it is got from loan amount and duration).
6. After training the logistic regression model, the coefficient we get determines how important a parameter is. The Bank has to focus more on the parameters - Employee title, verification status, dti and mortage_one_hot. The parameters that are not so important are - initial_list_status, earliest_cr_line_date, public record, total accounts and revol_balance.
7. If bank focuses on precision they would not give to people who won't return back the money, this will reduce NPA. Low false positive rate will give us higher precision and more profit to bank. To achieve this we can use SMOTE with weight balancing model. This approach is effective when the bank wants to play safe.¶
8. If bank wants to maintain customer relation/satisfaction they could give loan to more risky customer, this way they will be less likely to reject a good customer. To achieve this, bank needs to focus on recall and reduce false negative rate. Model best suited for this is the one without oversampling and weight balancing.
9. If the Bank wants a best overall model with high precision and recall then I would suggest to use model2 with weight balancing and without oversampling. Using this we could be 80% sure that we are correctly classifying positive as positive and negative as negative. This model has good recall as well as specificity.
10. Threshold can be adjusted to increase precision and decrease recall or vice versa. The ideal threshold to maximise both precision and recall and thus maximise f1 score is 0.57 for model 1 (without oversampling/weight balancing) and 0.27 for model 2 (with oversampling/weight balancing).

## Conclusion
This project provides LoanTap with a robust analytical framework to enhance their personal loan underwriting processes, thereby optimizing their risk management and customer satisfaction strategies.

## Usage
For reproducing the results, please follow the Jupyter notebooks provided in the repository which detail all the analytical steps and modeling procedures used in this project.

## Requirements
Python 3.8+, Pandas, NumPy, Matplotlib, Seaborn, Scikit-Learn, Imbalanced-Learn
