## Diabetes Prediction Using Machine Learning

## Project Overview

This project focuses on predicting the likelihood of diabetes using machine learning classification algorithms.

The project uses a dataset containing 1,00,000 records with medical and demographic attributes such as age, BMI, hypertension, heart disease, smoking history, HbA1c level, and blood glucose level.

The primary objective is to explore different classification algorithms, evaluate their performance, handle class imbalance, and identify a model that provides a reasonable balance between prediction accuracy and positive-class detection.

This project also includes a learning curve analysis to examine the model's training and validation performance and investigate potential overfitting.

## Objectives

- Perform exploratory data analysis (EDA) to understand the dataset.
- Preprocess the dataset and prepare features for machine learning.
- Understand and address class imbalance.
- Implement and compare multiple classification algorithms.
- Evaluate models using appropriate classification metrics.
- Analyze model performance using confusion matrices.
- Use a learning curve to investigate potential overfitting and generalization.

## Dataset Information

The dataset contains **1,00,000 records** and initially includes the following attributes:

| Feature | Description |
| Gender | Gender of the individual |
| Age | Age of the individual |
| Hypertension | Whether the individual has hypertension |
| Heart Disease | Whether the individual has heart disease |
| Smoking History | Individual's smoking history |
| BMI | Body Mass Index |
| HbA1c Level | HbA1c measurement |
| Blood Glucose Level | Blood glucose measurement |
| Diabetes | Target variable (0 or 1) |

### Class Distribution

The dataset contains an imbalanced target variable:

- Non-diabetic (0): 91.5%
- Diabetic (1): 8.5%

This imbalance makes accuracy alone an insufficient measure of model performance. Therefore, precision, recall, F1-score, and confusion matrices are also considered.

## Technologies & Libraries Used

- **Python** – Primary programming language
- **Pandas** – Data manipulation and analysis
- **NumPy** – Numerical computations
- **Matplotlib** – Data visualization
- **Seaborn** – Statistical visualization
- **Scikit-learn** – Machine learning algorithms and evaluation

## Project Workflow

### 1. Data Loading and Exploration

- Loaded the dataset using Pandas.
- Examined the initial records and statistical summaries.
- Explored the distribution of important features.
- Visualized blood glucose level distributions for diabetic and non-diabetic individuals.

### 2. Data Preprocessing

- Removed the `gender` column from the dataset.
- Converted categorical variables into numerical representations using One-Hot Encoding (`pd.get_dummies()`).
- Separated independent features (X) from the target variable (y).
- Divided the dataset into training and testing sets using an 80:20 split.
- Used stratified sampling to preserve the original class distribution in both sets.

### 3. Handling Class Imbalance

Since only 8.5% of the dataset belongs to the diabetic class, class imbalance was considered during model selection and evaluation.

The Logistic Regression and Random Forest models were configured with `class_weight='balanced'` to assign greater importance to the minority class.

### 4. Model Implementation

Three classification algorithms were implemented and evaluated.

**A. Logistic Regression**

- Used as a baseline classification algorithm.
- Configured with `max_iter=1000`.
- Applied balanced class weights to account for class imbalance.

**B. K-Nearest Neighbors (KNN)**

- Evaluated different values of K, ranging from 1 to 7.
- Compared the resulting accuracy and classification metrics.
- Identified the best-performing K value based on accuracy.

**C. Random Forest Classifier**

Implemented with the following hyperparameters:

- `n_estimators = 200`
- `max_depth = 18`
- `min_samples_split = 5`
- `min_samples_leaf = 3`
- `max_features = 'sqrt'`
- `class_weight = 'balanced'`
- `random_state = 42`

These settings were selected to control model complexity while maintaining predictive performance.

### 5. Model Evaluation

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

Special attention was given to the recall and F1-score of the diabetic class because identifying positive cases is particularly important in this prediction task.

### 6. Overfitting Analysis

A learning curve was generated for the Random Forest model using:

- Stratified K-Fold Cross-Validation (3 folds).
- Training sample sizes of 30%, 60%, and 100%.
- F1-score as the evaluation metric.

The training and cross-validation F1-scores were plotted against the number of training samples to examine model generalization and identify potential overfitting.

## 📈 Model Performance

The following results were obtained on the test dataset containing 20,000 records.

| Algorithm | Accuracy |
|---|---:|
| Logistic Regression | 89.01% |
| KNN (K=7) | 95.58% |
| Random Forest | 94.78% |

### Random Forest Classification Report

| Metric | Non-Diabetic (0) | Diabetic (1) |
|---|---:|---:|
| Precision | 0.98 | 0.66 |
| Recall | 0.96 | 0.81 |
| F1-Score | 0.97 | 0.72 |

**Overall Accuracy: 94.78%**

Random Forest achieved a diabetic-class recall of approximately 81%, meaning it correctly identified around 81% of the actual diabetic cases in the test dataset.

Although KNN achieved slightly higher overall accuracy, Random Forest provided a different balance between precision and recall for the minority class.


##  Key Learnings

Through this project, I gained practical experience in:

- Data preprocessing and exploratory data analysis.
- Working with imbalanced classification datasets.
- Implementing and comparing multiple machine learning algorithms.
- Understanding the trade-offs between precision and recall.
- Evaluating classification models using multiple performance metrics.
- Using cross-validation and learning curves to investigate model generalization.

## Disclaimer

This project is developed for educational and machine learning practice purposes only.

It is not a clinically validated diagnostic system and should not be used as a substitute for professional medical advice, diagnosis, or treatment.


