#Quickstart

##Prerequisites


* [Git](https://git-scm.com/downloads)
* [Docker](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/)

Clone the repository:

``git clone https://github.com/PatternPedia/pattern-pedia-docker.git``

##Run the pattern repository

To start up the system, run the following command:

``docker-compose up -d``

Afterwards, the pattern repository is running on http://localhost:4200 and is displaying demo data

To terminate the system, run the following command:

``docker-compose down -v``


##Overview

The following components are included in the docker-compose setup

| Pattern Atlas Component | URL | GitHub | Docker Hub |
|:------------------- |:--- |:------ |:---------- |
| Pattern-Atlas-DB | <http://localhost:5432> | [Link](https://www.github.com/PatternAtlas/initialized-pattern-atlas-db) | [Link](https://hub.docker.com/r/patternpedia/initialized-pattern-atlas-db) |
| Pattern-Atlas-Api | <http://localhost:8080/patternpedia> | [Link](https://github.com/PatternAtlas/pattern-atlas-api) | [Link](https://hub.docker.com/r/patternpedia/patternrepo-api) |
| Pattern-Atlas-UI | <http://localhost:4200> | [Link](https://github.com/PatternAtlas/pattern-atlas-ui) | [Link](https://hub.docker.com/r/patternpedia/patternrepo-ui) |


##Initialize the db on startup

On default, the initialized database image pulls data from our [public data repo](https://github.com/PatternAtlas/pattern-atlas-content).
If an ssh key named pattern-atlas-content-ssh_secret is located in the directory, the initialized-db image pulls data from the [private data repo](https://github.com/PatternAtlas/internal-pattern-atlas-content)
To obtain the ssh key, ask the dev team for it. Alternatively, you can generate a new pair of public/private ssh keys and add the public key as a deploy key to [internal-pattern-atlas-content/settings/keys](https://github.com/PatternAtlas/internal-pattern-atlas-content/settings/keys) The private key needs to be saved as pattern-atlas-content-ssh_secret in the directory of the docker-compose file.


!!! info
    Database initialization is skipped? --> Make sure the previous processes are terminated with docker-compose down, otherwise postgres might skip the initialization.
