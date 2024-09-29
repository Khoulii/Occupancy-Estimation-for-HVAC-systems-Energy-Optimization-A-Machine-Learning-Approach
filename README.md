# Occupancy-Estimation-For-HVAC-systems-Using-Machine-Learning-For-Energy-Optimization

## Overview
This project investigates the opportunity to optimize HVAC (Heating, Ventilation, and Air Conditioning) systems' energy usage and consumption by estimating the number of occupants in a room using machine learning. By leveraging non-intrusive environmental sensors, such as CO2, temperature, light, motion, and sound, we aim to make HVAC systems demand-driven, enhancing energy efficiency and user comfort.

### Importance of Optimization
Optimizing HVAC systems is crucial for several reasons:
- **Cost Savings:** Energy-efficient systems can lead to lower utility bills, reducing operational expenses.
- **Sustainability:** HVAC systems are significant contributors to energy consumption and emissions. Optimization can reduce their negative environmental impact.
- **Improved Comfort:** Optimized systems maintain consistent temperature and humidity levels.
- **Extended Equipment Lifespan:** Properly optimized systems reduce the need for costly repairs and premature replacements.

## Dataset

### Source and Collection Method
The dataset was collected using IoT devices (sensors) during an experiment for occupancy estimation introduced in the paper "Machine Learning-based Occupancy Estimation Using Multivariate Sensor Nodes" (Singh et al., 2018). The experiment was conducted in a controlled room (6m x 4.6m) with 7 sensor nodes and one edge node deployed in a star configuration. Data was collected over 4 days, capturing varying occupancy levels (0-3 people) without any HVAC systems in operation.

### Attributes and Size
The dataset contains 10,129 instances and 18 features, including:
- **Date and Time:** Timestamp of the data.
- **Temperature (S1_Temp, S2_Temp, S3_Temp, S4_Temp):** Continuous values in degrees Celsius.
- **Light (S1_Light, S2_Light, S3_Light, S4_Light):** Integer values representing Lux.
- **Sound (S1_Sound, S2_Sound, S3_Sound, S4_Sound):** Continuous values (volts).
- **CO2 (S5_CO2):** Integer values (PPM).
- **CO2 Slope (S5_CO2_Slope):** Continuous slope values.
- **PIR (S6_PIR, S7_PIR):** Binary motion detection values.
- **Room Occupancy Count:** Integer values representing the actual number of occupants.

### Domain
This dataset falls within the domain of energy engineering, specifically focusing on HVAC systems and the application of machine learning for occupancy estimation.

## Learning Problem
The learning problem involves non-binary classification to predict the number of occupants in a room using data from a wireless sensor network. 

### Key Aspects
- **Task:** Non-binary classification for occupancy estimation.
- **Features:** Data derived from various sensors.
- **Target Variable:** "Room_Occupancy_Count."
- **Learning Models:** Random Forest, Support Vector Machine (SVM), Gradient Boosting, XGBoost.
- **Evaluation Metrics:** Accuracy, F1 score, confusion matrix.

## Methodology

### Data Preparation
1. **Exploratory Data Analysis (EDA)**
   - Checked for null values.
   - Converted Date and Time into a single DateTime column.
   - Visualized feature distributions and Room_Occupancy_Count.
   - Applied Synthetic Minority Over-Sampling Technique (SMOTE) for class imbalance.
   - Used Minimax Normalization.

2. **Model Development**
   - Created a dummy classifier for baseline performance.
   - Employed Grid Search and Cross Validation for hyperparameter tuning.

## Evaluation Metrics
Performance of models (Random Forest, SVM, Gradient Boosting, XGBoost) was evaluated based on:
- Accuracy
- F1 Score
- Confusion Matrices

## Reliability of Results
<p align="center">
  <img src="https://github.com/user-attachments/assets/07e19977-d061-4d13-b102-c1b250ec5a9b" width="400">
</p>

### F1 Scores and Model Training

All four models demonstrated high F1 scores on both training and testing sets. The high F1 scores during training, close to or at 1.0, suggest that these models have effectively captured the underlying patterns in the training data. This indicates that they successfully achieved a balance between precision and recall, which is crucial for classification tasks where both false positives and false negatives carry significant costs. 

The training F1 scores indicate effective learning, with no signs of underfitting. Underfitting would be evident if the training F1 scores were significantly lower, suggesting the models failed to capture the necessary patterns in the data. In this case, however, the high training F1 scores imply that the models can represent the training data well.

### Generalization to Unseen Data

The testing F1 scores, while slightly lower than their training counterparts, still remained high. This discrepancy suggests good generalization capabilities. The models demonstrate that they can apply what they learned from the training data to unseen data without significant loss in performance. The high testing F1 scores are indicative of reliable results, as they suggest that the models have not merely memorized the training data—a sign of overfitting—but rather learned the relationships and patterns present within it.

### Bias-Variance Trade-off

Considering the bias-variance trade-off, the results suggest that the models have successfully balanced bias and variance. Models with high bias may underfit the data, while those with high variance may overfit. The combination of high training F1 scores and slightly lower testing F1 scores indicates that the models have maintained a healthy balance, avoiding both extremes.

