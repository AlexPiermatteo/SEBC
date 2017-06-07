## CM Lab


### What is ubertask optimization?
Whether to enable ubertask optimization, which runs "sufficiently small" jobs sequentially within a single JVM. "Small" is defined by the mapreduce.job.ubertask.maxmaps, mapreduce.job.ubertask.maxreduces, and mapreduce.job.ubertask.maxbytes settings.


### Where in CM is the Kerberos Security Realm value displayed?
The Kerberos Security Realm is displayed in Administration->Settings under "Kerberos Security Realm" (default_realm: HADOOP.COM).


### Which CDH service(s) host a property for enabling Kerberos authentication?
All the core services have a property to enable Kerberos authentication (HDFS, Hive, Hue, Oozie, YARN, ZooKeeper, and Cloudera Management Service)


### How do you upgrade the CM agents?
To update the CM agents "the upgrade wizard" can be used (simply click on "Re-run Upgrade Wizard" from the "All Hosts" page) or alternatively the updated version can be manually installed on every node of the cluster.


### Give the `tsquery` statement used to chart Hue's CPU utilization?
`select (cpu_system_rate + cpu_user_rate) where category=ROLE and serviceName=hue`


### Name all the roles that make up the Hive service
* Hive Metastore Server
* HiveServer2
* Hive Gateway


### What steps must be completed before integrating Cloudera Manager with Kerberos?
* `openldap-clients` have to be installed on the Cloudera Manager Server host
* `krb5-workstation` installed on every host
* `krb5-libs` installed on every host
* Ensure you have secured communication between the Cloudera Manager Server and Agents before you enable Kerberos on your cluster
* The realm has to support renewable tickets
* If using AES-256 encryption, install the JCE policy file
* Get or create a Kerberos Principal for the Cloudera Manager Server
* Enable Kerberos using the Wizard


After enabling Kerberos, you need to:
* Create HDFS superuser
* Get/Create a Kerberos principal for each user account
* Prepare in the cluster a user directory for each user
* Test that Kerberos is actually working (kinit for your user account, submit mapreduce job)