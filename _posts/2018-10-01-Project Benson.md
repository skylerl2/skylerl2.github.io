# Project Benson Retrospective

Our first project presented us with a straightforward task: Provide advice to a hypothetical group (WomenTechWomenYes) about optimal placement of street teams at NYC subway stations to solicit for the group’s summer gala.

Of course, thinking through how to deliver a recommendation (using data from the MTA) reveals that there are more steps and processes involved than originally meet the eye. As a data scientist in training, they provide a challenge, but also an opportunity to learn how tools and techniques can provide insights from data.

The first issue we had to address was the scope of the data that we wanted to use, geographically and temporally, given our objective. Geographically, we decided to restrict our analysis to stations located in NYC’s [Silicon Alley](https://www.builtinnyc.com/2016/12/13/big-tech-companies-nyc-locations) (a subset of Manhattan where tech firms are concentrated). We also decided to focus only on subway traffic during the springtime, as these are the months leading up to the gala held in the summer. We took data over three years (2016-18) to add robustness to our dataset.

![alt text](https://www.builtinnyc.com/sites/www.builtinnyc.com/files/screen_shot_2016-12-13_at_12.35.30_pm.png)

Applying the temporal restriction was pretty straightforward—the MTA’s website has [turnstile data](http://web.mta.info/developers/turnstile.html) saved in dated files by week, so we downloaded only those files and merged them together. The geographical restriction was not as simple, but still doable. We identified the (latitude, longitude) coordinates that effectively enclose Silicon Alley, and merged this with [coordinate data](http://web.mta.info/developers/data/nyct/subway/Stations.csv) for the MTA’s stations to return a filtered list of stations only in Silicon Alley.

We then merged this station list with the subway station traffic data to provide us with our list of the most heavily traversed stations in Silicon Alley, with which we were able to produce data visualizations to support our recommended stations for placing street teams. We checked our (unfiltered) data against the top stations listed on the MTA’s website to ensure that our data was pulling in correctly.

In one sense, it seems that the question we were provided would have been quite easy to answer with minimally processed traffic data and cross-referencing a map of New York City. However, the purpose of this exercise was to teach us how to use basic data science techniques—ones that will be useful for answering more complex or inconspicuous questions. And with this first project behind us, it will be easier to do that when facing future challenges.