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

cessda.pasc.reverse (reverse proxy used as part of the Certbot automated security sertificate renewal proces. Also provides authentication for components, as needed).

cessda.pasc.admin 9Spring Boot amin console. The logs are useful to check progress of harvesting).



## Getting Started

The various Jenkins jobs in the [DataCat](https://cit.cessda.eu/view/DataCat/) view are used to build, test and deploy the components. 
They are tricket automatically when code changes are commited to any of the Bitbucket repos listed above.

### Prerequisites

You need to set the values of various environment variables TODO list them.


### Installing

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

