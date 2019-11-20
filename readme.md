
# GETTING STARTED

1. Make sure you java version is at 1.8+. 


2. cd into fuseki/fuseki/apache-jena-fuseki-3.13.1 (“FUSEKI_HOME” directory) and run the “fuseki-server” script

```
./fuseki-server

```

3. open your browser at localhost:3030 and login with one of the fake credentials in fuseki/fuseki/apache-jena-fuseki-3.13.1/run/shiro.ini f.e. admin:admin

# BASIC WORKFLOWS

## Adding a new project


* add a new project*-config.ttl to ./apache-jena-fuseki-3.13.1/run/configuration/
* add a user credentials and an url/endpoint to shiro.ini
* Restart the fuseki server. The new project*-config.ttl will be loaded on startup. All needed components like the TDB2 (Triple store) will be generated. Check your project/endpoints at localhost:3030

## Importing/Exporting Data to your project

There are basically three ways to import data:

* Uploading files to your dataset over the UI at localhost:3030 (Import small sets of data)
* HTTP POST to SPARQL endpoint (Import small sets of data)
* Import/Load files via script (Import huge sets of data. Most performant)

### Load data via script

* Stop the fuseki server
* Cd into [FUSEKI_HOME] and hit
```
$ sh [yourscript] --loc=[location/of/your/tdb-database] [yourImportfile.ttl]
```
for example:
```
$ sh scripts/tdb2.tdbloader --loc=run/databases/lombardus-database run/databases/animal_example.ttl
```
* Wait until done and start the fuseki server
* hit sh scripts/tdb2.tdbloader --help for further options

### Exporting all data via script

* CD into your FUSEKI_HOME directory and hit
```
$ sh scripts/tdb2.tdbbackup --loc=run/databases/your-database --output=nq
```
* Check the created gzip containing your data in the given format (output) into the given directory [your-database]/backups. 
* hit sh scripts/tdb2.tdbbackup --help for further options

