# Big Data Analytics in Global Health Statistics

> Note: For a better view of the notebook, please kindly use this link to open it in Colab - https://colab.research.google.com/drive/16VILQObcnaQadDwMT-L0hz0qmOCfPPZA

## Introduction

During the pandemic of COVID-19, the importance of health data science has drawn wide attention around the world. We would love to acquire some insights of the global health situation by investigating the health statistics data (HealthStats) around the world.

HealthStats provides key health, nutrition and population statistics gathered from a variety of international sources. Themes include population dynamics, nutrition, reproductive health, health financing, medical resources and usage, immunization, infectious diseases, HIV/AIDS, DALY, population projections and lending. HealthStats also includes health, nutrition and population statistics by wealth quintiles.

The dataset we use in our project is the global health statistics dataset from World Bank, containing more than 340 indicators across more than 250 countries or regions around the world.

Our ultimate goal for this project is to predict the global life expectancy at birth using multiple models, including linear regression, logistic regression, neural networks, decision tree, and random forest.

In addition to this, we also applied KNN for value imputation, cross-validation for hyperparameter tuning, K-means for clustering in EDA, PCA for preprocessing, and so on.

In the end, we derived a novel model using ARIMA to get the predicted features, and then fit into the trained models to get final prediction for future global life expectancy.

## Data Loading and Preporcessing (Details in the notebook)

## Exploratory Data Analysis (EDA) (Details in the notebook)

## Modeling (Details in the notebook)

## Conclusion

### Regression Models

We have fitted five different linear regression models, i.e., the vanilla, LASSO (L1), Ridge (L2), Elastic Net (L1 + L2), and PCA. From the results shown in the model chapter, we can not find significance differences in the R2 scores and the RMSE values. Therefore, we can say that, using the cross validation, we can find a relatively good fit for all five models. And the influence of scale or regularization is limited for our dataset when using the linear regressions.

### Classification Models

We trained logistic regression, neural network, decision tree and random forest in our analysis above. The logistic regression and the neural network have test accuracy around 0.85, this is not a high score, but still acceptable. The decision tree and random forest have accuracy scores at around 0.95, which is quite impressive. Before the training, we do not forecast the accuracy score of the decision tree to be that high, because the decision tree is very likely to overfit. But it tends out the decision tree is highly reliable and this may be due to the fact that the values of some features are strongly related to life expectancy at birth. We can easily draw a separation line to distinguish the classes of life expectancy at birth.

### Novel ARIMA + Regression Prediction

From the last plot shown in the predicted life expectancy section, we can see that our model can successfully capture the trend and slope with the dataset to derive a reasonal prediction into the future. Therefore, we can say that the time series for the features in the current dataset can be well explained by the ARIMA model, and our ridge linear regression model is robust enough to convert the selected 24 features into the predicted life expectancy.

There should be some improvement space to address the gap between 2015 data and 2016 prediction, and we can try to work further on it when we found more suitable models.

## Discussion

According to the World Health Organization(WHO), “lifespans are getting longer…life expectancy has increased by more than 6 years between 2000 and 2019 – from 66.8 years in 2000 to 73.4 years in 2019,” which align with our analysis[1]. Interestingly, the report states that the healthy life expectancy (HALE), which is determined by “number of years a person is expected to live in good health,[2]” showing a 5.4 year increase, has not kept up with the increase in life expectancy which increased by 6.6 years. As the HALE index differs from life expectancy in mainly mortality and burden of disease, the above inconsistency implies that communicable disease programmes, such as HIV, tuberculosis, and malaria still need attention.

In a more general scenario, influencing factors of life expectancy includes genetics, lifestyle choices, and access to healthcare.

At the same time, a chronic failure to acknowledge the central role of primary health care, and to adequately fund key elements such as the health workforce, both slowed the effectiveness of the response to COVID-19 and triggered disruptions to routine care which threaten to further jeopardize countries’ abilities to reach the 2030 Sustainable Development Goals for health.

Some of the most important factors that can influence life expectancy include:

Genetics: Genetics play a significant role in determining a person's lifespan. People who have a family history of diseases like heart disease and cancer may have a shorter lifespan than those who don't.
Lifestyle choices: A person's lifestyle choices can also have a big impact on their life expectancy. Smoking, excessive alcohol consumption, poor diet, and lack of exercise can all increase the risk of serious health conditions and reduce life expectancy.
Access to healthcare: A person's access to quality healthcare can also have a big impact on their life expectancy. People who live in areas with good healthcare systems and access to medical treatment are more likely to live longer than those who don't have access to such services.
Environmental factors: The environment in which a person lives can also affect their life expectancy. Exposure to pollutants and other harmful substances can increase the risk of certain health conditions and reduce life expectancy.
Socioeconomic factors: Socioeconomic factors like education, income, and social support can also influence life expectancy. People who are better educated and have higher incomes and greater social support tend to live longer than those who don't.
Works Cited:

[1]World Health Organization. (n.d.). Ghe: Life expectancy and healthy life expectancy. World Health Organization. Retrieved December 12, 2022, from https://www.who.int/data/gho/data/themes/mortality-and-global-health-estimates/ghe-life-expectancy-and-healthy-life-expectancy

[2]World Health Organization. (n.d.). Indicator metadata registry details. World Health Organization. Retrieved December 12, 2022, from https://www.who.int/data/gho/indicator-metadata-registry/imr-details/66

## Potential Next Steps

We already fit many models in our analysis, however, there are still many points we can consider in the future.

First, we noticed that there are many missing values in the dataframe, we use both the K nearest neighbors method and filling with the mean value from all the existing feature values. Nevertheless, the disputed data is extremely likely to be biased. We can look up the data on the internet and fill it with the value on the internet.

Second, our data present in a time series format naturally, but we only used the ARIMA model in our analysis. In the future, we can try more time series methods to make predictions about the future trend.

Next, we could use more machine learning models. In the classification problems, we receive a not high score for logistic regression and neural network, we could try more classification models that may give better predictions.

Last but not least, we only focused on the life expectancy at birth in our analysis. There are more than 300 indicators in our data, we could try to fit more models based on other indicators.
