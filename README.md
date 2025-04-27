# HoneyTrap: AWS Honeypot Attack Detection Using Machine Learning


##  Overview

Cybersecurity threats are becoming increasingly sophisticated, and cloud infrastructures like AWS are popular targets.  
This project focuses on building a machine learning model to detect and predict attacks based on real-world honeypot data collected from AWS servers.

Using a carefully designed pipeline — including data preprocessing, feature engineering, model training, hyperparameter optimization, and evaluation — we aim to accurately differentiate between normal and malicious activities.  

The project demonstrates how traditional machine learning techniques can still achieve high reliability (91%+ accuracy) in a highly sensitive domain like cybersecurity.


##  Dataset

- **Source**: AWS Honeypot Attack Data
- **Nature**: Real-world network traffic logs
- **Features**:
  - IP addresses
  - Ports accessed
  - Protocols (TCP, UDP)
  - Attack categories (e.g., brute force, botnets)
  - Geolocation metadata
- **Label**:
  - `Attack` (1) — Malicious Activity
  - `No Attack` (0) — Normal Traffic
- **Challenges**:
  - Highly imbalanced data
  - Presence of outliers and noisy data


##  Methodology

###  Data Preprocessing
- **Label Encoding**: Converted categorical fields into numerical format.
- **SMOTE Oversampling**: Addressed class imbalance by synthetically generating new samples for minority class.
- **Scaling**: Applied `RobustScaler` to mitigate the effects of outliers.

###  Feature Engineering
- **Feature Selection**: Used Random Forest Feature Importances to select the most impactful features.

###  Model Building
- **Model Chosen**: Random Forest Classifier
- **Hyperparameter Tuning**: Used GridSearchCV with 5-fold cross-validation to tune:
  - `n_estimators`
  - `max_depth`
  - `min_samples_split`
  - `min_samples_leaf`

###  Model Evaluation
- **Cross-Validation**: 5-fold cross-validation to evaluate training set performance.
- **Testing**: Separate holdout test set to assess real-world model performance.

**Metrics Used**:
- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC Score


##  Results and Analysis

| Metric                      | Value |
|:-----------------------------|:------|
| **Training Cross-Validation Mean Score** | ~90–91% |
| **Test Set Accuracy**        | ~91%  |
| **ROC AUC Score**            | ~0.93 |
| **Precision (Attack Class)** | High (above 90%) |
| **Recall (Attack Class)**    | High (above 90%) |


Confusion Matrix:

![image](https://github.com/user-attachments/assets/5d34bca3-2378-43d7-8e2f-efecb029e859)


ROC Curve:

![image](https://github.com/user-attachments/assets/0c95c25d-76e0-4caa-a897-7c8ffc0772b2)


Feature Importance:

![image](https://github.com/user-attachments/assets/64e0144e-237c-4515-8e7f-99e5e1938fd6)


###  Detailed Insights:

- **High Accuracy (91%)**:
  - Shows the model generalizes well to unseen attack data.
- **High ROC-AUC (0.93)**:
  - Indicates a strong ability to distinguish between "attack" and "normal" classes.
- **Balanced Precision and Recall**:
  - Critical in cybersecurity — not missing real attacks (high recall) and avoiding too many false alarms (high precision).

### Observations:

- Imbalanced data was successfully handled using SMOTE.
- Feature selection improved both speed and accuracy.
- Random Forest after hyperparameter tuning outperformed basic models.
  






