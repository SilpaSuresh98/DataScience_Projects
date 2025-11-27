**Project Summary**

This project analyzes employee performance at INX Future Inc. to identify key drivers and predict performance ratings. Using EDA, statistical tests, and machine learning models, we determined the most influential factors and built a predictive system useful for HR decision-making and performance improvement.

**Models used and Why? :**

1. Random Forest — For handling mixed features & establishing a baseline

Why it fits:

    - Dataset contains both categorical and numerical variables, and Random Forest handles this mixture naturally.

    - It deals well with non-linear relationships, which EDA showed (e.g., salary hike vs performance is not linear).

    - Good for a baseline benchmark because it is robust even without heavy tuning.


2. XGBoost — For capturing complex feature interactions

Why it:

    - Dataset has strong feature interactions, like Work-Life Balance × Env. Satisfaction × Job Involvement.

    - XGBoost captures these interactions much better than RF or SVM.

    - XGBoost handles imbalanced classes (Performance Rating 4 is rare) better via built-in regularization.


3. LightGBM — Best choice for tabular HR datasets

Why it fits:

    - LightGBM is ideal when many features have ordered categorical levels and numeric distributions, exactly like INX future emplloyee data.

    - It handles feature importance cleanly — helping to discover top drivers (like Work-Life Balance & Salary Hike %).

    - It gave the highest accuracy and best generalization, proving it matches the dataset's patterns best.


4. CatBoost — Perfect for heavy categorical columns

Why it fits:

    - Dataset includes many categorical features:

    EmpDepartment

    EmpJobRole

    EducationBackground

    BusinessTravelFrequency

    MaritalStatus

    - CatBoost naturally handles categorical columns without one-hot encoding, reducing dimensionality and overfitting.

   - It performed strongly because dataset has multiple human-related factors — CatBoost is known to excel on HR datasets.


5. SVM — To check dataset linearity & as a contrast model

Why it fits:

- SVM helps verify whether the dataset is linearly separable.

- Dataset contains complex nonlinear patterns, so SVM performed weakest — confirming boosting was necessary.


**Most important features Used**

1. Work-Life Balance

    - This was the strongest predictor of performance. Employees with better work-life balance consistently showed higher performance - ratings. This aligns with the dataset patterns where employees rated “Good/Excellent” also reported high work-life balance scores.

2. EmpLastSalaryHikePercent (Salary Hike %)

    - ANOVA and model importance showed that employees receiving higher salary hikes tend to achieve better performance levels. This makes   sense because salary increments reflect both motivation and reward for contribution.

3. EmpEnvironmentSatisfaction

    - Higher environment satisfaction scores strongly correlated with Excellent or Outstanding performance. This feature ranked consistently high in LightGBM importance, indicating employees in supportive environments perform better.

4. YearsSinceLastPromotion

    - Employees who had long gaps without promotions were more likely to have lower performance ratings. This feature captured career stagnation and its impact on motivation.

5. DistanceFromHome

    - Employees living farther from the workplace showed slightly lower performance, reflecting fatigue, commute stress, and reduced work-life balance.

Why These Features Were Selected?

    - They appeared repeatedly among the top-10 features across LightGBM, CatBoost, and Random Forest importance charts.

    - They showed statistically significant differences across performance groups (via Chi-square and ANOVA tests).

    - They had business relevance, directly influencing employee well-being, motivation, and job satisfaction.

    - They explained the patterns observed in EDA (higher ratings clustered around better workplace and compensation conditions).


**Techniques and Tools Used in the Project:**
The project used label encoding, one-hot encoding, scaling , and SMOTE-based resampling to address class imbalance. Extensive EDA, correlation analysis, hypothesis testing, and outlier checks were performed. Modeling and analysis were done using Python, Pandas, NumPy, Scikit-learn, XGBoost, LightGBM, CatBoost, Matplotlib, and Seaborn within Jupyter Notebook.