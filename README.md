# 📈 Apple Inc. (AAPL) Stock Price Prediction using LSTM

This project implements a deep learning model to predict the daily closing price of Apple Inc. (AAPL) based on historical data. The project utilizes a **Long Short-Term Memory (LSTM)** network, which is specifically designed to capture long-term dependencies in time-series data.

## 🚀 Project Overview
The goal is to predict the next day's closing price using a sliding window of the previous 30 days. The model was developed using **PyTorch** and trained on historical data fetched from the **Yahoo Finance API**.

## 🛠️ Tech Stack
- **Language:** Python 3.x
- **Deep Learning Framework:** PyTorch
- **Data Handling:** Pandas, NumPy
- **Data Source:** yfinance (Yahoo Finance API)
- **Preprocessing:** Scikit-learn (MinMaxScaler)
- **Visualization:** Matplotlib
- **Environment:** Google Colab (T4 GPU / CUDA)

## 🧠 Model Architecture
- **LSTM Layers:** Stacked LSTM (2 Layers) to extract deep temporal patterns.
- **Prediction Head:** Linear layer to map LSTM hidden states to a single price value.
- **Loss Function:** Mean Squared Error (MSELoss).
- **Optimizer:** Adam Optimizer.
- **Data Loading:** PyTorch `DataLoader` with batch shuffling to prevent model collapse.

## 🛠️ Challenges & Solutions
During development, I encountered and solved two major machine learning hurdles:

1. **Underfitting (Flat Line Prediction):** 
   - *Issue:* Initially, the model predicted the median price (flat line).
   - *Solution:* Switched from `L1Loss` (MAE) to `MSELoss`, which penalizes larger errors more heavily, forcing the model to follow the trend.

2. **Model Collapse (Global Average):** 
   - *Issue:* The model stopped learning and predicted the global average of the entire 5-year history.
   - *Solution:* Implemented a `DataLoader` with `shuffle=True`. This broke the chronological rigidity and forced the model to learn the mathematical relationship between the 30-day window and the target price.

## 📈 Results
The final model successfully tracks the actual stock price movements with high accuracy, effectively capturing the volatility and trends of AAPL.

## ⚙️ How to Run
1. Open the `.ipynb` file in **Google Colab**.
2. Set the Runtime to **GPU (T4)**.
3. Run all cells sequentially.
