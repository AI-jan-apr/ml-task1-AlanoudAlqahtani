# Breast Cancer Classification – Model Comparison

## Project Overview

This project evaluates multiple classification models on the Breast Cancer Wisconsin Dataset from `sklearn`. The objective is to compare model performance in a medical diagnosis context and determine which model is most suitable for detecting malignant tumors.

---

## 1. Train-Test Split

The dataset was split using the following configuration:

- test_size = 0.2  
- random_state = 42  
- stratify = y  

Stratification ensures the class distribution (benign vs malignant) remains balanced in both training and test sets.

---

## 2. Models Trained

The following models were trained using default parameters unless otherwise justified:

- Logistic Regression  
- Support Vector Machine (Linear Kernel)  
- K-Nearest Neighbors (KNN)  

For KNN, cross-validation was used to select an optimal value of K:

- n_neighbors = 12  

---

## 3. Model Evaluation Metrics

Each model was evaluated using:

- Accuracy  
- Precision  
- Recall  
- F1-score  
- Confusion Matrix  
- ROC-AUC  

---

## 4. Model Comparison Results

### Comparison Table (Best by Recall)

| Model               | Accuracy | Precision | Recall | F1-score |
|--------------------|----------|-----------|--------|----------|
| Logistic Regression | 0.9561   | 0.9467    | 0.9861 | 0.9660   |
| SVM (Linear Kernel) | 0.9561   | 0.9467    | 0.9861 | 0.9660   |
| KNN (k=12)          | 0.9386   | 0.9452    | 0.9583 | 0.9517   |

---

## 5. Additional Analysis

Although Logistic Regression and SVM produced identical classification metrics, their predicted probabilities were not identical.

Average absolute difference between predicted probabilities:

0.0340

This confirms that while their predicted labels were similar, the underlying confidence levels differ slightly.

Additionally, Logistic Regression achieved:

ROC-AUC ≈ 0.996

This indicates near-perfect class separability.

---

## 6. Conclusion

### Which model performed best?

Both Logistic Regression and SVM (Linear Kernel) achieved identical performance across all classification metrics:

- Highest Recall (0.9861)  
- Highest F1-score (0.9660)  
- Highest Accuracy (0.9561)  

However, Logistic Regression is selected as the preferred model due to:

- Simplicity and interpretability  
- Comparable performance to SVM  
- Strong ROC-AUC score (~0.996)  
- Lower computational complexity  

---

### In a medical context, which metric is most important and why?

In medical diagnosis, Recall (Sensitivity) is the most critical metric.

Recall measures:

Recall = TP / (TP + FN)

It answers the question:

"Out of all actual cancer cases, how many did the model correctly detect?"

A False Negative (missing a real cancer case) is significantly more dangerous than a False Positive (incorrectly flagging a healthy patient).

False negatives can lead to:

- Delayed treatment  
- Disease progression  
- Increased mortality risk  

Therefore, maximizing Recall is prioritized over Precision or Accuracy in cancer detection tasks.

---

## Final Recommendation

Logistic Regression is recommended for this task due to:

- Highest Recall  
- Excellent ROC-AUC  
- Strong F1-score  
- Simplicity and interpretability  
- Comparable performance to SVM  

The dataset appears highly linearly separable, allowing linear models to perform exceptionally well.

---

## Notes

While performance is extremely high on this dataset, further validation using:

- Cross-validation  
- External datasets  
- Threshold tuning  

would be necessary before real-world deployment in a clinical setting.