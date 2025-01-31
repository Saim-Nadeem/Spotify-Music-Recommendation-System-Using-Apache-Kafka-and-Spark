# Spotify-Music-Recommendation-System-Using-Apache-Spark

Saim Nadeem (i221884@nu.edu.pk)

## Introduction

This project entails building an Extract, Transform, Load (ETL) pipeline using the Free Music Archive (FMA) dataset to create a comprehensive music recommendation system. With over 100,000 tracks covering 161 genres, the dataset presents an ideal opportunity to explore music information retrieval (MIR) tasks. Using Python's Library Librosa, audio features will be extracted and transformed, employing techniques like Mel-Frequency Cepstral Coefficients (MFCC) and normalization to convert audio files into numerical formats. MongoDB will be utilized for scalable storage of transformed data. Apache Spark will then be employed to train recommendation models, we used ALS (Alternating Least Square) and Regression Evaluator from Spark Machine Learning Library for training the whole model and enhancing the accuracy. Finally, a web application will be developed using Python Flask, leveraging Apache Kafka for real-time music recommendations tailored to user preferences, thereby offering a seamless music streaming experience.

## Dependencies

- [MongoDB](https://www.geeksforgeeks.org/what-is-mongodb-working-and-features/)
- [Kafka Producer](https://kafka-python.readthedocs.io/en/master/apidoc/KafkaProducer.html)
- [Kafka Consumer](https://kafka-python.readthedocs.io/en/master/apidoc/KafkaConsumer.html)
- [Apache Spark ML Library](https://spark.apache.org/docs/latest/ml-guide.html)
- [ALS](https://spark.apache.org/docs/latest/api/python/reference/api/pyspark.ml.recommendation.ALS.html)
- [Flask](https://flask.palletsprojects.com/en/3.0.x/)

## Extract, Transform, Load (ETL) Pipeline
The initial phase of the project involves creating an Extract, Transform, Load (ETL) pipeline utilizing the Free Music Archive (FMA) dataset. FMA is a comprehensive dataset suitable for various endeavors in Music Information Retrieval (MIR). The dataset consists of 106,574 tracks, each lasting 30 seconds and spanning 161 unevenly distributed genres. Additionally, the fma_metadata.zip file provides essential track details such as title, artist, genres, tags, and play counts for all tracks.

### 1) Data Acquisition: 

Download the fma_large.zip dataset containing audio tracks and the fma_metadata.zip file containing track details.

### 2) Feature Extraction: 

Perform feature extraction to convert audio files into numerical and vector formats. We used the technique of Mel-Frequency Cepstral Coefficients (MFCC).

### 3) Data Transformation: 

Explore normalization and standardization techniques to enhance the accuracy of the recommendation model.

### 4) Data Storage: 

Store the transformed data in a scalable and accessible manner using MongoDB for efficient retrieval and processing.

## Music Recommendation Model 

This phase related to building a music recommendation system using Apache Spark. It begins by creating a SparkSession and loading data from MongoDB into a DataFrame. Then the real time user preference has been catched by the system and then the producer send that to consumer and the whole training process performs in consumer. Then, it applies various transformations to the DataFrame, including converting string features to float lists, indexing string columns, and exploding arrays. Next, it assembles features into vectors and splits the data into training and test sets, removing outliers from the training data. The code then trains a collaborative filtering model using ALS (Alternating Least Squares) and generates recommendations for specific users. Finally, it evaluates the model's performance and displays the recommendations with their corresponding track titles before stopping the SparkSession. Then consumer sends the top 10 recommendations to the Flask process for real time web interface.

### 1) Kafka Producer: 

Kafka Prodcuer reads the data from mongodb and data about the user selected and send to the consumer and then the following steps are performed in consumer.

### 2) ALS (Alternating Least Squares): 

ALS is a matrix factorization technique commonly used in collaborative filtering for recommendation systems. It factors the user-item interaction matrix into two lower-dimensional matrices representing user and item latent features, iteratively minimizing the difference between the observed and predicted ratings.

### 3) String Indexer: 

String Indexer is a feature transformer in Spark ML that encodes categorical string columns into numerical indices. It is often used to prepare categorical data for machine learning algorithms.

### 4) Vector Assembler: 

Vector Assembler is a feature transformer in Spark ML that assembles multiple feature columns into a single vector column. It is typically used to combine feature columns before feeding data into machine learning algorithms.

### 5) Regression Evaluator: 

Regression Evaluator is a model evaluation metric in Spark ML used to evaluate regression models' performance. It calculates the root mean squared error (RMSE) between predicted and actual values to assess the model's accuracy. However, it's commented out in this code.

## Deployment
The final phase focuses on deploying the trained model onto a web application, specifically a streaming service. The web application is expected to provide an interactive user experience while seamlessly integrating the recommendation system.

### 1) Web Application Development: 

Develop an interactive music streaming web application with a user-friendly interface using Python Flask.

### 2) Real-time Recommendation: 

Implement Apache Kafka to dynamically generate music recommendations in real-time based on historical playback data, tailoring suggestions to each user's preferences.

### 3) User Activity Monitoring: 

Monitor user activity within the web application to generate personalized recommendations, without requiring users to upload audio files.

### 4) Integration: 

Integrate the recommendation system with the web application to provide a seamless user experience, where recommendations are generated in real-time as users interact with the platform.

## Conclusion:

The completion of this project will result in a robust music recommendation system deployed on a streaming web application. By leveraging ETL pipelines, advanced machine learning techniques, and real-time data processing, the system aims to deliver personalized music recommendations to users, enhancing their overall listening experience.

## References

- Apache Spark ML Library: https://medium.com/data-and-beyond/unleashing-the-power-of-machine-learning-with-spark-ml-and-pyspark-ml-9120697c0745
- Alternating Least Squares (ALS): https://github.com/recommenders-team/recommenders/blob/main/examples/02_model_collaborative_filtering/als_deep_dive.ipynb
- Database (MongoDB): https://en.wikipedia.org/wiki/MongoDB
- Flask: https://en.wikipedia.org/wiki/Flask_(web_framework)

![Screenshot 2024-06-30 014740](https://github.com/Saim-Nadeem/Spotify-Music-Recommendation-System-Using-Apache-Kafka-and-Spark/assets/137045037/d49f72b8-9e92-4744-98cc-a2c1f4f3744c)
![Screenshot 2024-06-30 014813](https://github.com/Saim-Nadeem/Spotify-Music-Recommendation-System-Using-Apache-Kafka-and-Spark/assets/137045037/197e9909-2b40-4360-a598-6814a751b4a6)
![s3](https://github.com/moiztanvir/Spotify-Music-Recommendation-System-Using-Apache-Spark/assets/151388609/15f9e477-5592-4059-b170-149f0156eb0b)

