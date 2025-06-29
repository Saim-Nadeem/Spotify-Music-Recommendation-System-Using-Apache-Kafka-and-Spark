🎵 Spotify Music Recommendation System Using Apache Spark & Kafka

[![Python](https://img.shields.io/badge/Built%20with-Python-blue.svg)](https://www.python.org/)
[![Spark](https://img.shields.io/badge/Engine-Apache%20Spark-orange.svg)](https://spark.apache.org/)
[![Kafka](https://img.shields.io/badge/Streaming-Apache%20Kafka-8B0000.svg)](https://kafka.apache.org/)
[![MongoDB](https://img.shields.io/badge/Database-MongoDB-green.svg)](https://www.mongodb.com/)
[![Flask](https://img.shields.io/badge/Web%20App-Flask-black.svg)](https://flask.palletsprojects.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A real-time AI-powered music recommendation system that uses the Free Music Archive dataset, Apache Spark (ALS model), and Apache Kafka to stream and deliver personalized track suggestions through a web app built with Flask.

---

## 📁 Project Structure

```
├── static/                   # Web static assets (CSS, JS, images)
├── templates/                # HTML templates for Flask
├── Project.py                # Main Spark ML model builder
├── auto_run.py               # Launch helper
├── change.py                 # Helper to switch user/genre settings
├── consumer.py               # Kafka consumer with Spark model pipeline
├── producer.py               # Kafka producer to stream user input
├── genre_find.py            # Genre categorization logic
├── music.txt                # Sample music metadata
├── similar.txt              # Similarity logs
├── web_app.py               # Flask server with front-end UI
├── README.md                # You are here
```

---

## 👋 Introduction

This project builds an end-to-end **music recommendation system** using:
- 🧱 ETL pipeline with audio features (MFCC)
- 🔄 Real-time stream processing with Apache Kafka
- 🎛️ Collaborative filtering using ALS in Apache Spark
- 🌐 Flask-based web interface
- 📊 MongoDB for scalable feature storage

We use the **Free Music Archive (FMA)** dataset with 100k+ tracks and 161 genres for robust MIR (Music Information Retrieval).

---

## ⚙️ Technologies Used

- Apache Spark ML (ALS, Regression Evaluator)
- Kafka Producer & Consumer
- MongoDB
- Librosa for feature extraction
- Flask for web UI

---

## 🔄 ETL Pipeline

### 1️⃣ Data Acquisition
- Download `fma_large.zip` and `fma_metadata.zip` datasets

### 2️⃣ Feature Extraction
- Extract Mel-Frequency Cepstral Coefficients (MFCC) using Librosa

### 3️⃣ Data Transformation
- Normalize and standardize audio features

### 4️⃣ Data Storage
- Store all track metadata and features in MongoDB

---

## 🎵 Model Training & Recommendation

### 🔸 Kafka Producer
- Sends user ID / genre preferences to the pipeline

### 🔸 Kafka Consumer
- Receives data, triggers Spark's ALS model
- Performs feature vectorization and filtering
- Applies `StringIndexer`, `VectorAssembler`

### 🔸 ALS Model
- Trained on historical preferences and metadata
- Outputs ranked recommendations

### 🔸 Regression Evaluator (Optional)
- Evaluates RMSE performance (commented in current code)

---

## 🌍 Deployment via Flask

### ✅ Real-Time Interaction
- Web app lets users select genre, mood, or artist

### ✅ Kafka Integration
- Sends input to Kafka → receives personalized output

### ✅ Real-Time UI
- Displays top 10 recommended tracks

### ✅ No Upload Required
- Playback history inferred from preloaded dataset

---

## ▶️ How to Run

### 1. Start MongoDB and Kafka
- Ensure `mongod`, `zookeeper`, and `kafka-server` are running

### 2. Launch Components
```bash
python producer.py
python consumer.py
python web_app.py
```
- Or use `auto_run.py` to simplify

### 3. Open Web App
- Visit `http://localhost:5000` in browser

---

## 📸 Screenshots

### 🔹 Homepage
![Screenshot 1](https://github.com/Saim-Nadeem/Spotify-Music-Recommendation-System-Using-Apache-Kafka-and-Spark/assets/137045037/d49f72b8-9e92-4744-98cc-a2c1f4f3744c)

### 🔹 Top Recommendations
![Screenshot 2](https://github.com/Saim-Nadeem/Spotify-Music-Recommendation-System-Using-Apache-Kafka-and-Spark/assets/137045037/197e9909-2b40-4360-a598-6814a751b4a6)

### 🔹 Similar Music Panel
![Screenshot 3](https://github.com/moiztanvir/Spotify-Music-Recommendation-System-Using-Apache-Spark/assets/151388609/15f9e477-5592-4059-b170-149f0156eb0b)

---

## 📌 References

- Apache Spark ML Guide: https://spark.apache.org/docs/latest/ml-guide.html
- ALS Deep Dive: https://github.com/recommenders-team/recommenders/blob/main/examples/02_model_collaborative_filtering/als_deep_dive.ipynb
- MongoDB Overview: https://en.wikipedia.org/wiki/MongoDB
- Flask Framework: https://flask.palletsprojects.com/

---

## 👤 Author

**Saim Nadeem**  
📧 Email: i221884@nu.edu.pk  
🔗 GitHub: [Saim-Nadeem](https://github.com/Saim-Nadeem)

