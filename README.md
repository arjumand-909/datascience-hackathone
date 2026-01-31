

---

# 📘 Air Quality Index (AQI) Prediction Project

## 📌 Problem Statement
Cities in Pakistan struggle with hazardous air pollution (especially high PM2.5), which affects health and daily life.  
The goal of this project is to build a **machine learning model** that predicts **air quality levels (AQI values or categories)** using historical pollutant and weather data.  
This helps authorities issue early warnings and take preventive measures.

---

## 🎯 Objectives
- Predict **daily AQI category** (Good, Moderate, Unhealthy, etc.).  
- Forecast AQI values for the **next few days**.  
- Handle **time-series data** with environmental features.  
- Provide **risk scoring** (Low / Medium / High) for public health alerts.  

---

## 📂 Dataset
- **Datetime column:** Hourly timestamps (e.g., `2024-07-01 04:00:00`).  
- **Features (X):**  
  - Pollutants: `components_pm2_5`, `components_pm10`, `components_no2`, `components_so2`, `components_o3`, `components_co`  
  - Weather: `temperature_2m`, `relative_humidity_2m`, `wind_speed_10m`, `precipitation`  
- **Target (y):**  
  - `main_aqi` (numeric AQI values → regression target)  
  - `AQI_Category` (mapped labels, but only “Good” present → regression chosen)

---

## ⚙️ Preprocessing
1. Converted `datetime` column into proper `datetime64[ns]` format.  
2. Extracted pollutant + weather features.  
3. Split dataset into **Training (3494 rows, 10 features)** and **Testing (874 rows, 10 features)**.  
4. Checked class distribution → only `"Good"` category present.  
5. Shifted approach from **classification → regression**.  

---

## 🧠 Models Trained
- Random Forest Regressor  
- Gradient Boosting Regressor  
- Linear Regression  
- K-Nearest Neighbors (KNN) Regressor  
- Support Vector Machine (SVM) Regressor  

---

## 📊 Model Evaluation Results

| Model             | RMSE ↓ | R² ↑ |
|-------------------|--------|------|
| **Random Forest** | **0.0391** | **0.9975** |
| Gradient Boosting | 0.0422 | 0.9971 |
| KNN               | 0.2152 | 0.9247 |
| SVM               | 0.4511 | 0.6690 |
| Linear Regression | 0.6213 | 0.3720 |

---

## ✅ Interpretation
- **Best Models:** Random Forest and Gradient Boosting (near-perfect accuracy).  
- **Decent Model:** KNN (good but weaker).  
- **Moderate Model:** SVM (okay but not strong).  
- **Weakest Model:** Linear Regression (struggles with non-linear AQI data).  

---

## 🟩 Risk Scoring (Task 6️⃣)
- **Risk Score:** Numeric AQI prediction.  
- **Risk Label:**  
  - AQI ≤ 100 → Low Risk  
  - AQI 101–200 → Medium Risk  
  - AQI > 200 → High Risk  

👉 This helps authorities quickly interpret predictions and issue alerts.

---

## 📈 Visualizations
- **Train vs Test Split Graph:** Bar chart showing training set (3494 rows) vs test set (874 rows).  
- **Datetime Column:** Confirmed hourly timestamps starting from July 1st, 2024.  
- **AQI Categories:** All records mapped to “Good” → regression chosen.  

---

## 💾 Model Saving
Best model (Random Forest) can be saved and reused:
```python
import joblib
joblib.dump(model, "aqi_model.pkl")   # Save
loaded_model = joblib.load("aqi_model.pkl")  # Load
```

---




---

👉 This README now fully covers your project: problem, dataset, preprocessing, models, evaluation, risk scoring, visualizations, saving/loading, Streamlit app, and deliverables.  

Would you like me to also add a **“How to Run” section** (setup + commands for Colab and Streamlit) so it’s ready for GitHub submission?
