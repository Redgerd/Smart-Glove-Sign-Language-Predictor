# IoT-Enabled Assistive Glove for Real-Time Sign Language Translation  

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)  [![TensorFlow](https://img.shields.io/badge/TensorFlow-2.9-orange?style=for-the-badge&logo=tensorflow&logoColor=white)](https://www.tensorflow.org/)  [![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.0-yellowgreen?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)  

## Overview  
This project introduces an **IoT-enabled assistive glove** for translating gestures from American Sign Language (ASL) into text and speech in real time. It bridges the communication gap between the deaf and hearing communities using innovative IoT, machine learning, and app development technologies.  

### Key Features:  
- Real-time gesture recognition (static and dynamic).  
- Flutter-based mobile app with text-to-speech and learning modules.  
- High accuracy (97%) using Random Forest for gesture classification.

## System Architecture  

![image](https://github.com/user-attachments/assets/0054fd96-2963-465c-a30d-840952a41356)


### Components:  
1. **Sensors**: Flex sensors, MPU-6050 gyroscope, accelerometer.  
2. **Processing**: Arduino Nano for sensor data collection and Bluetooth transmission.  
3. **Mobile App**: Flutter-based app with FastAPI backend for real-time gesture recognition.  

### Mobile Application  

Access the mobile application here: [Flutter Mobile App](https://github.com/hba777/sign_glove_application).  

## Dataset  

### Features:  
- **Input Sensors**:  
  - **Flex Sensors**: Track finger bending.  
  - **Accelerometer**: Measures device acceleration.  
  - **Gyroscope**: Tracks angular velocity.  
- **Target Variable**: ASL gestures (e.g., "hello," "sorry").  

### Dataset Details:  
- **Samples**: ~14,000 gesture points.  
- **Gestures**: Includes static gestures (A-F) and dynamic gestures ("hello," "sorry").  
- **Data Distribution**:  
  - "Yes" and "No" involve repetitive motions, prone to noise.  
  - Sensor variability highlights sensitivity and outliers.  

![image](https://github.com/user-attachments/assets/23691dc7-c286-43fe-9d74-7b50dc4b65db)


### Violin Plot Insights:  
- Flex sensors show variability due to external stimuli.  
- Accelerometer data is centered around zero during static conditions.  
- Gyroscope data shows minimal variation, reflecting stability in collection.  

![image](https://github.com/user-attachments/assets/83e03aea-1549-4dab-b464-88b80945a1ee)


### Model Training:  
- **Split**: 80% training, 20% testing.  
- **Hyperparameter Tuning**: GridSearchCV (3-fold cross-validation).  
- **Accuracy**: 97% on the test set.  

## Results  

| Metric       | Value  |  
|--------------|--------|  
| **Accuracy** | 97%    |  
| **Precision**| 98%    |  
| **Recall**   | 97%    |  
| **F1-Score** | 98%    |  

### Classification Report: 

| Gesture       | Precision | Recall | F1-Score | Support |  
|---------------|-----------|--------|----------|---------|  
| Awkward       | 1.00      | 0.96   | 0.98     | 140     |  
| Bathroom      | 1.00      | 1.00   | 1.00     | 149     |  
| Deaf          | 1.00      | 1.00   | 1.00     | 136     |  
| Goodbye       | 0.99      | 1.00   | 1.00     | 129     |  
| Hello         | 0.97      | 0.98   | 0.98     | 170     |  

_The complete report is available in `ModelTraining.ipynb`._  

