## Install cloudera manager server
The first step is to add the repo on every node:
```
[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster  all -a 'wget https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/cloudera-manager.repo'
 [WARNING]: Consider using get_url or uri module rather than running wget

ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>
--2017-06-09 05:12:34--  https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/cloudera-manager.repo
Resolving archive.cloudera.com (archive.cloudera.com)... 151.101.60.167
Connecting to archive.cloudera.com (archive.cloudera.com)|151.101.60.167|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 290
Saving to: ‘cloudera-manager.repo’

     0K                                                       100% 72.9M=0s

2017-06-09 05:12:34 (72.9 MB/s) - ‘cloudera-manager.repo’ saved [290/290]

ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>
--2017-06-09 05:12:34--  https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/cloudera-manager.repo
Resolving archive.cloudera.com (archive.cloudera.com)... 151.101.60.167
Connecting to archive.cloudera.com (archive.cloudera.com)|151.101.60.167|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 290
Saving to: ‘cloudera-manager.repo’

     0K                                                       100% 55.2M=0s

2017-06-09 05:12:34 (55.2 MB/s) - ‘cloudera-manager.repo’ saved [290/290]

ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>
--2017-06-09 05:12:34--  https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/cloudera-manager.repo
Resolving archive.cloudera.com (archive.cloudera.com)... 151.101.60.167
Connecting to archive.cloudera.com (archive.cloudera.com)|151.101.60.167|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 290
Saving to: ‘cloudera-manager.repo’

     0K                                                       100% 69.0M=0s

2017-06-09 05:12:34 (69.0 MB/s) - ‘cloudera-manager.repo’ saved [290/290]

ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>
--2017-06-09 05:12:34--  https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/cloudera-manager.repo
Resolving archive.cloudera.com (archive.cloudera.com)... 151.101.60.167
Connecting to archive.cloudera.com (archive.cloudera.com)|151.101.60.167|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 290
Saving to: ‘cloudera-manager.repo’

     0K                                                       100% 53.2M=0s

2017-06-09 05:12:34 (53.2 MB/s) - ‘cloudera-manager.repo’ saved [290/290]

ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>
--2017-06-09 05:12:34--  https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/cloudera-manager.repo
Resolving archive.cloudera.com (archive.cloudera.com)... 151.101.60.167
Connecting to archive.cloudera.com (archive.cloudera.com)|151.101.60.167|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 290
Saving to: ‘cloudera-manager.repo’

     0K                                                       100% 52.2M=0s

2017-06-09 05:12:34 (52.2 MB/s) - ‘cloudera-manager.repo’ saved [290/290]

[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster  all -a 'sudo cp cloudera-manager.re

po /etc/yum.repos.d'
 [WARNING]: Consider using 'become', 'become_method', and 'become_user' rather than
running sudo

ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>
```






We can now install cloudera manger server on node sebc2 (54.171.68.247):
```
[ec2-user@ip-10-1-0-7 ~]$ sudo yum install -y cloudera-manager-server cloudera-manager-daemons
```

And ran `scm_prepare_database.sh`:
```
sudo /usr/share/cmf/schema/scm_prepare_database.sh -u root --password=cloudera  --force mysql scm cloudera-scm cloudera-scm -h ip-10-0-0-47.eu-west-1.compute.internal
```

We can now start cloudra-scm-server:
```
[ec2-user@ip-10-0-0-124 ~]$ sudo service cloudera-scm-server start
Starting cloudera-scm-server (via systemctl):              [  OK  ]
```