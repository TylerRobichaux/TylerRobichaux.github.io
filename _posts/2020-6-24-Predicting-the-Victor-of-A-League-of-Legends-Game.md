 About three weeks ago I found a data set for League of Legends that contains information about the state of the game at ten minutes. I immediately wanted to use it to try and predict the winner; however, I did not yet possess the skill to accomplish this task. That has now changed, I am proud to present the highlights of the process I went through to create my model for predicting the victor of a League of Legends match at 10 minutes into the game. 

  My first goal was to create as many useful features as I could think of. Creating a feature that says something new about your data can be very valuable to a model.
In total I added 10 features that I thought could be helpful. I also removed features that were redundant. Such as Blue teams deaths and Red teams kills. These two columns essentially contain the same information. If blue team died, it is because red team killed them. Only one of them is needed. As an over eager kid in a candy store, I could not wait to to try a model. I fit the data set with all of my new features to a Random Forest Classifier and got its validation accuracy, 70.9% not bad! I was very pleased with this as a first pass. I decided to further examine the features in my data. I removed many columns that I used to create my new features. My thinking was a ratio of two values still contains information about their relative magnitude, which is the important part, a separate column contianing the madnitude is no longer needed. I fit a new model and indeed my validation accuracy went up to 72.7%.

  Next, I still wanted to focus on features. I found the permutation importance for each of my features. I was surprised with how small of an impact each of my features had. My highest permutation importance score was for the feature Blue/RedGoldRatio (*cough*I made this one*cough*) with a value of 0.0093. This means that if the Blue/RedGoldRatio feature were removed, the model would only lose 0.93% accuracy. Many of the features were scored with a negative value as well. Meaning if they were removed the accuracy went up. Based on my findings I decided to remove 30 of my 46 features. I fit another model, its validation accuracy was 72.3%. I was disappointed the accuracy hadn't gone up; however, I felt this was a great improvement. The decrease in accuracy wasn't enough to mean anything, and the model was far simpler. This would hopefully mean the model could generalize better.

  At this point I was curious about my feature importance. I created a feature importance graph. This graph showed that the Blue/RedGoldRatio feature far more important than any other feature. The next 2 features with the most importance were the two columns containing information about if a team had killed the Dragon. I started creating new models each one removing more and more of the features ranked with the least importance. I kept removing features and the validation accuracy wasn't going down an appreciable amount. By the end I had reduced my forty six features to just three. Blue/RedGoldRatio, RedDragons, and blueDragon. The first column, Blue/RedGoldRatio, is simply how much gold the blue team had in total divided by how much gold the red team had in total. The other two columns were simple binary features containing a 1 if that team had killed the dragon and a 0 if they had not. This model had essentially the same validation accuracy with 72.6%. While I wasn't pleased that I had not made my model more accurate. I reduced its complexity greatly while maintaining the same accuracy. With a reduction from 46 features to just 3 features and maintaining the same accuracy. This 3 feature model is a vast improvement.


![feature importance](https://i.imgur.com/qNtcrCK.png){: .mx-auto.d-block :}


  Furthering my quest to make my model more accurate. I decided to make a confusion matrix. I was expecting to see some imbalance between false positives and false negatives. The idea was I could see if my model is worse at predicting victories or defeats. Perhaps I could engineer a more custom feature to help resolve some of the confusion my model was having. My confusion matrix was not at all what I wanted. It showed a near perfect balance in all categories. This greatly hindered my ability to balance a weakness in my model, as my model was already very balanced. So I abandon the idea and moved on.
  
  
![confusion](https://i.imgur.com/Q9QntpR.png){: .mx-auto.d-block :}
  
  
  I created a partial dependence plot for the Blue/RedGoldRatio feature. This plot showed a fairly linear relationship between the blue and Red teams gold ratio and the chance that blue team would win the game. I also created a shaply plot, this plot showed how each of the columns effected a prediction. For the specific game I chose, as expected, the Blue/RedGoldRatio feature had the most influence. the two dragon columns actually had a negative impact on the prediction. While I realize this is just chance due to the game I chose, this combined with the somewhat linear relationship of gold ratio and predicting the winner of the game. I decided to try a Logistic Regression model.

![PDP](https://i.imgur.com/ixOMKAy.png){: .mx-auto.d-block :}







_________________________________________________________________________________________________________________________________________________________________________________


SHAP{: .mx-auto.d-block :}




![Shap plot](https://i.imgur.com/3bNc8Sr.png){: .mx-auto.d-block :}


  I made several Logistic Regression models. All containing varying features. My three most successful models were a model with the Blue/RedGoldRatio, BlueDragons, and RedDragons another with just Blue/RedGoldRatio, and one more with Blue/RedGoldRatio, and Blue/RedExpRatio. Blue/RedExpRatio is a feature that is the Blue teams total experience points gained divided by the Red teams total experience points gained. All three of these models with within ~1.3% of each other. The model with a single feature of Blue/RedGoldRatio being the least accurate with a validation accuracy of 71.93%, and the model with the Blue/RedGoldRatio, BlueDragons, and RedDragons features being the most accurate with a validation accuracy of 73.21%. Finally, an increase in accuracy, while maintaining simplicity. I believe my Logistic Regression model with the Blue/RedGoldRatio, BlueDragons, and RedDragons features to be my best model. I decided to find its testing accuracy. This models testing accuracy was 76.31%. while I was ecstatic to see a jump in accuracy, I was also curious as to why. My split was random. So I thought maybe the testing set happened to get fewer outlier games, thus making it easier to predict. I re-split my data. The new split received ~73.4% for both validation and testing accuracy. This is the model I chose as my final model.
