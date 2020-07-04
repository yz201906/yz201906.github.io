---
layout: post
title: JSON data and exploration with NHL API
---
## JSON Data  
JSON has become one of the most popular data formats not only for server-client web applications, but also for actual data querries. In the JSON data [**vignette**](https://yz201906.github.io/SST558_project1/), I briefly discussed the data format, available R packages for parsing JSON data, and had given an example of obtaining and parsing of JSON data from NHL cloud API.
## NHL Example
I have done some preliminary data exploration. Although I am not at all familiar with hockey, I will go through the steps I have taken and some conclusions that I had made based on what I see:  
### Connecting to NHL API, obtain data and parse  
URL for `GET()` command is formatted as documented in the API manual for each endpoint. Following `content()` command, `fromJSON()` from `jsonlite` package was used to convert JSON data into more human readable format.  
### List of all NHL franchises  
I first listed all 38 franchises. For people who are not familiar with NHL, this might be a good start as team names are listed.  
### New York Rangers and Boston Ruins  
I randomly picked two teams-New York Rangers and Boston Ruins- to look at what proportions of games they played were wins. By looking at the season totals data, it looks like there are two types of games, so I listed two separate summary tables for their win ratios.  
### Penalty time and win ratios  
I had a question about whether the penalty time and performance is correlated. So I plotted penalty times against win ratios for each game type. When plotted with linear method, the smooth line does suggest that there is a positive correlation. Howeverm the distrubution of data points looks odd. So I removed `method=lm` form `geom_smooth()` and we can see the correlation better. I am seeing match win ratio is positively correlated with penalty time to a certain point before the slope becomes close to 0. My guess is that these penalty time is a result of stratigic penalty, which might contributed to wins.  
### 'Modern teams' vs. 'pre-modern teams'  
I Googled about NHL history and had learnt that 1992 and later is called modern era. So I wanted to see if the teams joint during the modern era have better or worse performance than the teams joint before. The bar charts, again separated by game types, illustrates the relative number of teams that participated in each game type that has an win ratio above 0.3 (I artificially set this value). It seems that overall modern teams do better in this regard.  
### Road-win-loss  
Not knowing too much about specifics of the terminologies, I wanted to examine if road win-loss ratio is representative of teams total win ratio. So I artificially categorized all teams into 4 tiers based on total win ratios (<0.3, >=0.3&<0.4, >=0.4&<0.5, >=0.5) and generated boxplots for tiers. It seems that indeed, the tier 1 teams who has highest total win ratios also have highest road win-loss ratios. 
