# Bias Detection and Fairness Evaluation in Income Prediction Models

## 📌 Situation
Income prediction models often exhibit biases due to historical inequalities in data. These biases lead to unfair treatment of marginalized groups, particularly in financial decision-making. This project aims to analyze and mitigate such biases while ensuring model performance.

## 🎯 Task
- Identify and evaluate bias in income prediction models.
- Implement fairness-enhancing techniques to reduce disparities in predictions across demographic groups.
- Maintain a balance between model fairness and predictive performance.

## 🔨 Action
### **1️⃣ Data Preparation**
- **Dataset:** Publicly available income data.
- **Preprocessing:**
  - **Label Encoding:** Transformed categorical variables (e.g., `SEX` was encoded as `1` (Male) and `2` (Female)).
  - **Binary Target Variable:** Income labeled as:
    - `1` (Income > $50,000)
    - `0` (Income ≤ $50,000)
  - **Train-Test Split:**
    - **Training:** 80% (1,331,600 samples)
    - **Testing:** 20% (332,900 samples)

### **2️⃣ Exploratory Data Analysis (EDA)**
- Examined demographic distributions in the dataset.
- Identified imbalances in income distribution between males and females.

### **3️⃣ Model Training**
- **Decision Tree Classifier:**
  - Accuracy: **74.89%**
  - ROC-AUC: **0.7309**
- **HistGradientBoostingClassifier:**
  - Accuracy: **81.57%**
  - ROC-AUC: **0.7976**
- **LIME Analysis:** Used for model explainability.

### **4️⃣ Bias Mitigation**
- **Reweighing Method:**
  - Adjusted sample weights to counteract bias.
  - Increased weights for **females** (2.0) to counter their lower representation in the high-income class.
  - Maintained male sample weight at 1.0.
- **Threshold Adjustment:**
  - Set decision threshold at **0.4 for females** and **0.6 for males** to improve fairness.

### **5️⃣ Fairness Evaluation**
- **Pre-mitigation Disparity:**
  - **Males earning >$50k:** **43.41%**
  - **Females earning >$50k:** **25.46%**
- **Post-mitigation Disparity:**
  - **Males earning >$50k:** **41.46%**
  - **Females earning >$50k:** **32.48%**
- **Adversarial Debiasing:**
  - Accuracy: **81.10%**
  - ROC-AUC: **0.7912**

## 📊 Result
- Bias was significantly reduced while maintaining model accuracy.
- **HistGradientBoostingClassifier** achieved the best performance.
- **Threshold adjustment** and **reweighting** improved fairness without major drops in accuracy.
- The model became more **explainable and equitable** across demographic groups.
