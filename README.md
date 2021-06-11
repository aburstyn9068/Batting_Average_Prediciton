# Batting_Average_Prediciton
This respository contains a prediction model to calculate the end of season batting averages given a player's stats from the beginning of the season (March and April).

My approach to make the preditcion model was to create a linear regession model using a prior year's early season to post season data comparison. The model was created using Python code in a Jupyter Notebook.

The prediction model uses April 2017 data (there were no games in March 2017, opening day was 4/2/17) and final batting average data from the 2017 season to create a linear regression model. The March/April data from the 2018 season wasl then applied to the model to predict the final batting average for the 2018 season.

The data for this project was obtained from Baseball Savant Statcast Search (https://baseballsavant.mlb.com/statcast_search). Player hitting data was obtained for the 2018 and 2017 seasons.

The first step in the process was to explore the data. Players with less than 30 plate appearances were removed from the set as they can skew the results. Additionally, players with missing stats were eliminated from the data set.

The next step was to check for relationships between the player stats that would be used as input variables for the model. A correlation matrix was plotted and several variables were shown to be highly correlated with one another. Variables that are highly correleated to eachother will cause the model to be less accurate due to the multicollinearity between the variables.
![Correlation Matrix 1](/images/corr_matrix1.png)

A forward sequential feature selector was then used to find the best combination of input varibles. The combinations were rated based on mean squared error. The best combination of input variables found was At Bats, Strike Out Percentage, and Current Batting Average.

The charts below shows the reduction in the error with the three features used as inputs and the corresponding correlation matrix.

![Features](/images/features.png)
![Correlation Matrix 2](/images/corr_matrix2.png)

Using the selected features, the 2017 data was then split into training and testing sets. A linear regression model was then created using the training set. The model was then tested using the 2017 testing data. The test data predictions resulted in an r-squared value of .557 and a root mean squared error 0.029%.

For comaprison, a model was created using all of the players stats as input varaibles. That models test data yeilded an  r-squared value of .532 and a root mean squared error 0.030%.

The model with the limited selected input variables proved to be a better model with a higher testing set r-squared value and a lower root mean squared error.

The final step was to input the 2018 early season data into the model to obtain the prediction results. The final predictions had an average percent error of 10.59% with the range of percent errors from 0.01% - 63.09%.

While the average error being within about 10% is pretty good, the wide range of errors can possibly be attribed to the fact that no two seasons are alike. A players previous season is not necessarlily an indicator for future performance. There are several factors that can change between seasons and throughout the course of a season. Some of these factors include improved performance, injury, and off field issues/distractions.
A model accounting for offseason and inseason training activities in addition to the previous season data may lead to a more accurate prediction.
