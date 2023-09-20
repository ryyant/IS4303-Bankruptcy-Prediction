# IS4303 Bankruptcy Prediction with Machine Learning


## Problem Statement
Bankruptcy has been a huge problem in the financial world that has consequently rocked markets and resulted in major financial crises. As such, we hope to be able to leverage on various strategies for inventors to understand the risk level of investments and whether a certain company is financially stable based on past trends. Picking out financially stable companies serves beneficial in providing investment insights and managing bankruptcy risk. This ensures an efficient allocation of resources and identification of sector wide problems. The model will also help us identify the more important features used in consideration for such risk.

## Motivation & Insights
Historically, we have seen cases like Lehman Brothers Holdings Inc. Lehman was doing well with stock shares trading at US$86/share in February 2007, a market capitalization of US$60 billion and a record high net income of US$4 billion. This did not spare the 164-year-old firm from the largest bankruptcy in history, kicking off a global financial crisis. 14 years later, we saw FTX, one of the biggest crypto firms, filing for chapter 11 overnight with SBF losing 94% of its net worth. Evidently, no company is safe from bankruptcy risk. To ensure that substantial investments from firms do not get vaporised and employees do not lose their source of livelihood, an ML model that can predict organisations at risk of bankruptcy can help investors, lenders and institutions make more informed financial decisions, potentially saving billions of dollars. This is non-trivial given the consequences of bankruptcy in the markets that even reputable institutional investors could not predict. Temasek was the 3rd largest investor at $275 million in FTX among the list of high-profile investors like Sequoia Capital and Softbank.
Hence, ML can be leveraged to help investors mitigate risk and make more informed decisions regarding their investments.

# Models
## Regression
- Simple logistic, balanced logistic, undersampling logistic (near miss, random undersampling, tomeklinks, editednearestneighbours, condensednearestneighbours, neighborhoodcleaningrule)
## Tree-Based
- Bagging, adaboost, gradientboost, XGBoost

## Evaluation Metrics
In our bankruptcy prediction case, we likely prefer to label too many companies as potentially bankrupt than too few. In other words, we steer towards high recall. By more heavily penalising false negatives, we train the algorithm to label more cases as positive (at the risk of increasing false positives).
In our case, the recall metric is essential, as the financial losses our companies may encounter from investing in potentially bankrupt companies are many times higher than getting more revenue from investing in financially stable companies. However, the f1-score, which also takes into account both precision and recall, will also be factored in during our evaluation. Despite us prioritising recall, it would be useful to have our model adhere to a certain level of correctness when labelling companies.

## Results
Based on the recall metric, the Undersampling Logistic Regression model (our final baseline model) performed the best, achieving the highest recall score of 0.97. Given our goal of picking out financially stable companies, the model will be able to correctly identify companies that will go bankrupt given the set of financial indicators. Thus, companies that are flagged out from our model should not be selected in their investment portfolio given the high probability of fund write off.
However, the f1-score is also important in order to ensure a certain level of precision. From the results, the Bagging model has a relatively high recall score of 0.92, which is only slightly lesser than 0.97. However, the Bagging model has a much higher f1-score of 0.32 as compared to 0.22, hence, the final model we will be selecting is Bagging, which is more all-rounded.
We did not factor a high recall score for non-bankrupt (0) companies in the final selection of the model used as we prioritised the ability to identify true positive predictions of bankrupt companies compared to true positive predictions of non-bankrupt companies. It is more detrimental to misclassify bankrupt companies as non bankrupt companies instead. In a counter example, a model initially classified 10 companies as non-bankrupt. It is more costly that it misclassified 2 companies in that 10, that were actually supposed to go bankrupt in reality.

## Conclusion
In summary, while bankruptcy prediction can be a valuable tool, it can also be challenging due to highly skewed datasets that are reflective of real-world situations. However, with the use of machine learning, we are able to extract meaningful data analysis and predictions. Among the various evaluation metrics, we found that prioritising recall would be the most effective approach for our model's use case. This can enable investors to gain better insights for investment decisions and improve risk management. Despite the limitations we faced, we have plans for future work that may help us further enhance our model.
