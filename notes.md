# Keywords to search for

- trend following  
    Вероятно наиболее подходящий термин
- time series momentum
- trend marker prediction  
    ?
- trend prediction
- trend effect prediction
- short and long prediction
- market regime prediction / detection  
  (regime - это скорее про кризисы и законы, чем про тренды)

# Questions and Answers

- HMM выдает текущие или предыдущие состояния. 
  - Q: Как выдавать будущие?  
    A: Наверное вот так: A^n.
  - Q: Что считать трендом за N шагов?  
    A: Не знаю, но, например, чтобы хотя бы 70% состояний были трендовыми или observations были сильно выше, чем в текущий момент.
  - Q: Вероятно, бизнес от нас потребует не тригериться на слабый(по углу наклона?) тренд. Как заставить hmm предиктить сильные тренды?
- Q: Нужно ли и как учитывать влияние **НАШЕЙ** покупки или продажи на цену?

# Prog Frameworks

# Math Frameworks

- Hidden Markov Model
- Kalman Filter (baseline solution or not?)
- Partially observable Markov decision process

# Tips, hacks and ideas

- Y to categorical: [0; 100), [100; 500) and etc
- Приведение ряда к стационарному виду (полностью или частично)
- Ensembling


# Literature


# URLs

- [О hmm и их использовании в трейдинге](https://www.quantstart.com/articles/hidden-markov-models-an-introduction/)
- [Гайды по трейдингу](https://alphaarchitect.com)
  - [Статьи по тегу trend-following](https://alphaarchitect.com/category/architect-academic-insights/trend-following/)
  - []()
