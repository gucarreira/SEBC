# Hive Status
```
[centos@ip-172-31-7-135 ~]$ curl -u vvaldevite:cloudera  'http://localhost:7180/api/v1/clusters/vvaldevite/services/hive'
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-172-31-7-135.us-west-2.compute.internal:7180/cmf/serviceRedirect/hive",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD"
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD"
  } ],
  "configStale" : false
}
```

# Hive Stop
```
[centos@ip-172-31-7-135 ~]$ curl -X POST -u vvaldevite:cloudera  'http://localhost:7180/api/v12/clusters/vvaldevite/services/hive/commands/stop'
{
  "id" : 621,
  "name" : "Stop",
  "startTime" : "2017-04-05T14:02:22.735Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```

# Hive Start
```
[centos@ip-172-31-7-135 ~]$ curl -X POST -u vvaldevite:cloudera  'http://localhost:7180/api/v12/clusters/vvaldevite/services/hive/commands/start'
{
  "id" : 625,
  "name" : "Start",
  "startTime" : "2017-04-05T14:03:28.347Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```