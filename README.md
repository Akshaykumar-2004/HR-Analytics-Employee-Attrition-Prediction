# HR Analytics & Employee Attrition Prediction

## Overview
This project analyzes the IBM HR Analytics dataset to uncover the root causes of employee attrition and builds a predictive machine learning model to identify employees at high risk of leaving. The analysis aims to provide actionable insights for the HR department to reduce turnover and retain valuable talent.

## Dataset
The project uses the "IBM HR Analytics Employee Attrition & Performance" dataset from Kaggle. For a more realistic scenario, the single CSV was split into three simulated data sources: general employee data, satisfaction survey data, and manager performance data.

## Methodology
1.  **ETL Process:** An automated Python script using SQLAlchemy and Pandas was created to extract data from the simulated CSV files and load them into a central SQLite database (`hr_analytics.db`). Logging was implemented for monitoring.
2.  **SQL Aggregation:** Connected to the SQLite database and used SQL `JOIN` statements to merge the three tables (`employee_general_data`, `employee_survey_data`, `manager_survey_data`) into a single master DataFrame for analysis.
3.  **Exploratory Data Analysis (EDA) & Feature Engineering:**
    * Calculated the overall attrition rate.
    * Visualized attrition patterns across departments, income levels, salary hikes, job satisfaction, work-life balance, and employee tenure using Seaborn and Matplotlib.
    * Engineered new features like `Attrition_numeric`, `AgeGroup`, and mapped numerical satisfaction scores to labels (e.g., 'Low', 'High') for clearer analysis.
4.  **Predictive Modeling (Logistic Regression):**
    * Prepared data for modeling by converting categorical features into numerical format using one-hot encoding (`pd.get_dummies`).
    * Split the data into training (80%) and testing (20%) sets using `train_test_split`.
    * Scaled numerical features using `StandardScaler`.
    * Trained a Logistic Regression model using Scikit-learn to predict `Attrition_numeric`.
    * Evaluated model performance using Accuracy, Confusion Matrix, and Classification Report (Precision, Recall, F1-Score).
5.  **Prediction on New Data:** Demonstrated how to use the trained model and scaler to predict the attrition risk (including probability) for hypothetical new employee profiles.

## Key Questions Answered & Insights
* **Overall Attrition Rate:** What percentage of employees are leaving? (Calculated rate)
* **Leaky Departments:** Which departments face the highest attrition? (R&D had the highest count)
* **Compensation Impact:** Do lower income or smaller salary hikes correlate with leaving? (Leavers tend to have lower median income; salary hike showed less difference)
* **Burnout Factors:** Are low job satisfaction or poor work-life balance major drivers? (Yes, employees with 'Low' satisfaction or 'Bad' work-life balance leave more often)
* **Loyalty Puzzle:** Are new hires or long-term employees leaving? (Significant attrition occurs within the first 0-2 years)
* **Prediction:** Can we predict who is likely to leave? (Yes, the Logistic Regression model achieved ~88% accuracy, identifying key risk factors)

## Technologies Used
* Python
* Pandas, NumPy
* SQLAlchemy, SQLite
* Matplotlib, Seaborn
* Scikit-learn (LogisticRegression, train_test_split, StandardScaler, metrics)
* Jupyter Notebook / Google Colab

## Reporting
The final cleaned data (`data_for_dashboard.csv`) was exported for visualization in Power BI, enabling the creation of an interactive dashboard for managers.
