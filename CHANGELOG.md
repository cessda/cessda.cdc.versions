# Changelog

All notable changes to the CESSDA Data Catalogue will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/) and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

*For each release, use the following sub-sections:*

- *Added (for new features)*  
- *Changed (for changes in existing functionality)*  
- *Deprecated (for soon-to-be removed features)*  
- *Removed (for now removed features)*  
- *Fixed (for any bug fixes)*  
- *Security (in case of vulnerabilities)*

## [Unreleased]

### Added

- (cessda.cdc.osmh-indexer.cmm) Harvest separate repositories in parallel ([#178](https://bitbucket.org/cessda/cessda.cdc.version2/issues/178))
- (cessda.cdc.osmh-indexer.cmm) Add new PROGEDO endpoint ([#177](https://bitbucket.org/cessda/cessda.cdc.version2/issues/177))
- (cessda.cdc.osmh-repository-handler.oai-pmh) Add new PROGEDO endpoint ([#177](https://bitbucket.org/cessda/cessda.cdc.version2/issues/177))
- (cessda.cdc.osmh-repository-handler.nesstar) Add new PROGEDO endpoint ([#177](https://bitbucket.org/cessda/cessda.cdc.version2/issues/177))
- (cessda.cdc.osmh-indexer.cmm/cessda.cdc.osmh-repository-handler.oai-pmh/cessda.cdc.osmh-repository-handler.nesstar) Add HTTP compression to the repository handlers ([#167](https://bitbucket.org/cessda/cessda.cdc.version2/issues/167/add-http-compression-to-the-repository))
- (cessda.cdc.deploy) Deployed Kibana ([#196](https://bitbucket.org/cessda/cessda.cdc.version2/issues/196/deploy-kibana))
- (cessda.cdc.osmh-indexer.cmm/cessda.cdc.osmh-repository-handler.nesstar) Added option to set a default language as part of the endpoint specification ([#192](https://bitbucket.org/cessda/cessda.cdc.version2/issues/192/add-option-to-set-default-language-as-part))

### Changed

- (cessda.cdc.osmh-indexer.cmm) Log statistics for created, deleted and updated studies. This is an enhancement of 8ef04dce87. ([#181](https://bitbucket.org/cessda/cessda.cdc.version2/issues/181))
- (cessda.cdc.osmh-repository-handler.nesstar) Updated NESSTAR repository handler to Spring Boot 2.3.1 ([#189](https://bitbucket.org/cessda/cessda.cdc.version2/issues/189/update-nesstar-repository-handler-to))
- (cessda.cdc.osmh-indexer.cmm) Add more details to 'Configured Repos' log output ([#195](https://bitbucket.org/cessda/cessda.cdc.version2/issues/195/add-more-details-to-configured-repos-log))
- (cessda.cdc.osmh-indexer.cmm) Updated Elasticsearch to 5.6 ([#188](https://bitbucket.org/cessda/cessda.cdc.version2/issues/188/update-elasticsearch-to-56))
- (cessda.cdc.admin) Updated Spring Boot Admin to 2.2.3 ([#191](https://bitbucket.org/cessda/cessda.cdc.version2/issues/191/update-spring-boot-admin-to-223))

### Fixed

- (cessda.cdc.osmh-repository-handler.oai-pmh) Disable access to external XML entities in the repository handlers ([#176](https://bitbucket.org/cessda/cessda.cdc.version2/issues/176))
- (cessda.cdc.osmh-repository-handler.nesstar) Disable access to external XML entities in the repository handlers ([#176](https://bitbucket.org/cessda/cessda.cdc.version2/issues/176))
- (cessda.cdc.osmh-indexer.cmm) Ensure daily harvest does not take place during GCP maintenance window ([#193](https://bitbucket.org/cessda/cessda.cdc.version2/issues/193/ensure-daily-harvest-does-not-take-place))
- (cessda.cdc.deploy) Use the correct liveness and readiness endpoints in Spring Boot 2.3 ([#194](Use the correct liveness and readiness endpoints in Spring Boot 2.3))

## [2.2.1] - 2020-05-04

Searchkit - [10.5281/zenodo.3786300](https://zenodo.org/record/3786300)

OSMH Consumer Indexer - [10.5281/zenodo.3786356](https://zenodo.org/record/3786356)

OSMH Handler Nesstar - [10.5281/zenodo.3786438](https://zenodo.org/record/3786438)

OSMH Handler OAI-PMH - [10.5281/zenodo.3786446](https://zenodo.org/record/3786446)

### Added

- French language index
- new GESIS endpoint ([#162](https://bitbucket.org/cessda/cessda.cdc.version2/issues/162))
- file appender
- format error log message for successful indexing
- implemented correlation id using MDC.putClosable
- correlation ID to the log messages
- dependency for JSON logging support (logstash-logback-encoder 5.2)

### Changed

- default results sorting order (from relevance to collection date descending) ([#163](https://bitbucket.org/cessda/cessda.cdc.version2/issues/163))
- various UI label changes ([#153](https://bitbucket.org/cessda/cessda.cdc.version2/issues/153))), ([#154](https://bitbucket.org/cessda/cessda.cdc.version2/issues/154))
- changed GESIS endpoint from HTTP to HTTPS ([#162](https://bitbucket.org/cessda/cessda.cdc.version2/issues/162))
- use Java Time APIs for the PerfRequestSyncInterceptor stopwatch
- increased test coverage
- updated SonarQube scanner to 3.7.0
- updated Spring Boot to 1.5.21
- unified timeout and SSL verification settings
- refined error log for unsuccessful indexing
- marked all utility classes as final
- close the Elasticsearch client on shutdown
- revised and re-ordered list of endpoints
- use Jib to containerise the indexer
- updated Maven wrapper to 0.5.3
- refactored the error handling code in DaoBase.postForStringResponse to better align with Java best practices
- refactored exception handling to avoid catching RuntimeException and a cast
- print the config in StatusService.printPaSCHandlerOaiPmhConfig() directly
- change behaviour when Study PID Agency is not specified. Before: '10.5279/DK-SA-DDA-868 (not available)'. After: '10.5279/DK-SA-DDA-868 (Agency not available)' ([#156](https://bitbucket.org/cessda/cessda.cdc.version2/issues/156))
- log queries at the info level
- moved recursion out of the try-with-resources block to reduce resource consumption
- reformatted the message when the record headers could not be parsed (because the parser could have failed at any point and left the InputStream is in an inconsistent state
- use input streams instead of strings (avoids a double copy)
- renamed 'dev' profile to *gcp*
- improved logging to help determine quality of harvested metadata ([#191](https://bitbucket.org/cessda/cessda.cdc.version2/issues/91))

### Deprecated

- N/A

### Removed

- Norwegian language index
- caches of RuntimeException in ESIngestService
- option to disable HTTPS verification
- unnecessary null check

### Fixed

- compiler warnings, as recommended by Error Prone
- time zone bugs
- logging pattern for the file logger
- unused micrometer dependencies
- unused DocumentBuilder bean
- issues reported by SonarQube
- test data to match changes made to the expected conditions ('not available' -> 'Agency not available')
- register DocumentBuilderFactories as beans instead of DocumentBuilders. DocumentBuilders are not thread safe and need resetting after use. DocumentBuilderFactory.createDocumentBuilder() is thread safe and should be used instead
- fixed logs not showing in Spring Boot Admin
- encoded the resumption token in case characters invalid for URIs are returned
- time zone bugs

### Security

- verify SSL
- removed the option to disable HTTPS verification
