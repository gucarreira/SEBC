# Questions

## What is ubertask optimization?
Usually, Yarn starts a JVM for each job (MAP, REDUCE, others), what makes the process slow. Ubertask optimization runs small jobs sequentially within a single JVM. What is considered small is a set of configurations composed of 3 properties, the number of maps, the number of reducers and the amount of bytes for each task.

## Where in CM is the Kerberos Security Realm value displayed?
Cloudera Manager > Administration > Security

## Which CDH service(s) host a property for enabling Kerberos authentication?
Hive, Zookeeper, Hue, Oozie, HDFS, Yarn, Cloudera Management Service

## How do you upgrade the CM agents?
You can upgrade the CM Agents in 2 ways: 
* Upgrade and Start Cloudera Manager Agent (Packages)
* Restart Cloudera Manager Agents (Tarballs)

## Give the tsquery statement used to chart Hue's CPU utilization?
SELECT cpu_system_rate + cpu_user_rate WHERE entityName = "hue-HUE_SERVER-b4e26d7f440e4479241e7aeeede94b53" AND category = ROLE

## Name all the roles that make up the Hive service
HiveServer2, Hive Metastore Server and Gateway

## What steps must be completed before integrating Cloudera Manager with Kerberos?
* Set up a working KDC. Cloudera Manager supports MIT KDC and Active Directory.
* The KDC should be configured to have non-zero ticket lifetime and renewal lifetime. CDH will not work properly if tickets are not renewable.
* OpenLdap client libraries should be installed on the Cloudera Manager Server host if you want to use Active Directory. Also, Kerberos client libraries should be installed on ALL hosts.
* Cloudera Manager needs an account that has permissions to create other accounts in the KDC.