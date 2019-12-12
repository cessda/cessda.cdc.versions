# CESSDA Data Catalogue v2.2.0

The CESSDA Data Catalogue (CDC) harvests metadata from various endpoints.
It uses different repository handlers to adapt the payload for each type of endpoint to a standard format (the [CESSDA Metadata Model](https://doi.org/10.5281/zenodo.3236171), CMM).

## Project Structure

The CDC product is made up of several components, which can be grouped as Data Gathering, User Facing and Management. There are also some repositories which are concerned with Documentation & Issue Tracking and QA & Deployment respectively.

### Data Gathering components

The following *Open Source* code repositories are used to build the harvester components:

- [cessda.cdc.osmh-indexer.cmm](https://bitbucket.org/cessda/cessda.cdc.osmh-indexer.cmm) (harvester that periodically calls the repository handlers which build the Elasticsearch indicies).
- [cessda.cdc.osmh-repository-handler.nesstar](https://bitbucket.org/cessda/cessda.cdc.osmh-repository-handler.nesstar) (repository handler for OAI-PMH enabled NESSTAR endpoints serving DDI 1.2).
- [cessda.cdc.osmh-repository-handler.oai-pmh](https://bitbucket.org/cessda/cessda.cdc.osmh-repository-handler.oai-pmh) (repository handler for OAI-PMH endpoints serving DDI 2.5).

### User Facing components

The following *Open Source* code repository is used to build the user facing components:

- [cessda.cdc.searchkit](https://bitbucket.org/cessda/cessda.cdc.searchkit) (user interface).


### Management components

The following private source code repositories are used to build the management components:

- cessda.cdc.admin (Spring Boot admin console, the logs are useful to check progress of harvesting).
- cessda.cdc.deploy/elasticsearch (backend to user interface, provides search and browse functionality).
- cessda.cdc.deploy/mailrelay (used for sending messages relating to the health and status of the product to the DevOps team).
- cessda.cdc.reverse (reverse proxy used as part of the Certbot automated security certificate renewal process. Also provides authentication for components, as needed).
- cessda.cdc.sitemapgenerator (generates a sitemap for use by [Google Data Search](https://toolbox.google.com/datasetsearch) crawler).

### Documentation & Issue Tracking

The following private source code repositories are used to build the documentation components:
- cessda.cdc.userguide (source files in reStructuredText markup language that are converted via Sphinx to ReadTheDocs format).
- cessda.cdc.version2 (contains an issue tracker used internally to record the backlog).

### QA & Deployment

The following private source code repositories are used to test and deploy the product's components:

- cessda.cdc.deploy (contains all the scripts and infrastructure definitions needed to deploy the product).
- cessda.cdc.test (contains test scripts used to QA the product during the deployment process).
- cessda.cmm.profile (contains and XSD file that can be used to check that the XML provided by an endpoint is compliant with the CMM profile).

## Developer documentation

See [CDC Developer documentation](DEVELOPER_DOCUMENTATION.md) for details.

## Operations documentation

See [CDC Operations documentation](OPERATIONS_DOCUMENTATION.md) for details.

## User documentation

See [CDC User guide](https://datacatalogue.cessda.eu/documentation/) for details.

## Installing

The Jenkinsfile in each of the Data Gathering and User Facing component repositories defines the build pipeline for that component. See also the **'README.md'** file in each of those repositories.

## Running the tests

See the **'QA and Deployment'** section, above.

## Deployment

See the **'QA and Deployment'** section, above.

## Built With

The Jenkinsfile in each of the Data Gathering and User Facing component repositories defines the build pipeline for that component. See also the **'README.md'** file in each of those repositories.

## Contributing

Please read [CESSDA Guideline for developers](https://bitbucket.org/cessda/cessda.guidelines.cit/wiki/Developers) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

See [Semantic Versioning](https://semver.org/) for guidance.

## Contributors

You can find the list of contributors in the `CONTRIBUTORS.md` file for each component repository.

## License

See the [LICENSE](LICENSE) file for each component repository.

## FAQs

See the [FAQ](FAQ.md) file.

## Acknowledgments

None at present.
