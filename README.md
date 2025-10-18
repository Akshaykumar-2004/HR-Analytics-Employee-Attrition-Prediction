# HR Analytics & Employee Attrition Prediction

## Overview
[cite_start]This project analyzes the IBM HR Analytics dataset to uncover the root causes of employee attrition and builds a predictive machine learning model to identify employees at risk of leaving[cite: 1685, 1692]. [cite_start]The goal is to provide actionable insights for HR to reduce turnover and a tool for proactive intervention[cite: 1700].

## Business Problems / Mission Goals
[cite_start]The analysis aims to solve five critical mysteries for the business[cite: 1695]:
1.  [cite_start]**The Leaky Departments:** Identify the overall attrition rate and the departments with the highest turnover[cite: 1696].
2.  [cite_start]**The Money Question:** Investigate the link between income, salary hike, and attrition[cite: 1697].
3.  [cite_start]**The Burnout Factor:** Determine if low job satisfaction or poor work-life balance drives employees to leave[cite: 1698].
4.  [cite_start]**The Loyalty Puzzle:** Uncover whether the company is losing long-term employees or newer hires[cite: 1699].
5.  [cite_start]**The Crystal Ball (Prediction):** Build a machine learning model to predict the likelihood of an employee leaving[cite: 1700].

## Dataset
[cite_start]The project uses the "IBM HR Analytics Employee Attrition & Performance" dataset obtained from Kaggle[cite: 1702, 1703]. [cite_start]The single CSV file (`WA_Fn-UseC_-HR-Employee-Attrition.csv`) was used for analysis[cite: 1704].

## Methodology
1.  **ETL Process:**
    * [cite_start]An automated Python script using Pandas and SQLAlchemy was developed to read the source CSV and load it into a structured SQLite database (`hr_analytics.db`)[cite: 1725, 1735, 1741, 1746].
    * [cite_start]Logging was implemented to track the ingestion process[cite: 1730, 1732].
2.  **Data Loading & Preparation (Python):**
    * [cite_start]Connected to the SQLite database and loaded the `hr_data` table into a Pandas DataFrame[cite: 1761, 1764].
    * [cite_start]Performed initial checks using `.head()` and `.info()`[cite: 1766, 1767].
    * **Feature Engineering:** Created new columns for easier analysis:
        * [cite_start]`Attrition_numeric` (Yes=1, No=0)[cite: 1772].
        * [cite_start]`AgeGroup` (categorizing age into bins)[cite: 1774].
        * [cite_start]`JobSatisfaction_label` (mapping numeric score to text)[cite: 1776].
        * [cite_start]`WorkLifeBalance_label` (mapping numeric score to text)[cite: 1802].
    * [cite_start]Checked for missing values (none found in this dataset)[cite: 1777].
3.  **Exploratory Data Analysis (EDA):**
    * [cite_start]Calculated the overall attrition rate[cite: 1790].
    * [cite_start]Visualized attrition counts by `Department` using Seaborn countplot[cite: 1793].
    * [cite_start]Compared `MonthlyIncome` and `PercentSalaryHike` distributions between attrited and non-attrited employees using box plots[cite: 1797].
    * [cite_start]Analyzed the impact of `JobSatisfaction` and `WorkLifeBalance` on attrition using countplots[cite: 1801, 1802].
    * [cite_start]Examined the distribution of `YearsAtCompany` for employees who left using a histogram[cite: 1806].
4.  **Predictive Modeling (Logistic Regression):**
    * [cite_start]Prepared data for modeling by converting categorical features to numerical using `pd.get_dummies`[cite: 1821].
    * [cite_start]Dropped non-predictive or redundant columns[cite: 1823].
    * [cite_start]Separated features (X) and target variable (y = `Attrition_numeric`)[cite: 1824, 1825].
    * [cite_start]Split data into 80% training and 20% testing sets using `train_test_split`[cite: 1828].
    * [cite_start]Scaled numerical features using `StandardScaler`[cite: 1829].
    * [cite_start]Trained a `LogisticRegression` model on the scaled training data[cite: 1830].
    * [cite_start]Made predictions on the scaled test data[cite: 1831].
    * [cite_start]Evaluated model performance using Accuracy, Confusion Matrix, and Classification Report[cite: 1832, 1833].
5.  **Prediction on New Data:**
    * [cite_start]Created hypothetical new employee profiles[cite: 1840, 1842].
    * [cite_start]Prepared and scaled the new data using the same steps as the training data[cite: 1846, 1850, 1854].
    * [cite_start]Used the trained model to predict the probability of leaving and assigned a risk level[cite: 1855, 1856].

## Key Findings
* [cite_start]The overall attrition rate is approximately 16.12%[cite: 1793]. [cite_start]R&D department has the highest count of employees leaving[cite: 1793].
* [cite_start]Employees who leave tend to have lower median monthly incomes[cite: 1798]. [cite_start]Salary hike percentage showed no significant difference[cite: 1798].
* [cite_start]Lower Job Satisfaction and Work-Life Balance are strongly correlated with higher attrition rates[cite: 1801, 1802].
* [cite_start]A significant number of employees leave within the first 0-2 years at the company[cite: 1806].
* [cite_start]The Logistic Regression model achieved ~88% accuracy but struggled with recalling employees who actually left (low recall for class 1)[cite: 1832, 1833]. [cite_start]Model interpretation (coefficients) identified Overtime as a key predictor[cite: 17].
* [cite_start]The model successfully predicted risk levels for new hypothetical employees[cite: 1857, 1858].

## Technologies Used
* [cite_start]Python [cite: 1729, 1759]
* [cite_start]Pandas [cite: 1729, 1759]
* [cite_start]NumPy [cite: 1759]
* [cite_start]SQLAlchemy [cite: 1729]
* [cite_start]SQLite [cite: 1735, 1761]
* [cite_start]Matplotlib [cite: 1759]
* [cite_start]Seaborn [cite: 1759, 1760]
* [cite_start]Scikit-learn (LogisticRegression, train_test_split, StandardScaler, accuracy_score, confusion_matrix, classification_report) [cite: 1813, 1814, 1815, 1816, 1829, 1830, 1832]
* [cite_start]Jupyter Notebook [cite: 1705]
* [cite_start]Power BI (Planned for final dashboarding) [cite: 1862]
