# NLP_predict_index

**Goal**:trying to use NLP tech to predict the index.

## literature review

[S&P market intelligence](http://pages.marketintelligence.spglobal.com/rs/565-BDO-100/images/MI-Research-NLPLitSurvey-170725.pdf?mkt_tok=eyJpIjoiWlRoa016WmlZVEZpT1RRMyIsInQiOiJ2bklHRUptZFwvMFlDQ3duK3c3VGRPbklqMEpZM3dJVlhEb29GWng0bnlHRVFMbWVBdUlLV1VUQ2R4dW4xaExIYlRkRkVvbXBNT0tHRmFyRHY5V0R1a3VxZUNybkRzYjd5eXNPVzh0bVFLOEhhTndTTzJOY2JrTm5LY2NIWFlwXC9qIn0%3D) mainly foucus on earning call transcript analysis, which can be a direction for further improvement.

## existing baseline model

[股市情感分析（股吧）](https://github.com/algosenses/Stock_Market_Sentiment_Analysis)先把文本tokenlize，然后用标注好的中文文本训练（with lab postive or nagative），然后用各种模型训练，最后得到sentiment score.使用2018年数据

![image](https://user-images.githubusercontent.com/39251819/74498044-50b4ed80-4f1a-11ea-8c14-6a319d0878e1.png)

simply use LSTM to predict(like AR model)
: surprisingly, result is good! corr = 0.82
![image](https://user-images.githubusercontent.com/39251819/73824900-f212b400-4835-11ea-969e-6a1700ec8d1f.png)

[Sentiment Analysis for Event-Driven Stock Prediction](https://github.com/WayneDW/Sentiment-Analysis-in-Event-Driven-Stock-Price-Movement-Prediction#sentiment-analysis-for-event-driven-stock-prediction): Train a set of Bayesian Convolutional Neural Networks using Stochastic Gradient Langevin Dynamics to obtain more robustness

[lastest news classficaiton](https://github.com/miguelfzafra/Latest-News-Classifier) its code can be modified to scratch news online.

## work in the future...
 1. tune the parameters and modify the baseline models, use larger training set
 3. analyze the earning call scripts, making use of knowledge in behaviour finance.
 2. try some SOTA models, for example, BERT, LSTM
 
 ## relevent kaggle competition
 [predict disaster](https://www.kaggle.com/c/nlp-getting-started/overview)
 keep track of the new kernel and discussion part
