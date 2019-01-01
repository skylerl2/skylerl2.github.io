# Project Kojak Retrospective

My final Metis project, **Project Kojak**, was my chance to use anything and everything I had learned in the course and apply 
it to something I am interested in or passionate about in some way. Because of this, it was my most rewarding Metis project, but 
also my most challenging one.

The question I decided to tackle was one that I had been pondering ever since the 2016 presidential election: Can primary 
turnout be used to predict general election results? Supposedly, the answer was no, according to [this article](https://fivethirtyeight.com/features/primary-turnout-means-nothing-for-the-general-election/) from FiveThirtyEight written 
months before the November general election. While some had been keen to point out that Republicans were 
beating Democrats in primary turnout that year, FiveThirtyEight thought history showed it wasn’t predictive of the general 
election results.

But after the election had turned out the way it had, I started to doubt this. After all, FiveThirtyEight had only examined the 
primary-general correlation on a national level. Maybe the conclusion would be different and more reliable if we looked at 
individual states instead? After all, we would be getting a much larger sample size (50 states vs. 1 nation).

That was the question I decided to take up for my final project. To start out, I retrieved primary and general election data 
from the Federal Election Commission, as well as state-level economic data from the Bureau of Economic Analysis. After saving 
and cleaning all of this data in Pandas, I computed a modified version of Cook’s [Partisan Voter Index](https://www.cookpolitical.com/introducing-2017-cook-political-report-partisan-voter-index) (PVI) to use in the 
regressions.

And using these data, I made a logistic regression model using Scikit-learn that would return the probability of each state 
going for the Republican or Democratic candidate in the electoral college. My first regression was using just the PVI and the 
economic data; my second regression added in primary (and caucus) turnout. (I used a modest regularization factor to prevent 
overfitting.) By comparing the two regressions, I could ascertain what the effect of primary turnout was on the forecast.

To put together an overall election forecast using 51 probabilities (including DC), I ran 100,000 Monte Carlo simulations of the 
electoral college outcome. I assumed some correlation among the state-level outcomes, since polling errors typically aren’t 
random. Ultimately, my findings pointed to a significant effect from including primary turnout data, with the Republican 
candidate’s chances rising from 24 percent to 59 percent.

![alt text](https://skylerl2.github.io/images/MC_model_without_turnout.png)
![alt text](https://skylerl2.github.io/images/MC_model_with_turnout.png)

Looking at the specific changes in state-level probabilities, I was able to put the most significant changes into three groups:

**Competitive states that became likely Republican:**
* North Carolina
* Florida
* Ohio

**Likely Democratic states that became competitive:**
* Iowa
* Wisconsin
* Pennsylvania

**Competitive states that became likely Democratic:**
* Nevada
* New Mexico

While most of the shifts were in a Republican direction, some were not. This last group of states that shifted the other way 
gave me more confidence in my model’s results, considering these are two states where Hillary Clinton actually outperformed her 
polls on Election Day (see [here](https://www.realclearpolitics.com/epolls/2016/president/nv/nevada_trump_vs_clinton-5891.html) 
and [here](https://www.realclearpolitics.com/epolls/2016/president/nm/new_mexico_trump_vs_clinton-5894.html)). This is unlike 
most of the other states, including ones my model identified, where it was Donald Trump who beat the pollsters’ expectations.

So what did I learn from this? Besides the usefulness of these tools and reaffirming my learned ability to make use of them 
effectively, I discovered that pollsters may be leaving some information on the table when it comes to updating their likely 
voter screens. It seems like in 2016, they leaned too heavily on turnout patterns from the 2012 election, when perhaps they 
could have done more to factor in 2016 primary turnout. Then maybe the polls would have given us a better idea of just how close 
the 2016 presidential election was poised to be.