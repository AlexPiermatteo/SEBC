```
[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster all -a 'mysql --version'
ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>
mysql  Ver 14.14 Distrib 5.5.56, for Linux (x86_64) using readline 5.1

ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>
mysql  Ver 14.14 Distrib 5.5.56, for Linux (x86_64) using readline 5.1

ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>
mysql  Ver 14.14 Distrib 5.5.56, for Linux (x86_64) using readline 5.1

ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>
mysql  Ver 14.14 Distrib 5.5.56, for Linux (x86_64) using readline 5.1

ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>
mysql  Ver 14.14 Distrib 5.5.56, for Linux (x86_64) using readline 5.1


[ec2-user@ip-10-0-0-47 ~]$ mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 11
Server version: 5.5.56 MySQL Community Server (GPL)

Copyright (c) 2000, 2017, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hive               |
| hue                |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
9 rows in set (0.00 sec)

mysql> exit
Bye
```