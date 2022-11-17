# Operations Documentation - CESSDA Data Catalogue

## Managing the Elasticsearch (ES) indices

### Checking that indices exist

<!-- TODO: Rewrite this entire document, as it is painfully out of date -->

To check that language indexes have been created, look at the [cessda-cdc-es-backup storage bucket](https://console.cloud.google.com/storage/browser/cessda-cdc-es-backup/indices/?organizationId=776004534695&project=cessda-prod) in the **'CESSDA Production GCP project'**. Don't delete anything directly from here.

There should be a folder of the form **'cmmstudy_xx'** for each language code in the osmhConsumer.languages section of the osmh-indexer's [application.yaml file](https://bitbucket.org/cessda/cessda.cdc.osmh-indexer.cmm/src/master/src/main/resources/application.yml).

### Deleting one or more indices

One option is use [elasticsearch-head](https://mobz.github.io/elasticsearch-head/) either as an Elasticsearch plugin or a Chrome browser extension, and connect to one of clusters (be VERY careful if connecting to the Production cluster). You will need a username and password to connect to the ES cluster, which can be found in the password manager. Once connected, you can delete one or more language-specific indices as required, to prepare for a clean (i.e. from scratch) harvest.

### Re-harvesting

To re-harvest outside of scheduled harvesting periods, run the Jenkins job [cessda.cdc.deploy](https://jenkins.cessda.eu/view/CDC/job/cessda.cdc.deploy/job/master/build?delay=0sec) with module set to **'osmh-indexer'** and cluster set to **'development-cluster'** or **'staging-cluster'**, depending on which instance needs to be updated. If you have deleted one or more language-specific indices for a given instance of CDC since the harvester last ran for that instance, then you will get a clean harvest for that language, otherwise it will be incremental (any new, edited and deleted records will be added, updated and removed respectively, all others will remain unchanged).

### Create a snapshot

The [Jenkins ES backup job](https://jenkins.cessda.eu/view/CDC/job/cessda.cdc.es.backup/) creates a daily snapshot of the ES indices used by the production instance of CDC. [The Jenkins cleanup job](https://jenkins.cessda.eu/view/CDC/job/cessda.cdc.es.backup/job/Cleanup/) also runs daily, to limit the number of snapshots that are available, to save on disk space.

### Restore a snaspshot

Use the  restore function of the [Jenkins ES backup job](https://jenkins.cessda.eu/view/CDC/job/cessda.cdc.es.backup/job/Restore/). Select master, production or staging to specify the CDC instance to restore to then specify the snapshot to restore (e.g. **'snapshot_53'**).
