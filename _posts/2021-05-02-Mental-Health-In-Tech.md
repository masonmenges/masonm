---
layout: post
title: Mental Health in tech
subtitle: Predicting Willingness to Discuss Mental Health in Tech?
tags: [Data Science, Model Interpretation]
---
## Mental Health in Tech
How comfortable would you be discussing your mental health with your boss? What about your coworkers? Do you think your employer would respond negatively if you requested a day off strictly for your mental well being? While answers to these questions will obviously vary from person to person Chances are at the very least it’s not something you’d do lightly without considering the potential consequences, perhaps more so in the tech field where practices like “crunch” are considered commonplace. 

Now what if, as an employer, you wanted to change these perceptions and cast these conversations in a more positive light, what would you focus on to have the greatest impact? These are the questions I sought to answer while exploring Mental health in the Tech field.

## Data Exploration and Analysis

I began my analysis with a Mental Health in tech survey from OSMI and after organizing the data to a more digestible format. The survey was already organized in a tabular format but each column contained the Full Question asked on the survey making it difficult to work with initially, I noticed several of the questions on the survey dealt specifically with whether or not a person was willing to discuss their mental health in a variety of formats, i.e. with employers, coworkers, in interviews, etc. 

It was here that I decided to see if I could first predict how willing a person was to discuss their mental health in a work environment and more importantly see if I could determine what factors contributed to a survey participant's answers to these questions. I started by categorizing responses to these “willingness” questions into three categories with a value score assigned for each No(0), Maybe(1), and Yes(2). From there I generated a willingness score for each participant with scores ranging between 0 to 16 and then categorized high scores (9 or above) as Likely(2), mid-range scores(5-8) as Situational(1), and low scores(0-4) as Unlikely. I then assigned these to a new column “willingness” to be used as my target classification , I also removed the previous columns used to generate the scores to prevent leakage.



## Model Building

I generated two different models, one using logistic regression from sklearn and the other using XGBoost. I chose to use the accuracy score as my evaluation metric for this model as the frequency for the most frequent class was relatively close to 50%.

After splitting my data into training and test sets on an 80/20 split I established using the frequency of the Most frequent class (Situational) for the training data to compare to my models. I then generated a baseline model primarily using the default values for each type of model. I generated validation scores using cross validation for the training data sets, this resulted in a starting mean validation accuracy score of 69% for logistic regression and a starting mean validation score of 66% for XGBoost. I then used RandomizedSearchCV to tune the hyperparameters of my models resulting in a new validation accuracy score of 70% for logistic regression and 69% for XGBoost. Overall I was actually expecting XGBoost to outperform Logistic regression in this context but I was surprised to see Logistic regression consistently performing better which prompted me to use it to evaluate my test data which resulted in a Test accuracy score of 68%.

## Model Interpretation

To determine which features had the greatest impact I used Permutation Importance from eli5 to generate the permutation importances for each feature and removed features with weights relatively close to 0 and generated the graphs below:

![LogImportances](./assets/img/MHIT/LogImportances.png) 

![XGBImportances](./assets/img/MHIT/XGBImportances.png)

The two features with the greatest impact in both models “obs_poor_response_worklplace”, the participant has observed or experienced a poor reaction to mental health issues in their workplace, and “discussion_neg_consequences_mental”, the participant believes discussing their mental health will have negative consequences in regards to their career,  both intuitively make sense as in essence the model is stating that if you’ve had negative experiences in the workplace related to mental or you believe discussing mental health will negatively affect your position that will have a larger impact in regards to how likely you are to discuss those issues in your workplace.

## Conclusion

Overall I think the model presents some interesting information but due to the fact that I generalized many of the responses presented in the survey some information is lost and it’s difficult to draw any concrete conclusions from the data, in addition while I think the survey does a good job of accounting for outside factors some of the features are asking variations of what is essentially the same question, further refining the Features in regards to their relative importance I think could help in terms of simplifying my model but I think additional research, specifically in regards to work cultures and perspectives from participants and executives could help provided more insightful conclusions.
