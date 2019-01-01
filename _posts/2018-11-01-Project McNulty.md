# Project McNulty Retrospective

See [here](https://github.com/skylerl2/skylerl2.github.io/tree/master/project_3) for project files.

My third project at Metis, **Project McNulty**, introduced me to (another form of) supervised learning and data visualizations. 

Supervised learning is really just a formalized name for running models on labeled data so it can make label predictions on new 
data. But for this project, instead of running regression models, we had to run classification models—since the target (i.e., 
output) variable is categorical rather than continuous.

The classification models that we learned about, and the ones that I tested on my data, included:

* Logistic regression
* K-nearest neighbors
* Support vector machines
* Naive bayes
* Decision trees
* Random forests
* Gradient boosting

The [data](https://www.kaggle.com/nhtsa/2015-traffic-fatalities) I used were regarding fatal car accidents, and my target 
variable was the involvement of drunk driving in the crash. Testing these models (via SciKit Learn), I found that a logistic 
regression (side note: not really a regression) performed best, edging out a linear support vector classifier (a subset of SVMs) 
which was a close second. I liked this because logistic regressions seem the most intuitive to me of all the classification 
models. As with my previous project, my final model had a regularization factor to avoid overfitting.

The other new and important aspect of this project was producing an interactive data visualization. For this, I decided to use 
Tableau. I created a [histogram](https://public.tableau.com/profile/skyler.lehto#!/vizhome/DrunkDrivingModelProbabilities/Sheet1?publish=yes) of probabilities produced by my model on the dataset, and vertically split the bars by the actual incidence of drunk 
driving in the bins (which were very close to the model’s probabilities).

With both the model and the visualization developed, I was able to support my recommendation that my hypothetical police 
department use a 20 percent threshold to decide which crashes should be investigated further, to strike the right balance 
between identifying more of the drunk driving cases while wasting fewer resources on cases that did not involve drunk driving.

![alt text](https://classicruby.files.wordpress.com/2010/05/drunk-driving-crash.jpg)