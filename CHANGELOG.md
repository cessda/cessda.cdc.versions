# Changelog

All notable changes to the CESSDA Data Catalogue will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/) and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

N.B. From v2.4.0 onwards, only the changes that directly affect the User Experience are recorded here.
For details of all the changes, see the linked CHANGELOGS of the various components.

## CHANGELOGS of the components

- [aggregator.client CHANGELOG](https://github.com/cessda/cessda.cdc.aggregator.client/blob/main/CHANGELOG.md)
- [aggregator.doc-store CHANGELOG](https://github.com/cessda/cessda.cdc.aggregator.doc-store/blob/main/CHANGELOG.md)
- [aggregator.oai-pmh-repo-handler CHANGELOG](https://github.com/cessda/cessda.cdc.aggregator.oai-pmh-repo-handler/blob/main/CHANGELOG.md)
- [aggregator.shared-library CHANGELOG](https://github.com/cessda/cessda.cdc.aggregator.shared-library/blob/main/CHANGELOG.md)
- [osmh-indexer.cmm CHANGELOG](https://github.com/cessda/cessda.cdc.osmh-indexer.cmm/blob/main/CHANGELOG.md)
- [searchkit CHANGELOG](https://github.com/cessda/cessda.cdc.searchkit/blob/main/CHANGELOG.md)
- [cmv.console CHANGELOG](https://github.com/cessda/cessda.cmv.console/blob/main/CHANGELOG.md)
- [metadata.harvester CHANGELOG](https://github.com/cessda/cessda.eqb.metadata.harvester/blob/main/CHANGELOG.md)

## [3.5.0] - 2024-01-30

### Added

- Added a link to access the data of the study
- Added randomly chosen keywords below each result in the results list
- Implemented CDC to ELSST integration
- Modified ELSST link if it contains known prefix to add *clang* parameter

### Changed

- Use a normalised field for the "Topic and Keywords" filter
- Shortened the abstract in the results list
- Adjusted responsive placement of buttons on results in the results page
- Check that keywords exist for result before adding an element for them

### Fixed

- Fixed Panel elements incorrectly collapsing when a space character is entered
- Fixed text overflow and underflow issues

## [3.4.1] - 2023-09-26

### Changed

- No user-facing changes.

## [3.4.0] - 2023-08-29

### Changed

- A keyword filter function has been added.
- Topics and keywords have been moved higher up in the detailed study view.
- The display of countries have been changed from list to comma-separated.
- The ‘Send feedback’ button has been made more visible.
- The feedback form has been restyled.
- Some accessibility improvements have been made.

## [3.3.0] - 2023-06-13

### Changed

- No user-facing changes.

## [3.2.1] - 2023-03-23

### Changed

- No user-facing changes.

## [3.2.0] - 2022-12-08

### Changed

- Added Universe and Related publications fields to study details page.
- Made the search filters "float", keeping them onscreen when the search page is scrolled.

## [3.1.1] - 2022-11-08

### Changed

- No user-facing changes.

## [3.1.0] - 2022-09-22

### Changed

- Switched from JIRA to EOSC Helpdesk for capturing end-user issues.

## [3.0.3] - 2022-09-13

### Changed

- No user-facing changes.

## [3.0.2] - 2022-09-06

### Changed

- Fixed the search not returning expected results by restricting the search operators that can be used.

## [3.0.0] - 2022-06-07

### Changed

- Changed the order of the buttons on the right hand side of the menu bar.
- Added a button to take the user to the Search API documentation.
- Add the current language to the request URL in the User Interface.
- Record identifiers used in the OAI-PMH compliant endpoint are unified with those in the User Interface.
- Trimmed abstracts over a fixed number of characters on the search results page.
  
## [2.5.0] - 2021-11-23

### Changed

- Change the text in the browser page tab, depending on the current study or search query.
- Add sorting options for filtering studies by date published.
- Add Czech language support.
- Sort by the collection end date, rather than the collection start date.
- Only show the available date fields on the Detail page.
- Filter out PID objects that are missing a persistent identifier, fixing cases where the Agency would be displayed on its own.

## [2.4.0] - 2021-06-23

### Changed

- Autocomplete of the search terms is enabled in the Title, Abstract, Country, Keyword and Topic fields. As an example, using ‘Nurs’ as the search term finds 'nurses', 'nurse', 'nursing', 'nursed' etc.
- The default operator between search terms is AND. Therefore all the entered search terms will be present in each of the results returned by a simple multi-term search.
- The NOT search operator is enabled. See the Advanced Search section of the User Guide for details of AND, OR, NOT and other search operations.
- The Data Catalogue now displays a version number. See the About section.
- There is a separate button for the User Guide to make it easier to find.
- The User Guide has a version number, to show which version of the Data Catalogue it is for.

## [2.3.0] - 2021-02-09

### Added

- (cessda.cdc.osmh-indexer.cmm) Boost specific keywords ([#131](https://github.com/cessda/cessda.cdc.versions/issues/131))
- (cessda.cdc.osmh-indexer.cmm) Set the study url field from any language before replacing it with the language specific element ([#142](https://github.com/cessda/cessda.cdc.versions/issues/142))
- (cessda.cdc.osmh-indexer.cmm) Modify Harvester to output required logs for structured logging ([#159](https://github.com/cessda/cessda.cdc.versions/issues/159))
- (cessda.cdc.searchkit/cessda.cdc.osmh-indexer.cmm/cessda.cdc.osmh-repository-handler.nesstar) Remove (not available) if no PID agency ([#156](https://github.com/cessda/cessda.cdc.versions/issues/156))
- (cessda.cdc.osmh-indexer.cmm/cessda.cdc.osmh-repository-handler.oai-pmh/cessda.cdc.osmh-repository-handler.nesstar) Add HTTP compression to the repository handlers ([#167](https://github.com/cessda/cessda.cdc.versions/issues/167))
- (cessda.cdc.osmh-indexer.cmm/cessda.cdc.osmh-repository-handler.oai-pmh/cessda.cdc.osmh-repository-handler.nesstar) Add new PROGEDO endpoint ([#177](https://github.com/cessda/cessda.cdc.versions/issues/177))
- (cessda.cdc.osmh-indexer.cmm) Harvest separate repositories in parallel ([#178](https://github.com/cessda/cessda.cdc.versions/issues/178))
- (cessda.cdc.osmh-indexer.cmm/cessda.cdc.osmh-repository-handler.nesstar) Added option to set a default language as part of the endpoint specification ([#192](https://github.com/cessda/cessda.cdc.versions/issues/192))
- (cessda.cdc.deploy) Deployed Kibana ([#196](https://github.com/cessda/cessda.cdc.versions/issues/196))
- (cessda.cdc.osmh-indexer.cmm) Add ADP Kuha2 Endpoint ([#201](https://github.com/cessda/cessda.cdc.versions/issues/201))
- (cessda.cdc.osmh-indexer.cmm) Add stopwords for Hungarian and Portuguese language analysers ([#204](https://github.com/cessda/cessda.cdc.versions/issues/204))
- (cessda.cdc.osmh-indexer.cmm/cessda.cdc.searchkit) Delete inactive records ([#217](https://github.com/cessda/cessda.cdc.versions/issues/217))
- (cessda.cdc.searchkit) Boost titleStudy, abstract, creators and keywords.properties at query time ([#224](https://github.com/cessda/cessda.cdc.versions/issues/224))

### Changed

- (cessda.cdc.osmh-indexer.cmm) Log statistics for created, deleted and updated studies. This is an enhancement of 8ef04dce87. ([#181](https://github.com/cessda/cessda.cdc.versions/issues/181))
- (cessda.cdc.osmh-indexer.cmm) Updated Elasticsearch to 5.6 ([#188](https://github.com/cessda/cessda.cdc.versions/issues/188))
- (cessda.cdc.osmh-repository-handler.nesstar) Updated NESSTAR repository handler to Spring Boot 2.3.1 ([#189](https://github.com/cessda/cessda.cdc.versions/issues/189))
- (cessda.cdc.admin) Updated Spring Boot Admin to 2.2.3 ([#191](https://github.com/cessda/cessda.cdc.versions/issues/191))
- (cessda.cdc.osmh-indexer.cmm) Add more details to 'Configured Repos' log output ([#194](https://github.com/cessda/cessda.cdc.versions/issues/194))
- (cessda.cdc.osmh-indexer.cmm) Add more details to 'Configured Repos' log output ([#195](https://github.com/cessda/cessda.cdc.versions/issues/195))
- (cessda.cdc.osmh-indexer.cmm) Change SODA publisher name ([#197](https://github.com/cessda/cessda.cdc.versions/issues/197))
- (cessda.cdc.osmh-indexer.cmm) Update SND set spec ([#200](https://github.com/cessda/cessda.cdc.versions/issues/200))
- (cessda.cdc.osmh-indexer.cmm) Ignore deleted headers ([#206](https://github.com/cessda/cessda.cdc.versions/issues/206))
- (cessda.cdc.osmh-indexer.cmm/cessda.cdc.osmh-repository-handler.nesstar) Improve NESSTAR logging ([#207](https://github.com/cessda/cessda.cdc.versions/issues/207))

## Removed

- (cessda.cdc.searchkit) Convert the interface language to English only ([#164](https://github.com/cessda/cessda.cdc.versions/issues/164))
- (cessda.cdc.searchkit) Remove the Elasticsearch proxy ([#237](https://github.com/cessda/cessda.cdc.versions/issues/237))

### Fixed

- (cessda.cdc.osmh-indexer.cmm) Fix alphabetical sorting producing unexpected results with lowercase characters ([#171](https://github.com/cessda/cessda.cdc.versions/issues/171))
- (cessda.cdc.osmh-repository-handler.oai-pmh) Disable access to external XML entities in the repository handlers ([#176](https://github.com/cessda/cessda.cdc.versions/issues/176))
- (cessda.cdc.osmh-indexer.cmm) Fix rejection reason not showing in the logs ([#184](https://github.com/cessda/cessda.cdc.versions/issues/184))
- (cessda.cdc.osmh-indexer.cmm) Ensure daily harvest does not take place during GCP maintenance window ([#193](https://github.com/cessda/cessda.cdc.versions/issues/193))
- (cessda.cdc.deploy) Use the correct liveness and readiness endpoints in Spring Boot 2.3 ([#194](https://github.com/cessda/cessda.cdc.versions/issues/194))
- (cessda.cdc.osmh-indexer.cmm) Fix title ascending/descending sort options not working ([#209](https://github.com/cessda/cessda.cdc.versions/issues/209))
- (cessda.cdc.osmh-indexer.cmm) Fix being unable to run the harvester via Spring Boot Admin JMX ([#211](https://github.com/cessda/cessda.cdc.versions/issues/211))
- (cessda.cdc.searchkit) Fix translations not being applied to the sorting selector ([#215](https://github.com/cessda/cessda.cdc.versions/issues/215))

## [2.2.1] - 2020-05-04

### Added

- French language index
- new GESIS endpoint ([#162](https://github.com/cessda/cessda.cdc.versions/issues/162))
- file appender
- format error log message for successful indexing
- implemented correlation id using MDC.putClosable
- correlation ID to the log messages
- dependency for JSON logging support (logstash-logback-encoder 5.2)

### Changed

- default results sorting order (from relevance to collection date descending) ([#163](https://github.com/cessda/cessda.cdc.versions/issues/163))
- various UI label changes ([#153](https://github.com/cessda/cessda.cdc.versions/issues/153))), ([#154](https://github.com/cessda/cessda.cdc.versions/issues/154))
- changed GESIS endpoint from HTTP to HTTPS ([#162](https://github.com/cessda/cessda.cdc.versions/issues/162))
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
- change behaviour when Study PID Agency is not specified. Before: '10.5279/DK-SA-DDA-868 (not available)'. After: '10.5279/DK-SA-DDA-868 (Agency not available)' ([#156](https://github.com/cessda/cessda.cdc.versions/issues/156))
- log queries at the info level
- moved recursion out of the try-with-resources block to reduce resource consumption
- reformatted the message when the record headers could not be parsed (because the parser could have failed at any point and left the InputStream is in an inconsistent state
- use input streams instead of strings (avoids a double copy)
- renamed `dev` profile to `gcp`
- improved logging to help determine quality of harvested metadata ([#191](https://github.com/cessda/cessda.cdc.versions/issues/91))

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
