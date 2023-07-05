# CSC8498-Project-and-Dissertation-for-MComp
## Overview
Carbon intensity is a measure of the number of grams of CO2 that are released to produce one kWh of electricity.
The aim of this project was to develop a machine learning model that could make predictions of carbon intensity for the next 24 hours.
Accurately predicting carbon intensity allows for the scheduling of energy loads to times of low carbon intensity which reduces emissions.
## Data Collection
The source of carbon intensity data for this project was carbonintensity.org which has several datasets related to carbon intensity.
For this project the dataset of carbon intensity for every half hour for the UK was used.
To obtain the required data I wrote a batch file which executed the curl commands to get the data from 2018-2022.
## Data Preparation
Once the data was downloaded, I wrote a program to take the 60 json files of carbon intensity data and produce one csv file.
From here I began data exploration to determine what data processing steps would be necessary.
I found the data to be incomplete and to contain many outliers.
To complete the dataset, I used interpolation which was acceptable as only a small amount of the data was interpolated.
To correct outliers, I created a boxplot of the data and any values outside the minimum or maximum was deemed to be an outlier.
To maintain the completeness of the data the outliers were replaced with the average of its neighbouring values.
## LSTM Development
A Long Short-Term Memory (LSTM) model is a type of machine learning model which has the ability to memorise bits of data that are deemed to be useful.
This allows the LSTM to better recognise patterns in time-series data than other models would be able to.
I initially experimented with different training data lengths, model layers and model weights but found these were of negligible impact.
To move past this roadblock I conducted research and found a promising approach was to separate the data by hour.
This change meant that to make a prediction for 5pm the model would be given the previous 20 results at 5pm instead of the results from the previous 20 hours.
I found that this improved results greatly because this approach made the patterns in the data that the model would have to learn much simpler.
From here experimentation with different layers and model weights was conducted until the best model was found which was capable of accurately predicting carbon intensity values.
## ELM Development
A Extreme Learning Machine (ELM) is a machine learning model which contains only one layer.
In this layer the weights for each node are randomly assigned and never updated.
The advantage of this approach is that patterns can be learnt much faster than a typical CNN and training times are much faster than a CNN as well.
This model was chosen because it is a relatively new machine learning concept that has not yet been fully researched.
The academic papers I reviewed showed this model performed exceptionally well for certain machine learning problems.
But I was not able to find any use of an ELM for short-term time-series prediction, so I endeavoured to be the first to attempt it.
The development of the ELM was much simpler compared to the LSTM because the machine learning pipeline had already been developed and tested, so just the model needed to be changed.
With the ELM being a very simple model architecture, I found that there was a limited amount of changed that could be made.
I found that the ELM performed poorly at predicting carbon intensity values and changes to the model made little difference.
## Reflection
In reflection this project developed two machine learning models.
The LSTM was capable of making 24 hour ahead carbon intensity forecasts whilst the ELM was not.
However, exploring a new machine learning concept and implementing it for a new application was a challenging problem to solve.
Developing a functioning ELM proved to be challenging due to the lack of online resources related to ELM implementation.
This allowed me to improve my problem-solving skills and improve my ability to understand and implement complex topics.
