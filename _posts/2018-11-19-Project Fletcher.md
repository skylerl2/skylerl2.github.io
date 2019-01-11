# Project Fletcher Retrospective

See [here](https://github.com/skylerl2/skylerl2.github.io/tree/master/project_4) for project files.

The fourth project I did at Metis, **Project Fletcher**, felt a bit different than the previous ones. In this one, what I 
needed to do is something called “unsupervised learning.” What this means is that our task at hand is not using regression or 
classification to predict outcomes; rather, we need to take data and run algorithms to give us insights into the data that we 
didn’t necessarily know to look for. 

The key difference is in having *labeled* vs. *unlabeled* data. With the former, we tell our model which data tends to have 
which outcomes, and use that to predict new outcomes on new data. But with the latter, we aren’t providing the model with any 
labels to guide it. We let the model tell us what it sees in the data, in terms of which data is more or less similar to other 
data in the set.

Coming up with a project idea for this one was not as straightforward without a concept of what to be looking for. But the 
project I eventually settled on was to examine tweets about voting that were made on the day of the US midterm elections.

To do this, I scraped 18,000 public tweets containing the word “vote” on 11/6/18 using the [Twitter API](https://developer.twitter.com). I saved these tweets in Mongo DB to be accessed each time I reopened my working file. And I 
used Natural Language Processing (NLP) techniques (e.g., RegEx Tokenizer) to clean and prepare the data for analysis.

For the analysis, I first ran all the tweets through SciKit Learn’s Count Vectorizer to create a document-term matrix with all 
the tweets (documents) and unique words (terms) that exist across all 18,000 tweets. I then ran a [Non-Negative Matrix 
Factorization](https://en.wikipedia.org/wiki/Non-negative_matrix_factorization) on these. Put simply, NMF is a way of 
decomposing the matrix in order to identify certain groups of words that tend to be used together. In NLP, these groups of words 
are referred to as *topics*.

The algorithm only returns the words for each topic, and the identification/naming of the topics requires subjective 
interpretation. I identified the top five as: 

* Republican
* GOTV
* Can’t Complain
* Today’s Election Day 
* I Voted

I then made six clusters of tweets in the five-dimensional topic space that resulted, and represented these in a three-
dimensional scatterplot (using Principal Components Analysis to reduce the dimensionality).

![alt text](https://skylerl2.github.io/images/tweet_clusters.png)

As neat as the clusters may have appeared in my visualization, my takeaway from this project was that there really isn’t much 
insight to be had from tweets, since the “documents” are short—no more than 280 characters in a single tweet. Moreover, the 
insights are limited by what Twitter users are willing to disclose about their voting—for most of them, not much beyond sharing 
that they voted.

I’m sure there are ways to gather some insights from Twitter if the data are broad enough and the inquiries are specific. But 
for my next and final project, I’m sure I’ll be looking elsewhere to get good and relevant data.