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

## Concept Used
- **Exploratory Data Analysis (EDA)**
- **Feature Engineering**
- **Logistic Regression**
- **Precision vs Recall Tradeoff**

## Key Insights & Business Recommendations
1. **EDA Findings**: The initial data exploration revealed significant insights into loan repayment trends based on employment title, home ownership status, and loan grades.
2. **Feature Importance**: Analysis indicated that employment title, verification status, DTI, and mortgage status are crucial in predicting loan repayment.
3. **Model Performance**: Evaluated using ROC AUC curve, precision-recall curve, and classification reports. The model aims to balance the trade-offs between predicting defaulters and minimizing false positives to reduce potential losses.

## Results Evaluation
- **ROC AUC Curve**: Helps in understanding the model's capability to distinguish between classes.
- **Precision Recall Curve**: Provides insights into the trade-off between precision and recall, important for making lending decisions.
- **Classification Report**: Summarizes the model accuracy, precision, recall, and F1 score.

## Tradeoff Questions and Answers
- **Detecting Real Defaulters**: Emphasis on precision to minimize false positives, enhancing profitability by reducing the chance of lending to non-repaying individuals.
- **Minimizing Non-Performing Assets (NPAs)**: Focus on conservative lending strategies to ensure loans are disbursed to applicants most likely to repay.

## Actionable Insights
- **Adjusting Interest Rates**: Setting interest rates based on the predicted probability of repayment to manage risk effectively.
- **Focusing on Significant Predictors**: Prioritizing lending decisions based on employment verification, DTI, and mortgage-related attributes.

## Conclusion
This project provides LoanTap with a robust analytical framework to enhance their personal loan underwriting processes, thereby optimizing their risk management and customer satisfaction strategies.

## Usage
For reproducing the results, please follow the Jupyter notebooks provided in the repository which detail all the analytical steps and modeling procedures used in this project.

## Requirements
Python 3.8+, Pandas, NumPy, Matplotlib, Seaborn, Scikit-Learn, Imbalanced-Learn