### Conclusion on Reliability

In conclusion, the reliability of the results is reinforced by the models’ generalization abilities, as shown by the high testing scores. This suggests that the models are well-trained, adequately capturing the relationships in the data while remaining balanced in their predictions.


## Analysis of Results and Algorithm Effectiveness

An in-depth analysis of the models' performance measures reveals several key insights into their effectiveness. The consistently high F1 scores across both training and testing datasets indicate that the models effectively learned the underlying patterns in the training data. 

### Generalization and Model Evaluation

The slight reduction in performance on the testing set suggests good generalization. A balanced model is evidenced by the minor drop in F1 scores from training to testing, reinforcing that the models avoid overfitting. The fact that the models can maintain high accuracy when applied to unseen data further illustrates their reliability.

### Confusion Matrices

The confusion matrices provide a detailed view of the models' predictive accuracy across different classes:

- **Random Forest**: The confusion matrix for Random Forest reveals strong predictive performance, with most values concentrated along the diagonal, indicating correct predictions. However, there are slight off-diagonal values, particularly in classes 3 and 4, suggesting a small number of misclassifications in these categories.
<p align="center">
  <img src="https://github.com/user-attachments/assets/93b13472-d9b0-47bf-9158-109d07f55972" width="400">
</p>

- **Support Vector Machine (SVM)**: The SVM confusion matrix also shows high diagonal values, reflecting accurate predictions. Nevertheless, there are a few misclassifications, especially when predicting instances of Class 4, which could indicate that the SVM struggles with more complex boundaries in this class.
<p align="center">
  <img src="https://github.com/user-attachments/assets/939170ef-12bb-4e47-9622-455990707742" width="400">
</p>

- **Gradient Boosting**: Similar to the previous models, the confusion matrix for Gradient Boosting indicates a high level of accuracy, with most values on the diagonal. However, there are instances of misclassifications in classes 3 and 4, similar to Random Forest, suggesting that these classes may be more challenging to predict accurately.
<p align="center">
  <img src="https://github.com/user-attachments/assets/b80afed1-590e-4235-bbb9-289bbe544317" width="400">
</p>

- **XGBoost**: The confusion matrix for XGBoost indicates a high level of accuracy, with most values on the diagonal as well. However, there are instances of misclassifications in classes 3 and 2 suggesting that these classes may be more challenging to predict accurately.
<p align="center">
  <img src="https://github.com/user-attachments/assets/51b6c1ba-c080-4fcc-850b-c38173f9c354" width="400">
</p>

### Training Times

The training times for each model vary significantly:
- **Random Forest**: 9 minutes
- **SVM**: 3 minutes
- **Gradient Boosting**: 34 minutes
- **XGBoost**: 2 minutes
<p align="center">
  <img src="https://github.com/user-attachments/assets/a78d574c-c469-4722-9028-bdbf42eb54a4" width="400">
</p>

This variance in training times indicates that Gradient Boosting requires the most computational resources, which may limit its practicality for real-time applications or on resource-constrained devices. In contrast, XGBoost emerged as the most efficient model in terms of training time, making it an attractive option for scenarios where speed is essential.

### Results
- **Dummy Classifier:** Accuracy: 0.8124, F1 score: 0.224.
- **Model Performance:** All models showed high predictive power that exceeded 0.99, especially after applying SMOTE and hyperparameter tuning.

## Feature Importance
Key features influencing occupancy estimation included light sensors, with less importance assigned to PIR sensors and temporal variables.
<p align="center">
   <img src="https://github.com/user-attachments/assets/e8999931-303a-43b6-8906-8c4e5e0d1884" width="400">
   <img src="https://github.com/user-attachments/assets/3a54663e-d0f6-4171-ba0a-458455ce3769" width="400">
   <img src="https://github.com/user-attachments/assets/ad88830a-366c-4870-9085-bd9612e3bb50" width="400">
</p>

## Strengths and Weaknesses of Algorithms

| Algorithm       | Strengths                                                        | Weaknesses                                         |
|------------------|------------------------------------------------------------------|-----------------------------------------------------|
| Random Forest     | High accuracy, robust to noise, feature importance analysis     | Longer training time, many hyperparameters         |
| SVM               | High accuracy, efficient training time                          | Sensitive to data distribution, requires tuning    |
| Gradient Boosting | Strong predictive model, feature importance analysis            | High computation power, longest training time      |
| XGBoost          | Efficient training, L1/L2 regularization                        | Requires careful hyperparameter tuning              |

## Limitations and Future Enhancements
- **Imbalanced Dataset:** Further exploration of oversampling techniques is recommended.
- **Feature Selection:** Consider feature engineering and expert consultation.
- **Dataset Size:** A larger dataset may provide a more robust model.
- **Model Complexity:** Explore simpler models to assess trade-offs between performance and complexity.

## Conclusion
All four models exhibited strong predictive capabilities, with reliable performance metrics indicating good generalization to unseen data. Future work will focus on refining the model, exploring additional datasets, and implementing other techniques.


