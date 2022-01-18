# NBARookieTenurePrediction
Model created on python that inputs multiple box score statistics of NBA players in their first year in the league and predicts the variables that are most important in them remaining in the league for more than 5 years.

## Description of Data Set, Cleaning and Preprocessing
The dataset was used from the website data.world. The data set contains the statistics of first-year NBA players from 1986 to 2016, with 19 numeric columns, 1 character column, and 1 factor column with 1340 rows. The Dependent Variable called “Target_5Yrs,” which indicates whether a rookie player will be in the NBA for at least 5 years. A 1 represents whether a player’s career length is longer or equal to 5 years, while a 0 represents a career under 5 years. Given that teams have a big decision to make regarding the contract extension of a player after their rookie contract expires, an early indicator of metrics that are relevant to longevity in the league could save substantial money to the team in a sport where budget allocation in player salaries is a very important part of team building

Cleaning and Preprocessing Techniques Used- 
      a) Removal of duplicate rows- drop_duplicates()
      b) Changing Variable names to make it conducive to model- replace()
      c) Splitting the Data- stratified splitting of data (80% train, 20% test)
      d) Downsampling the data based on the dependent variable to avoid skewing of results
      e) Removing low-variance features to remove potential skewness while modelling- VarianceThreshold()
      f) Scaling the data to ensure variables are calculated on the same scale- RobustScaler()
      
## Setup of Models
As the target variable is of binary type, we knew that a logistic regression model would best serve our endeavour. We employed 4 models to check for the best accuracy; Decision Trees, AdaBoost, Random Forest, and Logistic Regression.   

## Model Evaluation

The best model found was the logistic regression with the highest AUC of 0.745. This regression helped model the probability of whether a rookie would stay for at least 5 years depending on their statistics. 

We used a barplot to visualize the quality of the models, and used an ROC plot to further solidify our findings. 

We then used the confusion matrix to check for errors in the logistic model. Predicting on the test data and creating a confusion matrix, we find a decent accuracy at 66.4% with low type 1 errors and medium type 2 errors. The significance in these errors comes down to their meanings. A low type 1 error means the model had a low chance of predicting a bad player would last more than 4 years. This insinuates that NBA teams would be less likely to give a contract to such a player saving them money. On the other hand, a medium type 2 error indicates that the model would have a medium chance of predicting a good player would not last more than 4 years. In business terms, this means that NBA teams may find some missed opportunities in some good players since they were predicted to play for a short period. Since the level of type 1 and type 2 errors are dependent, this may be our most optimal condition as NBA teams save money from spending on bad players.

Finally, we created a variable importance matrix to check for the most relevant or important variables for our model. As we were working with a lot of variables that could possibly overcomplicate our model, we picked the five most important variables and ran another logistic regression using them. 

The 5 most important variables were: Games Played, 3 Pointers Attempted, 3 Pointers Made, Offensive Rebounds and Free Throw %. Plot effect graphs were created to better visualize the impact of the metrics. 

## Conclusion
The fact that 3 of the top 5 metrics are related to shooting metrics, arguably the most important skill to possess in today's NBA. Additionally, the 3 point shooting boom in the NBA relates to the eye test that we have, that a good 3 point shooter will probably last in the NBA longer, as it has become one of the most desirable skills in the NBA. 
With all this being said, there is a lot that goes into a player being successful in the NBA. Team composition, coaching, internal development and other intangible factors such as injuries and mental health all play an important role in defining an NBA players future. However, we do believe that our model provides a great initial indicator as to which metrics are important in deciding a player's future in the NBA, and whether a player will be able to secure that second contract. 
