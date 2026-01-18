# Bank Marketing Campaign Analysis: Classifier Comparison

## Project Overview
This project compares the performance of various classification algorithms—**K-Nearest Neighbors (KNN)**, **Logistic Regression**, **Decision Trees**, and **Support Vector Machines (SVM)**—on a bank marketing dataset. 

The primary objective is to predict whether a client will subscribe to a term deposit, helping the banking institution optimize its marketing campaigns and improve resource allocation.

## Data Source
The dataset is sourced from the **UCI Machine Learning repository**: [Bank Marketing Data Set](https://archive.ics.uci.edu/ml/datasets/bank+marketing). It contains information about direct marketing campaigns (phone calls) conducted by a Portuguese banking institution from May 2008 to November 2010.

---

## Methodologies & Workflow

### 1. Data Understanding & Preprocessing
* **Initial Exploration:** Analyzed `bank-additional-full.csv` to understand feature types and distributions.
* **Cleaning:** Replaced 'unknown' categorical values with `np.nan`.
* **Encoding:** Converted the target variable `y` ('yes'/'no') to binary (1/0) and applied **One-Hot Encoding** to categorical features.
* **EDA:** Visualized numerical distributions and subscription rates to identify key drivers.

### 2. Modeling Strategy
* **Train/Test Split:** 80/20 split with stratification to maintain class balance.
* **Baseline:** Established a benchmark using a `DummyClassifier` (most_frequent strategy).
* **Model Comparison:** Evaluated four primary classifiers using default settings.
* **Hyperparameter Tuning:** Utilized `GridSearchCV` to optimize for the **F1-score**, ensuring a balance between Precision and Recall.

---

## Key Findings and Results

After extensive hyperparameter tuning, the models yielded the following results:

| Model | Train Time | Train Acc | Test Acc | Precision | Recall | F1-Score | Best Params |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Decision Tree** | 42.86s | 0.9160 | **0.9184** | 0.6773 | 0.5269 | **0.5927** | `max_depth: 5, min_samples_leaf: 4` |
| **KNN** | 541.01s | 0.9241 | 0.9103 | 0.6289 | 0.4968 | **0.5551** | `metric: manhattan, n_neighbors: 9` |
| **Logistic Regression** | 881.97s | 0.9096 | 0.9133 | 0.6989 | 0.4052 | **0.5130** | `C: 1, solver: liblinear` |
| **SVM (SVC)** | 773.23s | 0.8707 | 0.8699 | 0.4317 | 0.4903 | **0.4591** | `C: 10, kernel: linear` |

### Performance Highlights
* **Top Performer:** The **Tuned Decision Tree** emerged as the best model with an F1-score of **0.5927**.
* **Efficiency:** The Decision Tree was significantly faster to train (42.86s) compared to the others.
* **Trade-offs:** While Logistic Regression offered the highest Precision, it suffered from lower Recall.

## Conclusion
The **Tuned Decision Tree** model provides the most optimal balance between identifying potential subscribers and minimizing false positives. Due to its high F1-score and low computational cost, this model is recommended for the bank's future marketing campaigns.
