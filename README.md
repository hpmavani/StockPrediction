# Stock Price Trend Classification with Random Forest

## Overview 
Many individuals aim to invest their money in stocks and take advantage of the seemingly quick, but also risky way of making money. The movement of stock prices are impacted by so many factors such as crowd sentiment, world news, macroeconomic movement, and the intrinsic value of a company’s assets. Stock analysis is divided into two main categories: fundamental and technical analysis. Fundamental analysis focuses on the broader picture; it places an emphasis on a company’s financial records and market capitalization, while technical analysis focuses on creating an almost scientific method of stock prediction that’s based on patterns, trends, and momentum of a stock’s price. Keeping track of all the indicators and signals dictated in the technical analysis of a stock can be complex and time-consuming to do by hand, which is why machine learning techniques can be used to aid this process. Techniques such as Random Forest can essentially capture all these indicators and signals as features and classify the stock price as going up or down. This kind of classification offers investors a buy or sell signal from the technical perspective of stock prediction, which they can verify with real-world sentiments to help make decisions about their investments. 

## Dataset
The dataset used was a Kaggle Dataset with data on open, high, low, close, volume, and adjusted close prices for many stocks. The AAPL dataset was used for this project: www.kaggle.com/datasets/jacksoncrow/stock-market-dataset.
## Methodology
In this exploration of the applications of machine learning, I will focus on classifying the direction (up or down) of stocks, focusing on the stock price of Apple (AAPL). AAPL is known for its stability in the markets, which makes it a beneficial choice in this study in terms of reducing noise. The two classes are uptrend determined by 1 and downtrend determined by 0. These response variables are calculated by using a 5-day lag beteween close-prices: 
Price_Difference = Price(i) - Price(i - 5) where i is the day in consideration. If Price_Difference is positive, this is counted as an uptrend; if negative, this is marked as a downtrend. Essentially, the model aims to see the general trend of a price over the next 5 days. This decision was made to reduce the noise that occurs when considering the price trend after just 1 day and smooth out the prices so the algorithm could perform better. 

The features in consideration are several different indicators such as RSI, MACD, Williams %R, ADX, and Bollinger Bands. The main algorithm used was Random Forest, which is one of the industry standards for classification in terms of accuracy and prevention of overfitting. This project makes use of many different data science skills such as wrangling and pre-processing, feature engineering, data exploration through plots and correlation matrices, and model analysis using metrics such as accuracy, precision, specificity, sensitivity, and F1 score.  

## Results
One of the evaluation methods used is the Out-Of-Bag Error (OOB Error), which allows Random Forests to perform its own validation while training the model. Approximately, each resampled dataset will contain 67% of the original data, so about 33% of the original dataset hasn’t been seen by each tree. This allows for that 33% of “out-of-bag” datapoints to be used as a validation set for each tree. The OOB error represents how many of the out-of-bag points were misclassified. This is important because it opens the door for cross-validation of tuning parameters based on the OOB Error. Below is the OOB error result from training the Random Forest model. The calculated OOB-Error is 15.28% indicating an 85% accuracy. 

![image](https://github.com/user-attachments/assets/f6ca01da-e4d1-46bf-8848-ddd7411f62e9)

Another validation set was used with more unseen data to offer more confidence in the model. The 'Positive Class' is the downtrend class (0). The results of the accuracy, sensitivity, specificity, precision (Positive Predictive Value), and F1 score (balanced accuracy) are also shown as well as the related confusion matrix. Comparing the accuracy to the base-line no-information rate, the accuracy with random guessing, there is a significant improvement, from 56.83% (base-line) to 81.93% with the model. The accuracy of the validation set compared to the accuracy determined by the OOB-error has a 3% difference (81.93% to 85%), which most likely means the model isn't overfitting the data. Additionally, the PPV shows that the model is better at classifying uptrends than downtrends. The detection rate is also really low compared to the rest of the metrics, showing that there needs to be improvement in terms of correctly predicting downtrends. 

![image](https://github.com/user-attachments/assets/55b6f494-26e2-4a43-a518-9b3e2caca3cb)

Feature importance showed that Williams %R, RSI, and the ADX & directional movement -- trend strength -- index features were the most important features in terms of contribution to accuracy and decrease of gini index when constructing the random forest model. 

![image](https://github.com/user-attachments/assets/a159e28e-db76-4399-bca0-32b1f5cb320f)






