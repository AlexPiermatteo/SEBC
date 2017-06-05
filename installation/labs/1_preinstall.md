## 1. Check `vm.swappiness` on all your nodes
```
[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster all -a 'sudo sysctl vm.swappiness'

ip-10-0-0-206.eu-west-1.compute.internal | SUCCESS | rc=0 >>
vm.swappiness = 30

ip-10-0-0-120.eu-west-1.compute.internal | SUCCESS | rc=0 >>
vm.swappiness = 30

ip-10-0-0-223.eu-west-1.compute.internal | SUCCESS | rc=0 >>
vm.swappiness = 30

ip-10-0-0-161.eu-west-1.compute.internal | SUCCESS | rc=0 >>
vm.swappiness = 30

ip-10-0-0-22.eu-west-1.compute.internal | SUCCESS | rc=0 >>
vm.swappiness = 30
```
The default swappiness is 30, needs to be changed to one:
```
[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster all -a 'sudo sysctl vm.swappiness=1'
 [WARNING]: Consider using 'become', 'become_method', and 'become_user' rather than running sudo

ip-10-0-0-206.eu-west-1.compute.internal | SUCCESS | rc=0 >>
vm.swappiness = 1

ip-10-0-0-223.eu-west-1.compute.internal | SUCCESS | rc=0 >>
vm.swappiness = 1

ip-10-0-0-161.eu-west-1.compute.internal | SUCCESS | rc=0 >>
vm.swappiness = 1

ip-10-0-0-120.eu-west-1.compute.internal | SUCCESS | rc=0 >>
vm.swappiness = 1

ip-10-0-0-22.eu-west-1.compute.internal | SUCCESS | rc=0 >>
vm.swappiness = 1
```
Check if the swappiness is correctly configured:
```
[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster all -a 'sudo sysctl vm.swappiness'

ip-10-0-0-206.eu-west-1.compute.internal | SUCCESS | rc=0 >>
vm.swappiness = 1

ip-10-0-0-161.eu-west-1.compute.internal | SUCCESS | rc=0 >>
vm.swappiness = 1

ip-10-0-0-120.eu-west-1.compute.internal | SUCCESS | rc=0 >>
vm.swappiness = 1

ip-10-0-0-223.eu-west-1.compute.internal | SUCCESS | rc=0 >>
vm.swappiness = 1

ip-10-0-0-22.eu-west-1.compute.internal | SUCCESS | rc=0 >>
vm.swappiness = 1
```

