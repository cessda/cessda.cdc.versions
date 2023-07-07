# CESSDA Data Catalogue

The CESSDA Data Catalogue (CDC) can harvest any XML content provided by an OAI-PMH endpoint. It uses different sets of XPath mappings to adapt the different flavours of the XML payloads to a standard format, namely the [CESSDA Metadata Model](https://doi.org/10.5281/zenodo.4751455).

The CESSDA Metadata Validator (CMV) is part of the pipeline, and is used to perform bulk checks on the harvested files. Additional checks are also run (XML Schema validation on DDI 2.5 metadata files) and the validated files are saved to a Google Cloud storage bucket. Note that files are validated in the following sequence: XML Schema; CMV.

The results of the validation checks are sent to an ElasticSearch index that feeds a Kibana dashboard. The dashboard shows both summary and detailed information regarding violations (non-conformance with the CDC DDI profiles) and XML Schema validations. The Aggregator component loads the validated files into its storage component and makes them available for aggregators such as OpenAIRE, B2Find and GoTriple to harvest.  

## Project Structure

The CDC product is made up of several components, which can be grouped as Data Gathering, User Facing, Public API and Management. There are also some repositories which are concerned with Documentation & Issue Tracking and QA & Deployment respectively.

### Data Gathering components

The following *Open Source* code repositories are used to gather and index metadata:

- [cessda.metadata.harvester](https://github.com/cessda/cessda.metadata.harvester) (periodically harvests the configured endpoints).
- [cessda.cdc.osmh-indexer.cmm](https://github.com/cessda/cessda.cdc.osmh-indexer.cmm) (runs after the harvester has finished to update the Elasticsearch indicies).

### User Facing components

The following *Open Source* code repository is used to provide the user facing components:

- [cessda.cdc.searchkit](https://github.com/cessda/cessda.cdc.searchkit) (user interface).

### Public API components

The following components are part of the Aggregator (an OAI-PMH endpoint for the CDC):

- [cessda.cdc.aggregator.client](https://github.com/cessda/cessda.cdc.aggregator.client) (Command line client for synchronizing records to CESSDA CDC Aggregator DocStore).
- [cessda.cdc.aggregator.doc-store](https://github.com/cessda/cessda.cdc.aggregator.doc-store) (HTTP server providing an API in front of a MongoDB cluster).
- [cessda.cdc.aggregator.oai-pmh-repo-handler](https://github.com/cessda/cessda.cdc.aggregator.oai-pmh-repo-handler) (HTTP server providing an OAI-PMH aggregator endpoint serving DocStore records).
- [cessda.cdc.aggregator.shared-library](https://github.com/cessda/cessda.cdc.aggregator.shared-library) (Python library containing shared code for the CDC Aggregator).

### Management components

The following private source code repositories are used to build and deploy the management components:

- cessda.cdc.aggregator.deploy (deploys the CDC Aggregator components).
- cessda.cdc.reverse (reverse proxy used as part of the Certbot automated security certificate renewal process. Also provides authentication for components, as needed).
- cessda.cdc.sitemapgenerator (generates a sitemap for use by [Google Data Search](https://toolbox.google.com/datasetsearch) crawler).

The following public source code repository applies validation to the harvested metadata records:

- cessda.cmv.console (command line application of the CESSDA Metadata Validator).

### Documentation & Issue Tracking

The following private source code repositories are used to build the documentation components:

- cessda.cdc.userguide (source files in Markdown which are compiled to static html using Jekyll with the Just the docs theme).
- cessda.cdc.versions (contains an issue tracker used internally to record the backlog).

### QA & Deployment

The following private source code repositories are used to test and deploy the product's components:

- cessda.cdc.deploy (contains all the scripts and infrastructure definitions needed to deploy the product).
- cessda.cdc.test (contains test scripts used to QA the product during the deployment process).

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

Please read the [CESSDA Software Development Guidelines](https://docs.tech.cessda.eu/software/ta-sw-dev-guide.html) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

See [Semantic Versioning](https://semver.org/) for guidance.

## Contributors

You can find the list of contributors in the `CONTRIBUTORS.md` file for each component repository.

## License

See the [LICENSE](LICENSE.txt) file for each component repository.

## FAQs

See the [FAQ](FAQ.md) file.

## Acknowledgments

None at present.
