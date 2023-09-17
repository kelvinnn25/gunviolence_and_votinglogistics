Mass Shootings in correaltion to Racial and Political Demographics

In this project, we examine the demographics of state voters in correlation to gun violence. Although realistically it is visceral how these policies will correlate, our team thought it would nonetheless be a good idea to examine the data and possibilities behind it. 

Given limited time, this project's scope only utilizes racial demographics and voting demographics per state. In the future, steps will be taken to get a closer look at more predictor variables that include lobbying, political figures' investment, etc. 

For this benefit the public sphere, if you'd like, feel free to take this code for your own experiments. 

Definition: 
  Mass shooting: a shooting which causes 4 or more casualties
  Casualty: Injury or death

Note:
  Corrections have been made to states that only have one house of government to match. Example: If D.C only has a democratic majority house of delegates, we only considered Senate in which we categorized DC as a Dem senate majority. 
Datasets to use: 
    - https://ballotpedia.org/State_legislative_elections,_2022 house and senate majorities as of 2022
        labeled: chamberDf -> senateDf, houseDf
    - https://www.gunviolencearchive.org/reports/mass-shooting?year=2022 2022 mass shootings
        labeled: shootingsDf
    - https://www.kaggle.com/datasets/paultimothymooney/percent-voting-for-democratic-party-by-state?select=democratic_vs_republican_votes_by_usa_state_2020.csv 2020 presidential elections
        labeled: votingDf
    - https://www.census.gov/library/visualizations/interactive/racial-and-ethnic-diversity-in-the-united-states-2010-and-2020-census.html 2020 concensus
        labeled: raceDf
     ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/7c6d9185-594f-4bf2-8fd5-6fd33bf74b7e)
   
  voting Demographics
    ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/30b4c972-dd66-4e7e-84a6-bba0ef40e2fc)

  Racial Demographics 
    ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/8ee5be63-fa94-4dfa-aef1-9f799781ad33)

Analysis:
  Heatmap of Mass Shooting Incidents
    ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/6ee11529-e42a-4cec-b2d1-d2867b252402)
    The image above provides a heatmap of which states have the most shootings. 

  Percentage of shootings by State: 
    ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/00ad1342-2b70-46da-9131-b3cfa04635a4)

  State Majority count (split by party) next to a number of mass shooting incidents. The orange represents the number of states for each respective party and the blue represents the number of casualties. 
    ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/4311cc57-8185-4d0f-ad9f-efd93ccfe0d7)
    ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/1f3bc8b3-6921-46ca-b394-4eb87b2b2e7d)

  Shooting Deaths by party: 
    ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/806d77c4-ff36-4bda-9def-dff3eff1ddea)

Linear Regression:
  ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/7c15b158-3f65-4af5-ab74-aadd8022aa4b)

  Percentage of Shootings for number of REP vs DEM voters 
    ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/be1bbe93-2b89-471f-a237-9b96cd661ee6)
    ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/f68aaae3-4943-412f-8259-d095693ffff1)

    Though the p values were both statistically significant:
      Metrics for Republican:
  ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/99177bdd-f6fc-4c96-a095-ebd79e55ebf0)

      Metrics for Democratic: 
  ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/8124136e-a8b6-482d-87e3-6253ed0610af)

  For the Republican Voters: 
    Both the training and testing sets exuded good R^2 values and low errors. Variance is able to be explained by the model. 
  For Democratic voters:
    The training performed well but the testing r^2 measure had an alarming .23 meaning a big portion of the variance is unexplained for.
  Conclusion: 
    the republican voters' model was better which shows a good correlation. However, the Democratic voters had a good training set for correlation but poor testing. 
    This means the regressional model is able to show the correlation between Republican voters and the percentage of mass shootings nationally.

  Problems: 
    The reason you are unable to standardize the REP vs DEM voters is that they are inversely related. For instance, if your state had 40% Republican but 60% Democratic, the model would not make an accurate prediction because they would portray similar results. Most of these states are neck and neck and vary depending on population, therefore influencing legislation in a different manner. Therefore, we felt best that the number of voters according to the 2020 election results would be more appropriate to show how people feel about gun control laws. 

Random Forest: 
  Dataframe used:
    ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/9e1504eb-4b20-4c57-86ee-40e751c06072)
  Training Matrix:
    ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/a48e0456-270d-4b79-ad52-d3dfb545d2dd)
  Testing Matrix:
    ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/deafe02e-f76a-4946-956e-38225bd7dba0)

  Results: 
    This was an alarming 100% accuracy model for both testing and training. Results will be explained however to correct this, we used cross-validation to remove overfitting. 
  
  Cross Validation:
    ![image](https://github.com/kelvinnn25/gunviolenceproject/assets/80852728/da18bbb4-b9dc-4c4a-9ca7-7064ffa9004a)

  Explanation:
    We used a binary classifier
      0- democratic
      1- republican
    You can see in the image, the top left is True Democratic (true positive) - Bottom Left is falsely classified Democratic States (False negative). Top Right is Falsely classified republican states (False Positive) - Bottom Right is True Republican (true Negative) states. 
    Accuracy Rate: 86.84%
    False negative rate: 20.6%
    False positive rate: 6.67%

  Conclusion:
    This model had a high false negative rate of 20.6% which is dangerous. This simply means there are Democratic states that have been classified as high characteristics of shootings + racial demographics + voting demographics. However given the accuracy of the model it shows that you are able to classify states based on these metrics.  
      
    
  

  
