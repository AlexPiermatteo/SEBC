# Install mysql
Mysql is installed on my first node with public ip 54.229.249.113

## Add repositories
First step is to download the rpm and install the repo.
```
[ec2-user@ip-10-0-0-47 ~]$ wget http://repo.mysql.com/mysql-community-release-el7-5.no arch.rpm
--2017-06-09 04:21:13--  http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm

Resolving repo.mysql.com (repo.mysql.com)... 2.19.60.91
Connecting to repo.mysql.com (repo.mysql.com)|2.19.60.91|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6140 (6.0K) [application/x-redhat-package-manager]
Saving to: ‘mysql-community-release-el7-5.noarch.rpm’

100%[=============================================>] 6,140       --.-K/s   in 0s

2017-06-09 04:21:14 (473 MB/s) - ‘mysql-community-release-el7-5.noarch.rpm’ saved [6140/6140]

[ec2-user@ip-10-0-0-47 ~]$ sudo rpm -ivh mysql-community-release-el7-5.noarch.rpm
Preparing...                          ################################# [100%]
Updating / installing...
   1:mysql-community-release-el7-5    ################################# [100%]
[ec2-user@ip-10-0-0-47 ~]$ sudo yum update
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
epel/x86_64/metalink                                            |  26 kB  00:00:00

mysql-connectors-community                                      | 2.5 kB  00:00:00

mysql-tools-community                                           | 2.5 kB  00:00:00

mysql56-community                                               | 2.5 kB  00:00:00

rhui-REGION-client-config-server-7                              | 2.9 kB  00:00:00

rhui-REGION-rhel-server-releases                                | 3.5 kB  00:00:00

rhui-REGION-rhel-server-rh-common                               | 3.8 kB  00:00:00

(1/3): mysql-connectors-community/x86_64/primary_db             |  14 kB  00:00:00

(2/3): mysql-tools-community/x86_64/primary_db                  |  33 kB  00:00:00

(3/3): mysql56-community/x86_64/primary_db                      | 168 kB  00:00:00

Resolving Dependencies
--> Running transaction check
---> Package mariadb-libs.x86_64 1:5.5.52-1.el7 will be obsoleted
---> Package mysql-community-libs.x86_64 0:5.6.36-2.el7 will be obsoleting
--> Processing Dependency: mysql-community-common(x86-64) >= 5.6.10 for package: mysql-community-libs-5.6.36-2.el7.x86_64
--> Running transaction check
---> Package mysql-community-common.x86_64 0:5.6.36-2.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

=======================================================================================

 Package                    Arch       Version             Repository             Size =======================================================================================

Installing:
 mysql-community-libs       x86_64     5.6.36-2.el7        mysql56-community     2.0 M
     replacing  mariadb-libs.x86_64 1:5.5.52-1.el7
Installing for dependencies:
 mysql-community-common     x86_64     5.6.36-2.el7        mysql56-community     257 k

Transaction Summary
=======================================================================================

Install  1 Package (+1 Dependent package)

Total download size: 2.3 M
Is this ok [y/d/N]: y
Downloading packages:
warning: /var/cache/yum/x86_64/7Server/mysql56-community/packages/mysql-community-common-5.6.36-2.el7.x86_64.rpm: Header V3 DSA/SHA1 Signature, key ID 5072e1f5: NOKEY
Public key for mysql-community-common-5.6.36-2.el7.x86_64.rpm is not installed
(1/2): mysql-community-common-5.6.36-2.el7.x86_64.rpm           | 257 kB  00:00:00

(2/2): mysql-community-libs-5.6.36-2.el7.x86_64.rpm             | 2.0 MB  00:00:00

---------------------------------------------------------------------------------------

Total                                                      12 MB/s | 2.3 MB  00:00

Retrieving key from file:/etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
Importing GPG key 0x5072E1F5:
 Userid     : "MySQL Release Engineering <mysql-build@oss.oracle.com>"
 Fingerprint: a4a9 4068 76fc bd3c 4567 70c8 8c71 8d3b 5072 e1f5
 Package    : mysql-community-release-el7-5.noarch (installed)
 From       : file:/etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
Is this ok [y/N]: y
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
Warning: RPMDB altered outside of yum.
  Installing : mysql-community-common-5.6.36-2.el7.x86_64                          1/3

  Installing : mysql-community-libs-5.6.36-2.el7.x86_64                            2/3

  Erasing    : 1:mariadb-libs-5.5.52-1.el7.x86_64                                  3/3

  Verifying  : mysql-community-common-5.6.36-2.el7.x86_64                          1/3

  Verifying  : mysql-community-libs-5.6.36-2.el7.x86_64                            2/3

  Verifying  : 1:mariadb-libs-5.5.52-1.el7.x86_64                                  3/3


Installed:
  mysql-community-libs.x86_64 0:5.6.36-2.el7


Dependency Installed:
  mysql-community-common.x86_64 0:5.6.36-2.el7


Replaced:
  mariadb-libs.x86_64 1:5.5.52-1.el7


Complete!
```

Now we need to enable the repo for mysql 5.5 (after disabling the one for 5.6 and 5.7):
```
ansible -i alexcluster all -a 'sudo yum-config-manager --enable mysql56-community'
ansible -i alexcluster all -a 'sudo yum-config-manager --disable mysql56-community'
ansible -i alexcluster all -a 'sudo yum-config-manager --disable mysql57-community'
```

The previous commands need the be executed on every node in order to install the right version of the connector.


