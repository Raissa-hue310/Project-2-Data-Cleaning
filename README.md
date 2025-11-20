# 📊 Project 2 — Data Cleaning and Preparation  
**Business Intelligence Analyst Program – Willis College**

This project focuses on transforming raw historical stock market data into a fully cleaned, feature-engineered, and analysis-ready dataset suitable for advanced machine learning modeling. The work builds on the exploration performed in Project 1 and prepares the foundation for Project 3.

---

## 📁 **1. Dataset Description**
The original dataset contains historical daily stock prices for thousands of companies from 1970 to 2018.

Due to the extremely large dataset size (~27M rows), the analysis for this project was performed on **one representative ticker (AAPL)**. This is standard practice in time-series financial modeling when working within cloud notebook limitations (e.g., Google Colab).

Each row contains:
- Date  
- Open, High, Low, Close prices  
- Adjusted close price  
- Trading volume  
- Metadata fields from the second dataset  

---

## 🧹 **2. Data Cleaning Steps**
The following procedures were applied:

### **2.1 Date Handling**
- Converted `date` column to datetime.
- Removed rows with invalid or missing dates.
- Sorted dataset chronologically.

### **2.2 Missing Value Treatment**
- Applied **time-based interpolation** to price fields (open, high, low, close, adj_close).
- Applied **forward/backward fill** for volume.
- Removed remaining missing entries after interpolation.

### **2.3 Outlier Treatment**
- Winsorization (IQR-based capping) applied to:
  - Closing prices
  - Log-transformed trading volume
- Reduced influence of extreme spikes while preserving overall patterns.

### **2.4 Error Corrections**
- Removed rows with non-positive prices or volumes.
- Removed duplicate rows per ticker/date.

---

## 🧪 **3. Feature Engineering**
The following technical and statistical features were created:

| Feature | Description |
|--------|-------------|
| `return` | Daily percentage return |
| `log_return` | Logarithmic return |
| `ma_7`, `ma_30` | 7-day and 30-day moving averages |
| `volatility_7` | 7-day rolling standard deviation |
| `rsi_14` | 14-day Relative Strength Index |
| `close_lag_1` | Previous day’s closing price |
| `return_lag_1` | Previous day’s return |

These features are essential for forecasting and machine learning modeling.

---

## 🔠 **4. Encoding**
- Since only one ticker was used, label encoding was applied to convert the ticker to a numeric variable.

---

## 📏 **5. Scaling**
Performed using `StandardScaler` from scikit-learn:
- Fit on **training set only**
- Applied to validation and test sets
- Prevents leakage and ensures consistency

Scaled columns include:
- Price features  
- Returns  
- Moving averages  
- Volatility  
- RSI  
- Lag features  

---

## 🔀 **6. Train / Validation / Test Split**
A chronological split was used:

- **70%** → Training  
- **15%** → Validation  
- **15%** → Test  

This respects the time-series nature of financial data.

---

## 💾 **7. Saved Files**
The following output files were generated:

- `full_clean_dataset.csv`  
- `train_clean_scaled.csv`  
- `val_clean_scaled.csv`  
- `test_clean_scaled.csv`  
- `scaler.pkl` (StandardScaler object for reuse)

These files ensure reproducibility and can be used directly for modeling in Project 3.

---

## 📝 **8. Tools & Libraries**
- Python  
- Pandas  
- NumPy  
- Matplotlib / Seaborn  
- Scikit-learn  
- Joblib  
- Google Colab  

---

## ✔ **9. Conclusion**
This project successfully cleaned and transformed raw stock price data into a structured, feature-rich dataset optimized for machine learning. The resulting datasets and scaler form the foundation for predictive modeling tasks in the next project.

---

## 👩‍💻 **Author**
**Raïssa Matho Mekjele**  
Business Intelligence Analyst Program  
Willis College (Ottawa)
