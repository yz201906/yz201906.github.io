---
layout: post
title: R shiny app for SEER cancer data
---
## Purpose of this porject
As the final project of the Data Science for Stats course, here I try to piece together the skills and knowledge we have learnt to build a deployeable shiny app that includes some levels of data exploration, modeling and visualization. I am particularly interested in looking at number of months survived after diagnosis as response variable to many other potential predictors.  

## Data chosen project
The data I chose to use for this project comes from NIH. It is the obtained from The Surveillance, Epidemiology, and End Results ([NIH SEER](https://seer.cancer.gov/data/access.html)). The reason for choosing data from SEER is that I am personally interested in things bilogical sciences related, and also the fact that this data base has vast number of data points, as well as comprehensive variables that I can model from. 

Data is obtained by registering at  and requesting access through SEER\*Stat software. An exported matrix is then import to R for further processing. The specific sub data set is the **SEER18**, which contains data for cancer cases from year 2000 through 2017 (year of diagnosis). Although this set does not include data from earlier times such as from year 1975 or 1992 onward like the **SEER 9/13** data set, improvement in modern diagnosis, treatments and post-treatment care could impact the trend of survival. Thus, the **SEER 18** data set can be more appropriate for traditional ML predictions.  

## Data subsetting
Due to the size of the data set (more than 4 million rows of data points), I have selected just 10 years of data (2000-2010) for the purpose of this project. In the shiny app, the data set is further separated into yearly basis for the most part (excluding unsupervised learning part).  
I have opted to further subset the data even more considering performance of the app. 

## The app
* The shiny app allows visualization of some of the individual variables against number of months survived. User can select data year, and one of the variables at a time. 
* The app displays a data table with 50000 rows sampled from each year's data. Download is available for both the 50000-row data or the yearly data.  
* Visualization can be toggled by sex.  
* One of two models: multiple linear regression and bagged tree can be selected for modeling. Modeling parameters are available for bagged tree.  
* For PCA, data is subsetted directly from the full 2000-2010 data (also 50000 random rows selected). 

More details and the app itself can be found [**here**](https://github.com/yz201906/SST558_final_project) at GitHub.
