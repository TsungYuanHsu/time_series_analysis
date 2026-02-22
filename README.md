# 📝 Time Series - Machine Temperature

## 🌟 Highlights 
From this project "Time Series - Machine Temperature", the highlights are addressed as:
- Some approaches are demonstrated: Z score/ ARIMA/ Isolation Forest
- Z score conclusion: Z score is found not reliable as threshold changes over time
- ARIMA conclusion
  - ARIMA order (1, 1, 2) is determined by ACF/PACF and BIC value
  - ARIMA has a fixed threshold as 2.91
  - Residual based anomaly detection is chosen
  - ARIMA forecasting on test period follows too well on actual data. As a result, the residual remains small at anomaly timestamp, making it not flagged
- Isolation Forest conclusion
  - Approach 1 (train with the whole period): f1 score is 0.58 with 60 mins consistency check. Cons is data leakage (use the whole dataset to choose proper parameters)
  - Approach 2 (train with 70% data and test 30% data and whole data set): f1 score is 0.56 with mins consistency check for whole dataset and 0.73 in test set. Approach 2 is more practical to use since only reference period is used for model training and applies anomaly detection for unknown future with trained model

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