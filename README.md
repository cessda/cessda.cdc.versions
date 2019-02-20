# cessda.pasc.version2 

The CESSDA Data Catalogue harvests metadata from various endpoints. 
It uses different repository handlers to adapt the payload for each type of endpoint to a standard format (the Cessda Metadata Model, CMM). 

## Project Structure

It is made up of several components, which can be grouped as Data Gathering, User Facing and Management.

### Data Gathering components

The following source code repos are used to build the components:

cessda.pasc.osmh-indexer.cmm (harvester that periodically calls the repository handlers which build the Elasticsearch indicies). 

cessda.pasc.osmh-repository-handler.nesstar (repository handler for NESSTAR endpoints serving DDI 1.2).

cessda.pasc.osmh-repository-handler.oai-pmh (repository handler for NESSTAR endpoints serving DDI 2.5).


### User Facing components

The following source code repos are used to build the components:

cessda.pasc.searchkit (user interface).

cessda.pasc.elasticsearch (backend to user interface, provides search and browse functionality).



### Management components

The following source code repos are used to build the components:

cessda.pasc.reverse (reverse proxy used as part of the Certbot automated security certificate renewal proces. Also provides authentication for components, as needed).

cessda.pasc.admin 9Spring Boot amin console. The logs are useful to check progress of harvesting).


## Getting Started

The various Jenkins jobs in the [DataCat](https://cit.cessda.eu/view/DataCat/) view are used to build, test and deploy the components. 
They are triggered automatically when code changes are commited to any of the Bitbucket repos listed above.


### Common tasks

Reharvesting outside of scheduled harvesting periods - just run the Jenkins job [cessda.pasc.osmh-indexer.cmm](https://cit.cessda.eu/job/cessda.pasc.osmh-indexer.cmm/) 
for the branch or branches you want to updated.

Check language indexes have been created - look at the [storage bucket](https://console.cloud.google.com/storage/browser/cessda-pasc-es-dev/indices/?project=cessda-development) for a given branch.

Make sure the harvesters (dev, staging, live) are not run in parallel against the endpoints, as some of them will time out under the load, and not deliver all the available metadata. 
Set the harvesting times via the [application.yml](https://bitbucket.org/cessda/cessda.pasc.osmh-indexer.cmm/src/master/src/main/resources/application.yml) file for each branch.

Adjust the read timeout, as required, via the [application.yml](https://bitbucket.org/cessda/cessda.pasc.osmh-indexer.cmm/src/master/src/main/resources/application.yml) file for each branch. 
Update the cessda.pasc.osmh-indexer.cmm README files for each branch after making changes.

To add endpoint/update URL of existing endpoint, edit the following files (for each branch):

[harvester configuration](https://bitbucket.org/cessda/cessda.pasc.osmh-indexer.cmm/src/develop/src/main/resources/application.yml), 

[harvester tests](https://bitbucket.org/cessda/cessda.pasc.osmh-indexer.cmm/src/develop/src/test/java/eu/cessda/pasc/oci/repository/PascHarvesterDaoTest.java). 

Depending on the repository type, you also need to edit EITHER:

[oai-pmh repository handler configuration](https://bitbucket.org/cessda/cessda.pasc.osmh-repository-handler.oai-pmh/src/development/src/main/resources/application.yml), 

and [oai-pmh repository handler tests](https://bitbucket.org/cessda/cessda.pasc.osmh-repository-handler.oai-pmh/src/development/src/test/java/eu/cessda/pasc/osmhhandler/oaipmh/configuration/HandlerConfigurationPropertiesTest.java). 

OR:

[NESSTAR repository handler configuration](https://bitbucket.org/cessda/cessda.pasc.osmh-repository-handler.nesstar/src/development/src/main/resources/application.yml), 

and [NESSTAR repository handler tests](https://bitbucket.org/cessda/cessda.pasc.osmh-repository-handler.nesstar/src/development/src/test/java/eu/cessda/pasc/osmhhandler/nesstar/configuration/HandlerConfigurationPropertiesTest.java). 


To add language, create a new file (for each branch) in: 
[Harvester mappings directory](https://bitbucket.org/cessda/cessda.pasc.osmh-indexer.cmm/src/develop/src/main/resources/elasticsearch/mappings/), 

[Harvester settings directory](https://bitbucket.org/cessda/cessda.pasc.osmh-indexer.cmm/src/develop/src/main/resources/elasticsearch/settings/), 

[Searchkit locales directory](https://bitbucket.org/cessda/cessda.pasc.searchkit/src/master/src/locales/) 

and edit following files so lists of languages match:

[application.yaml](https://bitbucket.org/cessda/cessda.pasc.osmh-indexer.cmm/src/develop/src/main/resources/application.yaml).

[LanguageDocumentExtractorTest.java](https://bitbucket.org/cessda/cessda.pasc.osmh-indexer.cmm/src/develop/src/test/java/eu/cessda/pasc/oci/service/helpers/LanguageDocumentExtractorTest.java).

[Searchkit language.js](https://bitbucket.org/cessda/cessda.pasc.searchkit/src/dev/src/utilities/language.js) 


If you cannot see a component in the [Springboot Admin GUI for dev](https://datacatalogue-dev.cessda.eu/admin/#/) or [Springboot Admin GUI for staging](https://datacatalogue-staging.cessda.eu/admin/#/) or [Springboot Admin GUI for production](https://datacatalogue.cessda.eu/admin/#/),  
then reploy the missing component (cessda.pasc.osmh-indexer.cmm, cessda.pasc.osmh-repository-handler.nesstar or cessda.pasc.osmh-repository-handler.oai-pmh) for that branch via Jenkins, 
so it can register with Springboot Admin. Make sure that the Docker file has the "-Dspring.profiles.active" flag set to the correct profile name (dev, staging or live) otherwise the component will not register.

## Prerequisites

You need to set the values of various environment variables TODO list them.


## Installing

The Jenkinsfile defines the build, test and deployment pipeline for each branch of each component.


## Running the tests
 
The Jenkinsfile defines the test process for each branch of each component.

The selenium directory contains the tests for each branch of each component.


## Deployment

The Jenkinsfile defines the deployment process.


## Built With

The Jenkinsfile defines the build process.

## Contributing

Please read [CESSDA Guideline for developers](https://bitbucket.org/cessda/cessda.guidelines.cit/wiki/Developers) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

See [Semantic Versioning](https://semver.org/) for guidance.

## Contributors

You can find the list of contributors in the CONTRIBUTORS.md file for each component repository.

## License

See the LICENSE file in each component repository.

## Acknowledgments

None at present.

