# Project: Predicting Stock Prices
[cite_start][cite: 3, 297]

## 📈 Overview

[cite_start]This project trains and compares several data mining models, including those in **Orange Data Mining Tools**, to predict stock prices[cite: 5, 299]. [cite_start]The goal is to analyze the features and performance of these models to find the most suitable approach for financial forecasting[cite: 5, 299].

* **Stocks Analyzed:**
    * [cite_start]`0016.HK` (Sun Hung Kai Properties) [cite: 7, 301]
    * [cite_start]`0017.HK` (New World Development) [cite: 7, 301]
* [cite_start]**Data Source:** CSV datasets downloaded from **Yahoo Finance**[cite: 8, 302].
* [cite_start]**Training Data:** January 3rd, 2019 to June 29th, 2022[cite: 9, 303].
* [cite_start]**Test Data:** July 4th, 2022 to October 28th, 2022[cite: 9, 303].

*Fig. [cite_start]1: 0016 HK Training Data price trends (a) and trading volume (b)*[cite: 30, 307].

---

## 🛠️ Part 1: Analysis with Orange Data Mining

[cite_start]The initial analysis used the Orange data mining platform to compare five baseline models[cite: 77, 314]:
* k-Nearest Neighbors (kNN)
* Support Vector Machine (SVM)
* Random Forest
* Linear Regression
* Neural Network

### Workflow

[cite_start]The entire process was built in Orange, covering data preparation, model training, testing, and prediction[cite: 100, 315].

*Fig. [cite_start]4: The complete training process in Orange (Blue: Data preparation, Red: Training & Testing, Green: Predict & Saving)*[cite: 100, 315].

### Feature Engineering

[cite_start]Three different groups of features were tested to train the models[cite: 103, 319]:

1.  [cite_start]**Features 1:** Basic stock data (High, Open, Low, Volume, Close, AdjClose)[cite: 104, 320].
2.  [cite_start]**Features 2:** Time-lagged data (e.g., `Day_n-1`, `n-1%`, `Day_n-2`, `n-2%`) manually calculated in Excel[cite: 110, 112, 327, 329].
3.  [cite_start]**Features 3:** Technical indicators (5-day & 10-day moving average, 5-day & 10-day forecast) also calculated in Excel[cite: 118, 119, 336, 337].

### Orange Model Findings

* [cite_start]**Best Model:** **Linear Regression** was determined to be the most suitable model for these datasets[cite: 130, 349]. [cite_start]It consistently had the highest R2 scores and one of the fastest training times[cite: 127, 129, 346, 348].
* [cite_start]**Poorest Model:** The **Neural Network** model in Orange was found to be "completely unsuitable"[cite: 132, 351]. [cite_start]It had the longest training time and the poorest R2 scores[cite: 132, 351].

---

## 🧠 Part 2: Temporal Convolutional Network (TCN)

[cite_start]A **Temporal Convolutional Network (TCN)** was chosen as a new method to compare against the baseline models[cite: 136, 355].

### Rationale

[cite_start]The TCN model was selected for the "simple reason that **time plays an important role**" in stock prediction[cite: 137, 356]. [cite_start]Unlike the other models where time was just a feature, the TCN combines the strengths of CNNs and RNNs and can "remember" data from a long time ago to make proper predictions[cite: 138, 271, 357, 372].

### TCN Results

[cite_start]The TCN model proved to be **much more suitable** for this application[cite: 269, 370].

[cite_start]After 200 epochs, the Mean Absolute Error (MAE) dropped to **0.0242** for stock 0016 and **0.0155** for stock 0017[cite: 268, 369]. [cite_start]This error rate is approximately **30 times smaller** than the errors from the models used in Orange[cite: 268, 369].

The prediction graphs clearly show the TCN's predicted price (orange) closely tracking the real stock price (blue).

*Fig. [cite_start]10(a): 0016 TCN prediction curve (orange) and real curve (blue)*[cite: 173, 364].

*Fig. [cite_start]10(b): 0017 TCN prediction curve (orange) and real curve (blue)*[cite: 174, 365].

---

## 💡 Project Conclusions

This project yielded two main findings:

1.  [cite_start]**Model Suitability is Key:** The most important finding was the experience of choosing the *most suitable* model[cite: 273, 374]. [cite_start]There is "no priority between models"[cite: 278, 379]. [cite_start]The "advanced" Neural Network performed the worst, while the "inferior" Linear Regression performed the best in the initial tests [cite: 274-277, 375-378].
2.  [cite_start]**Feature Selection is Critical:** The second finding is that choosing the right features is essential[cite: 281, 383]. [cite_start]Adding "useless features" increases training time without improving R2 scores or lowering MAE[cite: 283, 385]. [cite_start]This highlights the practical need for correlation analysis to understand the relationship between data[cite: 284, 387].

---

## 💻 Tools & Data

* **Primary Tools:** Orange Data Mining, Python
* **Supporting Tools:** Microsoft Excel (for feature calculation)
* **Data Source:** [Yahoo Finance](https://finance.yahoo.com/)