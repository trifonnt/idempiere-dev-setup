# Linux scripts to setup new iDempiere Development environment

## Pre-requisite
* [Maven](https://maven.apache.org) (>=3.8.6)
* Git.
* Docker (optional, for installation of postgresql server).
* JDK 17 (optional since Eclipse is now bundle with JRE 17).

## Usage
* Clone or download to a folder.
* If you want to install and run postgresql docker container image, make sure your current login user has the necessary permission to run docker (https://www.baeldung.com/linux/docker-run-without-sudo).
* Run **autoload bashcompinit**
* Run **bashcompinit**
* Run **source completion.bash** to turn on auto completion for bundle shell scripts.
* Run **./setup.sh --help** to get help on options available.

Examples of usage:

    ./setup.sh --branch release-10 --docker-postgres-create --db-admin-pass <your-password>
    ./setup.sh --skip-setup-db


## What it does
* Clone idempiere source and run Maven build.
* Download and setup Eclipse JEE 2023-06.
* Create new workspace in the cloned idempiere folder and import all projects into the workspace.
* Set target platform and build the workspace.
* Setup connection properties (idempiere.properties) and jetty server (jettyhome).
* If DB doesn't exists yet, import iDempiere db. 
* If DB exists, apply migration scripts.
* You should have a ready to run Eclipse workspace after the completion of the script.

## Scripts
* Use **--help** option to get help in available options.
* **setup.sh** is the main entry point to invoke other scripts.
* **docker-postgres.sh** - script to install and run postgres 15.3 docker container image.
* **eclipse.sh** - script to start Eclipse IDE.
* **setup-db.sh** - script to setup DB connection propertis (idempiere.propertis), jetty server (jettyhome) and import iDempiere seed database (if DB does not exists) or apply migration scripts (if DB exists).
* **setup-ws.sh** - setup idempiere workspace, set target platform.
