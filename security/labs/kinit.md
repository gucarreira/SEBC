# Create user and Init session
```
[root@ip-172-31-8-114 centos]# kadmin.local addprinc vvaldevite/admin
Enter password for principal "vvaldevite/admin@HADOOP.LOCAL":
Re-enter password for principal "vvaldevite/admin@HADOOP.LOCAL":
[root@ip-172-31-8-114 centos]# kinit vvaldevite/admin
Password for vvaldevite/admin@HADOOP.LOCAL:
[root@ip-172-31-8-114 centos]# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: vvaldevite/admin@HADOOP.LOCAL

Valid starting       Expires              Service principal
04/06/2017 00:02:34  04/07/2017 00:02:34  krbtgt/HADOOP.LOCAL@HADOOP.LOCAL
```

# Testing permissions
```
[root@ip-172-31-8-114 centos]#
[root@ip-172-31-8-114 centos]# hdfs dfs -mkdir /user/vvaldevite/teste
[root@ip-172-31-8-114 centos]# hdfs dfs -rm -r /user/vvaldevite/teste
17/04/06 00:03:41 INFO fs.TrashPolicyDefault: Moved: 'hdfs://nameservice1/user/vvaldevite/teste' to trash at: hdfs://nameservice1/user/vvaldevite/.Trash/Current/user/vvaldevite/teste
[root@ip-172-31-8-114 centos]# hdfs dfs -mkdir /results/tete
mkdir: Permission denied: user=vvaldevite, access=WRITE, inode="/results":hdfs:supergroup:drwxr-xr-x
```