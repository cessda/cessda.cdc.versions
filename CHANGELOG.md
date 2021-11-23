# Changelog

All notable changes to the CESSDA Data Catalogue will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/) and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

N.B. From v2.4.0 onwards, only the changes that directly affect the User Experience are recorded here.
For details of all the changes, see the linked CHANGELOGS of the various components. 

## [2.4.0] - 2021-06-23

### Changed

- Autocomplete of the search terms is enabled in the Title, Abstract, Country, Keyword and Topic fields. As an example, using ‘Nurs’ as the search term finds 'nurses', 'nurse', 'nursing', 'nursed' etc.
- The default operator between search terms is AND. Therefore all the entered search terms will be present in each of the results returned by a simple multi-term search.
- The NOT search operator is enabled. See the Advanced Search section of the User Guide for details of AND, OR, NOT and other search operations.
- The Data Catalogue now displays a version number. See the About section.
- There is a separate button for the User Guide to make it easier to find.
- The User Guide has been updated to correspond to this version of the Data Catalogue, and some new examples/tips are included.
- The User Guide has a version number, to show which version of the Data Catalogue it is for.

### CHANGELOGS of the components

- [aggregator.client CHANGELOG](https://bitbucket.org/cessda/cessda.cdc.aggregator.client/src/main/CHANGELOG.md)
- [aggregator.doc-store CHANGELOG](https://bitbucket.org/cessda/cessda.cdc.aggregator.doc-store/src/main/CHANGELOG.md)
- [aggregator.oai-pmh-repo-handler CHANGELOG](https://bitbucket.org/cessda/cessda.cdc.aggregator.oai-pmh-repo-handler/src/main/CHANGELOG.md)
- [aggregator.shared-library CHANGELOG](https://bitbucket.org/cessda/cessda.cdc.aggregator.shared-library/src/master/CHANGELOG.md)
- [osmh-indexer.cmm CHANGELOG](https://bitbucket.org/cessda/cessda.cdc.osmh-indexer.cmm/src/master/CHANGELOG.md)
- [searchkit CHANGELOG](https://bitbucket.org/cessda/cessda.cdc.searchkit/src/master/CHANGELOG.md)
- [cmv.console CHANGELOG](https://bitbucket.org/cessda/cessda.cmv.console/src/master/CHANGELOG.md)
- [metadata.harvester CHANGELOG](https://bitbucket.org/cessda/cessda.eqb.metadata.harvester/src/master/CHANGELOG.md)


## [2.3.0] - 2021-02-09

### Added

- (cessda.cdc.osmh-indexer.cmm) Boost specific keywords ([#131](https://bitbucket.org/cessda/cessda.cdc.version2/issues/131))
- (cessda.cdc.osmh-indexer.cmm) Set the study url field from any language before replacing it with the language specific element ([#142](https://bitbucket.org/cessda/cessda.cdc.version2/issues/142))
- (cessda.cdc.osmh-indexer.cmm) Modify Harvester to output required logs for structured logging ([#159](https://bitbucket.org/cessda/cessda.cdc.version2/issues/159))
- (cessda.cdc.searchkit/cessda.cdc.osmh-indexer.cmm/cessda.cdc.osmh-repository-handler.nesstar) Remove (not available) if no PID agency ([#156](https://bitbucket.org/cessda/cessda.cdc.version2/issues/156))
- (cessda.cdc.osmh-indexer.cmm/cessda.cdc.osmh-repository-handler.oai-pmh/cessda.cdc.osmh-repository-handler.nesstar) Add HTTP compression to the repository handlers ([#167](https://bitbucket.org/cessda/cessda.cdc.version2/issues/167))
- (cessda.cdc.osmh-indexer.cmm/cessda.cdc.osmh-repository-handler.oai-pmh/cessda.cdc.osmh-repository-handler.nesstar) Add new PROGEDO endpoint ([#177](https://bitbucket.org/cessda/cessda.cdc.version2/issues/177))
- (cessda.cdc.osmh-indexer.cmm) Harvest separate repositories in parallel ([#178](https://bitbucket.org/cessda/cessda.cdc.version2/issues/178))
- (cessda.cdc.osmh-indexer.cmm/cessda.cdc.osmh-repository-handler.nesstar) Added option to set a default language as part of the endpoint specification ([#192](https://bitbucket.org/cessda/cessda.cdc.version2/issues/192))
- (cessda.cdc.deploy) Deployed Kibana ([#196](https://bitbucket.org/cessda/cessda.cdc.version2/issues/196))
- (cessda.cdc.osmh-indexer.cmm) Add ADP Kuha2 Endpoint ([#201](https://bitbucket.org/cessda/cessda.cdc.version2/issues/201))
- (cessda.cdc.osmh-indexer.cmm) Add stopwords for Hungarian and Portuguese language analysers ([#204](https://bitbucket.org/cessda/cessda.cdc.version2/issues/204))
- (cessda.cdc.osmh-indexer.cmm/cessda.cdc.searchkit) Delete inactive records ([#217](https://bitbucket.org/cessda/cessda.cdc.version2/issues/217))
- (cessda.cdc.searchkit) Boost titleStudy, abstract, creators and keywords.properties at query time ([#224](https://bitbucket.org/cessda/cessda.cdc.version2/issues/224))

### Changed

- (cessda.cdc.osmh-indexer.cmm) Log statistics for created, deleted and updated studies. This is an enhancement of 8ef04dce87. ([#181](https://bitbucket.org/cessda/cessda.cdc.version2/issues/181))
- (cessda.cdc.osmh-indexer.cmm) Updated Elasticsearch to 5.6 ([#188](https://bitbucket.org/cessda/cessda.cdc.version2/issues/188))
- (cessda.cdc.osmh-repository-handler.nesstar) Updated NESSTAR repository handler to Spring Boot 2.3.1 ([#189](https://bitbucket.org/cessda/cessda.cdc.version2/issues/189))
- (cessda.cdc.admin) Updated Spring Boot Admin to 2.2.3 ([#191](https://bitbucket.org/cessda/cessda.cdc.version2/issues/191))
- (cessda.cdc.osmh-indexer.cmm) Add more details to 'Configured Repos' log output ([#194](https://bitbucket.org/cessda/cessda.cdc.version2/issues/194))
- (cessda.cdc.osmh-indexer.cmm) Add more details to 'Configured Repos' log output ([#195](https://bitbucket.org/cessda/cessda.cdc.version2/issues/195))
- (cessda.cdc.osmh-indexer.cmm) Change SODA publisher name ([#197](https://bitbucket.org/cessda/cessda.cdc.version2/issues/197))
- (cessda.cdc.osmh-indexer.cmm) Update SND set spec ([#200](https://bitbucket.org/cessda/cessda.cdc.version2/issues/200))
- (cessda.cdc.osmh-indexer.cmm) Ignore deleted headers ([#206](https://bitbucket.org/cessda/cessda.cdc.version2/issues/206))
- (cessda.cdc.osmh-indexer.cmm/cessda.cdc.osmh-repository-handler.nesstar) Improve NESSTAR logging ([#207](https://bitbucket.org/cessda/cessda.cdc.version2/issues/207))

## Removed

- (cessda.cdc.searchkit) Convert the interface language to English only ([#164](https://bitbucket.org/cessda/cessda.cdc.version2/issues/164))
- (cessda.cdc.searchkit) Remove the Elasticsearch proxy ([#237](https://bitbucket.org/cessda/cessda.cdc.version2/issues/237))

### Fixed

- (cessda.cdc.osmh-indexer.cmm) Fix alphabetical sorting producing unexpected results with lowercase characters ([#171](https://bitbucket.org/cessda/cessda.cdc.version2/issues/171))
- (cessda.cdc.osmh-repository-handler.oai-pmh) Disable access to external XML entities in the repository handlers ([#176](https://bitbucket.org/cessda/cessda.cdc.version2/issues/176))
- (cessda.cdc.osmh-indexer.cmm) Fix rejection reason not showing in the logs ([#184](https://bitbucket.org/cessda/cessda.cdc.version2/issues/184))
- (cessda.cdc.osmh-indexer.cmm) Ensure daily harvest does not take place during GCP maintenance window ([#193](https://bitbucket.org/cessda/cessda.cdc.version2/issues/193))
- (cessda.cdc.deploy) Use the correct liveness and readiness endpoints in Spring Boot 2.3 ([#194](https://bitbucket.org/cessda/cessda.cdc.version2/issues/194))
- (cessda.cdc.osmh-indexer.cmm) Fix title ascending/descending sort options not working ([#209](https://bitbucket.org/cessda/cessda.cdc.version2/issues/209))
- (cessda.cdc.osmh-indexer.cmm) Fix being unable to run the harvester via Spring Boot Admin JMX ([#211](https://bitbucket.org/cessda/cessda.cdc.version2/issues/211))
- (cessda.cdc.searchkit) Fix translations not being applied to the sorting selector ([#215](https://bitbucket.org/cessda/cessda.cdc.version2/issues/215))

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
- renamed `dev` profile to `gcp`
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
