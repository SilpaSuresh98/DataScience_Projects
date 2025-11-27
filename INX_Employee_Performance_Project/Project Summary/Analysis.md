**Dataset source**

File path used in this project: 

    'data/raw/INX_Future_Inc_Employee_Performance_CDS_Project2_Data_V1.8.xlsx'

**Dataset Information**

The dataset provided by IABAC includes employee-level information such as:

- Personal attributes (Age, Gender, Marital Status, Distance From Home, etc.)

- Job attributes (Job Role, Department, Travel Frequency, Overtime, Training Times, etc.)

- Work metrics (Job Involvement, Environment Satisfaction, Work Life Balance, Performance Rating, etc.)

- Compensation and career attributes (Salary Hike %, Years Since Last Promotion, Experience Years, etc.)

**Analysis Performed**

1. Data Validation:

    - The dataset contains 1200 rows and 28 columns with a mix of numerical and categorical variables.

    - No missing values were found; the dataset is clean and ready for analysis.

    - No duplicate rows were present.

    - Categorical and numerical features were identified and separated for preprocessing.

    - PerformanceRating classes available were 2 (Good), 3 (Excellent), 4 (Outstanding) — class “1 = Low” was not present in the dataset.

2. Exploratory Data Analysis (EDA):

    -> Categorical Feature Insights:

        - Department-wise performance showed Development and Data Science employees performing the best, while Sales and Finance had comparatively lower performance.

        - Gender, Business Travel Frequency, and Overtime showed no statistically significant association with performance (Chi-square tests: p > 0.05).

        - EmpDepartment showed strong statistical significance with performance levels (p < 0.001).

    -> Numerical Feature Insights:

        - ANOVA tests revealed significant differences in Salary Hike Percent across performance groups (p < 0.001).

        - Features like Work-Life Balance, Environment Satisfaction, Job Involvement, Years Since Last Promotion, Distance From Home displayed  strong patterns correlating with performance.

        - Outliers detected in features like DistanceFromHome and SalaryHikePercent were validated and not removed unless impactful.

3. Feature Engineering:

    - Applied Label Encoding to binary variables (Gender, OverTime, Attrition).

    - Applied One-Hot Encoding to multi-category features (Department, JobRole, EducationBackground, etc.).

    - StandardScaler used where required (SVM, Logistic models); tree-based models used raw values.

    - Resampled training data using SMOTE to balance class distribution.

    - Target values (PerformanceRating) were label-encoded for XGBoost tuning and inverse-transformed before final evaluation.

4. Hypothesis Testing

    - Chi-square tests: Only EmpDepartment showed significant association with performance.

    - ANOVA tests: SalaryHikePercent significantly differs across performance groups (p < 0.001). Age and Job Involvement were not significant.

    -  These findings helped confirm feature importance trends.

5. Modeling Summary

Models trained:

    - RandomForest

    - XGBoost

    - CatBoost

    - LightGBM

    - SVM

Metrics used: Accuracy, Precision, Recall, F1-Score, ROC-AUC (OVR), Confusion Matrix.

Best models before tuning:
    LightGBM → 93.7%, 
    CatBoost → 93.0%

After tuning:
    LightGBM → 93.7%
    CatBoost → 93.3%
    XGBoost → 93.3%

Boosting models outperformed all others.

6. Key Business Insights

    - Higher Work-Life Balance, Salary Hike %, and Environment Satisfaction significantly drive high performance.

    - Employees farther from home often show lower performance.

    - Lack of promotion for many years negatively affects performance.

    - Sales & Finance departments require focused performance improvement strategies.