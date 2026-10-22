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

### 2. Window Size
I used a **50-day sliding window**, chosen to align with the 50-day rolling indicators (SMA, EMA, Volatility) so the model gets enough context to interpret those features. I did not run a full comparison against other window sizes.

### 3. Training
Each model was trained for **150 epochs** (Adam, learning rate 0.001, MSE loss, batch size 32). Final training losses converged to around 0.0003–0.0006 on the scaled data. I did not track a validation curve, so I make no claim about where overfitting would begin.

## 📈 Final Results
The **GRU model with a 50-day window** is my preferred architecture — it captures the price trends as well as the LSTM with fewer parameters and faster training (GRU final loss: 0.000334). Note this is an educational exercise, not investment advice.

## 🚀 How to Run
1. Clone the repo: `git clone https://github.com/kifayat-irfan/APPLE-Stock-Price-Prediction.git`
2. Install requirements: `pip install -r requirements.txt` (the notebooks also install `numpy<2.0` first for pandas compatibility)
3. Run the notebooks in the `/notebooks` folder — data is fetched from Yahoo Finance via `yfinance` and saved to `/data/AAPL_featured_data.csv`.

## 📁 Project Structure
- `notebooks/LSTM_Prediction.ipynb` — data download, feature engineering, LSTM training, results plot
- `notebooks/GRU_Prediction.ipynb` — same pipeline with the GRU architecture
- `data/AAPL_featured_data.csv` — AAPL data with the 6 engineered features
- `results/` — final actual-vs-predicted plots for both models
- `report.md` — full write-up of the methodology and findings
