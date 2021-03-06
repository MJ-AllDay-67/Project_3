![HOF_cover](https://user-images.githubusercontent.com/67566192/109255123-5990fe00-77c1-11eb-94e9-254e184c0b78.jpg)

# Classifying MLB Hall Of Fame Players

**Author**: Michael Tiernan

## Brief History
In recent years, we have seen how data has transformed the world of sports - most notably for me, Major League Baseball (MLB) teams implementing "the shift" - but turn on any live sporting event and you will see things like launch-angle and distance tracking. Turn on ESPN and they have full segments on "sport science", tracking a player's acceleration, speed, power, or things like best route taken, all powered using Amazon's AWS system. 

This whole movement into data-backed analysis for sport started with Major League Baseball General Manager, Billy Beane, of the Oakland Athletics'. His storied success was turned into a book and later box-office hit movie, "Moneyball." 

## Business Problem
With the history of using data for sport starting in baseball, it is no surprise that baseball is leaps and bounds ahead of all other major sports in using data analytics. But there is another important subset of sports that is behind in this data analytics arena as well, and that is the sports management agencies. 

My consulting firm focuses on this aspect of the sports business. For this particular client we are looking to:
1) Uncover what stats make a Hall Of Fame (HOF) player
2) Use these findings to help navigate current contract negotiations
3) Target active players to sign if they are on a HOF trajectory 

## Hypothesis
Null hypothesis (HO): Hits and Home Runs have no relationship to a player being inducted into the HOF. 
Alternative hypothesis (Ha): Hits and Home Runs do have a relationship with a player being inducted into the HOF.

## Data
The data used in this analysis comes from [Lahman's Baseball Database](http://www.seanlahman.com/baseball-archive/statistics/) as well as [baseballsavant](https://baseballsavant.mlb.com/leaderboard/custom?year=2019,2018,2017,2016,2015&type=batter&filter=&sort=4&sortDir=desc&min=q&selections=xba,xslg,xwoba,xobp,xiso,exit_velocity_avg,launch_angle_avg,barrel_batted_rate,&chart=false&x=xba&y=xba&r=no&chartType=beeswarm). After joining and manipulating the data, I ended up with 2,316 rows and 37 features (or stats) used to classify if a player is a HOFer or not. 


## Method
For this project I stuck to the CRISP-DM method. After retrieving the data, I cleaned and joined a number of different databases (Lahman's is an extensive database made up of 20+ csv files) in order to create my final database to use for modeling. 

For modeling, I chose to work mostly with DecisionTree classifiers. Logisitc regression was used intially, but due to the high multicolinearity effecting many of my main features, I had to focus mainly on DecisionTrees. I prioritized accuracy as my main metric, but also set out to have high recall score as well so that my model was focused on rewarding those who deserve to be in the HOF and making sure we were not missing them in my binary classification models; HOF or not.

**The following players were removed from the data after running a couple models with them included. The players were those who have HOF numbers, but are currently banned by the MLB HOF committee due to Performance Enhancing Drugs (PEDs) use or other reasons:
(Pete Rose, Alex Rodriguez, Barry Bonds, Sammy Sosa, Mark McGwire, Manny Ramirez, Rafael Palmero, and David Ortiz).

## Findings
I found the stats both by position and overall playing career.
![stats_subplots](https://user-images.githubusercontent.com/67566192/109269259-40487b80-77da-11eb-9537-db72fbce3be8.png)

Looking at the visuals above, it is clear that HOF players are vastly better than the rest of the field in every stat, however, there are different requirements depending on position i.e. Catchers ('C') not heavily rated on the number of hits or Shortstops ('SS') not heavily rated on homeruns. 



![hits](https://user-images.githubusercontent.com/67566192/109270845-a6ce9900-77dc-11eb-9621-0721baae4381.png)

As you can see from this second graph above, the vast majority of MLB leaders in career hits are HOFers (HOFers denoted by orange plots). 
**Also note one of the players noted above that is banned from the HOF, Pete Rose is the all-time leader in hits, but not a HOF (blue plot).


## Recommendations
![feature_importances_best](https://user-images.githubusercontent.com/67566192/109297156-8cf27d80-77ff-11eb-9032-08d929033f29.png)

The most important stats when it comes to evaluating a HOF player is Hits, Runs, and All-Star games made. With this newfound, I recommend to my client that they should use these metrics when negotiating their current contracts as well as look for active and upcoming players with these stats in mind. They will pay off large when these players sign their hundred-million dollar contracts! 

## Conclusion and Future Work
While my best model performed effectively with a 86% recall and 94% accuracy, it does not meet the requirement of within 5% to reject the null hypothesis. 

I am happy with the performance of my model, but with more time I would have loved to go deeper into the world of sabermetrics and work with stats like OPS+, WOBA, and WAR. These are stats that have come to more accurately define a player's ability, but I was unable to find this data, and calculating them is an extensive task because you must account for the time periods in which these players played in order to accurately implement these stats.
    
