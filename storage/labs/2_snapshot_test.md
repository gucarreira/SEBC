# Create directory

## Command
```
[hdfs@ip-172-31-8-114 centos]$ hdfs dfs -mkdir /tmp/precious
[hdfs@ip-172-31-8-114 centos]$ hdfs dfs -put /tmp/SEBC-master.zip /tmp/precious
[hdfs@ip-172-31-8-114 centos]$ hdfs dfs -ls /tmp/precious
Found 1 items
-rw-r--r--   3 hdfs supergroup     473950 2017-04-04 15:05 /tmp/precious/SEBC-master.zip
```

## Enable and create snapshot
Image file - 2_snapshot_list.png


## Delete file and directory
```
[hdfs@ip-172-31-8-114 centos]$ hdfs dfs -rm /tmp/precious/SEBC-master.zip
17/04/04 15:11:42 INFO fs.TrashPolicyDefault: Moved: 'hdfs://ip-172-31-8-114.us-west-2.compute.internal:8020/tmp/precious/SEBC-master.zip' to trash at: hdfs://ip-172-31-8-114.us-west-2.compute.internal:8020/user/hdfs/.Trash/Current/tmp/precious/SEBC-master.zip
```

## Restore file
Image file - 2_snapshot_list.png

## After restore
```
[hdfs@ip-172-31-8-114 centos]$ hdfs dfs -ls /tmp/precious
Found 1 items
-rw-r--r--   3 hdfs supergroup     473950 2017-04-04 15:21 /tmp/precious/SEBC-master.zip
```