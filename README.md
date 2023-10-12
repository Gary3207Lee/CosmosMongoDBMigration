# CosmosMongoDBMigration

## Migration Journey

![Migration Journey](./Image/00_01_Migration_Journey.png)

### 1. Assessment

- Check Cosmos DB features, syntax and limits
  * [Azure Cosmos DB for MongoDB (4.2 server version): Supported features and syntax](https://learn.microsoft.com/en-us/azure/cosmos-db/mongodb/feature-support-42)
  * [Limits and Quotas](https://learn.microsoft.com/en-us/azure/cosmos-db/concepts-limits#resource-limits)
  * [MongoDB compatibility and feature support with Azure Cosmos DB for MongoDB vCore](https://learn.microsoft.com/en-us/azure/cosmos-db/mongodb/vcore/compatibility) </br>

- Assess Applications
  * 1234 </br>

- Assess Source Databases
  * [Azure Data Studio for MongoDB Extension](https://learn.microsoft.com/en-us/sql/azure-data-studio/extensions/database-migration-for-mongo-extension?view=sql-server-ver16)
  * [Migration Assessment Helper Shells](01_Assessment/01_01.Assessment_Shell.md) </br>

- Check Business/Service Condition
  * Interview each Service / System Owner
  * Maximum available downtime for each system
  * Available downtime & schedule (Day & Time) for each system </br>

### 2. Planning

- Migration Timeline & Schedule
- Online vs Offline

| Mode | Pros  | Cons  |
|------|-------|-------|
| Offline | - Simple, easy and less complex to execute. | Downtime to applications. |
|         | - Very fewer chances of failure.            |                           |
|         | - No restrictions in terms of database objects it can handle|           |
| Online  | - Very minimal downtime to application. | - Replication used in online migration has multiple restrictions listed in this [doc](02_Planning/02_01.Online_MIG_Restrictions.md) |
|         | - Ideal for large databases and for customers having limited downtime requirements. | - Tough and much complex to execute than offline migration. |
|         |                        | - Greater chances of failure due to complexity of migration. |
|         |                        | There is an impact on the source server's storage and compute if the migration runs for a long time. The impact needs to be monitored closely during migration. |

- Cosmos DB for Mongo DB RU-Base vs vCore
  * [What is RU-based and vCore-based Azure Cosmos DB for MongoDB?](https://learn.microsoft.com/en-us/azure/cosmos-db/mongodb/choose-model)

- Migration Method
  * [Azure Cosmos DB API for MongoDB](https://learn.microsoft.com/en-us/azure/cosmos-db/migration-choices#azure-cosmos-db-api-for-mongodb)
  * [Azure Cosmos DB for MongoDB vCore](02_02.Online_Migration_vCore.md)

- Capacity Planning & Target Spec Sizing
  * [Convert the number of vCores or vCPUs in your nonrelational database to Azure Cosmos DB RU/s](https://learn.microsoft.com/en-us/azure/cosmos-db/convert-vcore-to-request-unit)
  * [Estimate RU/s using the Azure Cosmos DB capacity planner - Azure Cosmos DB for MongoDB](https://learn.microsoft.com/en-us/azure/cosmos-db/mongodb/estimate-ru-capacity-planner)
  * [How to choose between standard (manual) and autoscale provisioned throughput](https://learn.microsoft.com/en-us/azure/cosmos-db/how-to-choose-offer)
  * [How to choose between provisioned throughput and serverless](https://learn.microsoft.com/en-us/azure/cosmos-db/throughput-serverless)

- Build Test Scenario for Post-Migration (DEV/UAT)
  * Unit Test for Important or Mission Critical Task
  * Performance Validation
- Build Check Scenario for Post-Migration (PROD)
  * Check Server Configurations & Optimize if required
  * Check Data Consistency

- [Backup & Recovery (RTO/RPO)](https://learn.microsoft.com/en-us/azure/cosmos-db/online-backup-and-restore)
- [High Availability & BCDR](https://learn.microsoft.com/en-us/azure/cosmos-db/high-availability)

### 3. Rehearsal

- Rehearsal Migration in DEV/UAT Environment </br>
  (Capture Resource Utilization and Elapsed Time)
- Run Test Scenario for Post-Migration (DEV/UAT)
- Review the result and take necessary actions
- Apply additional WBS to Migration Plan if required
- [Common Errors](https://learn.microsoft.com/en-us/azure/postgresql/migrate/common-errors-and-special-scenarios-fms)
- [Troubleshooting Guides](https://learn.microsoft.com/en-us/azure/postgresql/flexible-server/how-to-troubleshooting-guides)

### 4. Execution

- Execute Migration including Production Environment

### 5. Cut-Over

- System Cut-Over

### 6. Post-Migration

- Run System Check Scenario for Post-Migration(PROD)
- Monitoring & Remedation
- [Post-migration optimization steps when using Azure Cosmos DB's API for MongoDB](https://learn.microsoft.com/en-us/azure/cosmos-db/mongodb/post-migration-optimization)
- [Best practices for scaling provisioned throughput (RU/s)](https://learn.microsoft.com/en-us/azure/cosmos-db/scaling-provisioned-throughput-best-practices)
