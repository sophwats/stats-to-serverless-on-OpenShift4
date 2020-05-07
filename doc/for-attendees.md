# For attendees

This workshop is designed to show application developers how to incorporate machine learning workflows into their everyday engineering discipline, and illustrate how to deploy serverless services on OpenShift. Our goal is that you will learn:

 - how to train, evaluate, and publish models in a contemporary serverless architecture,
 - how to monitor models in production and detect failures before they cause problems, and
 - how to start incorporating intelligent features into your apps.
 
 
## Background and workshop flow

The main structure of this workshop is given by [the notebooks](../source). If you havent used Jupyter ntoebooks before, make sure you spend time woking through notebook [00-getting-started](../source/00-getting-started.ipynb). 

The notebooks you'll work through today are numbered in order and (for the most part) you'll need to run them in order. Here's how to step through the notebooks:

- `01-eda.ipynb` steps through some exploratory data analysis, allowing you to gain insight into the transactions data you will be working with today. You'll also inspect and transform some of the data.
- `02-feature-engineering.ipynb` shows how to turn the transactions data into feature vectors. You'll transform each entry in the data set into numeric vector, whilst aiming to capture important information about the data. You will visualise these vectors to indicate if it is possible to identify any structure in the data that differentiates the legitimate transactions from the fraudulent ones.

**At this point in the workshop you can choose which type of model you train.** 
We have a `logistic regression model` and a `random forest model` for you to choose from. 

- `03-model-logistic-regression.ipynb` shows how to train a logistic regression model to distinguish between fraudulent and legitimate transactions; and
- `03-model-random-forest.ipynb` shows how to train an ensemble of decision trees to distinguish between fraudulent and legitimate transactions.

Try some different options! Did you notice anything improve or worsen your model's performance?

Next, you will see how to use OpenShift Pipelines to build a RESTful service for making predictions, using the model you just trained. Openshift Pipelines are used to give us a serverless service you can make predictions against, in this case using notebook [04-sevices](../source/04-services.ipynb). You can use prometheus to visualise model metrics and observe data drift.

Enjoy!
