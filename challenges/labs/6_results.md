!connect jdbc:hive2://localhost:10000/default;principal=hive/ip-10-0-0-124.eu-west-1.compute.internal@ALEXPIERMATTEO.COM.UK
CREATE ROLE politican1;

GRANT ALL ON DATABASE default TO ROLE politican1;

GRANT ROLE politican1 TO GROUP conservative;


CREATE ROLE politician2;

GRANT SELECT ON default.sample_07 TO ROLE politician2;

GRANT SELECT ON default.sample_08 TO ROLE politician2;

GRANT ROLE politician2 TO GROUP labour;

kinit jeremy

0: jdbc:hive2://localhost:10000/default> !connect jdbc:hive2://localhost:10000/default;principal=hive/ip-10-0-0-124.eu-west-1.compute.internal@ALEXPIERMATTEO.COM.UK
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/ip-10-0-0-124.eu-west-1.compute.internal@ALEXPIERMATTEO.COM.UK
Connected to: Apache Hive (version 1.1.0-cdh5.10.1)
Driver: Hive JDBC (version 1.1.0-cdh5.10.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
1: jdbc:hive2://localhost:10000/default> show tables;
INFO  : Compiling command(queryId=hive_20170609065454_4ecc024b-2ae9-4553-9c4e-e3606ebb43e2): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170609065454_4ecc024b-2ae9-4553-9c4e-e3606ebb43e2); Time taken: 0.681 seconds
INFO  : Executing command(queryId=hive_20170609065454_4ecc024b-2ae9-4553-9c4e-e3606ebb43e2): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170609065454_4ecc024b-2ae9-4553-9c4e-e3606ebb43e2); Time taken: 0.335 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
| sample_08  |
+------------+--+
2 rows selected (2.352 seconds)
1: jdbc:hive2://localhost:10000/default>



[ec2-user@ip-10-0-0-124 ~]$ kinit theresa
Password for theresa@ALEXPIERMATTEO.COM.UK:
[ec2-user@ip-10-0-0-124 ~]$ beeline
Beeline version 1.1.0-cdh5.10.1 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/ip-10-0-0-124.eu-west-1.compute.internal@ALEXPIERMATTEO.COM.UK
scan complete in 1ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/ip-10-0-0-124.eu-west-1.compute.internal@ALEXPIERMATTEO.COM.UK
Connected to: Apache Hive (version 1.1.0-cdh5.10.1)
Driver: Hive JDBC (version 1.1.0-cdh5.10.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> show tables;
INFO  : Compiling command(queryId=hive_20170609065454_525b7ccb-133d-42e7-ab9a-59e8b487ab1a): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170609065454_525b7ccb-133d-42e7-ab9a-59e8b487ab1a); Time taken: 0.068 seconds
INFO  : Executing command(queryId=hive_20170609065454_525b7ccb-133d-42e7-ab9a-59e8b487ab1a): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170609065454_525b7ccb-133d-42e7-ab9a-59e8b487ab1a); Time taken: 0.142 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.308 seconds)
0: jdbc:hive2://localhost:10000/default>