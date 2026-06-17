# 📝 Time Series - Machine Temperature

## 🌟 Highlights 
From this project "Time Series - Machine Temperature", the highlights are addressed as:
- Some approaches are demonstrated: Z score/ ARIMA/ Isolation Forest/ XGBoost/ LSTM
- **Z score conclusion**: Z score is found not reliable as threshold changes over time
- **ARIMA conclusion**
  - ARIMA order (1, 1, 2) is determined by ACF/PACF and BIC value
  - ARIMA has a fixed threshold as 2.91
  - Residual based anomaly detection is chosen
  - ARIMA forecasting on test period follows too well on actual data. As a result, the residual remains small at anomaly timestamp, making it not flagged
- **Isolation Forest conclusion**
  - Split data into 60/20/20 for training/validation/test
  - Fine tune model parameters with training and validation set to prevent data leakage
  - Chosen parameters of isolation forest: contamination=0.12 and n_estimators=100 based on f1 score of positive and negative
  - Trained model with training and validation set can achieve f1 score of 0.9 in test set.
  - Consistency condition check is added to prevent false alarm by detecting continuous anomalies: Improve to f1 score of 0.92 for test set  
    Note: Improve to f1 score of 0.59 from 0.54 for whole data set
- **XGBoost classification**
  - Key technique: permutation importance analysis, parameter effect study, consisitency effect analysis, and threshold effect analysis
  - Using permutation importance analysis indicates useful features for training. PR score increases from 0.28 to 0.51 for validation set
  - PR score of 0.51 is mainly caused by data problem instead of overfitting
  - Trained model (with training and validation set) can have 0.74 PR score at test set
  - 0.51 precision for positive can be improved to 0.54 via consistency check and 0.65 via modified threshold (0.7)
  - 0.67 f1 score for positive can be improved to 0.7 via consistency check and 0.78 via modified threshold (0.7)
- **LSTM conclusion**
  - Chosen normal period: Before the 1st anomaly window
    - LSTM trained with chosen normal period (before the 1st anomaly window) flags too many normal points (high false positive)
      - precision = 0.2
      - recall = 0.5
      - f1 score = 0.29
  - Chosen normal period: Between 2nd and 3rd anomaly window
    - LSTM trained with future baseline indeed can flag anomaly with fewer false positive
      - precision = 0.64
      - recall = 0.74
      - f1 score = 0.68

## ℹ️ Project Introduction 
**What is time series dataset**  
Time series data is data collected sequentially over time (e.g., every minute, hour, or day).  
A key characteristic is temporal dependency: the value at time t is often related to values at earlier times (t-1, t-2, …).  
Due to this specific characteristic, random split of data for analysis is not suitable and will pose a negative effect to the coming outcome.   

**Machine temperature time series data**  
In the manufacturing company, machine generates revenue by producing products.      
However, unexpected machine issue can result in production stop, defective products, and huge recovery cost.    
To balance production efficiency and machine maintenence, companyies rely on machine condition monitor as an important defense.

Among many machine monitor signals, machine operating temperature is one of the most critical indicators of meachine health.  
In this project, a time series dataset records machine operating temperature at different moment.  
By analyzing the relationship between machine temperature and time with time series analysis, many insights can be unveiled for necessary arrangment and action.   

## 🎯 Mission & Goal
As a data scentist working in manufacturing company, my main job is to monitor machine condition and flag any potential abnormality early.  

## 🏭 Build Flow
- Import libraries
- Data cleaning & EDA
- Anomaly detection
  - Z score method and improvement
  - ARIMA forecasting and residual based anomaly detection
  - Isolation forest
  - XGBoost classification