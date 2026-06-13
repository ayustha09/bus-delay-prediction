# bus-delay-prediction
# Predicting Bus Arrival Delays in London Using Machine Learning on Open Government Transport Data

**MSc Computer Science — Coventry University**  
**Author:** Ayusha Shrestha

---

## Overview

This project develops a machine learning framework to predict bus arrival delays across Transport for London's (TfL) bus network using publicly available open government datasets. Rather than reacting to delays after they occur, this system forecasts delays **before** they happen — enabling proactive decisions for passengers, operators, and planners.

---

## Problem

TfL's current bus systems are reactive — they show where a bus *is*, not where it *will be*. This leads to missed connections, poor passenger experience, and inefficient fleet management. This project addresses that gap with an interpretable, predictive ML solution.

---

## Data Sources

| Dataset | Type | Description |
|--------|------|-------------|
| **GTFS** (General Transit Feed Specification) | Static | Route structures, stop locations, scheduled timetables |
| **SIRI-VM** (Service Interface for Real-time Information – Vehicle Monitoring) | Real-time | Live bus positions and operational status |

Both datasets were merged, cleaned, and enriched with engineered features such as distance to next stop, time of day, and day of week.

---

## Models Compared

Six machine learning models were trained and evaluated alongside a baseline dummy classifier:

- Logistic Regression
- Decision Tree
- Random Forest ✅ *(Best Model)*
- XGBoost
- K-Nearest Neighbours
- Support Vector Machine
- Dummy Classifier (Baseline)

---

## Results

**Random Forest** achieved the best performance with near-perfect accuracy and recall, meaning it correctly identifies almost all delayed buses while keeping false negatives low.

### Key Metrics (Random Forest)
- High accuracy, precision, recall, and F1-score
- Strong ROC-AUC across all evaluated models
- Outperformed all other models on composite scoring

---

## Key Findings

- **Distance to next stop** was the most important predictor of delay, with a clear threshold around **0.15 km**
- Temporal features (time of day, day of week) and route-level congestion patterns also contributed significantly
- Explainability was validated using **SHAP values**, **Permutation Importance**, **Gini Importance**, and **Partial Dependence Plots (PDP)**

---

## Explainability

To ensure the model is trustworthy and usable in real operations, multiple interpretability techniques were applied:

- **SHAP** (SHapley Additive exPlanations) — global and local feature explanations
- **Permutation Importance** — model-agnostic feature ranking
- **Gini Importance** — native tree-based feature importance
- **Partial Dependence Plots** — visualising how features affect predictions

---

## Tech Stack

- **Language:** Python
- **Environment:** Google Colab
- **Libraries:** Pandas, NumPy, Scikit-learn, XGBoost, SHAP, Matplotlib, Seaborn, Joblib
- **Data:** TfL Open Data (GTFS + SIRI-VM)

---

## Project Structure

```
├── london_arrival_bus_delay_prediction.ipynb   # Main notebook
```

---

## Real-World Applications

- Real-time delay notifications for passengers
- Proactive fleet dispatch and driver alerts
- Integration into TfL operational dashboards
- Passenger information system enhancement

---

## Future Work

- Include additional contextual data (weather, events, roadworks)
- Scale to other urban transit networks
- Deploy as a real-time prediction API
- Explore deep learning approaches (LSTM, Transformer)

---

*This project was submitted in partial fulfilment of the requirements for the Degree of Master of Science in Computer Science at Coventry University (2025/26).*
