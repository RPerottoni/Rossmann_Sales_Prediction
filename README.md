![image](img/rossmann.png)

**Disclaimer**: The context, Company, CEO and business questions are ficticial.

The objective of this project is to delivery a sales forecast model for the Rossmann Chief Financial Officer, where it's possible to consult the forecast sales about the nexts 6 weeks for each store. Which this information, the CFO will be cappable to set a specific budget for store renovations.

This project was developed by using a CRISP-DM method,where the goal is do the first round as soon as possible, and at the end of the first development cycle it was possible to produce a prediction model with a MAPE Error index of 9% using the XGBoost algorithm.

# 1 - Business Problems

## 1.1 - Rossmann

Rossmann is one of the largest drug store chains in Europe with around 56,200 employees and more than 4000 stores. In 2019 Rossmann had more than €10 billion turnover in Germany, Poland, Hungary, the Czech Republic, Turkey, Albania, Kosovo and Spain.

The company was founded in 1972 by Dirk Rossmann with its headquarters in Burgwedel, near Hanover, Germany. The product range includes up to 21,700 items and may vary depending on the size of the store and location.

## 1.2 - Business Problems

The CFO of Rossmann needs to renovate the stores and to set up an accurate budget, he has requested a revenue forecast for each store for the next six weeks.

The data science team were resopnsible for the solution development, which is described bellow.

