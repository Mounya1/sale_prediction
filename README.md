
# Sales Revenue Prediction Pipeline

## 📌 Introduction

In the modern e-commerce landscape, businesses generate massive volumes of data daily. To leverage this data, they need efficient and scalable pipelines for real-time data processing and machine learning.

This project focuses on building a **machine learning pipeline** that predicts sales revenue based on historical and real-time data streams. We employ **Spark Streaming, Kafka, Apache Airflow, and Gradient Boosted Trees (GBT)** for a seamless flow from data ingestion to revenue prediction.

The integration of real-time data adds a layer of business relevance, helping businesses make quick, informed decisions. The goal is to develop a **robust, scalable, and accurate system** for forecasting sales revenue.

---

## 🚩 Problem Description

The primary problem addressed in this project is the **need for accurate revenue prediction using real-time data streams**.

E-commerce platforms face challenges due to high data volumes and delays in decision-making when data is unprocessed. By incorporating both historical and real-time data into a machine learning model, businesses can generate reliable forecasts and improve operational efficiency.

**Key Challenges**:

1. Handling large-scale data streaming with low latency.
2. Ensuring data quality and performing real-time validation.
3. Developing a scalable ML model capable of making accurate predictions in a dynamic environment.

---

## 📊 Dataset Description

The dataset comprises **global sales data** with variables such as:

* Region, Country
* Item Type, Sales Channel (Online/Offline)
* Order Priority, Order Date, Ship Date
* Units Sold, Unit Price, Total Revenue, Total Profit

**Data Source**: [Kaggle Dataset Link](#)

This dataset provides a comprehensive view of global sales trends and is essential for revenue forecasting.

---

## 🔄 Project Flow Diagram

*(Insert Flow Diagram here — e.g., PNG or Mermaid diagram)*

---

## ⚙️ Tools & Technologies

* **Apache Kafka** – Real-time data ingestion
* **Apache Spark (Streaming + MLlib)** – Data processing & machine learning
* **Apache Airflow** – Orchestration & scheduling
* **Google Cloud Platform (GCP)** – Cloud infrastructure
* **Python** – Data preprocessing & modeling

---

## 🛠 Methodology

### 1. Data Division

* **Historical Data (up to 2023):** Stored in DB, used for training/validation.
* **Real-Time Data (2024):** Simulated via Kafka, processed in Spark Streaming, validated, then integrated.

### 2. Real-Time Data Streaming

* Kafka streams live sales data.
* Spark Streaming validates and processes records in real-time.

### 3. Automated Validation (Airflow)

* Validated data stored in `salesStreamed` table.
* Airflow triggers when **50k rows** accumulate.
* Airflow merges real-time + historical data, exports unified datasets as CSV.
* Orchestration ensures modular, reliable workflows.

### 4. Data Preprocessing

* **Temporal Features:** Extracted *Order Year* & *Order Month*.
* **Categorical Features:** Encoded using `StringIndexer` + `OneHotEncoder`.
* **Scaling:** Normalized numerical features with `StandardScaler`.

### 5. Feature Engineering

* **Units Sold Prediction:** Used Order Year/Month, Unit Price/Cost, Revenue, Cost, and categorical encodings.
* **Revenue Prediction:** Used Units Sold, Unit Price/Cost, Order Year/Month, and categorical encodings.

### 6. Machine Learning Model

* **Gradient Boosted Trees Regressor (GBT)** used for both *Units Sold* and *Total Revenue* prediction.
* Handles **non-linear relationships** and complex sales patterns.

### 7. Pipeline Integration

* End-to-end Spark ML pipeline built for ingestion → preprocessing → prediction.
* Airflow orchestrates all tasks.

---

## 📈 Results

### 🔹 Total Revenue Model (GBT Regression)

* **RMSE:** `69451.15`
* **Performance:** Captured short- & long-term revenue trends.
* **Accuracy:** Outperformed traditional forecasting methods.
* **Scalability:** Robust integration of historical + real-time streams.

### 🔹 Units Sold Model (GBT Regression)

* **RMSE:** `393.85`
* **Performance:** Reliable unit sales prediction across diverse datasets.
* **Trends:** Robust for immediate and long-term sales forecasting.

---

## 💡 Discussion

**Challenges:**

1. Real-time validation while maintaining low latency.
2. Large-scale dataset required optimized Spark configurations.
3. Complex integration of Kafka, Spark, GCP.
4. Hyperparameter tuning for GBT.

**Limitations:**

1. Model doesn’t account for external market/economic factors.
2. Static features like unit price/cost limit adaptability.
3. Real-time processing may slow with increasing data volumes.

---

## ✅ Conclusion

This project demonstrates a **scalable sales prediction system** using **cloud computing & machine learning**.

By combining **historical and real-time data**, we built a robust pipeline that enables accurate revenue forecasting. Integration of **Kafka, Spark Streaming, and Airflow** ensures efficiency, scalability, and reliability in e-commerce data-driven decision-making.

---

## 📚 References

* Spark, Kafka, GCP Documentation
* Friedman, J. H. (2001). *Greedy function approximation: a gradient boosting machine.* Annals of statistics.
* Zaharia, M., et al. (2016). *Apache Spark: A Unified Engine for Big Data Processing.*
* Gama, J., & Rodrigues, P. P. (2007). *Stream-based methods for unsupervised online learning.*

---

## 👥 Team Contributions

* **Sashank Talakola:** Built Kafka + Spark Streaming pipeline & real-time validation (Airflow).
* **Mounya Inampudi:** Focused on ML model selection & tuning, implemented GBT for revenue prediction.
* **Junaid Ahmed Mohammed:** Handled data preprocessing, feature engineering, and report writing.

---

✨ *This project showcases how real-time big data pipelines combined with advanced ML models can transform e-commerce forecasting.*

---

Do you want me to also create a **Mermaid flow diagram** (so GitHub renders it directly) for your pipeline, or should I format it to expect an uploaded PNG instead?
