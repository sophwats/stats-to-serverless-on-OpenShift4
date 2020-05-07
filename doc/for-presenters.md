# For Presenters
This workshop is designed to show application developers how to incorporate machine learning workflows into their everyday engineering discipline, and illustrate how to deploy serverless services on OpenShift. Our goal is that attendees wil learn:

 - how to train, evaluate, and publish models in a contemporary serverless architecture,
 - how to monitor models in production and detect failures before they cause problems, and
 - how to start incorporating intelligent features into your apps.
 
 They'll learn all this in the context of a real application, namely detecting fraudulent transactions. 
 
## Background and workshop flow 

First, follow the instructions in [deploy.md](../deploy/deploy.md), installing the Ansible roles for the workshop into an RHPDS cluster.

The main structure of this workshop is given by [the notebooks](../source), but the slide presentation complements the notebook. We sugggestthat you step through all of the slides, then give attendees the URL to their OpenShift Console. 

Once logged into OpenShift, you'll need to step your attendees through accessing their project, and going to the `route` for their project's JupyterHub instance. 

From there, they will need to re-authenticate with their OpenShift username and password, and spawn the JupyterHub service. 

The spawner compares many settings, and these will be correctly pre-set.

From top to bottom, the variables in the spawner are:

 - an image to run our environment in. Notebook images contain pre-loaded libraries. For today's workshop this should be set to `ml-workflows-notbook:latest`. 
 - t-shirt sizing for the environment. Make sure you keep this as `Default`, else you won't be able to run the notebooks.
 - the number of GPUs you want to use. (We don't have any GPUs on the cluster we're working on today, so keep this at `0`!)
 - Environment variables relating to the persistent volume which JupyterHub creates in our project:
  * the location of a git repo containing the notebooks you want to clone into your persistant volume. The repo for this workshop is https://github.com/willb/fraud-notebooks. 
  * secrets and access keys for any other storage you wish to connect to. (This should be left blank.)
  * any extra variable names you want to specify. (This should also be left blank.)

Once JupyterHub has spawned, attendees should being to work through the Jupyter notebooks. 

Notebook `00-getting-started.ipynb` explains how to interact with Jupyter notebooks. The rest of the notebooks step through stages of the machine learning workflow. 


The notebooks attendees will work through are numbered in order and (for the most part) need to be run in order. Here's how to step through the notebooks:

- `01-eda.ipynb` steps through some exploratory data analysis, allowing attendees to gain insight into the transactions data they will be working with. They'll also inspect and transform some of the data.
- `02-feature-engineering.ipynb` shows attendees how to turn the transactions data into feature vectors. They'll transform each entry in the data set into numeric vector, whilst aiming to capture important information about the data. They will visualise these vectors to indicate if it is possible to identify any structure in the data that differentiates the legitimate transactions from the fraudulent ones.

**At this point in the workshop attendees can choose which type of model they want to train.** 
We have a `logistic regression model` and a `random forest model` for attendees to choose from. 

- `03-model-logistic-regression.ipynb` shows how to train a logistic regression model to distinguish between fraudulent and legitimate transactions; and
- `03-model-random-forest.ipynb` shows how to train an ensemble of decision trees to distinguish between fraudulent and legitimate transactions.

Ask attendees how their model perfomed. What kinds of metrics are they seeing? Did they change any model parameters? How did this impact model performance?

At this point in the lab, you should show students how to use OpenShift Pipelines to build a RESTful service for making predictions, using the model they just trained. 


Openshift Pipelines are used to give us a serverless service you can make predictions against, in this case using notebook `04-sevices.ipynb`. You can use Prometheus to visualise model metrics and observe data drift.

Data drift is the phenomenon in which a predictive model loses effectiveness because the distribution of the data it is evaluating in the real world has materially diverged from the data it was trained on. (For a real-world example, think back to the early days of automated spam filtering and the cat-and-mouse game that email scammers played with email providers -- messages for pharmaceuticals might escape detection one week, while messages for gambling or dubious mortgages might escape detection the next.)

