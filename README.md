# Data_Wrangle Project by Udacity Data Analyst Nano Degree (WeRateDogs Tweets)
## Warning: This is a passed project, copy this project may result in plagerism and program cancellation from Udacity.
## Set Up
- import pandas as pd

- import numpy as np

- import requests

- import tweepy (This is the Twitter API, you need to register twitter developer account to be able to use it)

- import json

- import matplotlib.pyplot as plt

- %matplotlib inline

## Files Explained 
1. **twitter-archive-enhanced.csv**: This is a given csv file in the project, it mainly includes general information about a tweet, include tweet_id,source_link,tweet content and rating etc.. 
2. **image-predictions.tsv**: This is a given tsv file in the project, it mainly include the dog image of the tweet and the prediction of the dog type using deep learning technique.
3. **tweet_json.txt**: This file is created through twitter API tweepy, I basically use the tweet_id in twitter-archive-enhanced file and pull all the tweet with those id and store in json format. 

## Wrangle Summary 
Since this is a data wrangling project, the notebook will mainly about data wrangling with minor focus on actual analysis. 

**In the notebook I identified 8 Quality Issues and 2 Tidiness Issues.**

### Quality Issues
- tweet_id from all three three tables should be store as str instead of int  
- In the image table, p1,p2,p3, the first letter of each dog name happens in either capital letter or lower case letter, need to keep consistent.  
- retweet and reply should't be included in the archive table while calculate ratings.  
- Timestamps should be a time series instead of pandas series 
- I have notice in rating_numerator and rating denominator, they are not capturing the whole value of rating when there is a decimal.  
- expanded_url in archive table have missing values  
- There are some name in archive dataset has name 'a', and this is not a name. 
- There are 163 record in df_tweet table show favorite count is 0, this is impossible for a tweet with that many retweet. 

### Tidiness Issues 
- In archive table, each dog stage has a new column. 
- df_tweet table and image table should belong in archive table because it's attributes about tweet. 

**Detailed Wrangle Process for each issue identified above is in the notebook.**

## Analysis Summary
1. The above code, I tested how likely that the algorithm actually think it's very likely of a dog breed and how it actually turns out. The result actually surprises me. In the second and third prediction, there are 0 prediction that exceeds the confident level of 50%, and there both have over 70% level indicate it's the actual dog breed. It seems this neural netowrk algorithm still not so mature, it definitely needs more image to improve its confident level.

2. From the graph above between retweet_count and favorite_count, we're able to see there is a linear relationship between retweet_count and favorite_count. Thus, it confirms my theory in the access section about some tweets have 0 favorite_counts while having a lot of retweet_count is not normal.

3. In this analysis, I compute all the different rating regards to different dog stage, surprisingly, there is no rating showing for dog stage pupper.. And according to all the visulization, it seems most of the score stay between 1 to 1.3, it gets to think that people only like to post cute dog on twitter, most score are above the max score 10, it rarely happen when the score is below 10, it's a popular culture in WERATEDOG.
