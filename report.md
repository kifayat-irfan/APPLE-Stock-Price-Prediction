# 📈 Project Report: APPLE Stock Price Prediction

## 1. Introduction
The objective of this project was to build a robust time-series forecasting model to predict the closing price of Apple Inc. (AAPL) stock. To move beyond simple price-only predictions, a **multivariate approach** was implemented, incorporating key technical indicators to provide the model with deeper market context.

## 2. Dataset and Feature Engineering
The data was acquired via the `yfinance` API. To provide the model with a comprehensive view of the stock's behavior, the following 6 features were engineered:
- **Close Price:** The primary target variable.
- **Volume:** To measure trading activity and liquidity.
- **SMA (50):** Simple Moving Average to identify the long-term trend.
- **EMA (50):** Exponential Moving Average for higher sensitivity to recent price changes.
- **RSI (14):** Relative Strength Index to identify overbought or oversold conditions.
- **Volatility (50):** Standard deviation of the price to measure market stability.

## 3. Model Architecture
Two state-of-the-art Recurrent Neural Network (RNN) architectures were implemented and compared:

### A. Long Short-Term Memory (LSTM)
- **Structure:** Stacked LSTM layers with a hidden size of 128.
- **Mechanism:** Uses three gates (Forget, Input, Output) to maintain a separate cell state for long-term memory.
- **Performance:** High accuracy but computationally heavier due to the number of parameters.

### B. Gated Recurrent Unit (GRU)
- **Structure:** Stacked GRU layers with a hidden size of 128.
- **Mechanism:** Uses two gates (Reset, Update) and merges the cell state into the hidden state.
- **Performance:** Nearly identical accuracy to LSTM but with significantly faster training and lower memory consumption.

## 4. Hyperparameter Analysis

### 4.1 Window Size Comparison (30 vs 50 Days)
- **Observation:** The model with a **50-day window** significantly outperformed the 30-day window.
- **Reasoning:** Since the technical indicators (SMA, EMA, Volatility) were calculated on a 50-day basis, the model required at least 50 days of context to properly interpret these features. Window 30 was too short to capture the full trend.

### 4.2 Epoch Tuning
- **Training:** The models were trained for **150 epochs**.
- **Result:** This duration allowed the models to converge without overfitting, ensuring the model learned the general trend rather than memorizing training noise.

## 5. Results and Conclusion
- **Best Model:** The **GRU architecture** was selected as the optimal choice due to its computational efficiency and comparable accuracy to the LSTM.
- **Optimal Configuration:** `GRU + 50-Day Window + 150 Epochs`.
- **Final Insight:** The model successfully captures the general trend of the stock. A slight "lag" is observed in the predictions, which is a common challenge in financial time-series forecasting.

---
*Report generated as part of the AAPL Stock Prediction Project.*
