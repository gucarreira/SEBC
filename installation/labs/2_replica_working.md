# MariaDB Install

## Status Banco
[root@ip-172-31-8-114 centos]# service mariadb status
Redirecting to /bin/systemctl status  mariadb.service
? mariadb.service - MariaDB database server
   Loaded: loaded (/usr/lib/systemd/system/mariadb.service; enabled; vendor preset: disabled)
   Active: active (running) since Mon 2017-04-03 17:34:43 UTC; 4min 9s ago
  Process: 26317 ExecStartPost=/usr/libexec/mariadb-wait-ready $MAINPID (code=exited, status=0/SUCCESS)
  Process: 26239 ExecStartPre=/usr/libexec/mariadb-prepare-db-dir %n (code=exited, status=0/SUCCESS)
 Main PID: 26316 (mysqld_safe)
   CGroup: /system.slice/mariadb.service
           +-26316 /bin/sh /usr/bin/mysqld_safe --basedir=/usr
           +-26710 /usr/libexec/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/l...

Apr 03 17:34:33 ip-172-31-8-114 mariadb-prepare-db-dir[26239]: The latest information about Maria....
Apr 03 17:34:33 ip-172-31-8-114 mariadb-prepare-db-dir[26239]: You can find additional informatio...:
Apr 03 17:34:33 ip-172-31-8-114 mariadb-prepare-db-dir[26239]: http://dev.mysql.com
Apr 03 17:34:33 ip-172-31-8-114 mariadb-prepare-db-dir[26239]: Support MariaDB development by buy...B
Apr 03 17:34:33 ip-172-31-8-114 mariadb-prepare-db-dir[26239]: Corporation Ab. You can contact us....
Apr 03 17:34:33 ip-172-31-8-114 mariadb-prepare-db-dir[26239]: Alternatively consider joining our...:
Apr 03 17:34:33 ip-172-31-8-114 mariadb-prepare-db-dir[26239]: http://mariadb.com/kb/en/contribut.../
Apr 03 17:34:34 ip-172-31-8-114 mysqld_safe[26316]: 170403 17:34:34 mysqld_safe Logging to '/var...'.
Apr 03 17:34:34 ip-172-31-8-114 mysqld_safe[26316]: 170403 17:34:34 mysqld_safe Starting mysqld ...ql
Apr 03 17:34:43 ip-172-31-8-114 systemd[1]: Started MariaDB database server.
Hint: Some lines were ellipsized, use -l to show in full.

## Created Databases
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| amon               |
| metastore          |
| mysql              |
| nav                |
| navms              |
| oozie              |
| performance_schema |
| rman               |
| sentry             |
+--------------------+
10 rows in set (0.00 sec)

## Replica Status
MariaDB [(none)]> SHOW SLAVE STATUS;
+----------------------------------+--------------------------------------------+-------------+-------------+---------------+-------------------------+---------------------+--------------------------+---------------+-------------------------+------------------+-------------------+-----------------+---------------------+--------------------+------------------------+-------------------------+-----------------------------+------------+------------+--------------+---------------------+-----------------+-----------------+----------------+---------------+--------------------+--------------------+--------------------+-----------------+-------------------+----------------+-----------------------+-------------------------------+---------------+---------------+----------------+----------------+-----------------------------+------------------+
| Slave_IO_State                   | Master_Host                                | Master_User | Master_Port | Connect_Retry | Master_Log_File         | Read_Master_Log_Pos | Relay_Log_File           | Relay_Log_Pos | Relay_Master_Log_File   | Slave_IO_Running | Slave_SQL_Running | Replicate_Do_DB | Replicate_Ignore_DB | Replicate_Do_Table | Replicate_Ignore_Table | Replicate_Wild_Do_Table | Replicate_Wild_Ignore_Table | Last_Errno | Last_Error | Skip_Counter | Exec_Master_Log_Pos | Relay_Log_Space | Until_Condition | Until_Log_File | Until_Log_Pos | Master_SSL_Allowed | Master_SSL_CA_File | Master_SSL_CA_Path | Master_SSL_Cert | Master_SSL_Cipher | Master_SSL_Key | Seconds_Behind_Master | Master_SSL_Verify_Server_Cert | Last_IO_Errno | Last_IO_Error | Last_SQL_Errno | Last_SQL_Error | Replicate_Ignore_Server_Ids | Master_Server_Id |
+----------------------------------+--------------------------------------------+-------------+-------------+---------------+-------------------------+---------------------+--------------------------+---------------+-------------------------+------------------+-------------------+-----------------+---------------------+--------------------+------------------------+-------------------------+-----------------------------+------------+------------+--------------+---------------------+-----------------+-----------------+----------------+---------------+--------------------+--------------------+--------------------+-----------------+-------------------+----------------+-----------------------+-------------------------------+---------------+---------------+----------------+----------------+-----------------------------+------------------+
| Waiting for master to send event | ip-172-31-8-114.us-west-2.compute.internal | root        |        3306 |            60 | mysql_binary_log.000004 |                 560 | mariadb-relay-bin.000002 |           536 | mysql_binary_log.000004 | Yes              | Yes               |                 |                     |                    |                        |                         |                             |          0 |            |            0 |                 560 |             832 | None            |                |             0 | No                 |                    |                    |                 |                   |                |                     0 | No                            |             0 |               |              0 |                |                             |                1 |
+----------------------------------+--------------------------------------------+-------------+-------------+---------------+-------------------------+---------------------+--------------------------+---------------+-------------------------+------------------+-------------------+-----------------+---------------------+--------------------+------------------------+-------------------------+-----------------------------+------------+------------+--------------+---------------------+-----------------+-----------------+----------------+---------------+--------------------+--------------------+--------------------+-----------------+-------------------+----------------+-----------------------+-------------------------------+---------------+---------------+----------------+----------------+-----------------------------+------------------+
1 row in set (0.00 sec)
