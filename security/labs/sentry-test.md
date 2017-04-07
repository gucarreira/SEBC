# Verify user privileges
Not enought privileges to use a database neither to show tables.
```
[root@ip-172-31-8-114 centos]# beeline
Beeline version 1.1.0-cdh5.10.1 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-8-114.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-8-114.us-west-2.compute.internal@HADOOP.LOCAL
Connecting to jdbc:hive2://ip-172-31-8-114.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-8-114.us-west-2.compute.internal@HADOOP.LOCAL
Connected to: Apache Hive (version 1.1.0-cdh5.10.1)
Driver: Hive JDBC (version 1.1.0-cdh5.10.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com> show databases;
INFO  : Compiling command(queryId=hive_20170406010202_f143d3df-591d-44bb-9143-eb74e4c277d7): show databases
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:database_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170406010202_f143d3df-591d-44bb-9143-eb74e4c277d7); Time taken: 0.66 seconds
INFO  : Executing command(queryId=hive_20170406010202_f143d3df-591d-44bb-9143-eb74e4c277d7): show databases
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170406010202_f143d3df-591d-44bb-9143-eb74e4c277d7); Time taken: 0.215 seconds
INFO  : OK
+----------------+--+
| database_name  |
+----------------+--+
| default        |
+----------------+--+
1 row selected (2.28 seconds)
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com> show tables;
INFO  : Compiling command(queryId=hive_20170406010303_9d7b1de1-b712-400f-8ef1-711c72e32bc5): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170406010303_9d7b1de1-b712-400f-8ef1-711c72e32bc5); Time taken: 0.1 seconds
INFO  : Executing command(queryId=hive_20170406010303_9d7b1de1-b712-400f-8ef1-711c72e32bc5): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170406010303_9d7b1de1-b712-400f-8ef1-711c72e32bc5); Time taken: 0.136 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (0.259 seconds)
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com> use default;
Error: Error while compiling statement: FAILED: SemanticException No valid privileges
 User vvaldevite does not have privileges for SWITCHDATABASE
 The required privileges: Server=server1->Db=*->Table=+->Column=*->action=select;Server=server1->Db=*->Table=+->Column=*->action=insert; (state=42000,code=40000)
```

## Grant priveleges for group vvaldevite
```
[vvaldevite@ip-172-31-8-114 ~]$ kinit hive
Password for hive@HADOOP.LOCAL:
[vvaldevite@ip-172-31-8-114 ~]$ beeline
Beeline version 1.1.0-cdh5.10.1 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-8-114.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-8-114.us-west-2.compute.internal@HADOOP.LOCAL
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-8-114.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-8-114.us-west-2.compute.internal@HADOOP.LOCAL
Connected to: Apache Hive (version 1.1.0-cdh5.10.1)
Driver: Hive JDBC (version 1.1.0-cdh5.10.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
****************
I LOST THE CREATE ROLE sentry_admin; COMMAND
****************
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20170406123535_21a20fc5-d54f-45a1-9f53-3ee167d03128): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170406123535_21a20fc5-d54f-45a1-9f53-3ee167d03128); Time taken: 0.054 seconds
INFO  : Executing command(queryId=hive_20170406123535_21a20fc5-d54f-45a1-9f53-3ee167d03128): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170406123535_21a20fc5-d54f-45a1-9f53-3ee167d03128); Time taken: 0.021 seconds
INFO  : OK
No rows affected (0.086 seconds)
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com> GRANT ROLE sentry_admin TO GROUP vvaldevite;
INFO  : Compiling command(queryId=hive_20170406123535_45bfef22-a640-46e1-8684-22208ea71e70): GRANT ROLE sentry_admin TO GROUP vvaldevite
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170406123535_45bfef22-a640-46e1-8684-22208ea71e70); Time taken: 0.054 seconds
INFO  : Executing command(queryId=hive_20170406123535_45bfef22-a640-46e1-8684-22208ea71e70): GRANT ROLE sentry_admin TO GROUP vvaldevite
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170406123535_45bfef22-a640-46e1-8684-22208ea71e70); Time taken: 0.02 seconds
INFO  : OK
No rows affected (0.085 seconds)
```