## 2. Show the mount attributes of all volumes
Result of the command `mount`:
``` 
[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster all -a 'mount'
 [WARNING]: Consider using mount module rather than running mount

ip-10-0-0-223.eu-west-1.compute.internal | SUCCESS | rc=0 >>
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime,seclabel)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
devtmpfs on /dev type devtmpfs (rw,nosuid,seclabel,size=7599360k,nr_inodes=1899840,mode=755)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev,seclabel)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,seclabel,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,seclabel,mode=755)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,seclabel,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/usr/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/net_cls type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpuacct,cpu)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
configfs on /sys/kernel/config type configfs (rw,relatime)
/dev/xvda2 on / type xfs (rw,relatime,seclabel,attr2,inode64,noquota)
selinuxfs on /sys/fs/selinux type selinuxfs (rw,relatime)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=29,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime,seclabel)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,seclabel)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,seclabel,size=1497312k,mode=700,uid=1000,gid=1000)

ip-10-0-0-206.eu-west-1.compute.internal | SUCCESS | rc=0 >>
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime,seclabel)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
devtmpfs on /dev type devtmpfs (rw,nosuid,seclabel,size=7599360k,nr_inodes=1899840,mode=755)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev,seclabel)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,seclabel,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,seclabel,mode=755)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,seclabel,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/usr/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpuacct,cpu)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/net_cls type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
configfs on /sys/kernel/config type configfs (rw,relatime)
/dev/xvda2 on / type xfs (rw,relatime,seclabel,attr2,inode64,noquota)
selinuxfs on /sys/fs/selinux type selinuxfs (rw,relatime)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=31,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime,seclabel)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,seclabel)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,seclabel,size=1497312k,mode=700,uid=1000,gid=1000)

ip-10-0-0-120.eu-west-1.compute.internal | SUCCESS | rc=0 >>
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime,seclabel)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
devtmpfs on /dev type devtmpfs (rw,nosuid,seclabel,size=7599360k,nr_inodes=1899840,mode=755)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev,seclabel)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,seclabel,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,seclabel,mode=755)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,seclabel,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/usr/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpuacct,cpu)
cgroup on /sys/fs/cgroup/net_cls type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
configfs on /sys/kernel/config type configfs (rw,relatime)
/dev/xvda2 on / type xfs (rw,relatime,seclabel,attr2,inode64,noquota)
selinuxfs on /sys/fs/selinux type selinuxfs (rw,relatime)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=31,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime,seclabel)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,seclabel)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,seclabel,size=1497312k,mode=700,uid=1000,gid=1000)

ip-10-0-0-161.eu-west-1.compute.internal | SUCCESS | rc=0 >>
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime,seclabel)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
devtmpfs on /dev type devtmpfs (rw,nosuid,seclabel,size=7599360k,nr_inodes=1899840,mode=755)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev,seclabel)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,seclabel,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,seclabel,mode=755)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,seclabel,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/usr/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpuacct,cpu)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/net_cls type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
configfs on /sys/kernel/config type configfs (rw,relatime)
/dev/xvda2 on / type xfs (rw,relatime,seclabel,attr2,inode64,noquota)
selinuxfs on /sys/fs/selinux type selinuxfs (rw,relatime)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=30,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime,seclabel)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,seclabel)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,seclabel,size=1497312k,mode=700,uid=1000,gid=1000)

ip-10-0-0-22.eu-west-1.compute.internal | SUCCESS | rc=0 >>
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime,seclabel)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
devtmpfs on /dev type devtmpfs (rw,nosuid,seclabel,size=7599360k,nr_inodes=1899840,mode=755)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev,seclabel)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,seclabel,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,seclabel,mode=755)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,seclabel,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/usr/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpuacct,cpu)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
configfs on /sys/kernel/config type configfs (rw,relatime)
/dev/xvda2 on / type xfs (rw,relatime,seclabel,attr2,inode64,noquota)
selinuxfs on /sys/fs/selinux type selinuxfs (rw,relatime)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=31,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime,seclabel)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,seclabel)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,seclabel,size=1497312k,mode=700,uid=1000,gid=1000)
```

## 3. Show the reserve space of any non-root, ext-based volumes
```
[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster all -a 'df -h'
ip-10-0-0-120.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2      100G  1.7G   99G   2% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   25M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000

ip-10-0-0-206.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2      100G  1.7G   99G   2% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   25M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000

ip-10-0-0-223.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2      100G  1.7G   99G   2% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   25M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000

ip-10-0-0-22.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2      100G  1.7G   99G   2% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G  180K  7.2G   1% /dev/shm
tmpfs           7.2G   25M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000

ip-10-0-0-161.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2      100G  1.7G   99G   2% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   25M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000
```
```
[ec2-user@ip-10-0-0-22 ~]$ sudo fdisk -l
WARNING: fdisk GPT support is currently new, and therefore in an experimental phase. Use at your own discretion.

Disk /dev/xvda: 107.4 GB, 107374182400 bytes, 209715200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk label type: gpt


#         Start          End    Size  Type            Name
 1         2048         4095      1M  BIOS boot parti
 2         4096    209715166    100G  Microsoft basic
 ```

 ## 4. Disable the transparent hugepages
