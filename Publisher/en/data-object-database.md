# Data object: database

A **database** linked to your account can be accessed in the data-scripts. 
To request a database object please see the documentation on [the account object](./data-object-copernica)
It is also possible to edit some of the information in the database.

## Available properties

* **ID**: the ID of the database (Read only)
* **name**: the name of the database (Read and write)
* **description**: the description of the database (Read and write)
* **archived**: a boolean value telling if database was archived (Read and write)
* **created**: timestamp of database creation (Read only)
* **profiles**: an array of all database [profiles](./data-object-profile). 
Keys in this array are profile IDs (see example).
* **data**: see the documentation on [the data object](./data-object-data)

## Example profile retrieval

The following example in javascript can be used to access a profile from a database.

    var profileID = 54840;
    var someProfile = database.profiles[profileID];

## More information
* [The data-script object](./data-object)
* [The data object](./data-object-data)
* [Profile variable](./data-object-profile)
* [Collection variable](./data-object-collection)
