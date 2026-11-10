# Correlation-Based Feature Weighting

An experimental binary classification approach that uses **Pearson correlation coefficients** to assign weights to input features and generate a weighted score for classification.

The approach is experimentally evaluated on a diabetes dataset.

## Overview

The main idea of this project is to use the statistical relationship between each feature and the target variable to determine its contribution to a classification score.

Instead of assigning equal weights to all features, the method calculates Pearson correlation coefficients using the training data and uses them as feature weights.

## Methodology

The classification process consists of the following steps:

1. **Data Splitting:** Divide the dataset into training (80%) and testing (20%) subsets.
2. **Feature Standardization:** Standardize the features using the mean and standard deviation of the training data.
3. **Correlation Analysis:** Calculate the Pearson correlation coefficient between each feature and the target variable.
4. **Weighted Score Calculation:** Multiply each standardized feature by its corresponding correlation coefficient and sum the results.
5. **Threshold Selection:** Compare the score distributions of the two classes using normalized histograms and determine a classification threshold.
6. **Prediction:** Classify each sample based on whether its weighted score is above or below the selected threshold.

## Mathematical Formulation

The weighted score is calculated as:

\[
S(x)=\sum_{i=1}^{n}r_i z_i
\]

Where:

- \(S(x)\) is the classification score.
- \(r_i\) is the Pearson correlation coefficient of feature \(i\) with the target.
- \(z_i\) is the standardized value of feature \(i\).
- \(n\) is the number of input features.

The final prediction is based on a threshold \(T\):

- If \(S(x)\geq T\), predict class 1.
- Otherwise, predict class 0.

## Dataset

The project uses a diabetes dataset containing 768 samples and 8 input features.

The input features are:

- Pregnancies
- Glucose
- BloodPressure
- SkinThickness
- Insulin
- BMI
- DiabetesPedigreeFunction
- Age

**Target variable:** `Outcome`

- `0`: Non-diabetic
- `1`: Diabetic

## Experimental Results

The current implementation produced the following results on the test set:

| Metric | Result |
|---|---:|
| Accuracy | 75.97% |

Confusion Matrix:

```text
[[69, 31],
 [ 6, 48]]
```

Rows represent actual classes and columns represent predicted classes.

## Limitations

- Pearson correlation measures linear association, not causation.
- Correlation coefficients do not necessarily represent the true predictive importance of features.
- The histogram-based threshold selection is sensitive to bin size and sample distribution.
- The method has only been experimentally evaluated on this diabetes dataset.
- This experimental approach is not a clinically validated diagnostic tool.

## Repository Structure

```text
correlation-based-feature-weighting/
│
├── correlation_based_knn.ipynb
├── diabetes.csv
└── README.md
```

## Future Work

- Compare the approach with standard classification algorithms.
- Investigate alternative feature-weighting methods.
- Evaluate performance using Precision, Recall and F1-score.
- Test the approach on additional datasets.

## Technologies Used

- Python
- NumPy
- Matplotlib
- Scikit-learn

