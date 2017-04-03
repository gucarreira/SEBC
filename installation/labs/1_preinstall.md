# Check Swapiness
## before
[centos@ip-172-31-7-135 ~]$ more /proc/sys/vm/swappiness
30
## after
[root@ip-172-31-7-135 centos]# echo 1 > /proc/sys/vm/swappiness
[root@ip-172-31-7-135 centos]# more /proc/sys/vm/swappiness
1

# Mount attributes
[root@ip-172-31-8-114 centos]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       40G  1.4G   39G   4% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   25M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000

# Hugepage
## before
[root@ip-172-31-15-123 centos]# cat /sys/kernel/mm/transparent_hugepage/enabled
[always] madvise never
## after
[root@ip-172-31-15-123 centos]# cat /sys/kernel/mm/transparent_hugepage/enabled
always madvise [never]

# List network
## Master
[root@ip-172-31-8-114 centos]# ifconfig -a
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 172.31.8.114  netmask 255.255.240.0  broadcast 172.31.15.255
        inet6 fe80::8ba:ffff:fef7:3065  prefixlen 64  scopeid 0x20<link>
        ether 0a:ba:ff:f7:30:65  txqueuelen 1000  (Ethernet)
        RX packets 147027  bytes 211300632 (201.5 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 67773  bytes 4808723 (4.5 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 70  bytes 5984 (5.8 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 70  bytes 5984 (5.8 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

## Standby Master
[root@ip-172-31-7-135 centos]# ifconfig -a
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 172.31.7.135  netmask 255.255.240.0  broadcast 172.31.15.255
        inet6 fe80::81b:91ff:fea2:ca13  prefixlen 64  scopeid 0x20<link>
        ether 0a:1b:91:a2:ca:13  txqueuelen 1000  (Ethernet)
        RX packets 1873484  bytes 2749044953 (2.5 GiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 906477  bytes 60489045 (57.6 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 86  bytes 7564 (7.3 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 86  bytes 7564 (7.3 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

## Worker 1
[root@ip-172-31-5-59 centos]# ifconfig -a
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 172.31.5.59  netmask 255.255.240.0  broadcast 172.31.15.255
        inet6 fe80::82c:c2ff:fe98:d5d3  prefixlen 64  scopeid 0x20<link>
        ether 0a:2c:c2:98:d5:d3  txqueuelen 1000  (Ethernet)
        RX packets 147537  bytes 211905337 (202.0 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 74687  bytes 5294656 (5.0 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 70  bytes 5984 (5.8 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 70  bytes 5984 (5.8 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

## Worker 2
[root@ip-172-31-2-15 centos]# ifconfig -a
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 172.31.2.15  netmask 255.255.240.0  broadcast 172.31.15.255
        inet6 fe80::8a5:e7ff:fe7c:b4ed  prefixlen 64  scopeid 0x20<link>
        ether 0a:a5:e7:7c:b4:ed  txqueuelen 1000  (Ethernet)
        RX packets 150760  bytes 212917730 (203.0 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 94278  bytes 7058433 (6.7 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 70  bytes 5984 (5.8 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 70  bytes 5984 (5.8 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

## Worker 3
[root@ip-172-31-15-123 centos]# ifconfig -a
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 172.31.15.123  netmask 255.255.240.0  broadcast 172.31.15.255
        inet6 fe80::8c1:69ff:fea4:d603  prefixlen 64  scopeid 0x20<link>
        ether 0a:c1:69:a4:d6:03  txqueuelen 1000  (Ethernet)
        RX packets 147979  bytes 211379818 (201.5 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 67309  bytes 4807922 (4.5 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 70  bytes 5984 (5.8 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 70  bytes 5984 (5.8 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

# Name resolving
## /etc/hosts
[root@ip-172-31-15-123 centos]# getent hosts
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
172.31.8.114    ip-172-31-8-114 ip-172-31-8-114.us-west-2.compute.internal master
172.31.7.135    ip-172-31-7-135 ip-172-31-7-135.us-west-2.compute.internal master2
172.31.5.59     ip-172-31-5-59 ip-172-31-5-59.us-west-2.compute.internal worker1
172.31.2.15     ip-172-31-2-15 ip-172-31-2-15.us-west-2.compute.internal worker2
172.31.15.123   ip-172-31-15-123 ip-172-31-15-123.us-west-2.compute.internal worker3

## forward and reverse name resolving
[root@ip-172-31-15-123 centos]# getent hosts 172.31.8.114
172.31.8.114    ip-172-31-8-114 ip-172-31-8-114.us-west-2.compute.internal master
[root@ip-172-31-15-123 centos]# getent hosts ip-172-31-8-114.us-west-2.compute.internal
172.31.8.114    ip-172-31-8-114 ip-172-31-8-114.us-west-2.compute.internal master

# NSCD status
[root@ip-172-31-8-114 centos]# service nscd status
Redirecting to /bin/systemctl status  nscd.service
? nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2017-04-03 17:16:12 UTC; 7s ago
  Process: 26008 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 26009 (nscd)
   CGroup: /system.slice/nscd.service
           +-26009 /usr/sbin/nscd

Apr 03 17:16:12 ip-172-31-8-114 nscd[26009]: 26009 monitoring file `/etc/hosts` (4)
Apr 03 17:16:12 ip-172-31-8-114 nscd[26009]: 26009 monitoring directory `/etc` (2)
Apr 03 17:16:12 ip-172-31-8-114 nscd[26009]: 26009 monitoring file `/etc/resolv.conf` (5)
Apr 03 17:16:12 ip-172-31-8-114 nscd[26009]: 26009 monitoring directory `/etc` (2)
Apr 03 17:16:12 ip-172-31-8-114 nscd[26009]: 26009 monitoring file `/etc/services` (6)
Apr 03 17:16:12 ip-172-31-8-114 nscd[26009]: 26009 monitoring directory `/etc` (2)
Apr 03 17:16:12 ip-172-31-8-114 nscd[26009]: 26009 disabled inotify-based monitoring for file `...ory
Apr 03 17:16:12 ip-172-31-8-114 nscd[26009]: 26009 stat failed for file `/etc/netgroup'; will t...ory
Apr 03 17:16:12 ip-172-31-8-114 nscd[26009]: 26009 Access Vector Cache (AVC) started
Apr 03 17:16:12 ip-172-31-8-114 systemd[1]: Started Name Service Cache Daemon.
Hint: Some lines were ellipsized, use -l to show in full.

# NTPD status
[root@ip-172-31-8-114 centos]# service ntpd status
Redirecting to /bin/systemctl status  ntpd.service
? ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2017-04-03 17:18:15 UTC; 5s ago
  Process: 26123 ExecStart=/usr/sbin/ntpd -u ntp:ntp $OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 26124 (ntpd)
   CGroup: /system.slice/ntpd.service
           +-26124 /usr/sbin/ntpd -u ntp:ntp -g

Apr 03 17:18:15 ip-172-31-8-114 ntpd[26124]: Listen and drop on 1 v6wildcard :: UDP 123
Apr 03 17:18:15 ip-172-31-8-114 ntpd[26124]: Listen normally on 2 lo 127.0.0.1 UDP 123
Apr 03 17:18:15 ip-172-31-8-114 ntpd[26124]: Listen normally on 3 eth0 172.31.8.114 UDP 123
Apr 03 17:18:15 ip-172-31-8-114 ntpd[26124]: Listen normally on 4 lo ::1 UDP 123
Apr 03 17:18:15 ip-172-31-8-114 ntpd[26124]: Listen normally on 5 eth0 fe80::8ba:ffff:fef7:3065...123
Apr 03 17:18:15 ip-172-31-8-114 ntpd[26124]: Listening on routing socket on fd #22 for interfac...tes
Apr 03 17:18:15 ip-172-31-8-114 systemd[1]: Started Network Time Service.
Apr 03 17:18:16 ip-172-31-8-114 ntpd[26124]: 0.0.0.0 c016 06 restart
Apr 03 17:18:16 ip-172-31-8-114 ntpd[26124]: 0.0.0.0 c012 02 freq_set kernel 0.000 PPM
Apr 03 17:18:16 ip-172-31-8-114 ntpd[26124]: 0.0.0.0 c011 01 freq_not_set
Hint: Some lines were ellipsized, use -l to show in full.

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
