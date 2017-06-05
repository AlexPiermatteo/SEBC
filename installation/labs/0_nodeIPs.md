# Node Ips & names
## /etc/hosts
```
[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster all -a 'cat /etc/hosts'
ip-10-0-0-206.eu-west-1.compute.internal | SUCCESS | rc=0 >>
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6

10.0.0.22       ip-10-0-0-22.eu-west-1.compute.internal         sebc1
10.0.0.206      ip-10-0-0-206.eu-west-1.compute.internal        sebc2
10.0.0.223      ip-10-0-0-223.eu-west-1.compute.internal        sebc3
10.0.0.161      ip-10-0-0-161.eu-west-1.compute.internal        sebc4
10.0.0.120      ip-10-0-0-120.eu-west-1.compute.internal        sebc5

ip-10-0-0-161.eu-west-1.compute.internal | SUCCESS | rc=0 >>
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6

10.0.0.22       ip-10-0-0-22.eu-west-1.compute.internal         sebc1
10.0.0.206      ip-10-0-0-206.eu-west-1.compute.internal        sebc2
10.0.0.223      ip-10-0-0-223.eu-west-1.compute.internal        sebc3
10.0.0.161      ip-10-0-0-161.eu-west-1.compute.internal        sebc4
10.0.0.120      ip-10-0-0-120.eu-west-1.compute.internal        sebc5

ip-10-0-0-120.eu-west-1.compute.internal | SUCCESS | rc=0 >>
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6

10.0.0.22       ip-10-0-0-22.eu-west-1.compute.internal         sebc1
10.0.0.206      ip-10-0-0-206.eu-west-1.compute.internal        sebc2
10.0.0.223      ip-10-0-0-223.eu-west-1.compute.internal        sebc3
10.0.0.161      ip-10-0-0-161.eu-west-1.compute.internal        sebc4
10.0.0.120      ip-10-0-0-120.eu-west-1.compute.internal        sebc5

ip-10-0-0-223.eu-west-1.compute.internal | SUCCESS | rc=0 >>
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6

10.0.0.22       ip-10-0-0-22.eu-west-1.compute.internal         sebc1
10.0.0.206      ip-10-0-0-206.eu-west-1.compute.internal        sebc2
10.0.0.223      ip-10-0-0-223.eu-west-1.compute.internal        sebc3
10.0.0.161      ip-10-0-0-161.eu-west-1.compute.internal        sebc4
10.0.0.120      ip-10-0-0-120.eu-west-1.compute.internal        sebc5

ip-10-0-0-22.eu-west-1.compute.internal | SUCCESS | rc=0 >>
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6

10.0.0.22       ip-10-0-0-22.eu-west-1.compute.internal         sebc1
10.0.0.206      ip-10-0-0-206.eu-west-1.compute.internal        sebc2
10.0.0.223      ip-10-0-0-223.eu-west-1.compute.internal        sebc3
10.0.0.161      ip-10-0-0-161.eu-west-1.compute.internal        sebc4
10.0.0.120      ip-10-0-0-120.eu-west-1.compute.internal        sebc5
```

## /etc/hostname
```
[ec2-user@ip-10-0-0-22 ~]$ ansible -i alexcluster all -a 'cat /etc/hostname'
ip-10-0-0-223.eu-west-1.compute.internal | SUCCESS | rc=0 >>
ip-10-0-0-223.eu-west-1.compute.internal

ip-10-0-0-120.eu-west-1.compute.internal | SUCCESS | rc=0 >>
ip-10-0-0-120.eu-west-1.compute.internal

ip-10-0-0-161.eu-west-1.compute.internal | SUCCESS | rc=0 >>
ip-10-0-0-161.eu-west-1.compute.internal

ip-10-0-0-22.eu-west-1.compute.internal | SUCCESS | rc=0 >>
ip-10-0-0-22.eu-west-1.compute.internal

ip-10-0-0-206.eu-west-1.compute.internal | SUCCESS | rc=0 >>
ip-10-0-0-206.eu-west-1.compute.internal
```