# Step by Step Logging

- Create JSON File
  * Based on two ~ three scenario, full Sample JSON is required.

<pre>
<code>
{
    "version": 2,
    "servers": {
        "sourceServer": {
            "type": "MONGODB",
            "name": "sourceServer",
            "url": "mongodb://#####"
        },
        "destinationServer": {
            "type": "MONGODB",
            "name": "destinationServer",
            "url": "mongodb://#####"
        },
        "intermediateServer": {
            "type": "COSMOSDB",
            "name": "intermediateServer",
            "url": "https://#####.documents.azure.com:443/",
            "key": "#####"
        },
        "statusServer": {
            "type": "COSMOSDB",
            "name": "statusServer",
            "url": "https://#####.documents.azure.com:443/",
            "key": "#####"
        }
    },
    "tasks": [
        {
            "migrationUnit": "COLLECTION",
            "source": {
                "serverName": "sourceServer",
                "databases": [
                    "MIGTestDB"
                ],
                "collections": [
                    "MIGTestCollection"
                ]
            },
            "destination": {
                "serverName": "destinationServer",
                "databases": [
                    "MIGTestDB"
                ],
                "collections": [
                    "MIGTestCollection"
                ],
                "throughput": 20000,
                "migrationThroughput": 20000,
                "scaling": "AUTOSCALE",
                "shardKey": "itemcode"
            },
            "intermediate": {
                "serverName": "intermediateServer",
                "databases": [
                    "IntermediateDB"
                ],
                "collections": [
                    "IntermediateCollection"
                ],
                "throughput": 20000
            },
            "excludedCollections": [
                "system.views"
            ],
            "uniqueConstraintViolationHandling":"IGNORE",
            "indexCreation":"ALL_INDEXES",
            "batchCount":30
        }
    ],
    "status": {
        "serverName": "statusServer",
        "database": "StatusDB",
        "collection": "StatusCollection",
        "throughput": 1000
    },
    "copyPartitions": 100,
    "copyBatchSize": 30,
    "streamingPartitions": 100,
    "streamingBatchSize": 30,
    "startStreamToIntermediate": false,
    "startBulkCopy": true,
    "startStreamToDestination": false,
    "offHeapMemory": false
}
  </code>
  </pre>

- Create ADB (Skipped) </br>

</br>

- Configure ADB
  * ![Create a JOB](/99_Practice/Image/99_01.create_a_job.png)
  * Put Task Name
  * ![Main Class](/99_Practice/Image/99_02.main_class.png)
  * ![Job_Cluster](/99_Practice/Image/99_03.job_cluster.png) </br>
  Can I use single node cluster? Do I have to use shared cluster? </br>
  * ![Add Jar File](/99_Practice/Image/99_04.add_jar_file.png)
  * ![Add Dependency](/99_Practice/Image/99_05.add_dependent_library.png)
  * Then Create.
  * ![Configure](/99_Practice/Image/99_06.click_configure_in_compute.png)
  * ![Spark Config](/99_Practice/Image/99_07.spark_config_in_Advanced_Option.png) </br>
  Detail explanation is required. </br>
  Need to have sample and guide based on cluster size and type. </br>
  * ![Spark Config Error](/99_Practice/Image/99_08.spark_config_error.png)

</br>

- JOB Parameter
  * ![JSON Upload](/99_Practice/Image/99_09.JSON_Upload.png)
  * ![Parameters](/99_Practice/Image/99_10.Parameters.png)

- Run
  * ![JOB Result](/99_Practice/Image/99_11.Result.png)
  * ![TargetDB](/99_Practice/Image/99_12.TargetDB.png)