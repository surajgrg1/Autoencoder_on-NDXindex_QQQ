# NDX Portfolio Optimization using Autoencoder & Communality Analysis

This project explores the use of an **autoencoder neural network** to analyze return patterns in the **Nasdaq-100 Index (NDX)** using data from the **QQQ ETF**. The goal is to determine whether a smaller portfolio composed of stocks with shared or unique return structures can replicate the performance of the full index.

---

## 🧠 Objective

- Use deep learning (autoencoder) to detect **common return structures**.
- Identify stocks that are **most and least communal**.
- Construct and evaluate portfolios based on these groupings.
- Compare their performance via reconstruction **Mean Squared Error (MSE)**.

---

## 🔧 Methodology

### 📥 Data Preparation
- **Index**: NDX (Nasdaq-100), tracked via QQQ ETF.
- **Source**: Holdings and data fetched using `yfinance`.
- **Cleaning**: Aligned trading days, removed missing values, standardized returns.

### 🧮 Log Return Calculation
- Daily log returns calculated using:

  log_return = log(P_t / P_{t-1})

### 🧬 Autoencoder Model
- **Architecture**:
- Input: 100 nodes
- Hidden layers: 2-3 layers with ReLU activation
- Bottleneck: 5–10 nodes
- Output: 100 nodes (reconstruction layer)

- **Training Parameters**:
- Epochs: 500
- Batch Size: 128
- Loss: MSE
- Optimizer: Adam
- Early stopping: Used to prevent overfitting

### 🔍 Communality Analysis
- **Communality Score**: Based on reconstruction error.
- Low error → “Most Communal” stocks
- High error → “Least Communal” stocks

---

## 💼 Portfolio Construction & Evaluation

Two portfolios were created using different groupings of stocks:

| Model | Portfolio Description                         | Size | MSE (Reconstruction Error) |
|-------|-----------------------------------------------|------|----------------------------|
| 1     | 10 Most Communal + 15 Least Communal          | 25   | 0.0004781                  |
| 2     | 20 Most Communal + 30 Least Communal          | 50   | 0.0004446                  |

- **Weights**: Equal-weighted portfolios.
- **Returns**: Calculated as a dot product of return matrix and weight vector.

---

## 📈 Results & Interpretation

- **Model 2** (larger portfolio) yielded a **lower MSE**, suggesting that increasing portfolio size and diversity improves index approximation.
- Combining **most and least communal** stocks provides a richer representation of market behavior.
- Even with reduced stock count, the models achieved strong fidelity in capturing return structure.

---

## 💡 Key Takeaways

- Autoencoders are effective for identifying latent factors in financial return data.
- Portfolios based on communality scores offer a **smart way to downscale ETF replication**.
- Smaller portfolios (25–50 stocks) can closely mimic broader index dynamics if constructed thoughtfully.

---

## 📁 Included Files

- `Project_Autoencoder.html`: Autoencoder implementation & communality analysis
- `holdings_1750537492999.csv`: Data on QQQ ETF downloaded from NDX

---

## 🧾 Author

**Suraj Gurung**  
Ph.D. Candidate – Applied Economics & Statistics  
University of Florida  
GitHub: [@surajgrg1](https://github.com/surajgrg1)
