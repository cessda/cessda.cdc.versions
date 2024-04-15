# Operations Documentation - CESSDA Data Catalogue

## Adding a new repository to the CESSDA Data Catalogue

Adding a repository to the Data Catalogue is a simple process. There is only one file that needs to be modified, which can be found at <https://github.com/cessda/cessda.cdc.aggregator.deploy/blob/main/charts/harvester/config/config.yaml>.

To create a new repository, create a new entry under `harvester.repos`. Feel free to use an existing repository configuration entry as a reference.

- `code` - Short name used in logs
- `name` - Friendly name shown in the user interface
- `url` - URL of the OAI-PMH endpoint of the repository
- `validationGate` - The CMV validation gate to use. See <https://cmv.cessda.eu/documentation/constraints.html> for validation gate definitions.
- `metadataPrefixes` - Specific harvester configurations

Multiple metadata prefixes and sets can be configured for the same repository.

- `metadataPrefix` - the metadata prefix to harvest
- `setSpec` - the set to harvest, can be omitted
- `validationProfile` - the CMV profile to validate against, see <https://cmv.cessda.eu/documentation/profiles.html>
- `ddiVersion` - the DDI version harvested, currently unused

See <https://github.com/cessda/cessda.metadata.harvester/blob/main/README.md> for the full definition of the configuration file.

## Managing the Elasticsearch (ES) indices

The Elasticsearch cluster used to run the Data Catalogue is available on the catalogues endpoint, i.e. at `https://datacatalogue.cessda.eu/es/`. This endpoint is password protected (the password can be found in 1Password).

To check that language indexes have been created, perform a `GET /_cat/indices` request to Elasticsearch (`https://datacatalogue.cessda.eu/es/_cat/indices`). This should return a result that looks like this.

```text
green open cmmstudy_da      9sAfhuSlTQ-0n5mUsA22NA 2 0  55866      0  22.9mb  22.9mb
green open cmmstudy_nl      lSp-CY3bT1GOqexcSbkh8Q 2 0  73839  33545  42.6mb  42.6mb
green open cmmstudy_sk      6CNX6nBmT3WSZiUtvIhSzg 2 0    370      0 264.6kb 264.6kb
green open cmmstudy_sl      5suTR6TfTWSlcw9aTbAIYQ 2 0   2362      0   1.1mb   1.1mb
green open cmmstudy_fi      2TsPwBbAQfScY2KDlOnjoQ 2 0  70431  12604  42.6mb  42.6mb
green open cmmstudy_sv      cLC8CFcsTduzt_V6lDmXDA 2 0  16702   1195   8.1mb   8.1mb
green open cmmstudy_pt      FpuyMaTeRAqakFiAOA2hOA 2 0      0      0    504b    504b
green open cmmstudy_sr      VayHh0mwQRCttHSCjYdmVA 2 0      0      0    504b    504b
green open cmmstudy_de      2Wabj5yiRNCdnZYLwYKvbA 2 0  90216      0 127.3mb 127.3mb
green open cmmstudy_no      fTOR_uY7SSmSxtfs7azlJA 2 0      0      0    504b    504b
green open cmmstudy_it      UUqW-oC7QWKmDASbkWiJvA 2 0      0      0    504b    504b
green open cmmstudy_fr      u-1zWeqQShyRs3O-C6i0mA 2 0  36012  32424  34.2mb  34.2mb
green open cmmstudy_hu      SND6EAN1QyajTfHWnZJWSQ 2 0      0      0    504b    504b
green open cmmstudy_el      VNq9cpPMSUS9dU6bLdfclQ 2 0   9026   2211     8mb     8mb
green open cmmstudy_en      rCJwDKb2Rd-ntMAg7tmuoA 2 0 948749 217044 519.3mb 519.3mb
green open cmmstudy_et      OtngDK4yQi2roJa-GUx6KQ 2 0      0      0    504b    504b
green open cmmstudy_cs      3hGeh3X1RxCZav_qydw6iw 2 0      0      0    504b    504b
```

There should be a `cmmstudy` index for each enabled language. Some languages may be missing if no studies in that language were harvested. For more details on the `_cat/indices` API, see <https://www.elastic.co/guide/en/elasticsearch/reference/7.17/cat-indices.html>.

### Deleting one or more indices

To delete an index, perform a `DELETE /${index_name}` request to Elasticsearch, where `${index_name}` is the name of the index that should be deleted. The wildcard character (`*`) can be used to specify multiple indices for deletion. For more details see <https://www.elastic.co/guide/en/elasticsearch/reference/7.17/indices-delete-index.html> for complete details of the API.

For example, to delete the English index the request to issue is `DELETE /cmmstudy_en`. To delete all indices, the request to issue is `DELETE /cmmstudy_*`.

### Re-harvesting

To re-harvest outside of scheduled harvesting periods, run the Kubernetes CronJob for the harvester. This can be done from the Google Cloud Console (see the development project: <https://console.cloud.google.com/kubernetes/workload/overview?project=cessda-dev>). For an incremental harvest run `cdc-agg-harvester-incremental` and for full harvests run `cdc-agg-harvester-full`.

The incremental harvest will only ingest records that were changed in the last week, whereas the full harvest will retrieve every record regardless on when it was updated. Full harvests will also delete records that are no longer present in the source repository.

### Re-indexing

### Create a snapshot

The [Jenkins ES backup job](https://jenkins.cessda.eu/view/CDC/job/cessda.cdc.es.backup/) creates a daily snapshot of the ES indices used by the production instance of CDC. [The Jenkins cleanup job](https://jenkins.cessda.eu/view/CDC/job/cessda.cdc.es.backup/job/Cleanup/) also runs daily, to limit the number of snapshots that are available, to save on disk space.

### Restore a snapshot

Use the restore function of the [Jenkins ES backup job](https://jenkins.cessda.eu/view/CDC/job/cessda.cdc.es.backup/job/Restore/). Select main, production or staging to specify the CDC instance to restore to then specify the snapshot to restore (e.g. **'snapshot_53'**).

## Checking the CDC XML store

The Data Catalogue stores harvested XML files from remote repositories in a Google Cloud storage bucket. This can be accessed via the Google Cloud console, or using `gsutil` on the command line ([`gsutil` documentation](https://cloud.google.com/storage/docs/gsutil)). The storage bucket is located at [gs://cessda-cdc-aggregator-storage](https://console.cloud.google.com/storage/browser/cessda-cdc-aggregator-storage).

The harvested XML files are stored in 2 folders:

- Source (all harvested OAI-PMH metadata)
- Validated (metadata that has passed XSD and CMV validation)

Repository configuration is stored in `pipeline.json` alongside the harvested XML files. The `pipeline.json` files are created by the harvester and consumed by downstream components.

The store should maintain itselfv automatically, deleting records when they are removed from endpoints.
