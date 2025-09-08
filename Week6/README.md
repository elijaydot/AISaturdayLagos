# Week 6: Linear Regression and Linear Classification

This folder contains two projects from Week 6, demonstrating the application of linear models for regression and classification tasks.

## Projects

1.  [Linear Regression: California Housing Price Prediction](#linear-regression-california-housing-price-prediction)
2.  [Linear Classification: SMS Spam Detection](#linear-classification-sms-spam-detection)

---

### Linear Regression: California Housing Price Prediction

This project focuses on building a Linear Regression model to predict median house values in California districts based on various features.

*   **Notebook**: `Week_6_Linear_Regression.ipynb`
*   **Dataset**: California Housing dataset from scikit-learn.
*   **Data Source**: scikit-learn California Housing Dataset

#### Methodology

1.  **Data Loading**: The dataset is loaded using `sklearn.datasets.fetch_california_housing`.
2.  **Data Cleaning and Preprocessing**:
    *   Outliers in numerical columns were identified using box plots and handled by capping extreme values.
    *   Features were scaled using `StandardScaler` to ensure they have a mean of 0 and a standard deviation of 1.
3.  **Exploratory Data Analysis (EDA)**:
    *   Histograms were used to visualize the distribution of each feature.
    *   A correlation heatmap was generated to understand the relationships between variables. The `MedInc` (Median Income) feature showed the strongest positive correlation (0.68) with the target variable `MedHouseVal`.
4.  **Model Building**:
    *   The data was split into an 80% training set and a 20% testing set.
    *   A `LinearRegression` model was trained on the preprocessed training data.
5.  **Evaluation**: The model's performance on the test set was evaluated using the following metrics:
    *   **Mean Squared Error (MSE)**: 0.4424
    *   **Root Mean Squared Error (RMSE)**: 0.6651
    *   **R-squared (R²) Score**: 0.6501

#### Conclusion

The Linear Regression model achieved a moderate performance, explaining approximately 65% of the variance in median house values. The `MedInc` feature was the most significant predictor. For improved performance, future steps could involve feature engineering and exploring non-linear models.

---

### Linear Classification: SMS Spam Detection

This project builds and compares two linear classification models (Logistic Regression and Support Vector Machine) to classify SMS messages as "spam" or "ham" (not spam).

*   **Notebook**: `Week_6_Linear_Classification.ipynb`
*   **Dataset**: SMS Spam Collection from the UCI Machine Learning Repository.
*   **Data Source**: https://raw.githubusercontent.com/justmarkham/pycon-2016-tutorial/master/data/sms.tsv

#### Methodology

1.  **Data Loading**: The dataset is loaded from a TSV file into a pandas DataFrame.
2.  **Text Preprocessing**:
    *   Categorical labels ('ham', 'spam') were converted to numerical (0, 1).
    *   Text messages were cleaned by removing punctuation, converting to lowercase, and removing common English stop words.
3.  **Feature Extraction**: The preprocessed text data was converted into numerical features using `TfidfVectorizer`.
4.  **Model Building**:
    *   The data was split into a 75% training set and a 25% testing set.
    *   Two models were trained: `LogisticRegression` and `SVC` (Support Vector Machine with a linear kernel).
5.  **Evaluation & Comparison**: Both models were evaluated on the test set.

    *   **Logistic Regression**:
        *   Accuracy: 96.48%
        *   Recall (for spam): 0.74
        *   F1-score (for spam): 0.85

    *   **Support Vector Machine (SVM)**:
        *   Accuracy: 99.07%
        *   Recall (for spam): 0.93
        *   F1-score (for spam): 0.96

#### Conclusion

Both models performed well, but the **Support Vector Machine (SVM) model significantly outperformed Logistic Regression**, especially in its ability to correctly identify spam messages (higher recall and F1-score). The SVM model had fewer false negatives (13 vs. 48 for Logistic Regression), making it a more effective choice for a spam filter.

---

### How to Run

1.  Ensure you have Python and Jupyter Notebook installed.
2.  Install the required libraries:
    ```bash
    pip install pandas scikit-learn matplotlib seaborn nltk
    ```
3.  Run the Jupyter notebooks (`Week_6_Linear_Regression.ipynb` and `Week_6_Linear_Classification.ipynb`) to see the full analysis and code execution.
