# P3_Database-Migration
Ample Technologies is planning to migrate data from on premise MySQL to AWS RDS.

Ample Technologies is planning to migrate data from on premise MySQL to AWS RDS. 
The current in-house production database is based on a 10TB, standby in DR site. The database has 1 main 
schemas, comprising of 1 table, 5000 concurrent session of which 100 are active at a given time and has an 
IOPS requirement of 50K read and 30K write IOPS. The development database is 1/10th of the production 
capacity.  

# Objective of DB Migration Plan:  
Recommend effectively process to manage the migration of Database from on-premise MySQL to AWS RDS. 
Core capabilities migration plan should involve.  
∙Scoping of the current database  
∙Approach to migration  
∙Production cutover plan  
∙Rollback Plan  
∙Execution Steps  
Deliverables:  
1.1)  Discuss  a Database Migration Plan  
2.2)  Implement your solution  

# Steps
* Comfirm if this is a homogenous or heterogenous migration (In homogenous migration, the source and destination DB are the same while in heterogenous, the reverse is the case.
* Connect to the source database using a DBMS, in this project, I will use Sqlectron. Ensure that the connection is successful. See details below: 54.163.41.196:3306 username - root password - Apple@12345.
* Create RDS on AWS or any other CSP, copy the endpoint information and use it to connect with the RDS from Sqlectron.
* Be sure that both connection to the On-premise and Cloud database from sqlectron are successful.
* Create replication instance in AWS DMS. Read more here: https://docs.aws.amazon.com/dms/latest/userguide/CHAP_ReplicationInstance.html. You use this replication instance to perform your database migration. By using a replication instance, you can get high availability and failover support. AWS DMS uses a replication instance to connect to your source data store, read the source data, and format the data for consumption by the target data store. A replication instance also loads the data into the target data store. Most of this processing happens in memory. However, large transactions might require some buffering on disk. Cached transactions and log files are also written to disk.
* Create two endpoints, one for the source and the other for the destination. Connect the destination endpoint to the RDS created (copy endpoint from the RDS and use as Server name when creation the destination endpoint. Use the provided IP address as the Server name at the source endpoint and 3306 for port number.
* Create a data migration task

# Creation Flow
* RDS >>>> Replication Instance >>>> Enpoints >>>> Replication Task
 
