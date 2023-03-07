# Keywords to search for

- [trend following](https://en.wikipedia.org/wiki/Trend_following>)  
  Это скорее про настоящее, чем про будущее.
- trend following indicator
- trend filter
- time series momentum
- trend momentum
- trend prediction
- trend effect prediction
- short and long prediction
- market regime prediction / detection  
  (regime - это скорее про кризисы и законы, чем про тренды)
- regime shift

# Questions and Answers

- HMM выдает текущие или предыдущие состояния. 
  - Q: Как выдавать будущие?  
    A: Наверное вот так: A^n.
  - Q: Что считать трендом за N шагов?  
    A: Не знаю, но, например, чтобы хотя бы 70% состояний были трендовыми или observations были сильно выше, чем в текущий момент.
  - Q: Вероятно, бизнес от нас потребует не тригериться на слабый(по углу наклона?) тренд. Как заставить hmm предиктить сильные тренды?
- Q: Нужно ли и как учитывать влияние **НАШЕЙ** покупки или продажи на цену?
- Q: Мы имеем дело с momentum trading или c trend following?  
  A: <https://www.quora.com/Is-trend-following-and-momentum-trading-the-same-thing/answer/Scott-Phillips-55>  
     Возможно мы имеем дело с чем-то другим. Я пока не уверен, что trend following - это про будущее, а не про настоящее.
- Q: Чем отличается filter от indicator?
- Q: Мы имеем дело с stock или futures?
- Q: Насколько силен импакт других алготрейдеров, не вызывает ли какой-либо алгоритм лавинообразный эффект? 
- Q: Нужно ли выбрать исторические данные для обучения так, чтобы в них входила только эпоха появления продвинутого алготрейдинга?
- Q: Kalman vs HMM. What is the difference?  
  A: В некоторых частных случаях, kalman и hmm -- это одно и тоже.  
     <https://stats.stackexchange.com/questions/183118/difference-between-hidden-markov-models-and-particle-filter-and-kalman-filter>
- Q: Как быть с трендами внутри трендов?

# Prog Frameworks

- mlfinlab
- prophet  
  by facebook for timeseries
- DeepAR
  framework by Amazon
- 

# Math Frameworks

- Hidden Markov Model
- Kalman Filter (baseline solution or not?)  
  иногда это частный случай hidden markov model
- Partially observable Markov decision process  
  для Reinforcement Learning
- Dynamic Bayesian Network  
  generalization of hidden markov models and kalman filter

# Tips, hacks and ideas

- Y to categorical: [0; 100), [100; 500) and etc
- Приведение ряда к стационарному виду (полностью или частично)
    - fractional differentiation -- trade-off между стационарностью и информативностью
    - различные filters могут убирать сезонность
- Ensembling
- Скомбинировать модель обученную на конкретном ряде с моделью обученной на многих рядах

# Literature

## LSTM + HMM

<https://arxiv.org/pdf/2104.09700.pdf>

### Что сделали

1. Разметка с использованием метода tripple barier(нужна для выбора фактора);
2. Из большого числа различных факторов выбрали наилучшие,
   обучив на них gmm-hmm и используя метки из прошлого пункта <https://arxiv.org/pdf/2104.09700.pdf#table.caption.5>;
3. Обучили на модели из предыдущего пункта xgb-hmm;
4. Прогнали модели из предыдущего пункта на нескольких факторах и выход пустили в lstm;

### Advantages

- многомерность: можно обучить на нескольких временных рядах (факторах) одновременно;
- реакция на изменение не только тренда, но и волатильности;
- в зависимости от препроцессинга может научиться детектить и предиктить не только тренды;
- позволяет отранжировать факторы по степени полезности;

### Disadvantages

- БЕЗ LSTM наблюдается некоторый лаг (после посещения локального максимума, все еще не меняет состояние). Вероятно, причина этому - марковость hmm. Именно поэтому и добавляется LSTM.
- Зависит от выбора факторов, но которых обучается. То бишь, препроцессинг играет большую роль.
- Зависит от выбора likelihood-распределений;

# URLs

- [О hmm и их использовании в трейдинге](https://www.quantstart.com/articles/hidden-markov-models-an-introduction/)
- [Гайды по трейдингу](https://alphaarchitect.com)
  - [Статьи по тегу trend-following](https://alphaarchitect.com/category/architect-academic-insights/trend-following/)
  - Цикл статей:
    - <https://alphaarchitect.com/2020/08/an-introduction-to-digital-signal-processing-for-trend-following/>
    - <https://alphaarchitect.com/2020/12/trend-following-filters-part-1-2/>
    - <https://alphaarchitect.com/2021/01/trend-following-filters-part-2-2/>
    - <https://alphaarchitect.com/2021/04/trend-following-filters-part-3/>
    - <https://alphaarchitect.com/2022/01/trend-following-filters-part-4/>
  - <https://alphaarchitect.com/2020/06/30/time-series-momentum-theory-and-evidence/>
- [trend following indicators](https://finance.yahoo.com/news/complete-guide-trend-following-indicators-100425674.html)
- [timeseries and models for them](https://neptune.ai/blog/select-model-for-time-series-prediction-task)
- [timeseries predictive tasks](https://towardsdatascience.com/6-time-series-predictive-tasks-you-should-know-about-b899fb83b6bf)
- <https://www.investopedia.com/articles/active-trading/111214/quants-what-they-do-and-how-theyve-evolved.asp#toc-what-area-of-statistics-is-most-useful-for-quants>
- <https://www.investopedia.com> 
- [kalman filter](https://bookdown.org/rdpeng/timeseriesbook/general-kalman-filter.html)