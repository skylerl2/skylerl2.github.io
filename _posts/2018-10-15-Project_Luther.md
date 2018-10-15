Our second project at Metis, Project Luther, provided us with several challenges:

1. Create an interesting and motivating project idea.
2. Collect data from the internet using web scraping tools (BeautifulSoup or Selenium).
3. Analyze the data using regression techniques such as Lasso and Ridge.
4. Present the finding in a clear and concise manner, easily enough to be digested by a non-technical audience.

Coming up with the original project idea was one of the most difficult parts of the process for me. Not being sure where to 
start can be frustrating and make the project seem daunting. An idea that eventually came to mind was to examine the amenities 
provided by luxury hotels and use those to predict their review scores. This idea came to me from my familiarity with a hotel 
booking website called [Five Star Alliance] (https://www.fivestaralliance.com) (not that I typically stay at luxury hotels).

![alt text](http://cdn1.viewpoints.com/pro-product-photos/000/422/070/300/five-star-alliance-logo-300-300.jpg)

To collect the data, I used Selenium to auto-navigate through each of the 114 hotels listed under [New York City] 
(https://www.fivestaralliance.com/luxury-hotels/271/north-america/united-states-northeast/new-york-ny) and copy the data into a 
Pandas dataframe. One of the challenges of this was that the page did not allow my web scraper to automatically click on **View 
more Hotels** to expand the listings—this was the only part I had to do manually.

Using the data I scraped, I ran several regressions using the amenities and activities as explanatory variables, and the review 
scores as the outcomes to be predicted. Because the explanatory variables I was gathering were categorical, interpreting the 
regression results was pretty straightforward. The downside, however, was that I could not explain much of the variance with my 
final model (which had R^2 of 0.12). Being a dataset with 111 datapoints (I dropped three hotels without review scores) and 34 
dimensions, overfitting was an easy trap, so I knew going in that I would probably need to use Lasso or Ridge in my final 
regression model, to reduce or eliminate less significant variables. (Lasso did a bit better than Ridge, so that’s what I went 
with.) Unfortunately, I could not use as strong of a lambda hyperparameter as my Grid Search indicated was optimal—my dataset 
was small, and so that would have resulted in a baseline model. This taught me that for future projects, a larger dataset would 
be desirable.

For me, presenting the findings in a PowerPoint presentation was the most fun part. I kept in mind the feedback that was given 
to me and my colleagues on our previous projects as I put together my narrative. I sought to make my slide content concise and 
to the point, digestible for those who may not be statistically savvy, and with a clear business purpose. The narrative I 
created was how to improve the quality reputation of “our” hotel franchise’s New York City location. My recommendations from the 
data were to upgrade the fitness center, end the no-pets-allowed policy, and expand disabled access. My presentation flowed more 
smoothly than I had expected it to—practice makes perfect, I guess.
