## Sentry Tutorial

## Verify user privileges
```
[ec2-user@ip-10-0-0-22 ~]$ kinit alexpiermatteo
Password for alexpiermatteo@HASHTAG.LOCAL:
[ec2-user@ip-10-0-0-22 ~]$ klist
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: alexpiermatteo@HASHTAG.LOCAL

Valid starting       Expires              Service principal
06/07/2017 08:40:50  06/08/2017 08:40:50  krbtgt/HASHTAG.LOCAL@HASHTAG.LOCAL
        renew until 06/14/2017 08:40:50



beeline> !connect jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL

Connecting to jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL
Enter username for jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL: alexpiermatteo
Enter password for jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL: **********

Connected to: Apache Hive (version 1.1.0-cdh5.8.3)
Driver: Hive JDBC (version 1.1.0-cdh5.8.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20170607084444_80e21066-93e4-4799-8588-a8a26119a01c): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170607084444_80e21066-93e4-4799-8588-a8a26119a01c); Time taken: 0.592 seconds
INFO  : Executing command(queryId=hive_20170607084444_80e21066-93e4-4799-8588-a8a26119a01c): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170607084444_80e21066-93e4-4799-8588-a8a26119a01c); Time taken: 0.053 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (1.946 seconds)
```

## Create a Sentry role with full authorization
Before to do that was necessary to change hive warehouse permissions folder into the hdfs and to enable from CM the Sentry in the Hive service.

```
[ec2-user@ip-10-0-0-22 ~]$ beeline
Beeline version 1.1.0-cdh5.8.3 by Apache Hive
beeline> !connect jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL
scan complete in 2ms
Connecting to jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL
Enter username for jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL: alexpiermatteo
Enter password for jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL: **********
Connected to: Apache Hive (version 1.1.0-cdh5.8.3)
Driver: Hive JDBC (version 1.1.0-cdh5.8.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu>
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu>
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu>
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu> CREATE ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20170607085757_9efd9814-b37b-45ef-896d-8781f58f977f): CREATE ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170607085757_9efd9814-b37b-45ef-896d-8781f58f977f); Time taken: 0.456 seconds
INFO  : Executing command(queryId=hive_20170607085757_9efd9814-b37b-45ef-896d-8781f58f977f): CREATE ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170607085757_9efd9814-b37b-45ef-896d-8781f58f977f); Time taken: 0.754 seconds
INFO  : OK
No rows affected (2.359 seconds)
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20170607085757_832489c7-61fe-4e98-97da-ed76afa92e83): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170607085757_832489c7-61fe-4e98-97da-ed76afa92e83); Time taken: 0.072 seconds
INFO  : Executing command(queryId=hive_20170607085757_832489c7-61fe-4e98-97da-ed76afa92e83): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170607085757_832489c7-61fe-4e98-97da-ed76afa92e83); Time taken: 0.121 seconds
INFO  : OK
No rows affected (0.206 seconds)
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu> GRANT ROLE sentry_admin TO GROUP alexpiermatteo;
INFO  : Compiling command(queryId=hive_20170607085757_74b05756-84d7-4eb7-a3c7-d4282be5d869): GRANT ROLE sentry_admin TO GROUP alexpiermatteo
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170607085757_74b05756-84d7-4eb7-a3c7-d4282be5d869); Time taken: 0.061 seconds
INFO  : Executing command(queryId=hive_20170607085757_74b05756-84d7-4eb7-a3c7-d4282be5d869): GRANT ROLE sentry_admin TO GROUP alexpiermatteo
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170607085757_74b05756-84d7-4eb7-a3c7-d4282be5d869); Time taken: 0.08 seconds
INFO  : OK
No rows affected (0.151 seconds)
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu>
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu> show tables;
INFO  : Compiling command(queryId=hive_20170607090000_dc743054-c19f-40b7-a540-e241792012a5): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170607090000_dc743054-c19f-40b7-a540-e241792012a5); Time taken: 0.054 seconds
INFO  : Executing command(queryId=hive_20170607090000_dc743054-c19f-40b7-a540-e241792012a5): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170607090000_dc743054-c19f-40b7-a540-e241792012a5); Time taken: 0.103 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.173 seconds)
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu>
```

## Create additional test users
```
[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster  all -a "sudo groupadd selector" --become
[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster  all -a "sudo groupadd inserters" -- become
[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster  all -a "sudo useradd -u 1100 -g selector george" --become
[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster  all -a "sudo useradd -u 1200 -g inserters ferdinand" --become

[ec2-user@ip-10-0-0-22 ~]$ kadmin.local: add_principal george
[ec2-user@ip-10-0-0-22 ~]$ kadmin.local: add_principal ferdinand
```

