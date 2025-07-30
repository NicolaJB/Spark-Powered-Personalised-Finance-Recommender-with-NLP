# Spark-Powered Personalised Finance Recommender with NLP

This project demonstrates a scalable, end-to-end machine learning pipeline using Apache Spark for building a **personalised product recommendation system** for financial services. It combines collaborative filtering (ALS) and natural language processing (NLP) techniques to deliver intelligent insights from user reviews, offering both predictive recommendations and sentiment analysis at scale.

This application is built and executed entirely in **Google Colab**, making it accessible and reproducible for learning and experimentation.

---

## Features

| Capability                | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| **Scalable NLP**         | Spark-based pipeline for tokenisation, stop word removal, TF-IDF, and classification |
| **Collaborative Filtering** | ALS-based recommendation system using user–item ratings                    |
| **Big Data Readiness**   | Built with PySpark pipelines and supports serialisation of trained models   |
| **Practical Use Case**   | Analyses customer sentiment and provides personalised recommendations for financial products |

---

## Sections Overview

### 1. Environment Setup

Configures Spark 3.4.3 with Hadoop in a Colab environment, including required dependencies and Java setup.

### 2. Sample Data Creation

Creates a synthetic dataset of users rating financial products and writing short review texts. Each record includes:
- `userId`
- `itemId`
- `rating` (1–5)
- `text` (customer feedback)

### 3. NLP Pipeline (Spark ML)

Builds a Spark ML pipeline for processing review text:
- Tokenisation
- Stop word removal
- Feature extraction via TF-IDF
- Logistic regression for sentiment or rating classification

This enables sentiment prediction from user reviews using distributed processing.

### 4. ALS Recommendation Engine

Implements Spark MLlib’s **Alternating Least Squares (ALS)** algorithm to generate personalised product recommendations from explicit ratings. Trained on the user–item matrix and configured to drop cold-start entries.

### 5. Model Serialisation

Demonstrates how to save and reload both the NLP and ALS models using:
```python
nlp_model.write().overwrite().save("path")
als_model.write().overwrite().save("path")
```

This ensures readiness for large-scale deployment or batch inference.

### 6. Example Inference & Predictions

Shows how to:
- Use the **ALS model** to predict ratings for unseen user–item pairs.
- Use the **NLP model** to classify sentiment from user review text.

Also explains cold-start handling and data verification against the training set.

---

## Educational Goals

This project is intended for:
- Data science learners exploring **PySpark**, **recommender systems**, and **NLP pipelines**
- Demonstrating scalable ML workflows in **financial services**
- Providing a reproducible setup in a low-barrier environment (Colab)

---

## Example Use Cases

- Recommend credit cards or investment tools based on user preferences and past reviews.
- Automatically assess and score customer feedback for support teams.
- Evaluate service quality trends from large-scale textual data.

---

## Extending the Project

You can further enhance the system by:
- Incorporating Spark NLP for advanced text analysis (NER, sentiment, embeddings)
- Scaling to real-world datasets from Kaggle, Amazon, or Reddit
- Adding dashboards (e.g. with Streamlit or Flask + Spark backend)

---

## Sample Data Sources

For larger or real-world datasets:
- [Kaggle](https://www.kaggle.com/) — Amazon reviews, financial product reviews
- [Alpha Vantage](https://www.alphavantage.co/) or [Quandl](https://www.quandl.com/) for market data
- Reddit (e.g. r/personalfinance) or Twitter — financial discussions and sentiment
- Public bank reviews, app store comments, or simulated user interaction logs

---

## Disclaimer

This project is created solely for **educational and demonstration purposes**. No real financial recommendations are made, and no personal data is used.

