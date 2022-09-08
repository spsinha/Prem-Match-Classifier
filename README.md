# Problem Specification

The goal of this project is to build a predictive model that is able to classify the outcome of a match in the English Premier League with enough accuracy to be able to make a profit in the betting market. The three possible outcomes are a win for the home team, a loss for the home team and a draw. We do not approach the problem using a dynamic model, whose probability vector is updated as the match progresses; instead our model outputs a single probability vector based on input that is collected prior to the start of the match.  



# Description of Data and Features
In terms of the betting data, there is one dataset per season, each consisting of 380 rows, one for each match, and 68 columns, most of which are the odds for various bets. Of the columns that contain data that are performance metrics we choose 3 to include in our model: goals, shots and corners. We create the features by using a simple moving average to capture the short term form of a team. We do this for both of the teams competing in the match. These averages are then subtracted from each other so we end up with 3 features derived from this data. We also have available to us data scraped from the web containing each team's position after each matchweek. We make use of this data by creating a 4 <sup>th</sup> feature by subtracting the position of the away team from the position of the home team. This feature captures the long term performances of the teams.


# Summary of Results
 | Model | Accuracy | Log Loss |
 | ------| ---------| ---------|
 | XGB classifier | 59% | .956 |
 | SVC | 56% | .959 |
 | Multinomial Logit | 56% | .937 |
 | Feedforward Neural Net | 56% | .938|
 
 The similarity of the results suggests that any improvement lies in creating a richer feature space.
 
 In term of the betting strategies, we were able to make profit using a conservative strategy that consists in placing a bet only if the probability outputted is larger than a given threshold. (i.e. the model is sufficiently confident) The smallest threshold that yielded a profit was .725. This strategy resulted in placing 34 bets (out of 330 matches) and a 1.9% return. Increasing the threshold to .75, we place 23 bets and achieve a 7.4% return. In evaluating these results, we must be aware of the tradeoff between the number of bets placed and the return; strategies that place fewer bets tend to have a higher return but in order to make a large profit we must place a large wager on each bet which increases the variance of the strategy.  


# Todo
Scrape the web for more data in order to create a richer feature set. One example of some useful information available on the web 
is whether or not the team had a mideweek game in another competition. <br/>
Develop more sophisticated betting strategies. <br/>