## Create test roles and all the grant privileges
```
[ec2-user@ip-10-0-0-22 ~]$ beeline
Beeline version 1.1.0-cdh5.8.3 by Apache Hive
beeline> !connect jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL
scan complete in 2ms
Connecting to jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL
Enter username for jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL: alexpiermatteo
Enter password for jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL: **********
Connected to: Apache Hive (version 1.1.0-cdh5.8.3)
Driver: Hive JDBC (version 1.1.0-cdh5.8.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu> CREATE ROLE reads;
INFO  : Compiling command(queryId=hive_20170607090808_952eb3d5-1ff3-4f4e-9be8-c1f4505f1769): CREATE ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170607090808_952eb3d5-1ff3-4f4e-9be8-c1f4505f1769); Time taken: 0.058 seconds
INFO  : Executing command(queryId=hive_20170607090808_952eb3d5-1ff3-4f4e-9be8-c1f4505f1769): CREATE ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170607090808_952eb3d5-1ff3-4f4e-9be8-c1f4505f1769); Time taken: 0.048 seconds
INFO  : OK
No rows affected (0.159 seconds)
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu> CREATE ROLE writes;
INFO  : Compiling command(queryId=hive_20170607090808_b3a60887-cbcf-41d4-b0a7-7c758f3bc067): CREATE ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170607090808_b3a60887-cbcf-41d4-b0a7-7c758f3bc067); Time taken: 0.048 seconds
INFO  : Executing command(queryId=hive_20170607090808_b3a60887-cbcf-41d4-b0a7-7c758f3bc067): CREATE ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170607090808_b3a60887-cbcf-41d4-b0a7-7c758f3bc067); Time taken: 0.036 seconds
INFO  : OK
No rows affected (0.091 seconds)
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu> GRANT SELECT ON DATABASE default TO ROLE reads;
INFO  : Compiling command(queryId=hive_20170607090808_706e7872-0940-4500-ad09-9e7799523702): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170607090808_706e7872-0940-4500-ad09-9e7799523702); Time taken: 0.056 seconds
INFO  : Executing command(queryId=hive_20170607090808_706e7872-0940-4500-ad09-9e7799523702): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170607090808_706e7872-0940-4500-ad09-9e7799523702); Time taken: 0.059 seconds
INFO  : OK
No rows affected (0.123 seconds)
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu> GRANT ROLE reads TO GROUP selector;
INFO  : Compiling command(queryId=hive_20170607090808_b1d549f1-50fe-4540-983b-7529a93eda8c): GRANT ROLE reads TO GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170607090808_b1d549f1-50fe-4540-983b-7529a93eda8c); Time taken: 0.048 seconds
INFO  : Executing command(queryId=hive_20170607090808_b1d549f1-50fe-4540-983b-7529a93eda8c): GRANT ROLE reads TO GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170607090808_b1d549f1-50fe-4540-983b-7529a93eda8c); Time taken: 0.045 seconds
INFO  : OK
No rows affected (0.101 seconds)
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu> REVOKE ALL ON DATABASE default FROM ROLE writes;
INFO  : Compiling command(queryId=hive_20170607090808_a94d0719-dbf4-4211-9dc8-ec9d730b2810): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170607090808_a94d0719-dbf4-4211-9dc8-ec9d730b2810); Time taken: 0.07 seconds
INFO  : Executing command(queryId=hive_20170607090808_a94d0719-dbf4-4211-9dc8-ec9d730b2810): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170607090808_a94d0719-dbf4-4211-9dc8-ec9d730b2810); Time taken: 0.1 seconds
INFO  : OK
No rows affected (0.176 seconds)
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu> GRANT SELECT ON default.sample_07 TO ROLE writes;
INFO  : Compiling command(queryId=hive_20170607090909_aa96eb89-2a2b-4f7b-a97e-a4816a06b465): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170607090909_aa96eb89-2a2b-4f7b-a97e-a4816a06b465); Time taken: 0.051 seconds
INFO  : Executing command(queryId=hive_20170607090909_aa96eb89-2a2b-4f7b-a97e-a4816a06b465): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170607090909_aa96eb89-2a2b-4f7b-a97e-a4816a06b465); Time taken: 0.05 seconds
INFO  : OK
No rows affected (0.109 seconds)
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu> GRANT ROLE writes TO GROUP inserters;
INFO  : Compiling command(queryId=hive_20170607090909_b9d98a72-645f-4597-9455-2fbef86b00c8): GRANT ROLE writes TO GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170607090909_b9d98a72-645f-4597-9455-2fbef86b00c8); Time taken: 0.049 seconds
INFO  : Executing command(queryId=hive_20170607090909_b9d98a72-645f-4597-9455-2fbef86b00c8): GRANT ROLE writes TO GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170607090909_b9d98a72-645f-4597-9455-2fbef86b00c8); Time taken: 0.033 seconds
INFO  : OK
No rows affected (0.089 seconds)
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu>
```

## kinit as george, then login to beeline
```
[ec2-user@ip-10-0-0-22 ~]$ kinit george
Password for george@HASHTAG.LOCAL:
[ec2-user@ip-10-0-0-22 ~]$ beeline
Beeline version 1.1.0-cdh5.8.3 by Apache Hive
beeline> !connect jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL

scan complete in 2ms
Connecting to jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL
Enter username for jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL: george
Enter password for jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL: **********
Connected to: Apache Hive (version 1.1.0-cdh5.8.3)
Driver: Hive JDBC (version 1.1.0-cdh5.8.3)
.
.
.
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.3 seconds)
```

## kinit as ferdinand, then login to beeline
```
[ec2-user@ip-10-0-0-22 ~]$ kinit ferdinand
Password for ferdinand@HASHTAG.LOCAL:
[ec2-user@ip-10-0-0-22 ~]$ beeline
Beeline version 1.1.0-cdh5.8.3 by Apache Hive
beeline> !connect jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL
scan complete in 2ms
Connecting to jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL
Enter username for jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL: ferdinand
Enter password for jdbc:hive2://ip-10-0-0-223.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-0-223.eu-west-1.compute.internal@HASHTAG.LOCAL: **********
Connected to: Apache Hive (version 1.1.0-cdh5.8.3)
Driver: Hive JDBC (version 1.1.0-cdh5.8.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-10-0-0-223.eu-west-1.compu> show tables;
INFO  : Compiling command(queryId=hive_20170607091313_9223fcaf-eef8-4bbb-850a-4a58477f5b0e): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170607091313_9223fcaf-eef8-4bbb-850a-4a58477f5b0e); Time taken: 0.058 seconds
INFO  : Executing command(queryId=hive_20170607091313_9223fcaf-eef8-4bbb-850a-4a58477f5b0e): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170607091313_9223fcaf-eef8-4bbb-850a-4a58477f5b0e); Time taken: 0.136 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.306 seconds)
```