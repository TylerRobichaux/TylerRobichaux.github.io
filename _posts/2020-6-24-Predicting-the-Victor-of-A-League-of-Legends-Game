  About thee weeks ago I found a data set for League of Legends that contained information about the state of the game at ten minutes. I immediatly wanted to use it
to try and predict the winner; however, I did not yet poccess the skill to accomplish this task. That has changed, I am proud to prest to you my models for predicting
the victor of a League of Legends match at 10 minutes. 

  My first goal was to create as many useful features as I could think of. As adding a new feature that says somthing new about your data can be very valuable to a model.
In total I added 10 features that I thought could be helpful. I also removed features that were redundant. Such as Blue teams deaths and Red teams kills. These two 
columns essenially contain the same information. If blue team died, it is because red team killed them. So only one is needed. As an over eager kid in a candy store, I 
could not wait to to try a model. I fit the data set with all of my new features and got its validation accuracy, 70.9% not bad! I was very pleased with this as a first
pass. I decided to further examine the features in my data. I removed many columns that I used to create my new features. My thinkingwas a gold ratio between the teams 
still contains infomation about how much gold each team had comparitivly. A seperate gold column is no longer needed. I fit a new model and indeed my accuracy went up to 
72.7%.

  Next I did permutation importance. I still wanted to focus on features. I was suprized with how small of an impact each of my features made. My highest permutation
importance Blue/RedGoldRatio *cough*I made this one*cough* with a value of 0.0093. This means that if the Blue/RedGoldRatio feature was removed the model would only lose
0.93% accuracy. I also had many features when removed the model performed better. Based on my findings I decided to remove 30 of my 46 features. I fit another model, its
accuracy was 72.3%. I felt this was a great imporvment. the decrease in accuracy wasn't enough to mean anything, but the model was far more simple. Which would hopefuly 
mean I could generalize better.

  At this point I was curious about my feature importance. This graph showed that Blue/RedGoldRatio feature far more important that any ofter feature. The next 2 features
with the most importance were the two columns containing information about if a team had killed the Dragon. I started creating new models each one removing more and more
of the features ranked with the lest importance. I kept removing features and the accuracy wasn't going an appriciatable down. By the end I had reduced my fourty six 
features to jsut three. Blue/RedGoldRatio, RedDragons, and BlueDragon. The first column, Blue/RedGoldRatio, is simply how much gold the blue team had in total devided by 
how much gold the red team had in total. The other two remaining columns were simple binary features containing a 1 if that team had killed the dragon and a 0 if they 
didn't. This model had essentialy the same accuracy again with 72.6%. While I wasnt pleased that I had not made my model more accurate. I reduced its complexity greatly 
while maintaingthe same accuracy. With a reduction from fourty 6 to jsut three features and maintaining the same accuacy. The three feature model is vastly better.

  Furthering my quest to make my model more accurate. I decieded to make a confusion matrix. I was expecting to see some imblanace between flase postives and false 
negatives. The idea was I could see if my model is worse at predicting victories or defeates. Perhaps I could engineer a more custom feature to help resolve some of the 
confusion my model was having. My confusion maxtrix was not at all what I wanted. It showed a near perfect balance in all catagories. This greatly hindered my ability to 
balance a weakness in my moddle, as my model was already very balanced. So I abandand the idea and moved on.

  I created a partial dependence plot for the Blue/RedGoldRatio feature. This plot showed a fairly linear relationship between the blue and Red teams gold ratio and the 
chance that blue team would win the game. I also created a shaply plot, this plot showed how each of the columns effected a prediction. For the specific game I chose, as 
expected, the Blue/RedGoldRatio feature had the most imfluence. the two dragon columns actually had a negitive impact on the prediction. While I realize this is just chance 
due to the game, I chose. This combined with the somewhat linear relationship of gold ratio and predicting th winner of the game. I decided to make a Logisitc Regresssion 
model with the only feature being Blue/RedGoldRatio.

  I made serveral Logistic Regression models. All containing varying features. My three most successful models were a model with the Blue/RedGoldRatio, BlueDragons, and 
RedDragons another with just Blue/RedGoldRatio, and one more with Blue/RedGoldRatio, and Blue/RedExpRatio. Blue/RedExpRatio is a feature that is the Blue teams total 
experience points gained devided by the Red teams total expeince points gained. All three of these models with within ~1.3% of each other. The model with Blue/RedGoldRatio
as its only feature being the least accurate with an accuracy of 71.93%, and the model with  Blue/RedGoldRatio, BlueDragons, and RedDragons being the most accurate with 
and accuracy of 73.21%.
