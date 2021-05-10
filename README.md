![picture alt](https://useruploads.cdn-thecorrespondent.com/image/wWTnZUtk-vZoO0H9u_7Hs4SKVZk=/1920x1080/tc-useruploads-images/a012b0df6cac4ece8aacc4561d7c5fd4.gif)

# Track(ed) Together

This repository contains code and data from the Track(ed) Together Project, a project from the online magazine De Correspondent that ran between May 1st 2020 and May 1st 2021. The purpose was to establish an overview of surveillance measures taken to combat the covid-19 pandemic and to get insights into the scope, use and effectiveness of those measures. The project was meant to last for a year on the assumption that the crisis would be over by then. That wasn't the case. 

It would be great if other people and organization built further on our dataset. Therefore we share our data and code with you. Feel free to use the data and code as you see fit, but please attribute the data collection to us. All data have been frequently manualy updated and verified. Data sources are provided as well. 

If you want to get a sense of the type of stories or research you can do with this data, please take a look at some of our [stories at The Correspondent](https://thecorrespondent.com/collection/track-ed-together) or, in Dutch, at [De Correspondent](https://decorrespondent.nl/collectie/track-ed-together). 

## About the data

The data was manualy collected from public sources between May 1st 2020 en May 1st 2021 by several journalists (Lais Martens, Morgan Meaker and Dimitri Tokmetzis). All data have been verified. In the end, we collected information on approximately 650 surveillance measures worldwide. Here you can [find a list](https://github.com/decorrespondent/trackedtogether/blob/master/mongodb/dumps/_public_fields.txt) of collected fields.

The data are available in several formats:
1. [CSV dumps](https://github.com/decorrespondent/trackedtogether/tree/master/mongodb/dumps/public)
2. A cleaned up [csv file](https://github.com/decorrespondent/trackedtogether/blob/master/public_data/tt_measures%20.csv) (with some data omitted)
3. Or the [whole MongoDB set](https://github.com/decorrespondent/trackedtogether/tree/master/mongodb)

## About the MongoDB

In the root you'll find two files:
* **mongo_schema**: this file contains the MongoDB shell command that creates the validation JSON schema for the surveillance collection.
* **sample_insert**: this file contains an example of a MongoDB shell command that creates one document in the surveillance collection.

There's also a `_dumps` directory which contains three folders:
* **mongo**: this folder contains a dump of the db that can be imported with the `mongorestore` command.
* **private**: this folder contains raw csv dumps of the surveillance collection with all fields..
* **mongo**: this folder contains csv dumps of the surveillance collection with some fields and object fields split up over multiple columns. 

To create dumps use these commands:

**mongo**

`mongodump --db=surveillance --collection=measures --out=_dumps/mongo`

**private**

`mongoexport --db=surveillance --collection=measures --type=csv  --fieldFile=_dumps/_private_fields.txt --out=_dumps/private/$(date +%s).csv`

**public**

`mongoexport --db=surveillance --collection=measures --type=csv  --fieldFile=_dumps/_public_fields.txt --out=_dumps/public/$(date +%s).csv`

## Notebooks

We've added two notebooks with some code for your convenience. Of course the code could be made more pythonic, suggestions are welcome.
* [Measure data](https://github.com/decorrespondent/trackedtogether/blob/master/notebooks/measure_data.ipynb) contains code to parse several datasets with covid-19 measures from several reliable sources.
* [CoronaMelder](https://github.com/decorrespondent/trackedtogether/blob/master/notebooks/CoronaMelder_stats.ipynb) contains code snippets for analyzing several statistics concerning the Dutch contact tracing app CoronaMelder.

## Some thoughts on possible research and data collection

There is plenty of interesting research possible, like:
* Analysis of companies providing surveillance technologies.
* Comparisson of tracked together data with other measures as described in:
  * [CoronaNet](https://www.coronanet-project.org/download.html): (Cheng et al, 2020)
  * [CCCSL](https://github.com/amel-github/covid19-interventionmeasures): (Desvars-Larrive et al, 2020)
  * [Oxford Covid Policy Tracker](https://github.com/OxCGRT/covid-policy-tracker): (Hale et al, 2021)
* Once the crisis has abated, a more in-depth assessment of efficacy of the measures. 

If you have any questions, please feel free to reach out to us.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
