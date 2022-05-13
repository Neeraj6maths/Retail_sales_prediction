# Rented bikes demand prediction (Regression)


## Objective
Rossmann operates over 3,000 drug stores in 7 European countries. Currently, Rossmann store managers are tasked with predicting their daily sales for up to six weeks in advance. Store sales are influenced by many factors, including promotions, competition, school and state holidays, seasonality, and locality. With thousands of individual managers predicting sales based on their unique circumstances, the accuracy of results can be quite varied.

 The objective is to forecast the "Sales" for each store on the basis of given input features.
## Dataset used

Two datasets are used:

### (1) Rossmann Stores Data.csv 
 The dataset contains historical data including Sales of each Rossmann store across Europe.

```
- Store : a unique Id for each store
- DayOfWeek : Day of week (1-7)
- Date :  Date    
- Sales : the turnover for any given day (DEPENDENT VARIABLE)         
- Customers : the number of customers on a given day  
- Open : an indicator for whether the store was open: 0 = closed, 1 = open         
- Promo : indicates whether a store is running a promo on that day       
- StateHoliday : indicates a state holiday.a = public holiday, b = Easter holiday, c = Christmas, 0 = None
- SchoolHoliday : indicates if the (Store, Date) was affected by the closure of public schools

```

- Total number of rows in data : 1017209
- Total number of columns : 9


### (2) Store.csv

The dataset conatains general information of each store.

```
- Store :   a unique Id for each store                 
- StoreType :                  differentiates between 4 different store models: a, b, c, d 
- Assortment :    describes an assortment level: a = basic, b = extra, c = extended              
- CompetitionDistance :  distance in meters to the nearest competitor store    
- CompetitionOpenSinceMonth :  gives the approximate  month of the time the nearest competitor was opened
- CompetitionOpenSinceYear :  gives the approximate year of the time the nearest competitor was opened            
- Promo2 :   Promo2 is a continuing and consecutive promotion for some stores: 0 = store is not participating, 1 = store is participating                   
- Promo2SinceWeek :  describes the calendar week when the store started participating in Promo2         
- Promo2SinceYear :      describes the year when the store started participating in Promo2      
- PromoInterval :   describes the consecutive intervals Promo2 is started, naming the months the promotion is started anew. E.g. "Feb,May,Aug,Nov" means each round starts in February, May, August, November of any given year for that store         

```

- Total number of rows in data : 1115
- Total number of columns : 10
## Data Cleaning and Feature Engineering

### (1) Removing Duplicate rows
- No duplicate rows were present in dataset.

### (2) Handling null values
- No null values were present in Rossmann dataset.  
- Null values were present in sales dataset.


### (3) Converting columns to appropriate data types

- Changed datatype of `Date` to date type. 

### (5) Creating new columns
- Created new column `sales per customer` from `date` column.
- Created new column `day of month` from `date` column.

### (6) Feature encoding
- Used One hot encoding to transform categorical feature - `Seasons`.
- Used Label encoding to transform categorical features - `Holiday`, `Functional Day`.

### (7) Handling skewness
- Used square root transformation to reduce skewness of skewed features.

### (8) Standardization of features
- Used `Z-score` for normalization of features.This step scales data into a uniform format that would utilize the data in a better way while performing fitting and applying different algorithms to it. 

## Exploratory Data Analysis

Mainly performed using Matplotlib and Seaborn library and the following graph and plots had been used:
  - Bar Plot.
  - Histogram.
  - Scatter Plot.
  - Pie Chart.
  - Line Plot.
  - Heatmap.
  - Box Plot
             


- 

### Feature Selection

Feature Selection is crucial step before model training as it improves the performance of model and also to reduce multicollinearity in dataset.
Since tree based algorithms are immune to multicollinearity that's why in this project feature selection is performed only before training `Linear', `Lasso`, `Ridge` and `Elastic Net` regression.

```

         Feature selection increases the predictive power of machine learning algorithms by selecting the most important variables 
         and eliminating redundant and irrelevant features. I removed all the multicollinear features from the dataset prior training 
         the model. For removing multicollinearity I used Vif and heatmap.
         
         (a) Correlation Matrix: 
                 (i)   Found that `Dew point temperature` and `temperature` are highly collinear.
                 
                 
          (b) VIF:  Variation Inflation Factor is another way of measuring multicollinearity. A high VIF indicates that the associated independent 
          variable is highly collinear with the other variables in the model.
                 (i) `Dew point temperature`, `Humidity` and `Visibility` found to have high Vif Values.
                 
                 
           Therefore, `Dew point temperature`, `Humidity` and `Visibility` were dropped.
```

### Features for model building

For `Decision Tree Regressor` and `Random Forest` we have not removed highly correlated features. Therefore features while training these algorithms are:

```
 - 
```



## Model Building


Since we have to predict the count of rented bikes, so this is a regression problem. Based on the problem statement which is basically to predict the demand of rented bikes for each hour I decided to develop predictive models using following algorithms and haev compared ther performance.
```
- Decision Tree Regressor
- Random Forest
- Linear Regression
- Lasso
- Ridge
- Elastic Net


Following necessary steps have been employed for better model performance.
                (i)   train test split for model evaluation.
                (ii)  Hyperparameter tuning for best learning parameters that developed a better model. Hyperparameter tuning was done with the help
                      of GridSearchCV.
                      
                      
                  
```


### Evaluation metrics

To evaluate the models I have used MSE( Mean Square error) and Adjusted R2-Score.


## Conclusion

```
                 
           

```

