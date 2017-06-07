## Upgrade to the latest C5.9 release
I already had the latest version installed on my cluster (5.11)


## Report the latest version of the API
```
[ec2-user@ip-10-0-0-22 ~]$ curl -u AlexPiermatteo:cloudera 'http://ec2-54-194-118-24.eu-west-1.compute.amazonaws.com:7180/api/version'
v16
```

## Report the CM version
```
[ec2-user@ip-10-0-0-22 ~]$ curl -u AlexPiermatteo:cloudera 'http://ec2-54-194-118-24.eu-west-1.compute.amazonaws.com:7180/api/v16/cm/version'
{
  "version" : "5.11.0",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20170412-1255",
  "gitHash" : "70cb1442626406432a6e7af5bdf206a384ca3f98",
  "snapshot" : false
}
```

## List all CM users
```
[ec2-user@ip-10-0-0-22 ~]$ curl -u AlexPiermatteo:cloudera 'http://ec2-54-194-118-24.eu-west-1.compute.amazonaws.com:7180/api/v16/users'
{
  "items" : [ {
    "name" : "AlexPiermatteo",
    "roles" : [ "ROLE_ADMIN" ]
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ]
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  } ]
}
```

## Report the database server in use by CM
```
[ec2-user@ip-10-0-0-22 ~]$ curl -u AlexPiermatteo:cloudera 'http://ec2-54-194-118-24.eu-west-1.compute.amazonaws.com:7180/api/v16/cm/scmDbInfo'
{
  "scmDbType" : "MYSQL",
  "embeddedDbUsed" : false
}
```
