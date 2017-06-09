```
[ec2-user@ip-10-0-0-124 ~]$ ls /etc/yum.repos.d
cloudera-manager.repo      mysql-community.repo         redhat.repo                     redhat-rhui.repo
cloudera-manager.repo.~1~  mysql-community-source.repo  redhat-rhui-client-config.repo  rhui-load-balancers.conf
```
```
[ec2-user@ip-10-0-0-124 ~]$ sudo /usr/share/cmf/schema/scm_prepare_database.sh -u root --password=cloudera  --force m ysql scm cloudera-scm cloudera-scm -h ip-10-0-0-47.eu-west-1.compute.internal
JAVA_HOME=/usr/java/jdk1.7.0_67-cloudera
Verifying that we can write to /etc/cloudera-scm-server
[                          main] DbProvisioner                  ERROR Exception when creating/dropping database with user 'root' and jdbc url 'jdbc:mysql://ip-10-0-0-47.eu-west-1.compute.internal/?useUnicode=true&characterEncoding=UTF-8'
java.sql.SQLException: Access denied for user 'root'@'ip-10-0-0-124.eu-west-1.compute.internal' (using password: YES)
        at com.mysql.jdbc.SQLError.createSQLException(SQLError.java:964)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:3970)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:3906)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:873)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.MysqlIO.proceedHandshakeWithPluggableAuthentication(MysqlIO.java:1710)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.MysqlIO.doHandshake(MysqlIO.java:1226)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.ConnectionImpl.coreConnect(ConnectionImpl.java:2253)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.ConnectionImpl.connectOneTryOnly(ConnectionImpl.java:2284)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2083)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:806)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.JDBC4Connection.<init>(JDBC4Connection.java:47)[mysql-connector-java.jar:5.1.40]
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)[:1.7.0_67]
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)[:1.7.0_67]
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)[:1.7.0_67]
        at java.lang.reflect.Constructor.newInstance(Constructor.java:526)[:1.7.0_67]
        at com.mysql.jdbc.Util.handleNewInstance(Util.java:425)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:410)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:328)[mysql-connector-java.jar:5.1.40]

        at java.sql.DriverManager.getConnection(DriverManager.java:571)[:1.7.0_67]
        at java.sql.DriverManager.getConnection(DriverManager.java:215)[:1.7.0_67]
        at com.cloudera.enterprise.dbutil.DbProvisioner.executeSql(DbProvisioner.java:283)[db-common-5.10.1.jar:]
        at com.cloudera.enterprise.dbutil.DbProvisioner.doMain(DbProvisioner.java:95)[db-common-5.10.1.jar:]
        at com.cloudera.enterprise.dbutil.DbProvisioner.main(DbProvisioner.java:110)[db-common-5.10.1.jar:]
[                          main] DbProvisioner                  ERROR Stack Trace:
java.sql.SQLException: Access denied for user 'root'@'ip-10-0-0-124.eu-west-1.compute.internal' (using password: YES)
        at com.mysql.jdbc.SQLError.createSQLException(SQLError.java:964)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:3970)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:3906)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:873)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.MysqlIO.proceedHandshakeWithPluggableAuthentication(MysqlIO.java:1710)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.MysqlIO.doHandshake(MysqlIO.java:1226)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.ConnectionImpl.coreConnect(ConnectionImpl.java:2253)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.ConnectionImpl.connectOneTryOnly(ConnectionImpl.java:2284)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2083)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:806)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.JDBC4Connection.<init>(JDBC4Connection.java:47)[mysql-connector-java.jar:5.1.40]
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)[:1.7.0_67]
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)[:1.7.0_67]
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)[:1.7.0_67]
        at java.lang.reflect.Constructor.newInstance(Constructor.java:526)[:1.7.0_67]
        at com.mysql.jdbc.Util.handleNewInstance(Util.java:425)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:410)[mysql-connector-java.jar:5.1.40]
        at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:328)[mysql-connector-java.jar:5.1.40]

        at java.sql.DriverManager.getConnection(DriverManager.java:571)[:1.7.0_67]
        at java.sql.DriverManager.getConnection(DriverManager.java:215)[:1.7.0_67]
        at com.cloudera.enterprise.dbutil.DbProvisioner.executeSql(DbProvisioner.java:283)[db-common-5.10.1.jar:]
        at com.cloudera.enterprise.dbutil.DbProvisioner.doMain(DbProvisioner.java:95)[db-common-5.10.1.jar:]
        at com.cloudera.enterprise.dbutil.DbProvisioner.main(DbProvisioner.java:110)[db-common-5.10.1.jar:]
--> Error 1, ignoring (because force flag is set)
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jdk1.7.0_67-cloudera/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
[                          main] DbCommandExecutor              INFO  Successfully connected to database.
All done, your SCM database is configured correctly!

```

