
# Spark-Powered Personalised Finance Recommender with NLP

## Overview
This repository demonstrates a scalable, end-to-end machine-learning pipeline using **Apache Spark** to build a personalised financial-product recommender system.  
It combines **collaborative filtering (ALS)** and **natural-language processing (NLP)** to deliver predictive recommendations and sentiment analysis from customer reviews at scale.

The entire pipeline runs in **Google Colab**, making it reproducible and easy to adapt for learning or prototyping.

## Features
| Capability | Description |
|------------|-------------|
| **Scalable NLP** | Spark ML pipeline for tokenisation, stop-word removal, TF-IDF and logistic regression classification of review text. |
| **Collaborative Filtering** | ALS-based recommendation engine using user–item ratings. |
| **Big-Data Readiness** | Built with PySpark pipelines; supports serialisation of trained models for deployment. |
| **Practical Use Case** | Analyses customer sentiment and provides personalised recommendations for financial products. |

## Technologies Used
- **PySpark** – Distributed data processing and ML pipelines  
- **Spark MLlib** – ALS collaborative filtering, ML pipelines  
- **NLP Techniques** – Tokenisation, stop-word removal, TF-IDF, logistic regression  
- **Google Colab** – Reproducible cloud environment  
- **Python 3.11+** – Core programming language  

## Repository Structure
```bash
spark-finance-recommender/
├─ README.md # This file
├─ FinanceRecommender.ipynb # End-to-end pipeline in Colab
├─ data/ # Optional sample data
└─ models/ # Saved NLP and ALS models
```
## Quick Start

### 1. Environment Setup in Colab
```python
# Install Spark and dependencies
!apt-get install openjdk-11-jdk-headless -qq > /dev/null
!wget -q https://archive.apache.org/dist/spark/spark-3.4.3/spark-3.4.3-bin-hadoop3.tgz
!tar -xzf spark-3.4.3-bin-hadoop3.tgz
!pip install -q findspark
```
Configure environment variables and start Spark:
```bash
import os, findspark
os.environ["JAVA_HOME"] = "/usr/lib/jvm/java-11-openjdk-amd64"
os.environ["SPARK_HOME"] = "/content/spark-3.4.3-bin-hadoop3"
findspark.init()

from pyspark.sql import SparkSession
spark = SparkSession.builder.appName("FinanceRecommender").getOrCreate()
```
### 2. Create or Load Data
Use the provided sample dataset of user ratings and review texts, or load your own.

### 3. Build the NLP Pipeline
The notebook demonstrates how to:
- Tokenise review text
- Remove stop words
- Compute TF-IDF features
- Train a logistic regression classifier for sentiment or rating prediction

### 4. Train the ALS Recommender
Use Spark MLlib’s ALS algorithm to generate personalised product recommendations:
```bash
from pyspark.ml.recommendation import ALS
als = ALS(userCol="userId", itemCol="itemId", ratingCol="rating", coldStartStrategy="drop")
als_model = als.fit(df)
```
### 5. Save and Reload Models
Demonstrates model serialisation:
```bash
als_model.write().overwrite().save("/content/als_model")
nlp_model.write().overwrite().save("/content/nlp_pipeline_model")
```
### 6. Run Predictions
Examples are included for:
- ALS model – predicting ratings/recommendation scores for new user–item pairs
- NLP model – classifying sentiment of new review texts

### 7. Interpret Outputs
Output	Meaning:
- ALS prediction	Estimated rating or recommendation score for a user–item pair.
- NLP prediction	Predicted sentiment/rating class from review text.

### 8. Extend the Project
- Integrate Spark NLP for named-entity recognition or transformer embeddings
- Scale to real datasets (Kaggle, Amazon, Reddit, bank-app reviews)
- Add dashboards (Streamlit or Flask) backed by Spark for live demos

## Educational Goals
This project is aimed at:
- Data-science learners exploring PySpark, recommender systems and NLP pipelines
- Teams wanting a reproducible, low-barrier environment to test scalable ML workflows in financial services

## Disclaimer
This project is for educational and demonstration purposes only.
It does not make real financial recommendations and contains no personal data.

## License
This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

