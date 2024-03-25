# APIM-SQL-Spark-Delta-Table
This repo shows how we can directly query SQL table through GraphQL API with a Resolver of SQL policy (sql-data-source). If the Spark cluster access info is known, leveraging Databricks SQL Statement Execution API 2.0, then we can use curl to query the data in Delta table. To run this repo, you need to have
- APIM (standard v2)
- Azure SQL with default DB data populated
- Azure Databricks Service

## Connections
- We create a SQL user (user id and password) in the SQL server/db to let him query the data. Thus, the connection string looks like
Server=tcp:xinxuedbsvr.database.windows.net,1433;Initial Catalog=xinxuedb;Persist Security Info=False;User ID=sql_users_id;Password=sql_user_password;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;
- The Spark Delta tables connection needs the following:
  1. DATABRICKS_HOST, representing the workspace instance name, for example adb-1234567890123456.7.azuredatabricks.net, for your Azure Databricks workspace.
  2. DATABRICKS_TOKEN, representing an Azure Databricks personal access token for your Azure Databricks workspace user.
  3. DATABRICKS_SQL_WAREHOUSE_ID, representing the ID of your Databricks SQL warehouse.

## Query SQL DB
- Create a GraphQL API in APIM with the shcema.graphql as the Schema and sql_policy.xml as the Resolver.
- Test the API from APIM API Test
- Test the API from Postman with the same Http body

## Query Spark Delta Table
- On your local machine, run Databricks CLI and then curl to make sure you can query the table
- Create an API in APIM and test it from APIM API Test
- Test it again from Postman with the same Http body.
