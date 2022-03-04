<img src="https://github.com/RPerottoni/Rossmann_Sales_Prediction/blob/main/img/rossmann.png" width=100% height=40%/>

# ROSSMANN SALES PREDICTION

The objective of this project is to delivery a sales forecast model for the Rossmann Chief Financial Officer, where it's possible to consult the forecast sales about the nexts 6 weeks for each store. Which this information, the CFO will be cappable to set a specific budget for store renovations. 

This project was developed by using a CRISP-DM method,where the goal is do the first round as soon as possible,  and at the end of the first development cycle it was possible to produce a prediction model with a MAPE Error index of 9% using the XGBoost algorithm.

## About Rossmann

Rossmann is one of the largest drug store chains in Europe with around 56,200 employees and more than 4000 stores. In 2019 Rossmann had more than €10 billion turnover in Germany, Poland, Hungary, the Czech Republic, Turkey, Albania, Kosovo and Spain.

## Business Questions

Rossmann store managers are tasked with predicting their daily sales for up to six weeks in advance. And its demands were passed over to a DataSciente team. 
To understand better the problem and why every manager was asking the same thing, the DataScience Team talked with some managers and they realised that was a CFO demands.
A meeting with the CFO was made, and was possible to indentify the objective of this project, which is to carry out the sales forecast for up to the next six weeks and the result should be accessed by mobile, helping the CFO to set a investment for each store, to restore the building and make some improvements.

## Datas

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

## Solution Strategy

The solution follows the CRISP-DS method (Cross Industry Process - Data Science). Which is a cyclic method of development, and at the end of the first cycle, the team will have a first version end to end of this solution, achieve good result faster, mapping all the possible problems.

<img src="https://github.com/RPerottoni/Rossmann_Sales_Prediction/blob/main/img/crispds_one.png" width=100% height=40%/>


## Business Assumptions

## Results

## Conclusion

## Next Steps
