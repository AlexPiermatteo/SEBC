## Amazon instances info
* Region: eu-west-1a
* AMI ID: RHEL-7.2_HVM_GA-20151112-x86_64-1-Hourly2-GP2 (ami-8b8c57f8)
* OS: Red Hat 7.2

## Show the reserve space of any non-root, ext-based volumes
```
[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster all -a 'df -h'
ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2      100G  1.7G   99G   2% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   33M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000

ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2      100G  1.7G   99G   2% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   25M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000

ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2      100G  1.7G   99G   2% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G  180K  7.2G   1% /dev/shm
tmpfs           7.2G   25M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000

ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2      100G  1.7G   99G   2% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   25M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000

ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2      100G  1.7G   99G   2% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   25M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000
```

## Show releases
```
[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster all -a 'cat /etc/redhat-release'
ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Red Hat Enterprise Linux Server release 7.3 (Maipo)

ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Red Hat Enterprise Linux Server release 7.3 (Maipo)

ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Red Hat Enterprise Linux Server release 7.3 (Maipo)

ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Red Hat Enterprise Linux Server release 7.3 (Maipo)

ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Red Hat Enterprise Linux Server release 7.3 (Maipo)
```


## `yum repolist enabled`
```
[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster all -a 'sudo yum repolist enabled'
 [WARNING]: Consider using 'become', 'become_method', and 'become_user' rather than
running sudo

ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                           repo name               status
!rhui-REGION-client-config-server-7/x86_64        Red Hat Update Infrastr      6
!rhui-REGION-rhel-server-releases/7Server/x86_64  Red Hat Enterprise Linu 14,447
!rhui-REGION-rhel-server-rh-common/7Server/x86_64 Red Hat Enterprise Linu    228
repolist: 14,681

ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                           repo name               status
!rhui-REGION-client-config-server-7/x86_64        Red Hat Update Infrastr      6
!rhui-REGION-rhel-server-releases/7Server/x86_64  Red Hat Enterprise Linu 14,447
!rhui-REGION-rhel-server-rh-common/7Server/x86_64 Red Hat Enterprise Linu    228
repolist: 14,681

ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                           repo name               status
!rhui-REGION-client-config-server-7/x86_64        Red Hat Update Infrastr      6
!rhui-REGION-rhel-server-releases/7Server/x86_64  Red Hat Enterprise Linu 14,447
!rhui-REGION-rhel-server-rh-common/7Server/x86_64 Red Hat Enterprise Linu    228
repolist: 14,681

ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                           repo name               status
!epel/x86_64                                      Extra Packages for Ente 11,777
!rhui-REGION-client-config-server-7/x86_64        Red Hat Update Infrastr      6
!rhui-REGION-rhel-server-releases/7Server/x86_64  Red Hat Enterprise Linu 14,447
!rhui-REGION-rhel-server-rh-common/7Server/x86_64 Red Hat Enterprise Linu    228
repolist: 26,458

ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                           repo name               status
!rhui-REGION-client-config-server-7/x86_64        Red Hat Update Infrastr      6
!rhui-REGION-rhel-server-releases/7Server/x86_64  Red Hat Enterprise Linu 14,447
!rhui-REGION-rhel-server-rh-common/7Server/x86_64 Red Hat Enterprise Linu    228
repolist: 14,681
```

## Add Users

### Add users and groups
```
[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster all -a 'sudo useradd theresa -u 2000 '
 [WARNING]: Consider using 'become', 'become_method', and 'become_user' rather than
running sudo

ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>


[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster all -a 'sudo useradd jeremy -u 3000'

 [WARNING]: Consider using 'become', 'become_method', and 'become_user' rather than
running sudo

ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>


[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster all -a 'sudo groupadd conservative - g 1001'
 [WARNING]: Consider using 'become', 'become_method', and 'become_user' rather than
running sudo

ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>


[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster all -a 'sudo groupadd labour -g 1002 '
 [WARNING]: Consider using 'become', 'become_method', and 'become_user' rather than
running sudo

ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>


[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster all -a 'sudo usermod -aG conservativ e theresa'
 [WARNING]: Consider using 'become', 'become_method', and 'become_user' rather than
running sudo

ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>


[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster all -a 'sudo usermod -aG labour jere my'
 [WARNING]: Consider using 'become', 'become_method', and 'become_user' rather than
running sudo

ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>

```

### List `/etc/passwd` and `/etc/group`
```
[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster all -a 'getent passwd theresa'
ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>
theresa:x:2000:2000::/home/theresa:/bin/bash

ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>
theresa:x:2000:2000::/home/theresa:/bin/bash

ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>
theresa:x:2000:2000::/home/theresa:/bin/bash

ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>
theresa:x:2000:2000::/home/theresa:/bin/bash

ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>
theresa:x:2000:2000::/home/theresa:/bin/bash

[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster all -a 'getent passwd jeremy'
ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>
jeremy:x:3000:3000::/home/jeremy:/bin/bash

ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>
jeremy:x:3000:3000::/home/jeremy:/bin/bash

ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>
jeremy:x:3000:3000::/home/jeremy:/bin/bash

ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>
jeremy:x:3000:3000::/home/jeremy:/bin/bash

ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>
jeremy:x:3000:3000::/home/jeremy:/bin/bash

[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster all -a 'getent group conservative'
ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>
conservative:x:1001:theresa

ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>
conservative:x:1001:theresa

ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>
conservative:x:1001:theresa

ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>
conservative:x:1001:theresa

ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>
conservative:x:1001:theresa

[ec2-user@ip-10-0-0-47 ~]$ ansible -i alexcluster all -a 'getent group labour'
ip-10-0-0-184.eu-west-1.compute.internal | SUCCESS | rc=0 >>
labour:x:1002:jeremy

ip-10-0-0-201.eu-west-1.compute.internal | SUCCESS | rc=0 >>
labour:x:1002:jeremy

ip-10-0-0-124.eu-west-1.compute.internal | SUCCESS | rc=0 >>
labour:x:1002:jeremy

ip-10-0-0-23.eu-west-1.compute.internal | SUCCESS | rc=0 >>
labour:x:1002:jeremy

ip-10-0-0-47.eu-west-1.compute.internal | SUCCESS | rc=0 >>
labour:x:1002:jeremy
```