## 1.3 - About the Data
The datasets were from a [Kaggle Competition](https://www.kaggle.com/c/rossmann-store-sales) ![kaggle](https://img.shields.io/badge/Kaggle-20BEFF?style=for-the-badge&logo=Kaggle&logoColor=white)

The datasets were about 1.115 stores, and the descripton about some filds can be checked bellow. 

|Variable | Definition|
|-------- | -------------|
|Assortment| describes an assortment level: a = basic, b = extra, c = extended |
|CompetitionDistance| distance in meters to the nearest competitor store|
|CompetitionOpenSince[month/year]| gives the approximate year and month of the time the nearest competitor was opened |
|Customers | the number of customers on a given day |
|Date| represents the date the drugstore information began to be collected |
|Id | represents a (Store, Date) duple within the test set |
|Is_promo | indicates whether a store is running a promo on that month |
|Open | an indicator for whether the store was open: 0 = closed, 1 = open |
|Promo | indicates whether a store is running a promo on that day |
|Promo2 | is a continuing and consecutive promotion for some stores: 0 = store is not participating, 1 = store is participating |
|Promo2Since[year/week] | describes the year and calendar week when the store started participating in Promo2 |
|PromoInterval | describes the consecutive intervals Promo2 is started, naming the months the promotion is started anew. E.g. "Feb,May,Aug,Nov" means each round starts in February, May, August, November of any given year for that store |
|Sales | the turnover for any given day |
|SchoolHoliday | indicates if the (Store, Date) was affected by the closure of public schools|
|StateHoliday | indicates a state holiday. Normally all stores, with few exceptions, are closed on state holidays. Note that all schools are closed on public holidays and weekends. a = public holiday, b = Easter holiday, c = Christmas, 0 = None|
|Store | a unique Id for each store |
|StoreType | differentiates between 4 different store models: a, b, c, d|<br>


# 2 - Solution Strategy

The solution follows the CRISP-DM (Cross-Industry Standard Process for Data Mining), which is a cyclic method of development. At the end of the first cycle, the team will have a first version end-to-end of this solution, allowing them to achieve good results faster and identify and address potential problems effectively.

<img src="img/crispds_one.png" width=100% height=50%/>

## 2.1 - Business Understanding

In this initial phase, the focus was on understanding the company's business and clarify wich are the project's objectives and requirements.

## 2.2 - Data Extraction

The data science team received a csv file containing the sales made for each store during one year period. And the solution was developed with these datas.

## 2.3 - Data Descriptive

Also were done a data descriptive, focusing on identify and udenderstand if there are some outliers, missing values and data distribution for each feature, individually.
The descriptive analysis can be accessed at the link bellow.

[Descriptive Analysis](notebooks/data_descriptive.html)

## 2.4 - Data Cleaning

As part of data cleaning the missing values were identified and filled following some assumptions that are described on the notebook.

## 2.5 - Feature Engineering

On this step, some features were created aiming to improve the model performance as well as gain some some business experience and insights.

For this task, a technique called Mind Map Hypothesis was used, where new features were created based on hypotheses that were made and later validated.
![image](img/mindmaphypothesis.png)

## 2.6 - Data Filtering

In this phase, we have implemented a filter on our dataset as it doesn't make sense to include data where, for example, the store was closed and no sales were made. Our objective is to predict sales ($$), and such data would be irrelevant.

## 2.7 - Exploratory Data Analysis
This phase has involved exploring the data, identifying patterns, and gaining insights into its characteristics. As part of the exploratory data analysis, were made the analysis below:

- Univariate Analysis for variable response
![image](img/sales.png)

- Univariate Analysis for numerical features
![image](img/univariate.png)

- Univariate Analysis for categorical features
![image](img/univariate.png)

- Bivariate Analysis
The hypothesis made during the feature engineering process were validated on this phase.

![image](img/h1.png)
![image](img/h2.png)
![image](img/h3.png)
![image](img/h4.png)
![image](img/h7.png)
![image](img/h8.png)
![image](img/h9.png)
![image](img/h10.png)
![image](img/h11.png)
![image](img/h12.png)
![image](img/h13.png)


- Multivariate Analysis
![image](img/multivariate.png)

## 2.8 - Data Modeling
In this phase were done data transformations to normalize the scale of features, help make the distribution more summetrical aiming to improve the ML model performance.

Data transformations methods used:
- Robust Scaler
- Min. Max. Scaler
- Hot Encoding
- Label Encoding
- Ordinal Encodign

These transformation were applied on training and validation dataset.

## 2.9 - Machine Learning Algorithms

### 2.9.1 - Feature Selection
This phase started by doing a feture selection using Extra Trees Classifier, aiming to select only the most important features to be used to train the machine learning models.

Besides these features, during the hypothesis validation, some other important features were identified and considered for the application of Machine Learning.

### 2.9.2 - Machine Learning Model training and performance
In this phase, some machine learning model were trained and their performance were calculated by evaluation throguh cross validation technique.

| ML Model                | MAE Cross_Validation    | MAPE Cross_Validation  | RMSE alidation     |
|:------------------------|:------------------------|:-----------------------|--------------------|
| Randon Forest Regressor | 938.85  +/- 230.31      | 0.14 +/- 0.03          | 1358.37 +/- 309.4  |
| Average Model           | 1370.961                | 0.217                  | 1817.747           |
| Lasso                   | 2152.12 +/- 224.22      | 0.34 +/- 0.03          | 2946.12 +/- 389.22 |
| Linear Regression       | 2152.19 +/- 224.17      | 0.34 +/- 0.03          | 2946.14 +/- 389.12 |
| XGBoost Regressor       | 2937.37 +/- 433.65      | 0.35 +/- 0.02          | 3739.77 +/- 529.9  |


Considering not only the ML results but also the resources such as processor, memory and performance, the XGBoost Regressor were selected to be the main algorithm to solve this business problem.
The fine tuning technique was made aiming to find the best parameters for XGB Regressor and one last training were performed using the best parameters and the performance were calculated using the test dataset, to be more accurate and closer to the real performance for the algorithm. The XGBoost Regressor performance, after fine tuning process could be checked bellow.

| ML Model                | MAE Cross_Validation    | MAPE Cross_Validation  | RMSE alidation     |
|:------------------------|:------------------------|:-----------------------|--------------------|
| XGBoost Regressor       | 802.640                 | 0.125                  | 1125.825           |

# 3 - Business Results

According to the business problem which was to predict how much each store will sell over the next 6 weeks, the DataScience Team deployed the machine learning model to production using flask framework and developed a Telegram Bot which can be accessed from computer or even a mobile phone.

The user can simply send a text message to the Telegram bot, specifying the store number. The bot, will then provide a text message response indicating the projected sales for that particular store over the next 6 weeks.

You can check the Telegram BOT working below.

![ezgif com-gif-maker (1)](img/gif.gif)

To access the Telegram bot, you can either use the provided link or scan the QR code below:

[Telegram Bot](https://t.me/rossmannribot)

![image](img/bot.png)

# 5 - Next Steps

As this was the first cycle, there are improvements to be considered in order to achieve the best performance.
- Work on feature engineering, creating new features that could better explain the phenomenon.
- Use others ML models for stores that had a bad performance.
- New business hypothesys validation.
- New Telegram BOT where the user can access more information about the stores, sales, graphs.

## 6 - Technologies ( Tecnologias )

[![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)](https://numpy.org/)
[![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Plotly](https://img.shields.io/badge/Plotly-%233F4F75.svg?style=for-the-badge&logo=plotly&logoColor=white)](https://plotly.com/python/plotly-express/)
[![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![SciPy](https://img.shields.io/badge/SciPy-%230C55A5.svg?style=for-the-badge&logo=scipy&logoColor=%white)](https://scipy.org/)
[![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)](https://git-scm.com/)
[![Flask](https://img.shields.io/badge/flask-%23000.svg?style=for-the-badge&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![Render](https://img.shields.io/badge/-Render-%23430098.svg?style=for-the-badge&logo=Render&logoColor=white)](https://www.render.com/)

# AUTHOR
Ricardo Perottoni

# All Rights Reserved - Comunidade DS 2022
 