## Stop Hive Service
```
[ec2-user@ip-10-0-0-22 ~]$ curl -X POST -u AlexPiermatteo:cloudera 'http://ec2-54-194-118-24.eu-west-1.compute.amazonaws.com:7180/api/v2/clusters/AlexPiermatteo/services/hive/commands/stop'
{
  "id" : 419,
  "name" : "Stop",
  "startTime" : "2017-06-07T08:55:03.358Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```

## Start Hive Service
```
[ec2-user@ip-10-0-0-22 ~]$ curl -X POST -u AlexPiermatteo:cloudera 'http://ec2-54-194-118-24.eu-west-1.compute.amazonaws.com:7180/api/v2/clusters/AlexPiermatteo/services/hive/commands/start'
{
  "id" : 423,
  "name" : "Start",
  "startTime" : "2017-06-07T08:56:19.659Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```

## Check State Hive Service
```
[ec2-user@ip-10-0-0-22 ~]$ curl -u AlexPiermatteo:cloudera 'http://ec2-54-194-118-24.eu-west-1.compute.amazonaws.com:7180/api/v2/clusters/AlexPiermatteo/services/hive'
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-10-0-0-22.eu-west-1.compute.internal:7180/cmf/serviceRedirect/hive",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD"
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD"
  } ],
  "configStale" : false,
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive"
}
```