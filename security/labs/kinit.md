## kinit and klist command to authenticate my user

```
[ec2-user@ip-10-0-0-22 ~]$ kinit alexpiermatteo@HASHTAG.LOCAL
Password for alexpiermatteo@HASHTAG.LOCAL:
[ec2-user@ip-10-0-0-22 ~]$
[ec2-user@ip-10-0-0-22 ~]$
[ec2-user@ip-10-0-0-22 ~]$
[ec2-user@ip-10-0-0-22 ~]$ klist
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: alexpiermatteo@HASHTAG.LOCAL

Valid starting       Expires              Service principal
06/07/2017 08:19:11  06/08/2017 08:19:11  krbtgt/HASHTAG.LOCAL@HASHTAG.LOCAL
        renew until 06/14/2017 08:19:11
```
