Exercise - Machine Learning and Prediction
================
Ken Benoit
29 October 2020

## Predicting continuous outcomes

This question should be answered using the `Carseats` data set, which is
part of the **ISLR** package. This data contains simulated data set
containing sales of child car seats at 400 different stores.

``` r
data("Carseats", package = "ISLR")
```

1.  Fit a regression model predicting Sales using Advertising and Price
    as predictors. Interpret the coefficients, the \(R^2\), and the
    Residual standard error from the regression (by explaining each in a
    few statements).

2.  Fit a second model by adding Urban as an interactive variable with
    Advertising. Interpret the two new coefficients produced by adding
    this interaction to the Advertising variable that was already
    present from the first question, in a few statements.

3.  Which of these two models is preferable, and why?

## Predicting the stock market\!

You will need to load the core library for the course textbook and any
other libraries you find suitable to answer the question:

``` r
data("Weekly", package = "ISLR")
library("MASS")
library("class")
```

This question should be answered using the `Weekly` data set, which is
part of the **ISLR** package. This data contains 1,089 weekly stock
returns for 21 years, from the beginning of 1990 to the end of 2010.

1.  Perform exploratory data analysis of the `Weekly` data (produce some
    numerical and graphical summaries). Discuss any patterns that
    emerge.

2.  Fit a logistic regression with `Direction` as the response and
    different combinations of lag variables plus `Volume` as predictors.
    Use the period from 1990 to 2008 as your training set and 2009-2010
    as your test set. Produce a summary of results.
    
    Do any of the predictors appear to be statistically significant in
    your training set? If so, which ones?

3.  From your test set, compute the confusion matrix, and calculate
    accuracy, precision, recall and F1.
    
    Explain what the confusion matrix is telling you about the types of
    mistakes made by logistic regression, and what can you learn from
    additional measures of fit like accuracy, precision, recall, and F1.
    
    Hint: To compute a confusion matrix, you can use the **caret**
    package.
    
    ``` r
    set.seed(100)
    outcomes <- c("positive", "negative")
    tab <- table(sample(outcomes, size = 100, replace = TRUE),
                 sample(outcomes, size = 100, replace = TRUE))
    caret::confusionMatrix(tab, mode = "prec_recall")
    ```
    
        ## Confusion Matrix and Statistics
        ## 
        ##           
        ##            negative positive
        ##   negative       27       23
        ##   positive       27       23
        ##                                           
        ##                Accuracy : 0.5             
        ##                  95% CI : (0.3983, 0.6017)
        ##     No Information Rate : 0.54            
        ##     P-Value [Acc > NIR] : 0.8168          
        ##                                           
        ##                   Kappa : 0               
        ##                                           
        ##  Mcnemar's Test P-Value : 0.6714          
        ##                                           
        ##               Precision : 0.5400          
        ##                  Recall : 0.5000          
        ##                      F1 : 0.5192          
        ##              Prevalence : 0.5400          
        ##          Detection Rate : 0.2700          
        ##    Detection Prevalence : 0.5000          
        ##       Balanced Accuracy : 0.5000          
        ##                                           
        ##        'Positive' Class : negative        
        ##