## Command and output for hdfs dfs -ls /user
```
[ec2-user@ip-10-0-0-47 ~]$ export HADOOP_USER_NAME=hdfs
[ec2-user@ip-10-0-0-47 ~]$ hdfs dfs -mkdir -p /user/theresa
[ec2-user@ip-10-0-0-47 ~]$ hdfs dfs -mkdir -p /user/jeremy
[ec2-user@ip-10-0-0-47 ~]$ hdfs dfs -ls /user
Found 6 items
drwxrwxrwx   - mapred hadoop              0 2017-06-09 05:55 /user/history
drwxrwxr-t   - hive   hive                0 2017-06-09 05:56 /user/hive
drwxrwxr-x   - hue    hue                 0 2017-06-09 05:56 /user/hue
drwxr-xr-x   - hdfs   supergroup          0 2017-06-09 06:02 /user/jeremy
drwxrwxr-x   - oozie  oozie               0 2017-06-09 05:56 /user/oozie
drwxr-xr-x   - hdfs   supergroup          0 2017-06-09 06:02 /user/theresa
```


## The output from the CM API call ../api/v14/hosts
```
[ec2-user@ip-10-0-0-124 ~]$ curl -u admin:admin "http://ip-10-0-0-124.eu-west-1.compute.internal:7180/api/v14/hosts"
{
  "items" : [ {
    "hostId" : "c506cdb8-102f-4c65-a66f-ed9afe8ec9dd",
    "ipAddress" : "10.0.0.124",
    "hostname" : "ip-10-0-0-124.eu-west-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-10-0-0-124.eu-west-1.compute.internal:7180/cmf/hostRedirect/c506cdb8-102f-4c65-a66f-ed9afe8ec9dd",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "b748868b-1dd6-4f4d-8168-3d65527fe1dc",
    "ipAddress" : "10.0.0.184",
    "hostname" : "ip-10-0-0-184.eu-west-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-10-0-0-124.eu-west-1.compute.internal:7180/cmf/hostRedirect/b748868b-1dd6-4f4d-8168-3d65527fe1dc",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "2743dfc9-ed08-4f1a-b832-7f2f326ed163",
    "ipAddress" : "10.0.0.201",
    "hostname" : "ip-10-0-0-201.eu-west-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-10-0-0-124.eu-west-1.compute.internal:7180/cmf/hostRedirect/2743dfc9-ed08-4f1a-b832-7f2f326ed163",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "9f1eb54c-5531-43d5-9f18-b316bd5b5100",
    "ipAddress" : "10.0.0.23",
    "hostname" : "ip-10-0-0-23.eu-west-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-10-0-0-124.eu-west-1.compute.internal:7180/cmf/hostRedirect/9f1eb54c-5531-43d5-9f18-b316bd5b5100",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "03a06b7f-2675-4edf-999f-e7f9536c67d3",
    "ipAddress" : "10.0.0.47",
    "hostname" : "ip-10-0-0-47.eu-west-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-10-0-0-124.eu-west-1.compute.internal:7180/cmf/hostRedirect/03a06b7f-2675-4edf-999f-e7f9536c67d3",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  } ]
}

```