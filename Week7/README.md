# Week 7: Advanced Classification and Regression Modeling

This week's project covers two distinct machine learning tasks: a classification problem to detect SMS spam and a regression problem to predict California housing prices. Both analyses explore linear and non-linear models, robust evaluation techniques like k-fold cross-validation, and hyperparameter tuning.

---

## Part 1: SMS Spam Classification Analysis

This project extends the SMS spam detection analysis from Week 6 by introducing non-linear models and more advanced evaluation techniques to identify the best-performing model for classifying SMS messages.

*   **Notebook**: `Week_7_Linear_Classification_Non_Linear_Modeling.ipynb`
*   **Dataset**: SMS Spam Collection from the UCI Machine Learning Repository.
*   **Data Source**: https://raw.githubusercontent.com/justmarkham/pycon-2016-tutorial/master/data/sms.tsv

### Classification Methodology

The analysis follows a structured workflow to build, compare, and optimize a suite of classification models.

1.  **Data Preparation and EDA**:
    *   The SMS dataset was loaded and preprocessed by converting labels to a numerical format (0 for 'ham', 1 for 'spam').
    *   Text cleaning involved removing punctuation, converting to lowercase, and filtering out common English stop words.
    *   Exploratory Data Analysis (EDA) was performed to understand the data, including analyzing word frequencies and the distribution of message lengths.

2.  **Feature Engineering**:
    *   The cleaned text messages were transformed into a numerical format suitable for machine learning using `TfidfVectorizer`, which reflects the importance of a word in a document relative to a collection of documents.

3.  **Model Building and Initial Evaluation**:
    *   The dataset was split into training (75%) and testing (25%) sets.
    *   A comprehensive set of six models was trained and evaluated:
        *   **Linear Models**: Logistic Regression, Support Vector Machine (SVM).
        *   **Non-Linear Models**: Decision Tree, Random Forest, XGBoost, CatBoost.

4.  **K-Fold Cross-Validation**:
    *   To ensure the models' performance was robust and not dependent on a single train-test split, 5-fold cross-validation was performed on the training data for all six models.
    *   This provided a more reliable estimate of each model's generalization performance.

5.  **Hyperparameter Tuning**:
    *   `GridSearchCV` was used to systematically search for the optimal hyperparameters for each of the six models, further enhancing their predictive power.

6.  **Final Evaluation and Comparison**:
    *   The tuned models were evaluated on the held-out test set.
    *   A detailed comparison was conducted based on key metrics like Accuracy, Precision, Recall, and F1-score, with a special focus on identifying spam (class 1).

### Classification Model Performance and Comparison

The project involved a multi-stage comparison to determine the most effective model.

#### Initial Model Performance (Before Tuning)

Even before extensive tuning, the ensemble and more complex models showed strong performance. The Support Vector Machine (SVM) stood out with the highest accuracy and an excellent balance of precision and recall for the spam class.

*   **SVM Accuracy**: 98.5%
*   **Random Forest Accuracy**: 98.1%
*   **XGBoost Accuracy**: 97.6%

#### Cross-Validation Results

The 5-fold cross-validation confirmed the superiority of the more advanced models.

*   **Highest Mean Accuracy**: The **SVM** model achieved the highest average accuracy across the folds (**97.8%**), indicating strong and reliable performance.
*   **Most Consistent Model**: The **XGBoost** model had the lowest standard deviation (**0.0027**), making it the most stable and consistent performer across different data subsets.

#### Tuned Model Performance

After hyperparameter tuning with `GridSearchCV`, the models were re-evaluated on the test set. This final comparison is the most critical for selecting the best model.

!Accuracy Comparison of Tuned Models

#### Performance Summary of Tuned Models

| Model                 | Accuracy | Precision (Spam) | Recall (Spam) | F1-score (Spam) | False Negatives |
| :-------------------- | :------- | :--------------- | :------------ | :-------------- | :-------------- |
| **Logistic Regression** | **98.49%** | 0.98             | **0.91**      | **0.94**        | **17**          |
| SVM                   | 98.49%   | 0.99             | 0.90          | 0.94            | 19              |
| CatBoost              | 98.28%   | 0.99             | 0.88          | 0.93            | 22              |
| Random Forest         | 98.21%   | **1.00**         | 0.87          | 0.93            | 25              |
| XGBoost               | 97.63%   | 0.98             | 0.84          | 0.90            | 29              |
| Decision Tree         | 95.91%   | 0.91             | 0.77          | 0.83            | 42              |

#### Key Insights from the Final Comparison:

*   **Top Performers**: After tuning, **Logistic Regression** and **SVM** emerged as the top models, both achieving an impressive accuracy of **98.49%**.
*   **Best for Spam Detection**: For a spam filter, minimizing false negatives (spam messages classified as ham) is crucial. The **tuned Logistic Regression model** excelled here, achieving the highest **Recall (0.91)** and the lowest number of **False Negatives (17)**.
*   **Precision vs. Recall Trade-off**: The **Random Forest** model achieved perfect precision (1.00), meaning every message it flagged as spam was indeed spam. However, it missed more spam messages (25 false negatives) compared to Logistic Regression and SVM.
*   **Overall Winner**: Considering the critical need to catch as much spam as possible (high recall) while maintaining high accuracy, the **tuned Logistic Regression model** is the best-performing model for this task.