```
[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster  all -a "bash -c \"echo never > /sys/k ernel/mm/transparent_hugepage/defrag\"" --become
ip-10-0-0-206.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-161.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-223.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-120.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-22.eu-west-1.compute.internal | SUCCESS | rc=0 >>


[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster  all -a "bash -c \"echo never > /sys/k ernel/mm/transparent_hugepage/enabled\"" --become
ip-10-0-0-120.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-161.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-206.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-223.eu-west-1.compute.internal | SUCCESS | rc=0 >>


ip-10-0-0-22.eu-west-1.compute.internal | SUCCESS | rc=0 >>

```

## 5. Report the network interface attributes
```
[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster all -a 'sudo ifconfig'
 [WARNING]: Consider using 'become', 'become_method', and 'become_user' rather than running sudo

ip-10-0-0-120.eu-west-1.compute.internal | SUCCESS | rc=0 >>
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 10.0.0.120  netmask 255.255.255.0  broadcast 10.0.0.255
        inet6 fe80::413:43ff:fe1b:4968  prefixlen 64  scopeid 0x20<link>
        ether 06:13:43:1b:49:68  txqueuelen 1000  (Ethernet)
        RX packets 183298  bytes 268847946 (256.3 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 65747  bytes 5955402 (5.6 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 4  bytes 340 (340.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4  bytes 340 (340.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

ip-10-0-0-22.eu-west-1.compute.internal | SUCCESS | rc=0 >>
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 10.0.0.22  netmask 255.255.255.0  broadcast 10.0.0.255
        inet6 fe80::423:2dff:fe12:69d2  prefixlen 64  scopeid 0x20<link>
        ether 06:23:2d:12:69:d2  txqueuelen 1000  (Ethernet)
        RX packets 208564  bytes 283875362 (270.7 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 66764  bytes 11783562 (11.2 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 1657  bytes 1095134 (1.0 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1657  bytes 1095134 (1.0 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

ip-10-0-0-206.eu-west-1.compute.internal | SUCCESS | rc=0 >>
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 10.0.0.206  netmask 255.255.255.0  broadcast 10.0.0.255
        inet6 fe80::42b:10ff:fe85:476c  prefixlen 64  scopeid 0x20<link>
        ether 06:2b:10:85:47:6c  txqueuelen 1000  (Ethernet)
        RX packets 183892  bytes 269440575 (256.9 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 53802  bytes 5166287 (4.9 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 4  bytes 340 (340.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4  bytes 340 (340.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

ip-10-0-0-161.eu-west-1.compute.internal | SUCCESS | rc=0 >>
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 10.0.0.161  netmask 255.255.255.0  broadcast 10.0.0.255
        inet6 fe80::41c:dfff:fe95:751a  prefixlen 64  scopeid 0x20<link>
        ether 06:1c:df:95:75:1a  txqueuelen 1000  (Ethernet)
        RX packets 184357  bytes 269072251 (256.6 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 63891  bytes 6065914 (5.7 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 4  bytes 340 (340.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4  bytes 340 (340.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

ip-10-0-0-223.eu-west-1.compute.internal | SUCCESS | rc=0 >>
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 10.0.0.223  netmask 255.255.255.0  broadcast 10.0.0.255
        inet6 fe80::40a:2eff:fe28:6606  prefixlen 64  scopeid 0x20<link>
        ether 06:0a:2e:28:66:06  txqueuelen 1000  (Ethernet)
        RX packets 183503  bytes 268855574 (256.4 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 52778  bytes 5091187 (4.8 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 4  bytes 340 (340.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4  bytes 340 (340.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

## 6. Show forward and reverse host lookups using `getent` and `nslookup`
```
[ec2-user@ip-10-0-0-22 ~]$ getent hosts ip-10-0-0-22
10.0.0.22       ip-10-0-0-22.eu-west-1.compute.internal
[ec2-user@ip-10-0-0-22 ~]$ getent hosts ip-10-0-0-206
10.0.0.206      ip-10-0-0-206.eu-west-1.compute.internal
[ec2-user@ip-10-0-0-22 ~]$ getent hosts ip-10-0-0-223
10.0.0.223      ip-10-0-0-223.eu-west-1.compute.internal
[ec2-user@ip-10-0-0-22 ~]$ getent hosts ip-10-0-0-161
10.0.0.161      ip-10-0-0-161.eu-west-1.compute.internal
[ec2-user@ip-10-0-0-22 ~]$ getent hosts ip-10-0-0-120
10.0.0.120      ip-10-0-0-120.eu-west-1.compute.internal
```
```
[ec2-user@ip-10-0-0-22 ~]$ nslookup ip-10-0-0-22
Server:         10.0.0.2
Address:        10.0.0.2#53

