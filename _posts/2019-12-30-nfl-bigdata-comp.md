---
layout: post
title: "NFL Big Data Comp 2 Post"
date: 2019-12-30
---
Happy Holidays!
My goal with the data was to convert as many categorical columns to numeric and binary columns as possible. The reason behind this is to 
not run into curse of dimensionality problems, along with in order to run a XGBoost model all the data must be one hot encoded. One hot 
encoding categorical variables that have more than 10 unique categories can lead to sparsity in my dataset, which can lead to bad models. 
That is why only position and team name are categorical columns with more than 10 columns that I kept, the rest I modified. There are 
originally 49 columns and 25 of them are numeric and after feature engineering I ended up with 110 numeric or binary columns. 

I dropped the columns, GameId, PlayId, NflId, DisplayName, JerseyNumber, PlayerCollegeName, TimeHandoff, TimeSnap, NflIdRusher, Location, 
Team, Stadium, WindDirection due to either irrelevance or the potential to overfit. For example if I have the columns Location, 
DisplayName, VisitorTeamAbb, HomeTeamAbb, and Season, my model which is tree based will be very accurate in terms of the training set but 
it will be heavily overfit. It would have accurate predictions for Ezekiel Elliott rushes during the 2018 season, at the Washington 
Redskins, where he ran for 33 yards on 15 carries. But it will not be accurate when trying to predict each rush in his 2019 game at the 
Washington Redskins where he ran for 111 yards on 23 carries. I want to force my model to only predict based on factors that vary from 
game to game but are not completely different game to game, like offensive formation, defensive formation, amount of defenders in the box 
etc. My top ten features ended up being, X, Y, S, A, Dis, Orientation, Season, DefendersInTheBox, and IsOnTurf, with X being the most 
important, I am satisfied with that outcome. 

The columns that were kept but modified are: PlayerBirthDate, HomeTeamAbbr, VisitorTeamAbbr, Turf, GameWeather, GameClock, StadiumType, 
PlayerHeight, DefensePersonnel, OffensePersonnel, PossessionTeam, FieldPosition, WindSpeed. All but GameWeather was converted into numeric 
or binary, while each GameWeather row was converted into one of 3 categories rainy, snowy or clear. 

When handing NA’s, I did not keep the column with the most NA’s, do in part to irrelevance along with the data itself being very messy. 
There are not just north, south, east and west or even the midpoints between those direction like northeast but there are also rows that 
are ‘South Southwest’ and ‘East Northeast’ which is not a wind direction and I could either leave it and therefor have 15 or so new 
columns due to one hot encoding or drop it due to being messy and irrelevant in terms of predicting rushing yards, I choose to drop it. 

I had a choice to make with how to include if it was windy in the dataframe. I could either use the category of windy used in GameWeather 
or use WindSpeed. I choose wind speed due unknown nature of the definition of windy and because numeric data has more information then 
binary data. That is why in the new GameWeather column that I created there is just snowy, rainy or clear and not a windy category. 

I did not eliminate any columns solely based on number of missing values due to having 509,762 rows in the first place. I felt the gain 
of columns like WindSpeed, Temperature, GameWeather, and StadiumType was worth more than having 423,348 instead of 509,762. 

I was able to optimize the parameters learning_rate, max_depth, subsample, colsample_bytree with 2 or 3 options for each parameter and 
it took 9 hours to run. Adding max_features, min_samples_split and min_samples _leaf was taking over 24 hours to run and at this point 
in learning analytics I don’t know how to have it run faster, I believe it would be run faster in Spark using AWS which we will learn 
in the spring, currently we have just learned Hadoop and MapReduce using AWS which is great for simple functions but not so much for 
running models.  