---

## Part 2: California Housing Price Regression Analysis

This project analyzes the California Housing dataset to predict median house values. It starts with a baseline Linear Regression model and progresses to more complex non-linear models, using cross-validation and hyperparameter tuning to find the most accurate regressor.

*   **Notebook**: `Week_7_Linear_Regression_Non_Linear_Modeling.ipynb`
*   **Dataset**: California Housing from Scikit-learn.

### Regression Methodology

1.  **Data Preparation and EDA**:
    *   The California Housing dataset was loaded. It contains numerical features like median income, house age, and location coordinates.
    *   The data was checked for missing values (none were found).
    *   Outliers were identified using box plots and handled by capping extreme values to reduce their influence on the model.
    *   Exploratory Data Analysis (EDA) included visualizing feature distributions with histograms and examining relationships using a correlation heatmap and scatter plots.

2.  **Feature Engineering**:
    *   All features were scaled using `StandardScaler` to ensure that no single feature disproportionately influences the model due to its scale.

3.  **Model Building and Evaluation**:
    *   The dataset was split into training (80%) and testing (20%) sets.
    *   A baseline **Linear Regression** model was built.
    *   Four non-linear models were also trained and evaluated: **Decision Tree, Random Forest, XGBoost, and CatBoost**.

4.  **K-Fold Cross-Validation**:
    *   To get a robust estimate of performance, 5-fold cross-validation was performed on the non-linear models.

5.  **Hyperparameter Tuning**:
    *   `GridSearchCV` was used to find the optimal hyperparameters for the best-performing model, **CatBoost**.

6.  **Final Evaluation and Comparison**:
    *   All models, including the tuned CatBoost model, were evaluated on the test set using metrics like Mean Squared Error (MSE), Root Mean Squared Error (RMSE), and R-squared (R2).

### Regression Model Performance and Comparison

The models were compared based on their ability to predict house prices accurately.

#### Performance Summary of All Models (on Test Set)

| Model                | MSE    | RMSE   | R-squared (R2) |
| :------------------- | :----- | :----- | :------------- |
| **CatBoost (Tuned)** | **0.1942** | **0.4406** | **0.8464**     |
| CatBoost (Untuned)   | 0.1904 | 0.4363 | 0.8494         |
| XGBoost              | 0.2025 | 0.4500 | 0.8398         |
| Random Forest        | 0.2427 | 0.4927 | 0.8080         |
| Linear Regression    | 0.4424 | 0.6651 | 0.6501         |
| Decision Tree        | 0.4864 | 0.6974 | 0.6153         |

#### Key Insights from the Regression Comparison:

*   **Non-Linear Models Excel**: All non-linear ensemble and boosting models (CatBoost, XGBoost, Random Forest) significantly outperformed the baseline Linear Regression and the single Decision Tree model. This indicates that the relationships between the features and house prices are complex and non-linear.
*   **Top Performers**: **CatBoost** and **XGBoost** were the clear top performers, both achieving an R-squared score of approximately **84-85%**. This means they could explain about 85% of the variance in house prices.
*   **Tuning Impact**: In this case, hyperparameter tuning for CatBoost did not lead to a significant improvement over the default settings. The untuned model performed slightly better on this particular test split, which can sometimes happen. However, the cross-validation results confirmed CatBoost's overall robustness.
*   **Overall Winner**: The **CatBoost model** (both tuned and untuned) demonstrated the highest predictive accuracy, making it the best choice for this regression task.

---

## Overall Conclusion

These two analyses demonstrate the power of building, evaluating, and tuning a range of machine learning models for both classification and regression tasks.

*   For the **SMS Spam Classification** task, a **tuned Logistic Regression model** provided the best balance of accuracy and high recall, making it the most effective choice.
*   For the **California Housing Price Regression** task, the **CatBoost model** proved to be the most accurate, effectively capturing the complex, non-linear relationships in the data.

## Technologies Used

*   **Python**: Core programming language.
*   **Jupyter Notebook**: Interactive development environment.
*   **Pandas**: Data manipulation and analysis.
*   **Scikit-learn**: For data preprocessing, model building, and evaluation (`TfidfVectorizer`, `LogisticRegression`, `SVC`, `DecisionTreeClassifier`, `RandomForestClassifier`, `GridSearchCV`, `cross_val_score`).
*   **NLTK**: For natural language processing tasks (stop word removal).
*   **XGBoost**: For implementing the XGBoost classifier.
*   **CatBoost**: For implementing the CatBoost classifier.
*   **Matplotlib & Seaborn**: For data visualization.

---

### How to Run

1.  Ensure you have Python and Jupyter Notebook installed.
2.  Install the required libraries:
    ```bash
    pip install pandas scikit-learn matplotlib seaborn nltk xgboost catboost
    ```
3.  Run the notebooks to see the full analysis and code execution:
    *   `Week_7_Linear_Classification_Non_Linear_Modeling.ipynb`
    *   `Week_7_Linear_Regression_Non_Linear_Modeling.ipynb`