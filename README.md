# Fraud Detection System: End-to-End Medallion Architecture
This project demonstrates a high-scale financial fraud detection pipeline built on Databricks. It processes over 6.3 million transactions, moving data through a structured Medallion Architecture—from raw ingestion to deep learning-based classification.

## Project Overview
The objective was to identify fraudulent financial activities within a massive dataset. By leveraging Spark for data engineering and TensorFlow for modeling, the system identifies high-risk transaction types (Transfer/Cash-out) and flags them with high recall.

## Technical Architecture
The pipeline follows the Medallion Architecture to ensure data quality and lineage:

Bronze (Raw): Ingestion of the 6.3M row financial dataset into Delta tables.

Silver (Refined): Data cleaning, schema enforcement, and currency localization to ZAR.

Gold (Aggregated): Feature engineering specifically focusing on transaction behavior and flagging high-risk categories identified during EDA.

## Tech Stack
Platform: Databricks

Storage: Azure Data Lake Storage (ADLS) / Delta Lake

Language: PySpark, Python

Machine Learning: TensorFlow (Deep Learning), Scikit-Learn (Random Forest)

Visualization: Matplotlib/Seaborn for EDA

## Machine Learning Approach
To ensure the highest possible detection rate, a "Challenger" modeling strategy was used:

Baseline Model: A Random Forest classifier was trained to establish performance benchmarks.

Deep Learning Model: A TensorFlow Neural Network was implemented to improve Recall, ensuring that fraudulent transactions are captured even when patterns are complex.

## Key Insights
Fraud Isolation: Exploratory analysis revealed that fraud is almost exclusively tied to TRANSFER and CASH_OUT transaction types.

Scalability: The use of Spark allows this pipeline to scale horizontally, making it capable of handling even larger financial datasets.

## How to Use
Data Ingestion: Run the 01_bronze_ingestion notebook to load raw data.

Transformation: Execute 02_silver_cleaning to process ZAR localization and data scrubbing.

Feature Engineering: Run 03_gold_features to prepare the modeling set.

Training: Execute 04_model_training to compare the Random Forest and TensorFlow results.