# Occupancy-Estimation-For-HVAC-systems-Using-Machine-Learning-For-Energy-Optimization

## Overview
This project investigates the opportunity to optimize HVAC (Heating, Ventilation, and Air Conditioning) systems' energy usage and consumption by estimating the number of occupants in a room using machine learning. By leveraging non-intrusive environmental sensors, such as CO2, temperature, light, motion, and sound, we aim to make HVAC systems demand-driven, enhancing energy efficiency and user comfort.

### Importance of Optimization
Optimizing HVAC systems is crucial for several reasons:
- **Cost Savings:** Energy-efficient systems can lead to lower utility bills, reducing operational expenses (Sankaranarayanan et al., 2022).
- **Sustainability:** HVAC systems are significant contributors to energy consumption and emissions. Optimization can reduce their negative environmental impact (Utilities One, 2023).
- **Improved Comfort:** Optimized systems maintain consistent temperature and humidity levels (Saman Taheri, 2022).
- **Extended Equipment Lifespan:** Properly optimized systems reduce the need for costly repairs and premature replacements (Utilities One, 2023).

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

### Results
- **Dummy Classifier:** Accuracy: 0.8124, F1 score: 0.224.
- **Model Performance:** All models showed high predictive power, especially after applying SMOTE and hyperparameter tuning.

## Feature Importance
Key features influencing occupancy estimation included light sensors, with less importance assigned to PIR sensors and temporal variables.

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
All four models exhibited strong predictive capabilities, with reliable performance metrics indicating good generalization to unseen data. Future work will focus on refining the model, exploring additional datasets, and implementing dimensionality reduction techniques.

## References
- Sankaranarayanan, et al. (2022). [Reference details].
- Utilities One (2023). [Reference details].
- Saman Taheri (2022). [Reference details].
- Singh, et al. (2018). [Reference details].


