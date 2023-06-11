# Player Valuation Forecasting and Talent Scouting
For this project we tackled two different tasks:
1. Player Valuation Forecasting -> For every couple (player, date) we want to forecast the market valuation.
2. Talent Scouting -> Searching young player (age <= 25) based on similarity with an older (age > 25) player in input

## Dataset
The starting dataset was downloaded from kaggle, you can find it in the directory archive. It represents the database of the football site "transfermarkt". It is made up of 8 .csv tables:
- appearances.csv (1.170.381 rows): all appearances for all players in clubs;
- club_games.csv (123.097 rows): all club games in the dataset
- clubs.csv (412 rows): all clubs in leagues (competitions)
- competitions.csv (43 rows): all competitions in the dataset (a game is played in a competitions;
- game_events.csv (559.854 rows): the events in a game;
- games.csv (61.459 rows): all games in the dataset
- player_valuation.csv (421.565 rows): evolution of market values of players;
- players.csv (21.097 rows): all players in the dataset;

In the plots directory you can find some plots of the dataset and of the results.

### Features Extraction
The goal of this part is to create a single dataset that can be used in subsequent steps for both the tasks. 

Through the tables described in the previous section, a dataset is created in which the key of each row is represented by the columns "player_id", which uniquely represents a player, and "date_v", which represents the date on which the market value of " player_id" is updated. Then for each player there are as many rows as there are update dates (date_v) associated with him.

The features that have been extracted and calculated from the tables represent useful informations as appearances, assists, goals, winning rate and many others. In particular the statistics relate to the year preceding the date of "date_v", that is the date of the valuation.

This part is in pre-processing/features_engineering.ipynb


## Players Valuation Forecasting
To tackle this task we developed some machine learning and deep learning models:
-  Multivariate Linear Regression
-  Multilayer Perceptron (MLP) 
-  Long-Short Term Memory (LSTM)
-  Random Forest
-  Bagging of Decision Trees
-  Gradient Boosting Regressor

You can find the files that we created for this task in the directory valuation_forecasting: 
1. In feature_transformations.ipynb we encode the categorical features and we apply some transformation to the data, such as zscore.
2. dataset_normalized.csv is the ready to run dataset after the feature transformations
3. In train_test.ipynb there is the creation of the pytorch datasets and dataloaders, the classes of the models and the training, validating and testing methods.
4. demo_task1.ipynb is a simple demo where the trained models are loaded, tested and the results are showed.
5. In models you can find the trained models.   

### Results 
![](https://github.com/mguarins/BDC_project/blob/main/plots/tables.png)


