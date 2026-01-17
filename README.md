# **AI for Market Trend Analysis – Project Report (Module E)**

**Student Name:** Diya Vohra

**Project Type:** Individual Open Project

**Project Title:** AI-Based Market Trend Prediction Using Business Signals & Events

---

## **Abstract**

This project focuses on predicting daily market trend direction (**Uptrend/Downtrend**) using business indicators such as AI revenue, AI revenue growth percentage, R&D spending, and company-related events. A supervised machine learning pipeline was built covering data loading, cleaning, exploratory data analysis, feature engineering, model training, and evaluation. Three models were implemented and compared: Logistic Regression (baseline), Random Forest, and Gradient Boosting. The best performance was achieved using Logistic Regression with an accuracy of **0.743** and ROC-AUC of **0.839**, demonstrating that engineered business and time-based features contain useful signal for trend prediction.

---

## **1. Introduction**

Market trend analysis helps in understanding the direction of market movement based on observable signals. Businesses and analysts often monitor financial growth metrics, spending patterns, and key events to estimate how markets may respond. However, manually tracking and interpreting these signals daily is challenging.

This project demonstrates an AI-based approach to market trend analysis by using structured financial signals and events to predict whether the market trend will move upward or downward. The aim is not perfect prediction accuracy, but to build an end-to-end workflow that reflects the complete lifecycle of an AI project: from problem definition and data preprocessing to model building, evaluation, and documentation.

---

## **2. Problem Statement & Objective**

### **Problem Statement**

Given daily company-level financial and event-based signals, predict whether the market trend will be:

* **Uptrend (1)** if `Stock_Impact_% > 0`
* **Downtrend (0)** if `Stock_Impact_% ≤ 0`

### **Objective**

* Build an AI/ML classification system to predict trend direction (Up/Down)
* Compare baseline and advanced models
* Evaluate performance using multiple metrics
* Document limitations and ethical considerations

### **Real-world Relevance**

A trend prediction system can assist in:

* Market monitoring and decision support
* Understanding event-driven market impact
* Risk awareness and strategy planning
  *(Note: this project is educational and not financial advice.)*

---

## **3. Dataset Description**

### **Dataset Used**

**File Name:** `ai_financial_market_daily_realistic_synthetic.csv`
**Type:** Synthetic realistic daily financial market dataset

### **Key Columns**

* **Date**: Daily timestamp
* **Company**: Company identifier
* **R&D_Spending_USD_Mn**: R&D spending (in million USD)
* **AI_Revenue_USD_Mn**: AI revenue (in million USD)
* **AI_Revenue_Growth_%**: AI revenue growth percentage
* **Event**: Major business event/news label
* **Stock_Impact_%**: Daily market impact percentage

### **Dataset Size**

The dataset contains ~11,000 rows, making it sufficiently large for ML training and evaluation while still being manageable for debugging and experimentation.

---

## **4. Methodology / Workflow**

This project follows the end-to-end AI workflow expected in the module:

### **Step 1: Data Loading and Exploration**

The dataset was loaded into Python using Pandas. Basic exploration was conducted using:

* `head()`, `info()`, `describe()`
* Missing value checks
* Duplicate record checks

### **Step 2: Data Cleaning and Preprocessing**

The following cleaning steps were applied:

* Duplicate rows were removed to avoid biased training
* `Date` column was converted to proper datetime format
* Missing values in **Event** were filled using `"No_Event"`
* The dataset was sorted by **Company** and **Date** to preserve time-series order

### **Step 3: Exploratory Data Analysis (EDA)**

EDA was performed to understand dataset behavior through:

* Distribution of `Stock_Impact_%` values
* Time trend visualization for sample companies
* Outlier checking (market shocks may appear as outliers)

### **Step 4: Feature Engineering**

The following features were created to improve prediction:

* **Target label:**

  * `Target_Trend = 1` if stock impact > 0
  * `Target_Trend = 0` otherwise
* **Time-based features:** Year, Month, Day, DayOfWeek
* **Lag features:** Previous day values for impact, growth, revenue, R&D
* **Rolling features:** Rolling mean/std (3-day window)

These features help models learn time-based and historical dependency patterns, which is essential for trend analysis.

### **Step 5: Model Building**

Three models were implemented:

1. **Logistic Regression (Baseline Model)**

   * Chosen because it is simple, fast, and interpretable
   * Used as a benchmark model

2. **Random Forest Classifier**

   * Handles non-linear relationships
   * Works well with multiple engineered features

3. **Gradient Boosting Classifier**

   * Uses boosting strategy to correct previous prediction errors
   * Often improves performance over standard tree-based methods

### **Step 6: Train/Test Split Strategy**

A **time-based split (80/20)** was used to avoid future data leaking into training, which is important in market trend prediction.

---

## **5. Experiments & Results**

### **Evaluation Metrics Used**

* **Accuracy**
* **Error Rate (1 − Accuracy)**
* **Precision, Recall, F1-score**
* **Confusion Matrix**
* **ROC-AUC Score** (threshold-independent performance evaluation)

### **Model Performance Summary**

| Model               | Accuracy | Error Rate | ROC-AUC |
| ------------------- | -------- | ---------- | ------- |
| Logistic Regression | 0.743    | 0.257      | 0.839   |
| Random Forest       | 0.719    | 0.281      | 0.817   |
| Gradient Boosting   | 0.726    | 0.274      | 0.829   |

### **Observations**

* Logistic Regression achieved the best accuracy and ROC-AUC score.
* Random Forest and Gradient Boosting performed competitively, but slightly below Logistic Regression.
* The strong ROC-AUC values indicate that the models can separate Uptrend vs Downtrend reasonably well.

---

## **6. Limitations**

* Since the dataset is synthetic, patterns may not perfectly reflect real-world market behavior.
* Actual stock market movement depends on many external factors not included in the dataset, such as macroeconomic conditions, investor sentiment, and global news.
* Trend prediction is inherently noisy, so performance may vary across different market conditions and companies.

---

## **7. Ethical Considerations & Responsible AI**

* This project is created for educational purposes and should not be treated as investment or trading advice.
* AI-based market prediction systems can cause harm if blindly trusted for financial decisions.
* Synthetic data may introduce bias due to assumptions in data generation.
* Any real-world deployment would require transparency, monitoring, retraining, and strong validation across market situations.

---

## **8. Conclusion & Future Scope**

### **Conclusion**

This project successfully demonstrates a complete AI pipeline for market trend analysis using supervised machine learning. The workflow includes dataset exploration, cleaning, feature engineering, training baseline and advanced models, and evaluating results using multiple metrics. Logistic Regression achieved the best overall performance, showing that the engineered business signals are useful for predicting daily market trend direction.

### **Future Scope**

Possible improvements include:

* Adding more lag features (Lag2, Lag3, etc.)
* Hyperparameter tuning for Random Forest and Gradient Boosting
* Trying advanced algorithms like XGBoost/LightGBM (if allowed)
* Using deep learning models such as LSTM for time-series learning
* Integrating external signals such as macroeconomic indicators or news sentiment
* Building a Streamlit dashboard for interactive predictions

---

## **Submission Links**

* **Project Report (Google Docs):** [Project Report](https://docs.google.com/document/d/1mKNLJwgEvnkLJJUMH8ZzpnmEfKqe62xKctkVOYC4oAc/edit?usp=drive_link)
* **Project Presentation (Google Slides):** [Project Slides](https://docs.google.com/document/d/1mKNLJwgEvnkLJJUMH8ZzpnmEfKqe62xKctkVOYC4oAc/edit?usp=drive_link)
* **Demo Video:** 
