**Heart Failure Readmission Prediction Project**

**Overview**

This project aims to predict the likelihood of readmission for heart failure patients within 365 days of discharge using advanced machine learning techniques. Using data from the MIMIC-IV dataset, the study leverages logistic regression, XGBoost, Random Forest, and Support Vector Machine (SVM) models to identify patients at high risk of readmission. The insights gained from this study can help healthcare professionals implement preventive measures, improve patient outcomes, and optimize healthcare resources.

**Data Sources**

The project uses the MIMIC-IV dataset, which contains electronic health records of ICU patients. Data preprocessing includes extracting clinical features such as demographic information, comorbidities, ejection fraction, BNP, cholesterol levels, and blood pressure measurements. The extracted features were used to predict patient readmission within a year.

**Files**
- `group5_COMP90089.ipynb`: Main notebook containing the complete workflow, including data extraction, feature engineering, model building, and evaluation.
- `final_merged_data.csv`: Preprocessed dataset containing relevant clinical information used for model training and evaluation.
- `model_data.csv`: Dataset used for model training and testing after feature selection and engineering.

**Project Workflow**

1. **Data Extraction and Preparation**
   - Data was extracted from the MIMIC-IV dataset using SQL queries executed via Google BigQuery.
   - Important features such as heart failure ICD codes, ejection fraction, BNP, cholesterol, and blood pressure readings were extracted and merged.
   - Data cleaning included handling missing values using median imputation and standardizing features.

2. **Feature Engineering**
   - Key clinical features, such as NT-proBNP and troponin, were selected based on their relevance to heart failure.
   - Feature engineering involved creating average values for repeated measurements, ensuring representative feature values for each patient.
   - Handling class imbalance using SMOTETomek to balance the dataset for training.

3. **Model Building**
   - **Logistic Regression**: A baseline logistic regression model was implemented, and hyperparameter tuning was conducted using nested cross-validation to improve its performance.
   - **XGBoost**: Implemented to achieve better predictive performance, with hyperparameter tuning applied using a grid search.
   - **Random Forest**: Utilized to assess feature importance and explore an ensemble approach.
   - **Support Vector Machine (SVM)**: Tested as a non-linear approach to model readmission risk, with hyperparameter tuning done using random search.

4. **Evaluation**
   - Models were evaluated using metrics such as accuracy, precision, recall, F1-score, ROC-AUC, and average precision scores.
   - **XGBoost** achieved the highest accuracy, with a good balance between precision and recall, making it the most suitable model for clinical use.
   - The logistic regression model improved with hyperparameter tuning, but it still showed moderate performance compared to more complex models.

**Results**

- **Key Predictors**: NT-proBNP emerged as the most significant predictor, highlighting the importance of robust clinical features in predictive models.
- **Best Performing Model**: XGBoost outperformed the other models, demonstrating strong accuracy, precision, and recall for predicting readmission.
- **Model Limitations**: Imbalanced data and computational limitations affected the performance of some models, particularly the SVM. Additionally, the models were not validated on external datasets, raising concerns about generalizability.

**How to Run the Project**

1. Clone this repository to your local machine.
2. Set up Google Cloud credentials for BigQuery access.
4. Run the Jupyter notebook (`group5_COMP90089.ipynb`) to replicate the data extraction, preprocessing, model training, and evaluation steps.

**Dependencies**

- Python 3.7+
- Google BigQuery Python client
- Pandas, NumPy, Matplotlib, Seaborn
- Scikit-learn, Imbalanced-learn
- XGBoost