## Results of the grant for vvaldevite
```
[root@ip-172-31-8-114 centos]# kinit vvaldevite
Password for vvaldevite@HADOOP.LOCAL:
[root@ip-172-31-8-114 centos]# beeline
Beeline version 1.1.0-cdh5.10.1 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-8-114.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-8-114.us-west-2.compute.internal@HADOOP.LOCAL
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-8-114.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-8-114.us-west-2.compute.internal@HADOOP.LOCAL
Connected to: Apache Hive (version 1.1.0-cdh5.10.1)
Driver: Hive JDBC (version 1.1.0-cdh5.10.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com>
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com>
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com>
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com> show tables;
INFO  : Compiling command(queryId=hive_20170406134545_9e3adafa-390c-481b-b23e-77a7cefa80fb): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170406134545_9e3adafa-390c-481b-b23e-77a7cefa80fb); Time taken: 0.066 seconds
INFO  : Executing command(queryId=hive_20170406134545_9e3adafa-390c-481b-b23e-77a7cefa80fb): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170406134545_9e3adafa-390c-481b-b23e-77a7cefa80fb); Time taken: 0.14 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.308 seconds)
```

# User george, group selectors and role reads
```
[root@ip-172-31-8-114 centos]# groupadd selector
[root@ip-172-31-8-114 centos]# useradd -u 1100 -g selector george
[root@ip-172-31-8-114 centos]# kadmin.local addprinc george
Enter password for principal "george@HADOOP.LOCAL":
Re-enter password for principal "george@HADOOP.LOCAL":
[root@ip-172-31-8-114 centos]# beeline
Beeline version 1.1.0-cdh5.10.1 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-8-114.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-8-114.us-west-2.compute.internal@HADOOP.LOCAL
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-8-114.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-8-114.us-west-2.compute.internal@HADOOP.LOCAL
Connected to: Apache Hive (version 1.1.0-cdh5.10.1)
Driver: Hive JDBC (version 1.1.0-cdh5.10.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com> CREATE ROLE reads;
INFO  : Compiling command(queryId=hive_20170406013434_eaf6daa7-5635-4adc-aca6-e9ea7d7a3117): CREATE ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170406013434_eaf6daa7-5635-4adc-aca6-e9ea7d7a3117); Time taken: 0.061 seconds
INFO  : Executing command(queryId=hive_20170406013434_eaf6daa7-5635-4adc-aca6-e9ea7d7a3117): CREATE ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170406013434_eaf6daa7-5635-4adc-aca6-e9ea7d7a3117); Time taken: 0.028 seconds
INFO  : OK
No rows affected (0.159 seconds)
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com> GRANT SELECT ON DATABASE default TO ROLE reads;
INFO  : Compiling command(queryId=hive_20170406013535_98555501-a86e-4d21-86c6-f21ff35c00c5): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170406013535_98555501-a86e-4d21-86c6-f21ff35c00c5); Time taken: 0.054 seconds
INFO  : Executing command(queryId=hive_20170406013535_98555501-a86e-4d21-86c6-f21ff35c00c5): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170406013535_98555501-a86e-4d21-86c6-f21ff35c00c5); Time taken: 0.034 seconds
INFO  : OK
No rows affected (0.099 seconds)
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com> GRANT ROLE reads TO  GROUP selector;
INFO  : Compiling command(queryId=hive_20170406013535_37011415-ce38-493a-a290-f3ff9c131287): GRANT ROLE reads TO  GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170406013535_37011415-ce38-493a-a290-f3ff9c131287); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20170406013535_37011415-ce38-493a-a290-f3ff9c131287): GRANT ROLE reads TO  GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170406013535_37011415-ce38-493a-a290-f3ff9c131287); Time taken: 0.028 seconds
INFO  : OK
No rows affected (0.096 seconds)
```

## Result of SHOW TABLES with george
```
[root@ip-172-31-8-114 centos]# kdestroy
[root@ip-172-31-8-114 centos]# kinit george
Password for george@HADOOP.LOCAL:
[root@ip-172-31-8-114 centos]# beeline
Beeline version 1.1.0-cdh5.10.1 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-8-114.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-8-114.us-west-2.compute.internal@HADOOP.LOCAL
scan complete in 1ms
Connecting to jdbc:hive2://ip-172-31-8-114.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-8-114.us-west-2.compute.internal@HADOOP.LOCAL
Connected to: Apache Hive (version 1.1.0-cdh5.10.1)
Driver: Hive JDBC (version 1.1.0-cdh5.10.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com> show tables;
INFO  : Compiling command(queryId=hive_20170406013838_5ef80dd3-8753-4d94-a4e8-41ba70bc2c78): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170406013838_5ef80dd3-8753-4d94-a4e8-41ba70bc2c78); Time taken: 0.064 seconds
INFO  : Executing command(queryId=hive_20170406013838_5ef80dd3-8753-4d94-a4e8-41ba70bc2c78): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170406013838_5ef80dd3-8753-4d94-a4e8-41ba70bc2c78); Time taken: 0.12 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.282 seconds)
```

