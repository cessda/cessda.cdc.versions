# Developer Documentation - CESSDA Data Catalogue

[BACK](README.md)

## Getting Started

The various Jenkins jobs in the Jenkins [CDC](https://jenkins.cessda.eu/view/CDC/) view are used to build, test and deploy the CDC components. They are triggered automatically when code changes are committed to any of the [Data Catalogue Bitbucket repos](https://github.com/account/user/cessda/projects/CDC).

## Harvesting Runs

1. **Full run** - Triggered from the `cdc-agg-harvester-full` CronJob.  Does a full harvest of all records for all configured endpoints (see 'add endpoint/update URL' for endpoint configuration details).
1. **Incremental run** - Triggered from the `cdc-agg-harvester-incremental` job. Runs daily.  Does an incremental harvest and ingestion of records for all configured endpoints, based on the most recent ingested lastModified date.

### Adding a new endpoint

To add a new endpoint, add the necessary configuration to the [cessda.metadata.harvester configuration file](https://github.com/cessda/cessda.metadata.harvester/blob/main/src/main/resources/application-cdc.yml)

The configuration format is documented in the [README for the Metadata Harvester](https://github.com/cessda/cessda.metadata.harvester/blob/main/README.md).

The required configuration will be automatically propagated through the pipeline.

### Adding a new language

Adding a new language to the Data Catalogue requires configuring the indexer so that the language's index can be created and has the correct text analysis settings. Each language has its own Elasticsearch index which needs language specific configuration. The naming conventions for settings files is `settings_cmmstudy_{lang}.json` where `{lang}` is a 2 letter ISO language code.

The text analysis settings files can be found in the [cessda.cdc.osmh-indexer.cmm indexer settings directory](https://github.com/cessda/cessda.cdc.osmh-indexer.cmm/tree/main/src/main/resources/elasticsearch/settings/). Use one of the existing files as a template. The documentation of text analysis settings can be found at <https://www.elastic.co/guide/en/elasticsearch/reference/7.17/analysis-overview.html>.

The locales also need to be configured in `src/main/java/eu/cessda/pasc/oci/configurations/AppConfigurationProperties.java`. Modify the `languages` field to include the new language.

The language also needs to be configured in Searchkit in the `languages` array in `src/utilities/language.ts`.

```js
{
	code: 'en', // ISO language code
	label: 'English', // Label to present in the user interface
	index: 'cmmstudy_en' // The Elasticsearch index to use
}
```

Translations for the language should also be added to `translations/{lang}.json`. Use one of the existing language files as a template.

## Data Catalogue Data Model

The internal model of the Datacatalogue is defined as below. All intermediate formats are JSON.

See <https://github.com/cessda/cessda.cdc.osmh-indexer.cmm/blob/main/src/main/resources/json/schema/CMMStudySchema.json> for the multilingual schema definition.

### CMMStudy Field Definitions

| Field Name | Description |
| ---------- | ----------- |
| `id`       | The internal identifier for the study |
| `code`     | The short name of the repository that the study originates from |
| `creators` | A string array of the creators of the study |
| `dataCollectionPeriodStartdate` | The starting date of the data collection period, ideally represented as an ISO date |
| `dataCollectionPeriodEnddate` | The ending date of the data collection period, ideally represented as an ISO date |
| `dataCollectionYear` | The year in which the data was collected, in most cases represented as an integer |
| `dataCollectionFreeTexts` | An array of objects containing text describing extra information on how the data was collected, as well as the event related to this data collection |
| `dataAccessFreeTexts` | An string array describing the conditions of access to the source data |
| `publicationYear` | The year that the study was published |
| `typeOfModeOfCollections` | An array of vocabulary objects describing the collection modes used |
| `keywords` | An array of vocabulary objects describing the keywords of the study |
| `samplingProcedureFreeTexts` | A string array of the sampling procedures that were used in the study |
| `classifications` | An array of vocabulary objects describing the topic classifications |
| `abstract` | The abstract of the study |
| `titleStudy` | The title of the study |
| `studyUrl` | The URL of the study description page in the SP's catalogue |
| `studyNumber` | |
| `fileLanguages` | A string array of the languages that the source data file is available in |
| `typeOfTimeMethods` | An array of vocabulary objects describing the type of time methods used |
| `typeOfSamplingProcedures` | An array of vocabulary objects describing the sampling procedures used in the study |
| `publisher` | A publisher object describing the publisher of the study |
| `studyAreaCountries` | An array of country objects describing the countries that participated in the study |
| `unitTypes` | An array of vocabulary objects describing the unit types of the study |
| `pidStudies` | An array of PID objects describing the persistent identifiers of the study |
| `lastModified` | The time when the metadata of the study was last modified as an ISO date |
| `langAvailableIn` | An array of strings describing the languages the metadata description of the study is available in |
| `studyXmlSourceUrl` | The URL of the OAI-PMH repository where the source of the metadata is located |
| `universes` | The universes that were studied in the study |

### Vocabulary Object Definition

| Field Name | Description |
| ---------- | ----------- |
| `vocab` | The name of the vocabulary |
| `vocabUri` | The URI of the vocabulary (but not the URI of the item) |
| `id` | The ID of the item in the vocabulary being referenced |
| `term` | The text content of the item in the vocabulary |

### Country Object Definition

| Field Name | Description |
| ---------- | ----------- |
| `country` | The name of the country as presented in the source DDI document |
| `abbr` | The ISO code representing the country |
| `searchField` | The country name normalised for searching using the ISO code |

### Data Collection Free Text Object Definition

| Field Name | Description |
| ---------- | ----------- |
| `dataCollectionFreeText` | The text describing the data collection |
| `event` | The event corresponding to this data collection |

### Persistent Identifier Object Definition

| Field Name | Description |
| ---------- | ----------- |
| `agency` | The agency responsible for the persistent identifier, i.e. DOI |
| `pid` | The persistent identifier |

### Publisher Object Definition

| Field Name | Description |
| ---------- | ----------- |
| `abbr` | The short name or abbreviation of the publisher |
| `publisher` | The full name of the publisher |

## Adding a new field to the CDC

### Indexer

- Add field to `models/cmmstudy/CMMStudy.java` and `models/cmmstudy/CMMStudyOfLanguage.java`
	- For multilingual fields the field in `models/cmmstudy/CMMStudy.java` should be a `Map<String, T>` where T is the desired type
	- This will be unwrapped to `T` in `models/cmmstudy/CMMStudyOfLanguage.java`
	- Add `@JsonProperty` annotations to ensure the field names remain consistent
- Add JSON definition to `src/main/resources/json/schema/CMMStudy.schema.json`
	- This must match the multilingual definitions
- Add Elasticsearch field definition to `src/main/resources/elasticsearch/mappings/mappings_cmmstudy.json`

### Searchkit

- Add field and normalisation (`getStudyModel()`) to  `common/metadata.ts`
	- Once normalised, there should be no instances of `undefined`
- Add display information to `src/components/Detail.tsx`