We can check if it's correctly configured using the following command:
```
[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster all -a 'sudo yum repolist enabled |
grep "mysql*"'
 [WARNING]: Consider using 'become', 'become_method', and 'become_user' rather than
running sudo

ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                 repo name                         status
mysql-connectors-community/x86_64       MySQL Connectors Community         36
mysql-tools-community/x86_64            MySQL Tools Community              47
mysql55-community/x86_64                MySQL 5.5 Community Server        325
repolist: 408

ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                 repo name                         status
mysql-connectors-community/x86_64       MySQL Connectors Community         36
mysql-tools-community/x86_64            MySQL Tools Community              47
mysql55-community/x86_64                MySQL 5.5 Community Server        325
repolist: 408

ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                 repo name                         status
mysql-connectors-community/x86_64       MySQL Connectors Community         36
mysql-tools-community/x86_64            MySQL Tools Community              47
mysql55-community/x86_64                MySQL 5.5 Community Server        325
repolist: 408

ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                 repo name                         status
mysql-connectors-community/x86_64       MySQL Connectors Community         36
mysql-tools-community/x86_64            MySQL Tools Community              47
mysql55-community/x86_64                MySQL 5.5 Community Server        325
repolist: 408

ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                 repo name                         status
mysql-connectors-community/x86_64       MySQL Connectors Community         36
mysql-tools-community/x86_64            MySQL Tools Community              47
mysql55-community/x86_64                MySQL 5.5 Community Server        325
repolist: 408
```

### Installation mysql
On the first node, we can install mysql-server, check the version and start the service:
```
sudo yum install -y mysql-server
sudo service mysqld start
```

### Installation mysql client on each node
```
ansible -i alexcluster mysql -a 'sudo yum install mysql -y'


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

```

## Installation mysql connector
## Installation Oracle JDK 8
On every node of the cluster:
```
ansible -i alexcluster all -a 'wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/8u131-b11/d54c1d3a095b4ff2b6607d096fa80163/jdk-8u131-linux-x64.rpm"'
ansible -i alexcluster  all -a 'sudo yum localinstall jdk-8u131-linux-x64.rpm -y'
ansible -i alexcluster  all -a 'sudo mkdir -p /usr/share/java/'
```
And then download the mysql connector driver on every node:
```
wget http://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.40.tar.gz
tar -zxvf mysql-connector-java-5.1.40.tar.gz
sudo mkdir -p /usr/share/java
sudo cp mysql-connector-java-5.1.40/mysql-connector-java-5.1.40-bin.jar /usr/share/java/mysql-connector-java.jar
sudo su

[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster  all -a 'echo "export CLASSPATH=/usr /share/java/mysql-connector-java.jar:$CLASSPATH" > /etc/profile.d/classpath.sh'
ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>
export CLASSPATH=/usr/share/java/mysql-connector-java.jar:$CLASSPATH > /etc/profile.d/classpath.sh

ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>
export CLASSPATH=/usr/share/java/mysql-connector-java.jar:$CLASSPATH > /etc/profile.d/classpath.sh

ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>
export CLASSPATH=/usr/share/java/mysql-connector-java.jar:$CLASSPATH > /etc/profile.d/classpath.sh

ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>
export CLASSPATH=/usr/share/java/mysql-connector-java.jar:$CLASSPATH > /etc/profile.d/classpath.sh

ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>
export CLASSPATH=/usr/share/java/mysql-connector-java.jar:$CLASSPATH > /etc/profile.d/classpath.sh
```



## Stup root password for mysql:
```
[ec2-user@ip-10-0-0-47 ~]$ mysql_secure_installation




NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!


In order to log into MySQL to secure it, we'll need the current
password for the root user.  If you've just installed MySQL, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none):
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MySQL
root user without the proper authorisation.

Set root password? [Y/n] y
New password:
Re-enter new password:
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MySQL installation has an anonymous user, allowing anyone
to log into MySQL without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] y
 ... Success!

By default, MySQL comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] y
 ... Success!

Cleaning up...



All done!  If you've completed all of the above steps, your MySQL
installation should now be secure.

Thanks for using MySQL!
```

## Create databases
We need to create the databases needed by CDH"
```
[ec2-user@ip-10-0-0-47 ~]$ mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 10
Server version: 5.5.56 MySQL Community Server (GPL)

Copyright (c) 2000, 2017, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> create database scm DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

mysql> grant all on scm.* TO 'cloudera-scm'@'%' IDENTIFIED BY 'cloudera-scm';
Query OK, 0 rows affected (0.00 sec)

mysql> create database rman DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

mysql> grant all on rman.* TO 'rman'@'%' IDENTIFIED BY 'rman';
Query OK, 0 rows affected (0.00 sec)

mysql>  create database hive DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

mysql> grant all on hive.* TO 'hive'@'%' IDENTIFIED BY 'hive';
Query OK, 0 rows affected (0.00 sec)

mysql> create database hue DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

mysql> grant all on hue.* to 'hue'@'%' IDENTIFIED BY 'hue';
Query OK, 0 rows affected (0.00 sec)

mysql> create database oozie DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

mysql> grant all on oozie.* to 'oozie'@'%' IDENTIFIED BY 'oozie';
Query OK, 0 rows affected (0.00 sec)

mysql>  create database sentry DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

mysql>  grant all on sentry.* to 'sentry'@'%' IDENTIFIED BY 'sentry';
Query OK, 0 rows affected (0.00 sec)

mysql> exit
Bye
```