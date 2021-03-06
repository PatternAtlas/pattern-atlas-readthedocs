#Development Setup


##Prerequisites

To run Pattern Atlas as a developer on your local system, you need the following:

* [Git](https://git-scm.com/downloads)
* [Docker](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/)
* [Maven](https://maven.apache.org/download.cgi)
* [Java JDK 1.8](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)
* [Yarn](https://yarnpkg.com/)
* [Node.js](https://nodejs.org/en/about/releases/)
* (optional for LaTeX rendering) [LaTeX-Renderer Installation](https://www.jetbrains.com/idea/)
* (recommended) [Intellij](https://github.com/UST-QuAntiL/latex-renderer)


Install Angular CLI:

``npm install -g @angular/cli``

Clone the repositories:

``git clone https://github.com/PatternAtlas/pattern-atlas-ui.git``
``git clone https://github.com/PatternAtlas/pattern-atlas-api.git``
``git clone https://github.com/PatternPedia/pattern-pedia-docker.git``


##Startup

###Database

To start the database execute:

``C:\PATH\pattern-atlas-docker> docker-compose up -d db``

To terminate the system execute:

``C:\PATH\pattern-atlas-docker> docker-compose down -v``

!!! info
   Database initialization is skipped? --> Make sure the previous processes are terminated with docker-compose down, otherwise postgres might skip the initialization.

###Frontend


Install all required packages with:

``C:\PATH\pattern-pedia> yarn install``

To start the frontend run:

``C:\PATH\pattern-pedia> yarn start``

###Backend


To package the application run:

``C:\PATH\pattern-pedia-api> mvn package -DskipTests``

To run the application execute:

``C:\PATH\pattern-pedia-api> mvn spring-boot:run``

###Database Initialization
On default, the initialized database image pulls data from our [public data repo](https://github.com/PatternAtlas/pattern-atlas-content).
If an ssh key named pattern-atlas-content-ssh_secret is located in the directory, the initialized-db image pulls data from the [private data repo](https://github.com/PatternAtlas/internal-pattern-atlas-content)
To obtain the ssh key, ask the dev team for it. Alternatively, you can generate a new pair of public/private ssh keys and add the public key as a deploy key to [internal-pattern-atlas-content/settings/keys](https://github.com/PatternAtlas/internal-pattern-atlas-content/settings/keys) The private key needs to be saved as pattern-atlas-content-ssh_secret in the directory of the docker-compose file.


!!! info
Database initialization is skipped? --> Make sure the previous processes are terminated with docker-compose down, otherwise postgres might skip the initialization.
