---
layout: post
title: Predicting share numbers using online new popularity data
---
## The data
The goal is to use online news popularity data set<sup>6</sup>, where various features of news published by masheable are collected, to build appropriate model and evaluate performance on predicting how often a piece of news is shared. I will apply 1 linear regression model and 1 non-linear regression model to the data set.    

## Initial data exploration
The entire content can be found [here.](https://github.com/yz201906/SST558_project2)

### Data parsing and inspection
* After reading in the data, I first examined if there are NAs, which there aren't.  
* Then I looked at the structure of the data, and it seems that channel categories should be factors and so I converted those variables into factors.  

### Partitioning data
* For the initial exploration, I focus on data from Monday. As such I extracted the Monday portion from the complete date.  
* It is then partitioned into training and testing data by the ratio of 80% and 20%.  

### Visualization
* From the 5-number summary statistics, first density and box plots we can see that shares number extremely skewed.  
My first reaction is to see if those data points are true data entry errors. Upon looking at the actual data, I do not believe they are.  
Thus, for visualization purpose, I log transformed the shares variable.  
* Due to lack of general knowledge about the variables for online news, it would be hard for me to look at each individual predictors. So I looked things that I feel could have the most impact on popularity, which is the type of the channel.  
By plotting log transformed shares against channel types. From the boxplots we can see that there is no statistically significant correlations.  
* Next I plotted a correlation matrix between all variables. We can see that there is no direct correlation between shares and any predictor.  

## Linear regression model
Due to the number of predictors of this data set being numerous, it is necessary to automate the predictor selection process.  
* I utilized the `oslrr` package and used the step-wise forward+backward selection based on AIC values.  
* In the end, 11 predictors are chosen. Training AIC and test RMSE are saved and compared with other models later.  

## Non-linear regression model
To see which non-linear regression models perform better, I ran all 3 common ones and saved training AICs and test RMSEs.  
Model training on large data sets are computationally expensive, so I want to determine the best method before proceeding to apply the method to the entire data set for all seven days.  

## The comparison
For the purpose of this project, I will just pick random forests model in addition to the linear regression model since it performed the best.  

## Automation
I them used `rmarkdown::render()` function together with `map()` function to automate the application of the two models to all 7 days of data.  

## Conclusion
From the output we can see that none of the models are performing particularly well, where RMSEs are very large. When looking at the predictions on test data and compare with the actual share numbers in test data, we can see that the predictions are not very accurate.  This might be indicative of further tuning is neccessary.  

## References
**1.** The data set used can be found [here](https://archive.ics.uci.edu/ml/datasets/Online+News+Popularity)
