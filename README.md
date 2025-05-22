# Caravan Insurance Prediction  

## 📌 Problem Statement  
A company wants to optimize direct mail campaigns for caravan insurance by predicting which customers are likely to buy. The goal is to **reduce wasteful marketing spend** while maximizing conversions.  

**Challenge:**  
- Severe class imbalance (Only 6.3% of customers were interested).  
- 85 anonymized features (mix of numeric and categorical variables).  

## 📂 Data  
- **Training Data:** `carvan_train.csv` (5,822 rows × 86 cols)  
- **Test Data:** `carvan_test.csv` (4,000 rows × 85 cols)  
- **Target Variable:** `V86` (Binary: 0 = No interest, 1 = Interest)  

## 🛠️ Approach  
1. **Exploratory Analysis (EDA):**  
   - Identified imbalance: 5,474 "0"s vs. 348 "1"s.  
   - Checked missing values (none) and data types (all numeric).  
   - Flagged low-cardinality features as categorical.  

2. **Data Preprocessing:**  
   - Stratified train-validation split (80:20) to preserve imbalance.  
   - Applied **SMOTE** to oversample the minority class.  

3. **Modeling:**  
   - **Random Forest** with class weighting (`{0:1, 1:15}`) and hyperparameter tuning:  
     - `n_estimators=200`, `max_depth=10`.  
   - Evaluated using **Fβ-score (β=2)** to prioritize recall for rare class.  

4. **Results:**  
   - **Fβ-score = 0.306** (Surpassed benchmark of 0.26).  
   - Top predictive features: `V44`, `V38`, `V10`.  
 
