# 📈 Apple Inc. (AAPL) Advanced Stock Price Prediction using Multivariate LSTM

This project implements a professional-grade deep learning model to predict the daily closing price of Apple Inc. (AAPL). Unlike basic models that only use the closing price, this project utilizes a **Multivariate LSTM (Long Short-Term Memory)** network to capture complex market patterns.

## 🚀 Project Evolution: From Univariate to Multivariate
Initially, the project used a Univariate approach (only Close Price). To increase accuracy and robustness, I upgraded the model to a **Multivariate Architecture**, incorporating **Feature Engineering** to provide the model with market context.

## 🛠️ Technical Indicators (Feature Engineering)
To give the model a "trader's perspective," I integrated 6 key features:
1. **Closing Price:** The primary target variable.
2. **Trading Volume:** To confirm the strength of price movements.
3. **SMA (Simple Moving Average - 50 Days):** To identify the long-term trend.
4. **EMA (Exponential Moving Average - 50 Days):** To capture fast-reacting trend changes.
5. **RSI (Relative Strength Index - 14 Days):** To detect overbought and oversold conditions (Momentum).
6. **Volatility (50-Day Std Dev):** To measure market instability and risk.

## 🧠 Model Architecture
- **Model:** Stacked LSTM (2 Layers)
- **Input Shape:** (Batch, 30 Days Window, 6 Features)
- **Hidden Layers:** 128 units for higher complexity handling.
- **Optimization:** Adam Optimizer with Mean Squared Error (MSE) loss.
- **Scaling:** MinMaxScaler used to normalize diverse feature ranges (e.g., Volume vs RSI)

## 🛠️ Challenges Solved
- **Fixed Model Collapse:** Resolved the "Flat Line" prediction issue by implementing a shuffled DataLoader and optimizing the loss function.
- **Reduced Lag:** Increased the hidden layer capacity to 128 units to better track high-volatility peaks.
- **Data Leakage Prevention:** Ensured proper temporal splitting to maintain the integrity of the test set.

## 📈 Results
The model successfully tracks the actual stock price with high precision, capturing both the overall trend and short-term volatility of AAPL.

## ⚙️ How to Run
1. Open the `.ipynb` file in Google Colab.
2. Set Runtime to **GPU (T4)**.
3. Run all cells sequentially.
