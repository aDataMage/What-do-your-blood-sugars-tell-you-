# What-do-your-blood-sugars-tell-you-
![alt text](img/image.jpg)

### Project Overview
This project involves analyzing a dataset for predicting the likelihood of diabetes using several features such as glucose levels, blood pressure, insulin, and body mass index (BMI). The primary objective is to build a predictive model that accurately identifies individuals at risk of diabetes based on both biological factors and family history.

### Data Preprocessing and Feature Engineering
- **Outliers Handling**: Outliers were identified and handled using both the IQR method and a custom technique based on the z-score (3 standard deviations). This ensured that extreme values did not unduly influence the model.
- **Missing Values**: Missing values, primarily represented as zeros in columns like **Insulin**, **SkinThickness**, and **BloodPressure**, were replaced by predicted values using other available features rather than simple mean imputation. This enhanced the data’s predictive power.
- **Feature Scaling**: The dataset was scaled using methods appropriate for each feature, used RobustScalar to ensure the outliers that weren't dealt with doesn't affect the model performance, ensuring that no feature disproportionately impacted the model.
- **Mutual Information Analysis**: A mutual information analysis was performed to rank features based on their importance in predicting the target variable (diabetes outcome). Key features such as **Glucose**, **BloodPressure**, **Insulin**, and **Age** had the highest mutual information scores, indicating they are most predictive. features were also scaled by theri importance to the target variable.

### Feature Importance

Based on mutual information, the most important features for predicting diabetes are:
|  **Feature** | **Mutual Information** |
|:---:|:---:|
|  Insulin   |  0.385976 |
|  SkinThickness   | 0.262024  |
| Glucose  | 0.170098  |
| BloodPressure  | 0.135170  |
| BMI  | 0.106836  |
| Age  | 0.098755  |
| DiabetesPedigreeFunction  | 0.027636  |
| Pregnancies  | 0.026698  |
|-- |- -|

Less important features like **Pregnancies** and **DiabetesPedigreeFunction** were also retained but are less informative.

### Multicollinearity Detection
- Variance Inflation Factor (VIF) analysis revealed significant multicollinearity among features such as **BMI** (VIF: 18.4) and **Glucose** (VIF: 16.7).
- Which wasn't addressed as the modelling algorithem used are not affected by it.

### Modeling Approaches
Several classification algorithms were explored, including:
- **Logistic Regression**
- **RandomForestClassifier**
- **GradientBoostingClassifier**
- **XGBClassifier**
- **SVC**
- **GaussianNB**

SMOTE was used to ensure that class imbalances did not bias the model results, and **class weighting** was adjusted to further handle the imbalanced target variable.

The final model was a combination of the best model with the best paramiters found using RandomSearchCV. and was created with StackingClassifier. Achiving an accuracy of 0.95.

### Model Evaluation
The models were evaluated using the following metrics:
- **Accuracy**: The proportion of correct predictions.
- **Precision**: The proportion of true positive predictions among all positive predictions.
- **Recall**: The proportion of true positive predictions among all actual positive instances.
- **F1 Score**: The harmonic mean of precision and recall.
- **ROC-AUC**: The area under the receiver operating characteristic curve, which measures the model's ability to distinguish between classes.

### Results
- The models achieved strong performance,`StackingClassifier`. Achiving an accuracy of 0.95.
- To improve performance further, feature engineering, such as combining correlated features and scaling, played a crucial role.
- The results also highlighted the importance of **Glucose**, **Insulin**, and **Age** in predicting diabetes.

### Handling Real-World Scenarios
- The Person class was created to handle missing values and predict the likelihood of diabetes based on the available data, filling the missing values with the mean.
- The Person class was also used to predict the likelihood of diabetes for a new patient based on their medical history and demographic information.

### Future Work
- **Hyperparameter Tuning**: Further hyperparameter tuning could be performed to optimize the model's performance.
- **Feature Selection**: Advanced feature selection techniques like recursive feature elimination could be used to identify the most predictive features.
- **Ensemble Methods**: Additional ensemble methods like AdaBoost could be explored to further enhance model performance.
- **Website Implementation**: I plan on creating a website where users can input their medical data and receive a prediction of their diabetes risk.

### Conclusion
This notebook provides a comprehensive workflow for data preprocessing, feature engineering, and model building to predict diabetes. The approach is robust, handling issues like outliers, missing values, and multicollinearity, while leveraging key features like **Glucose**, **SkinThickness** and **Insulin** to achieve high prediction accuracy.

### 📚 Libraries
In this notebook, we will use the following libraries:
- `numpy` and `pandas` for data manipulation
- `matplotlib` and `seaborn` for data visualization
- `sklearn` for model building and evaluation
- `xgboost` for gradient boosting algorithms

### 📝 Note
This notebook is a work in progress, and I will continue to update it with new insights and model improvements. If you have any suggestions or feedback, please feel free to leave a comment.
This model was trained for a competition with limited data and features and is in no way a substitute for professional medical advice. Always consult a healthcare provider for medical advice and treatment.

>[Linkedin: Adejori Eniola]('https://www.linkedin.com/in/adatamage/')