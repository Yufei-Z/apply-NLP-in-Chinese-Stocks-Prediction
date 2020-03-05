# 中文NLP预测股价变化

**Goal**:  trying to use NLP tech to predict the stock. 

## literature review

[S&P market intelligence](http://pages.marketintelligence.spglobal.com/rs/565-BDO-100/images/MI-Research-NLPLitSurvey-170725.pdf?mkt_tok=eyJpIjoiWlRoa016WmlZVEZpT1RRMyIsInQiOiJ2bklHRUptZFwvMFlDQ3duK3c3VGRPbklqMEpZM3dJVlhEb29GWng0bnlHRVFMbWVBdUlLV1VUQ2R4dW4xaExIYlRkRkVvbXBNT0tHRmFyRHY5V0R1a3VxZUNybkRzYjd5eXNPVzh0bVFLOEhhTndTTzJOY2JrTm5LY2NIWFlwXC9qIn0%3D) mainly foucus on earning call transcript analysis, which can be a direction for further improvement.


## Method 1: train our own model
Existing baseline model

[股市情感分析（股吧）](https://github.com/algosenses/Stock_Market_Sentiment_Analysis)先把文本tokenlize，然后用标注好的中文文本训练（with lab postive or nagative），然后用各种模型训练，最后得到sentiment score.使用2018年数据

![image](https://user-images.githubusercontent.com/39251819/74498044-50b4ed80-4f1a-11ea-8c14-6a319d0878e1.png)

>Remark:

 1.Although the orignial author did segmamention in raw dataset, at the tokenization step his model still divide a sentence into chars instead of words.
 2. Although from above picture it fits well, when we foucs on clsoe price change, you can see its prediction power is nearly zero...
 ![image](https://user-images.githubusercontent.com/39251819/75966522-758ef600-5f05-11ea-94bc-1de95708e369.png)
 
 I tried this model and use it to predict the stock '000002.SZ'. Similar as above, results are frustrating😒. Worse still, my correlation is much lower. The reason may be that the training set is too small and not suitable.( the training set is from the forums of index, not of this stock) 
 
 
 

### Reflection: is word segamentation necessary?
In Chinese, a word, instead of a character, is the smallest unit to express meaning. However, in reality using char is a better idea.
![image](https://user-images.githubusercontent.com/39251819/75848313-cb3ba380-5e1c-11ea-9e95-0c66b8916911.png)
There are several reasons why it's unnecessary: 
 1. segamentation in Chinese is much more difficult to implement，and there are different standards for word segamentation. This process will introduce another kind of error. 
 2. we don't know in neutral network' eyes, whether words or characters express the meanings better. With the development of deep learning models，like RNN, LSTM, BERT, models using charaters improved a lot. 
 3. the word matrix is too sparse, meaning high overfitting risk. And there are lot's of OOV, which restricts the model's preformance.
 4. to be continoued
 
## Method 2: transfer learning
use ernie model provided by baidu
two directions now: 
 1. use dataset provided by baidu and may financial dataset.
 2. use my financial dataset only.
## work list...
 
- [x] tokenzie before word2vec
- [x] study the relationship between sentiment score in weekends and the pct_change in next Monday
- [x] analyze the earning call scripts, making use of knowledge in behaviour finance.
 
 
 ## relevent kaggle competition
 [predict disaster](https://www.kaggle.com/c/nlp-getting-started/overview)
 keep track of the new kernel and discussion part
 
 ## **Appendix**
 ### previous studies which may be helpful
simply use LSTM to predict(like AR model)
: surprisingly, result is good! corr = 0.82
![image](https://user-images.githubusercontent.com/39251819/73824900-f212b400-4835-11ea-969e-6a1700ec8d1f.png)

[Sentiment Analysis for Event-Driven Stock Prediction](https://github.com/WayneDW/Sentiment-Analysis-in-Event-Driven-Stock-Price-Movement-Prediction#sentiment-analysis-for-event-driven-stock-prediction): Train a set of Bayesian Convolutional Neural Networks using Stochastic Gradient Langevin Dynamics to obtain more robustness

[lastest news classficaiton](https://github.com/miguelfzafra/Latest-News-Classifier) its code can be modified to scratch news online.
### Reference
Is Word Segmentation Necessary for Deep Learning of Chinese Representations?
author：Yuxian Meng, Xiaoya Li, Xiaofei Sun, Qinghong Han, Arianna Yuan, and Jiwei Li
