# Corona

## Surveillance: Track(ed) Together

In this directory you can find everything related to the Track(ed) Together database. We're running a MongoDB database to keep track of the measurements taken by governments during the COVID-19 crisis. 

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
