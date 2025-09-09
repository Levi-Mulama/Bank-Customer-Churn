# Bank Customer Churn Prediction

This project explores and predicts **customer churn** for a bank using machine learning.  
The dataset contains details about customers such as age, tenure, balance, products, credit score, and whether they churned (left the bank) or not.  

The goal is to understand **what factors drive churn** and to build a model that can predict which customers are likely to leave, helping banks improve retention strategies.

---

## Dataset
- **Source**: [Kaggle - Bank Customer Churn Dataset](https://www.kaggle.com/datasets/gauravtopre/bank-customer-churn-dataset)  
- **Size**: 10,000 rows × 14 columns (original; reduced after cleaning)  
- **Key Columns**:  
  - `credit_score` → customer’s credit score  
  - `age` → customer’s age  
  - `tenure` → years with the bank  
  - `balance` → customer’s account balance  
  - `num_of_products` → number of bank products used  
  - `is_active_member` → whether customer is active  
  - `estimated_salary` → salary estimate  
  - `exited` (renamed to `churn`) → 1 if customer left, 0 if stayed  
  - Other: `geography` (country), `gender`, `has_cr_card`

---

## Tools & Libraries
- **Python 3**
- **Jupyter Notebook**
- **Pandas** (data handling)  
- **NumPy** (numerical operations)  
- **Matplotlib & Seaborn** (visualization)  
- **Scikit-learn** (ML models, preprocessing, evaluation, tuning)  
- **Imbalanced-learn** (SMOTE for handling class imbalance)

---

## Project Workflow
1. Data Loading & Initial Exploration  
   - Load dataset from CSV using pandas.  
   - Display first few rows (head), data info, descriptive statistics (describe), and extended preview (head(21)).  

2. Data Cleaning  
   - Drop unnecessary columns (e.g., customer_id).  
   - Rename columns for clarity (e.g., products_number to num_products).  
   - Check for missing values, duplicates, and re-verify data info/describe.  

3. Preprocessing & Feature Engineering  
   - One-hot encode categorical variables (e.g., country).  
   - Binary encode gender (Male=1, Female=0).  
   - Scale numeric features using StandardScaler (e.g., credit_score, age, tenure, balance, etc.).  

4. Train/Test Split  
   - Split features (X) and target (y=churn) into training/testing sets (80/20 split with stratification).  

5. Modeling  
   - Logistic Regression (baseline training and prediction).  
   - Decision Tree (baseline with max_depth=5, and class-weighted variant for imbalance).  
   - Random Forest (baseline with class_weight='balanced', tuned with GridSearchCV on parameters like n_estimators, max_depth, etc., and variant with SMOTE oversampling).  
   - Neural Networks (planned for additional comparison).  

6. Model Evaluation  
   - Individual metrics for each model (accuracy, classification report, confusion matrix).  
   - Feature importance extraction (from class-weighted Decision Tree and Random Forest).  

7. Model Comparison & Conclusion  
   - Compile metrics (accuracy, precision, recall, F1-score for churn class) into a DataFrame with highlighting.  
   - Visualize comparison with a heatmap.  
   - Generate conclusions (best models per metric) and recommend overall best (Random Forest Tuned based on F1-score).  

8. Feature Importance Analysis  
   - Extract and sort importances from tuned Random Forest.  
   - Visualize top 10 features with a colorful barplot (using seaborn).  

9. Correlation & Key Insights  
   - Compute correlations for top features with churn.  
   - Visualize correlation heatmap (using seaborn with coolwarm cmap).  

10. Exploratory Data Analysis (EDA) & Visualizations  
    - Recreate 'country' column from one-hot encoded dummies.  
    - Countplots for churn by geography (country), age groups (binned), and activity status (is_active).  

11. Insights Report (`Insights.md`)  
    - Summarize key findings.  

12. Power BI Dashboard (Interactive Reporting)  
    - Create dashboard for visualizing churn insights and predictions.  

---

## Key Results & Findings
- **Best Model**: Random Forest (Tuned) with 84% accuracy and 0.63 F1-score for churn class (balances precision and recall).  
- **Top Churn Drivers** (from feature importance): Age (highest), Number of Products, Balance, Estimated Salary, Credit Score.  
- **Insights**:  
  - Higher churn in older age groups (40+).  
  - Inactive members and customers from Germany show higher churn rates.  
  - Models like Random Forest with SMOTE improve recall for churn prediction, useful for retention efforts.  

---

## Goal
Build a predictive model that can **classify customers as churn or not churn** with good accuracy, and identify the **key drivers of churn**.

---

Author: **Levi Mulama**  
Aspiring Data Analyst | IT Personel | Data Science Enthusiast  