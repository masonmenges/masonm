---
layout: post
title: Anxiety In Gamers
subtitle: Is there a difference in General Anxiety between Gamers with different playstyles?
tags: [Vizualizations, Data Science]
---

## Anxiety in Gamers

Anxiety is a relatable topic for pretty much anyone driven by numerous factors that are ultimately different for each of us while looking for research related to this topic I found a dataset for a global survery performed by the Center for Open Science. In the study researchers gathered data related to Anxiety, Life satisfaction, and Social phobias in gamers by asking survey participants simple screening questions used to generate scores for General Anxiety Disorder, Satisfaction with Life, and Social Phobias Inventory in addition to various questions related to the their playstyles, lifestyles and habits. It should be noted that while these screening questions are informative they are not a substitute for Diagnosis they are simply a measurement of a persons Level of anxiety at the time the questions were asked.

After exploring the data I noticed that the Survey had included a question for participants playstyles in regards to whether or not they focus on Singleplayer games vs Multiplayer games or both So I decided I wanted to know if there was a difference in anxiety scores of gamers who Primarily play Multiplayer games vs Singleplayer games. I chose to use the General Anxiety Disorder (GAD-7) Score as a way to measure this, for context the scores range between 0 and 21, a Score of; 0-4 indicates minimal Anxiety; 5-9 indicates mild anxiety; 10-14 indicates moderate anxiety and a score of 15-21 indicates severe anxiety.

Data was originally gathered by Marian Sauter and Dejan Draschkow.
[Kaggle Dataset](https://www.kaggle.com/divyansh22/online-gaming-anxiety-data) 

## Data Analysis

First and foremost while the Survey was a Global survey I decided to Limit the data I was analyzing to participants in the US being that I live in the US and was most interested in the answer from a regional context that I can relate to. After filtering the dataset to contain only records in the US I further simplified it to contain only the Participants Playstyles and their General Anxiety Disorder scores. I then seperated the Dataset to contain only participants who primarily focus on Singleplayer games and participants who primarily focus on Multiplayer games or both. 

The answers to the Playstyles questions were in a free form format there weren't set responses for each category so I had to filter different playstyles based on the Key phrases for each specifically Singleplayer , Multiplayer, and all. As a result some participants may have been excluded from my analysis. 

> 
I chose to include gamers who focus on both with the the gamers that focus on Multiplayer games as I was most interested in the difference from a Singleplayer perspective but further analysis could be done to analyze the differences between the different categories.

To further vizualise any difference between the two groups I graphed the distribution of GAD scores for both in the graphs below:

![MP_GAD_Scores.png](.../assets/img/OnlineGamingAnxiety/MP_GAD_Scores.png) ![SP_GAD_Scores.png](.../assets/img/OnlineGamingAnxiety/SP_GAD_Scores.png)

As you can see both ended up looking pretty similar as they are both skewed pretty heavily to the left and follow a similar pattern, I then calculated the mean GAD score for both data sets with Multiplayers having a mean GAD score of 5.32 and Singleplayers having a Mean GAD score of 5.66.

I then chose to perform a t-test to determine if their is a statistically significant difference between the mean GAD scores for participants with a Multiplayer playstyle vs. those with a Single player playstyle at a 95% confidence level or in other words:

Null Hypothesis: The mean GAD score for participants with a multiplayer playstyle is not different from participants with a singleplayer playstyle

Alternative Hypothesis = The mean GAD score for participants with a multiplayer playstyle is different from participants with a singleplayer playstyle

## Results

The P-value for this test calculated to ~0.25 which based on a significance level of 0.05 would not allow us to reject the Null hypothesis so we can conclude that there is not a statistically significant difference between the mean General Anxiety Disorder scores for Survey Participants with a Singleplayer playstyle vs. a Multiplayer playstyle.

It should be noted that in this analysis I simplified the "Playstyles" to only Singleplayer and Multiplayer when in actuality the responses to the Playstyle question on the data set were a bit more varied containing information related to playing only with friends or with complete strangers. In addition there was a significantly larger number of Multiplayer Participants than Singleplayer, roughly a ratio of 16:1 in the US, though both had a sufficiently large enough sample size (greater than 40) so while it may have impacted the results a bit I don't think it would be enough to affect my conclsion.

Though there doesn't appear to be any difference between the mean GAD scores for survery participants it would be interesting to see how this compares to the GAD scores for Participants outside of the US, Another question I thought would be interesting to look into with this data set would be if there is any sort of predictive relationship between the Satisfaction with Life scores and the General Anxiety scores.
