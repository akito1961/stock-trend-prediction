# Stock Trend Prediction

Stock price prediction becomes popular in crafting trading strategies. People attemped to forecast what will happend in the near future. My approach to this project will utilize traditional machine learning to correctly predict whether the price will going up or not, i.e. I will transform price predition to classification problem.

# Explore Data
This project will use the `GOOGL` daily price data from `yfinance` as the demo in 5-years span. You can swap out for any stocks you want.

![GOOGL Stock Chart](norm_GOOGL.png "Normalised Closing Price over Time (%Change)")

# Approach
- Feature Engineering: Engineering technical indicators for better predicition, e.g. `WMA, ATR14, MACD`
- NaN Handling: Drop any empty values since only few first datapoint do not have any indicators values
- Training: Dividing a `test_set` to be `0.2` of all data points not randomly selected to preserve the lastest data points for predicting the future movements. Then, apply the Support Vector Classification model to the `train_set`
- Evaluation: `f1_score, precision, recall, accuracy` to understand the classification model

# Result
```
Test Dataset Confusion Matrix:
[[  0 114]
 [  0 131]]
Test Dataset Report:
              precision    recall  f1-score   support

           0       0.00      0.00      0.00       114
           1       0.53      1.00      0.70       131

    accuracy                           0.53       245
   macro avg       0.27      0.50      0.35       245
weighted avg       0.29      0.53      0.37       245
```
Given `1` labeled as "going up" and `0` is otherwises, we can see from the result that the model only predicting bullish movement as obvious as the exploration. However, the model cannot captures any bearish movement or sideway.

# Improvement
- Try intra-day data points might capture some small movements if I were to adopt the model for day trading
- Use different ML models to find better movement prediction.
- Apply `backtesting` with the adopt strategy to test and evalute the strategy 