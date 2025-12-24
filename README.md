# MACHINE-LEARNING-MODEL-IMPLEMENTATION

## Credit Card Fraud Detection Using Machine Learning

__Company Name__ : Codtech IT Solutions Private Limited

__Name__ : Vijayashree R

__Intern ID__ : CTIS0573

__Domain Name__ : Python Programming.

__Duration__ : 4 weeks

__Internship Period__ : 18 December 2025 - 15 January 2026

__Mentor__ : Neela Santhosh Kumar 

__Output__

<img width="822" height="568" alt="Image" src="https://github.com/user-attachments/assets/ae335723-c8a0-4bad-a950-077360dd48ac" />

__1. Project Overview__

Credit card fraud is a significant problem for banks and financial institutions. The objective of this project is to build a predictive model that can classify transactions as fraudulent (1) or legitimate (0) using historical transaction data. Machine Learning allows early detection of fraud, reducing financial losses.

__2. Dataset__

- Source: Kaggle / Public GitHub URL.

- Number of Rows: 284,807.

- Number of Columns: 31.


__Features:__

- V1 to V28 → anonymized PCA components.

- Amount → Transaction amount.

- Class → Target variable (0 = legitimate, 1 = fraud).

##### Class Distribution:

0 → 284,315 transactions (Legitimate)
1 → 492 transactions (Fraudulent)


Note: The dataset is highly imbalanced.

__3. Data Preprocessing__

- Checked for missing values → None found.

- Scaled Amount column using StandardScaler to normalize values.

- Separated features (X) and target (y).

- Split dataset into training and testing sets (75% train, 25% test) using train_test_split with stratify=y to maintain class balance.

__4. Model Selection__

- Classifier Used: Logistic Regression.

- Suitable for binary classification.

- Handles large datasets well.

##### Probability outputs allow threshold adjustment

from sklearn.linear_model import LogisticRegression
model = LogisticRegression(max_iter=5000, solver='saga')
model.fit(X_train, y_train)


Note: max_iter increased to ensure convergence.

__5. Model Evaluation__
🔹 Accuracy
from sklearn.metrics import accuracy_score
accuracy_score(y_test, y_pred)


Accuracy: ~99.9%

High accuracy is misleading due to class imbalance.

🔹 Confusion Matrix
Predicted
          0      1
Actual 0 71049    5
       1    28    86


True Positives (TP) → 86 (fraud detected correctly)

False Negatives (FN) → 28 (fraud missed)

True Negatives (TN) → 71,049

False Positives (FP) → 5

Heatmap plotted for visualization.

🔹 Classification Report

| Class | Precision | Recall | F1-score |
| ----- | --------- | ------ | -------- |
| 0     | 1.00      | 1.00   | 1.00     |
| 1     | 0.95      | 0.75   | 0.84     |

Recall for fraud class is important: higher recall means fewer fraudulent transactions are missed.

__6. Observations__

- Dataset is highly imbalanced → accuracy alone is not enough.

- Logistic Regression performs well but may miss some fraud cases (FN).

- Recall and F1-score for fraud class are critical metrics.

- Feature scaling and train-test stratification improve performance.

__7. Conclusion__

- Logistic Regression successfully detects fraudulent transactions.

- For better results, ensemble methods like Random Forest or XGBoost could be used.

- Further improvement can include SMOTE or other techniques to handle class imbalance.

- Model can be deployed in a real-time fraud detection system to minimize financial losses.

__8. Future Work__

- Implement Random Forest and XGBoost for comparison.

- Apply SMOTE for balancing minority class.

- Analyze feature importance to identify key fraud indicators.

- Build a real-time fraud alert system.