Non-authoritative answer:
Name:   ip-10-0-0-22.eu-west-1.compute.internal
Address: 10.0.0.22

[ec2-user@ip-10-0-0-22 ~]$ nslookup ip-10-0-0-206
Server:         10.0.0.2
Address:        10.0.0.2#53

Non-authoritative answer:
Name:   ip-10-0-0-206.eu-west-1.compute.internal
Address: 10.0.0.206

[ec2-user@ip-10-0-0-22 ~]$ nslookup ip-10-0-0-223
Server:         10.0.0.2
Address:        10.0.0.2#53

Non-authoritative answer:
Name:   ip-10-0-0-223.eu-west-1.compute.internal
Address: 10.0.0.223

[ec2-user@ip-10-0-0-22 ~]$ nslookup ip-10-0-0-161
Server:         10.0.0.2
Address:        10.0.0.2#53

Non-authoritative answer:
Name:   ip-10-0-0-161.eu-west-1.compute.internal
Address: 10.0.0.161

[ec2-user@ip-10-0-0-22 ~]$ nslookup ip-10-0-0-120
Server:         10.0.0.2
Address:        10.0.0.2#53

Non-authoritative answer:
Name:   ip-10-0-0-120.eu-west-1.compute.internal
Address: 10.0.0.120
```

## 7. Verify the <code>nscd</code> service is running
The `nscd` service is not installed, so it has to be installed on every node. To do that, the following command has been executed:
```
ansible -i alexcluster all -a 'sudo yum install -y nscd'
```
And then the service has been started on every node:
```
[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster all -a 'sudo service nscd restart'
 [WARNING]: Consider using 'become', 'become_method', and 'become_user' rather than running sudo

ip-10-0-0-223.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Redirecting to /bin/systemctl restart  nscd.service

ip-10-0-0-206.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Redirecting to /bin/systemctl restart  nscd.service

ip-10-0-0-120.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Redirecting to /bin/systemctl restart  nscd.service

ip-10-0-0-22.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Redirecting to /bin/systemctl restart  nscd.service

ip-10-0-0-161.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Redirecting to /bin/systemctl restart  nscd.service
```
To check that the service is running, simply run the following command:
```
[ec2-user@ip-10-0-0-22 ~]$ sudo service nscd status
Redirecting to /bin/systemctl status  nscd.service
● nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2017-06-05 09:38:03 EDT; 52s ago
  Process: 28824 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 28825 (nscd)
   CGroup: /system.slice/nscd.service
           └─28825 /usr/sbin/nscd

Jun 05 09:38:03 ip-10-0-0-22.eu-west-1.compute.internal nscd[28825]: 28825 monitoring directory `/etc` (2)
Jun 05 09:38:03 ip-10-0-0-22.eu-west-1.compute.internal nscd[28825]: 28825 monitoring file `/etc/resolv.conf` (5)
Jun 05 09:38:03 ip-10-0-0-22.eu-west-1.compute.internal nscd[28825]: 28825 monitoring directory `/etc` (2)
Jun 05 09:38:03 ip-10-0-0-22.eu-west-1.compute.internal nscd[28825]: 28825 monitoring file `/etc/services` (6)
Jun 05 09:38:03 ip-10-0-0-22.eu-west-1.compute.internal nscd[28825]: 28825 monitoring directory `/etc` (2)
Jun 05 09:38:03 ip-10-0-0-22.eu-west-1.compute.internal nscd[28825]: 28825 disabled inotify-based monitoring for file `/etc/netgroup': No ...ctory

Jun 05 09:38:03 ip-10-0-0-22.eu-west-1.compute.internal nscd[28825]: 28825 stat failed for file `/etc/netgroup'; will try again later: No ...ctory

Jun 05 09:38:03 ip-10-0-0-22.eu-west-1.compute.internal nscd[28825]: 28825 Access Vector Cache (AVC) started
Jun 05 09:38:03 ip-10-0-0-22.eu-west-1.compute.internal systemd[1]: Started Name Service Cache Daemon.
Jun 05 09:38:22 ip-10-0-0-22.eu-west-1.compute.internal nscd[28825]: 28825 checking for monitored file `/etc/netgroup': No such file or directory Hint: Some lines were ellipsized, use -l to show in full.
```

## 8. Verify the <code>ntpd</code> service is running<br>
As for the previous service, `ntpd` has to be installed on every node. 
To do that, the following command was used:
```
ansible -i alexcluster all -a 'sudo yum install -y ntp'
```
Once the service was installed, we just need to start it and check that it's properly working:
```
[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster all -a 'sudo service ntpd restart'
 [WARNING]: Consider using 'become', 'become_method', and 'become_user' rather than running sudo

ip-10-0-0-206.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Redirecting to /bin/systemctl restart  ntpd.service

ip-10-0-0-120.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Redirecting to /bin/systemctl restart  ntpd.service

ip-10-0-0-223.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Redirecting to /bin/systemctl restart  ntpd.service

ip-10-0-0-22.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Redirecting to /bin/systemctl restart  ntpd.service

ip-10-0-0-161.eu-west-1.compute.internal | SUCCESS | rc=0 >>
Redirecting to /bin/systemctl restart  ntpd.service
```
```
[ec2-user@ip-10-0-0-22 ~]$ sudo service ntpd status
Redirecting to /bin/systemctl status  ntpd.service
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2017-06-05 09:40:14 EDT; 23s ago
  Process: 29155 ExecStart=/usr/sbin/ntpd -u ntp:ntp $OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 29156 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─29156 /usr/sbin/ntpd -u ntp:ntp -g

Jun 05 09:40:14 ip-10-0-0-22.eu-west-1.compute.internal ntpd[29156]: Listen normally on 2 lo 127.0.0.1 UDP 123
Jun 05 09:40:14 ip-10-0-0-22.eu-west-1.compute.internal ntpd[29156]: Listen normally on 3 eth0 10.0.0.22 UDP 123
Jun 05 09:40:14 ip-10-0-0-22.eu-west-1.compute.internal ntpd[29156]: Listen normally on 4 lo ::1 UDP 123
Jun 05 09:40:14 ip-10-0-0-22.eu-west-1.compute.internal ntpd[29156]: Listen normally on 5 eth0 fe80::423:2dff:fe12:69d2 UDP 123
Jun 05 09:40:14 ip-10-0-0-22.eu-west-1.compute.internal ntpd[29156]: Listening on routing socket on fd #22 for interface updates
Jun 05 09:40:14 ip-10-0-0-22.eu-west-1.compute.internal systemd[1]: Started Network Time Service.
Jun 05 09:40:14 ip-10-0-0-22.eu-west-1.compute.internal ntpd[29156]: 0.0.0.0 c016 06 restart
Jun 05 09:40:14 ip-10-0-0-22.eu-west-1.compute.internal ntpd[29156]: 0.0.0.0 c012 02 freq_set kernel 0.000 PPM
Jun 05 09:40:14 ip-10-0-0-22.eu-west-1.compute.internal ntpd[29156]: 0.0.0.0 c011 01 freq_not_set
Jun 05 09:40:21 ip-10-0-0-22.eu-west-1.compute.internal ntpd[29156]: 0.0.0.0 c614 04 freq_mode
```