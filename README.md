# Interpretable Breast Cancer Prediction Using XGBoost

This project uses XGBoost to classify breast tumors as benign or malignant, focusing on **model interpretability** through feature importance analysis.

---

##  Dataset Description

Source: Kaggle  
The dataset includes 699 samples and the following features:

- Clump Thickness  
- Uniformity of Cell Size  
- Uniformity of Cell Shape  
- Marginal Adhesion  
- Single Epithelial Cell Size  
- Bare Nuclei  
- Bland Chromatin  
- Normal Nucleoli  
- Mitoses  
- Class (2 = benign, 4 = malignant)

---

##  Methodology

###  Preprocessing

- Converted `Bare Nuclei` to numeric
- Dropped non-informative `Sample Code Number`
- Mapped `Class` values: `{2: 0, 4: 1}`
- Train-test split: 80% / 20%

###  Model

- Used `XGBClassifier` in a `Pipeline`
- Standardized features with `StandardScaler`
- Optimized hyperparameters using `GridSearchCV`

###  Evaluation Metrics

- Confusion Matrix  
- ROC-AUC Curve  
- Feature Importance Plot  

---

##  Results

###  Feature Importance

- **Uniformity of Cell Size** is the top predictor
- This feature contributed over **60%** of the model’s decision power

###  Confusion Matrix

- High accuracy, precision, and recall
- Very low false-positive and false-negative rates

###  ROC Curve

- Area under the curve (AUC): **> 0.95**
- Indicates excellent separation between classes

---

##  Interpretability Insights

- **Uniformity of Cell Size** aligns with known medical indicators for malignancy
- Clinically useful for prioritizing features in **diagnostic tools**
- Enables **trust** and **explainability** in ML-based medical systems

---

##  Future Work

- Add SHAP (SHapley Additive exPlanations) for feature-level interpretability
- Compare with CNN-based image models
- Test on real EHR (Electronic Health Records) data

---

##  Conclusion

This project shows that:

- XGBoost can classify tumors with high accuracy  
- Feature importance enhances trust and transparency  
- Simpler, interpretable models can assist medical decisions effectively  

---

>  **Note:** This project is intended for educational and academic purposes only. Not a clinical diagnostic tool.

