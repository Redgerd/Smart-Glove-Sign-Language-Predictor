# ASL-Sensor-Dataglove-Dataset

## Abstract

The **ASL-Sensor-Dataglove-Dataset** contains sensor data captured from a dataglove designed to perform gestures in American Sign Language (ASL). The dataset includes measurements from five flex sensors and three gyroscopes, enabling gesture recognition models for ASL. The data is publicly available for research and educational purposes and can be accessed via the [Figshare repository](https://figshare.com/articles/dataset/ASL-Sensor-Dataglove-Dataset_zip/20031017?file=35776586).

## Dataset Overview

This dataset consists of time-series data collected using a sensor-equipped dataglove. The dataset is intended for research on recognizing ASL gestures. The sensors capture various hand gestures, which are annotated with a corresponding label representing the ASL symbol. The dataset includes:

- **Flex Sensors**: These sensors measure the bend in each of the five fingers.
- **Gyroscope Sensors**: These measure the rotational movement along three axes (X, Y, and Z).
- **Gesture Labels**: Each data point is annotated with a label representing the ASL gesture being performed at the time.

The dataset is organized into multiple CSV files, each corresponding to a different set of gestures. 

## Data Columns

The dataset includes the following columns:

- **flex_1, flex_2, flex_3, flex_4, flex_5**: Flex sensor readings for each finger.
- **GYRx, GYRy, GYRz**: Gyroscope readings (rotation along X, Y, and Z axes).
- **label**: A categorical label for the ASL gesture being performed.

## Dataset Access

The dataset can be downloaded from the following link:

[Download ASL-Sensor-Dataglove-Dataset (ZIP)](https://figshare.com/articles/dataset/ASL-Sensor-Dataglove-Dataset_zip/20031017?file=35776586)

After downloading the ZIP file, it can be extracted to access the individual data files for further analysis.

## Data Preprocessing

Before training machine learning models, the dataset requires preprocessing. Key preprocessing steps include:

1. **Label Encoding**: The `label` column is converted from categorical labels to numeric labels using label encoding.
2. **Feature Selection**: Only the relevant sensor columns (e.g., `flex_1`, `flex_2`, etc.) are selected for training.
3. **Normalization**: Sensor readings are normalized to ensure consistent scale, facilitating model training.

The following Python code snippet shows how to load and preprocess the dataset:

```python
import pandas as pd
from sklearn.preprocessing import LabelEncoder

# Load dataset
def load_csv_files(dataset_directory):
    dataset = pd.read_csv(f'{dataset_directory}/data.csv')  # Adjust file path as needed
    return dataset

# Preprocess dataset
def preprocess_data(dataset):
    # Encode labels as numeric values
    label_encoder = LabelEncoder()
    dataset['encoded_label'] = label_encoder.fit_transform(dataset['label'])
    
    # Select relevant columns
    feature_columns = ["flex_1", "flex_2", "flex_3", "flex_4", "flex_5", "GYRx", "GYRy", "GYRz"]
    X = dataset[feature_columns]
    y = dataset['encoded_label']
    
    return X, y, label_encoder
```

## Visualizations

### Pairwise Plots

Pairwise plots provide a visual understanding of how different features correlate with each other. This can help identify patterns and correlations within the dataset.

![image](https://github.com/user-attachments/assets/6bb2dabe-2aa7-475f-962b-c8c906fd60df)


### Correlation Heatmap

A heatmap of feature correlations helps visualize the relationships between the flex and gyroscope sensor readings.

![image](https://github.com/user-attachments/assets/d82a3806-d68d-45cb-8d60-6e508ed05d9e)


### Feature Importance

Bar plots showing the importance of each feature based on machine learning model performance can reveal which sensor readings contribute the most to gesture recognition.

![image](https://github.com/user-attachments/assets/cd02d5b2-299e-4eb2-a2b1-47ed1d6dbdd8)


## Machine Learning Model

### Model Description

For gesture recognition, we applied a **Random Forest Classifier** to classify the ASL gestures based on the sensor data. The model is trained using the preprocessed features (`flex_1`, `flex_2`, etc.) and the corresponding gesture labels.

### Model Evaluation

The trained model is evaluated using common metrics such as **accuracy** and **confusion matrix**. 

### Model Results

The classifier achieved an accuracy of **X%** in predicting ASL gestures. These results can be improved by experimenting with other machine learning algorithms or tuning hyperparameters.

## Acknowledgments

- The dataset is made publicly available by the original contributors and can be accessed via [Figshare](https://figshare.com/articles/dataset/ASL-Sensor-Dataglove-Dataset_zip/20031017?file=35776586).
- We would like to thank the developers of the ASL Sensor Dataglove for making this valuable dataset available for research purposes.
