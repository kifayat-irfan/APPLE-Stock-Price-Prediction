# 📈 Apple Inc. (AAPL) Multivariate Stock Price Prediction

## 📌 Project Overview
This project implements a Time-Series Forecasting model to predict the closing price of AAPL stock. Unlike univariate models, this project uses a **Multivariate approach**, incorporating technical indicators to provide the model with deeper market context.

## 🛠 Tech Stack
- **Language:** Python
- **Deep Learning Framework:** PyTorch
- **Data Handling:** Pandas, NumPy, YFinance
- **Preprocessing:** Scikit-Learn (MinMaxScaler)
- **Indicators:** SMA, EMA, RSI, Volatility

## 🧬 Feature Engineering
To improve accuracy, the following 6 features were used:
1. **Close Price:** The target variable.
2. **Volume:** Trading activity.
3. **SMA (50):** Long-term trend.
4. **EMA (50):** Fast trend sensitivity.
5. **RSI (14):** Momentum and overbought/oversold conditions.
6. **Volatility (50):** Market stability measurement.

## 🔬 Comparative Analysis

### 1. LSTM vs GRU
I implemented both LSTM and GRU architectures. While the **LSTM** provided high accuracy, the **GRU** achieved nearly identical results with significantly faster training times and fewer parameters, making it more efficient for this dataset.

### 2. Impact of Window Size
I experimented with different sliding window sizes:
- **Window 30:** Resulted in higher lag and lower accuracy.
- **Window 50:** Provided the best results as it aligned with the rolling indicators, allowing the model to capture the 50-day trend more effectively.

### 3. Epoch Tuning
The model was trained for **150 epochs**. Beyond this point, the model showed signs of overfitting, where it began to memorize training noise rather than learning the general trend.

## 📈 Final Results
The **GRU model with a 50-day window** emerged as the best performing architecture, successfully capturing the price trends with minimal error.

## 🚀 How to Run
1. Clone the repo: `git clone https://github.com/yourusername/AAPL-Stock-Prediction.git`
2. Install requirements: `pip install -r requirements.txt`
3. Run the notebooks in the `/notebooks` folder.