# User ferdinand, group inserters and role writes
```
[root@ip-172-31-8-114 centos]# groupadd inserters
[root@ip-172-31-8-114 centos]# useradd -u 1200 -g inserters ferdinand
[root@ip-172-31-8-114 centos]# kadmin.local addprinc ferdinand
Enter password for principal "ferdinand@HADOOP.LOCAL":
Re-enter password for principal "ferdinand@HADOOP.LOCAL":
[root@ip-172-31-8-114 centos]# beeline
Beeline version 1.1.0-cdh5.10.1 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-8-114.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-8-114.us-west-2.compute.internal@HADOOP.LOCAL
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-8-114.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-8-114.us-west-2.compute.internal@HADOOP.LOCAL
Connected to: Apache Hive (version 1.1.0-cdh5.10.1)
Driver: Hive JDBC (version 1.1.0-cdh5.10.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com> CREATE ROLE writes;
INFO  : Compiling command(queryId=hive_20170406013434_11f3c62f-9cf2-48ee-910e-c272397b2528): CREATE ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170406013434_11f3c62f-9cf2-48ee-910e-c272397b2528); Time taken: 0.055 seconds
INFO  : Executing command(queryId=hive_20170406013434_11f3c62f-9cf2-48ee-910e-c272397b2528): CREATE ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170406013434_11f3c62f-9cf2-48ee-910e-c272397b2528); Time taken: 0.021 seconds
INFO  : OK
No rows affected (0.092 seconds)
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com> REVOKE ALL ON DATABASE default FROM ROLE writes;
INFO  : Compiling command(queryId=hive_20170406013636_2009765d-f34f-4122-a648-933481ddc991): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170406013636_2009765d-f34f-4122-a648-933481ddc991); Time taken: 0.077 seconds
INFO  : Executing command(queryId=hive_20170406013636_2009765d-f34f-4122-a648-933481ddc991): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170406013636_2009765d-f34f-4122-a648-933481ddc991); Time taken: 0.089 seconds
INFO  : OK
No rows affected (0.179 seconds)
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com> GRANT SELECT ON default.sample_07 TO ROLE writes;
INFO  : Compiling command(queryId=hive_20170406013737_84729858-ebcf-48aa-90b6-1f7310314420): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170406013737_84729858-ebcf-48aa-90b6-1f7310314420); Time taken: 0.056 seconds
INFO  : Executing command(queryId=hive_20170406013737_84729858-ebcf-48aa-90b6-1f7310314420): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170406013737_84729858-ebcf-48aa-90b6-1f7310314420); Time taken: 0.033 seconds
INFO  : OK
No rows affected (0.114 seconds)
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com> GRANT ROLE writes TO GROUP inserters;
INFO  : Compiling command(queryId=hive_20170406013737_35aadcb8-00eb-4b48-83f8-e9b3f4f67f01): GRANT ROLE writes TO GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170406013737_35aadcb8-00eb-4b48-83f8-e9b3f4f67f01); Time taken: 0.052 seconds
INFO  : Executing command(queryId=hive_20170406013737_35aadcb8-00eb-4b48-83f8-e9b3f4f67f01): GRANT ROLE writes TO GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170406013737_35aadcb8-00eb-4b48-83f8-e9b3f4f67f01); Time taken: 0.023 seconds
INFO  : OK
No rows affected (0.088 seconds)
```

## Result of SHOW TABLES with ferdinand
```
[root@ip-172-31-8-114 centos]# kdestroy
[root@ip-172-31-8-114 centos]# kinit ferdinand
Password for ferdinand@HADOOP.LOCAL:
[root@ip-172-31-8-114 centos]# beeline
Beeline version 1.1.0-cdh5.10.1 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-8-114.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-8-114.us-west-2.compute.internal@HADOOP.LOCAL
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-8-114.us-west-2.compute.internal:10000/default;principal=hive/ip-172-31-8-114.us-west-2.compute.internal@HADOOP.LOCAL
Connected to: Apache Hive (version 1.1.0-cdh5.10.1)
Driver: Hive JDBC (version 1.1.0-cdh5.10.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-8-114.us-west-2.com> show tables;
INFO  : Compiling command(queryId=hive_20170406014747_d703bb48-43ef-4f7b-94db-4ec91bf91fbe): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170406014747_d703bb48-43ef-4f7b-94db-4ec91bf91fbe); Time taken: 0.064 seconds
INFO  : Executing command(queryId=hive_20170406014747_d703bb48-43ef-4f7b-94db-4ec91bf91fbe): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170406014747_d703bb48-43ef-4f7b-94db-4ec91bf91fbe); Time taken: 0.123 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.281 seconds)
```