# FinBERT-Stock-News



Link to Dataset : https://www.kaggle.com/datasets/miguelaenlle/massive-stock-news-analysis-db-for-nlpbacktests

The idea is to use the dataset of stock news: headline, links, date, etc. to predict (or test) the prices movements of those stocks (increase or decrease or remain stable) based on sentiment score of the news using FinBert. 
> FinBert is an opensource pre trained Natural Language Processing (NLP) model, that has been specifically trained on Financial data, and outperforms almost all other NLP techniques for financial sentiment analysis.

**Currently:** Sentiment scored on news headlines *not news content* <br>

**RESULTS:** 
`
Result for df ( null values removed )
              precision    recall  f1-score   support

    decrease       0.09      0.23      0.13        31
    increase       0.06      0.19      0.09        26
      stable       0.86      0.60      0.71       355

    accuracy                           0.55       412
   macro avg       0.34      0.34      0.31       412
weighted avg       0.75      0.55      0.63       412
`
##### Looks like its pretty good to predict for stable days i.e. stock price remaing between +/- 0.20%
*Precision, recall and f1 score metrics for 'stable' prediction seems good*
-  Usefull for predicting higher / lower volatility during the trading days  (closing prices)
-  Money can be made by using Option Strategies such as:
-    Iron Condor for less volatility (within -0.20% +0.20% price change range)
-    Straddle for high volatiolity (lower or higher than +/- 0.20% price change)
---

Removing 'stable' days to just look at 'increase' and 'decrease' performance:
`
Result for filtered df ( only for stocks that made over -/+.2% )
              precision    recall  f1-score   support

    decrease       0.58      0.23      0.33        31
    increase       0.56      0.19      0.29        26
      stable       0.00      0.00      0.00         0

    accuracy                           0.21        57
   macro avg       0.38      0.14      0.20        57
weighted avg       0.57      0.21      0.31        57
`
##### Not good enough.


#### **Next:** 
-  [ ] Scrape each stock news *content* with the links in dataset
-  [ ] Use the news body content for sentiments
-  [ ] Compile results of predictions 
