# Teragen
## Command
time hadoop jar /opt/cloudera/parcels/CDH-5.10.1-1.cdh5.10.1.p0.10/jars/hadoop-examples.jar teragen \
-Ddfs.blocksize=32M \
-Ddfs.replication=1 \
-Dmapreduce.job.maps=4 \
100000000 \
/user/vvaldevite/terasort-input > out.txt 2>&1

## Execution time
[vvaldevite@ip-172-31-8-114 ~]$ time hadoop jar /opt/cloudera/parcels/CDH-5.10.1-1.cdh5.10.1.p0.10/jars/hadoop-examples.jar teragen \
> -Ddfs.blocksize=32M \
> -Ddfs.replication=1 \
> -Dmapreduce.job.maps=4 \
> 100000000 \
> /user/vvaldevite/terasort-input > out.txt 2>&1

real    1m56.701s
user    0m6.019s
sys     0m0.296s

## Output
17/04/04 14:16:50 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-8-114.us-west-2.compute.internal/172.31.8.114:8032
17/04/04 14:16:50 INFO terasort.TeraGen: Generating 100000000 using 4
17/04/04 14:16:50 INFO mapreduce.JobSubmitter: number of splits:4
17/04/04 14:16:51 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1491310226923_0002
17/04/04 14:16:51 INFO impl.YarnClientImpl: Submitted application application_1491310226923_0002
17/04/04 14:16:51 INFO mapreduce.Job: The url to track the job: http://ip-172-31-8-114.us-west-2.compute.internal:8088/proxy/application_1491310226923_0002/
17/04/04 14:16:51 INFO mapreduce.Job: Running job: job_1491310226923_0002
17/04/04 14:16:57 INFO mapreduce.Job: Job job_1491310226923_0002 running in uber mode : false
17/04/04 14:16:57 INFO mapreduce.Job:  map 0% reduce 0%
17/04/04 14:17:17 INFO mapreduce.Job:  map 34% reduce 0%
17/04/04 14:17:24 INFO mapreduce.Job:  map 48% reduce 0%
17/04/04 14:17:30 INFO mapreduce.Job:  map 66% reduce 0%
17/04/04 14:17:36 INFO mapreduce.Job:  map 76% reduce 0%
17/04/04 14:17:42 INFO mapreduce.Job:  map 77% reduce 0%
17/04/04 14:17:48 INFO mapreduce.Job:  map 79% reduce 0%
17/04/04 14:17:54 INFO mapreduce.Job:  map 81% reduce 0%
17/04/04 14:18:00 INFO mapreduce.Job:  map 83% reduce 0%
17/04/04 14:18:06 INFO mapreduce.Job:  map 85% reduce 0%
17/04/04 14:18:12 INFO mapreduce.Job:  map 88% reduce 0%
17/04/04 14:18:18 INFO mapreduce.Job:  map 90% reduce 0%
17/04/04 14:18:24 INFO mapreduce.Job:  map 93% reduce 0%
17/04/04 14:18:30 INFO mapreduce.Job:  map 96% reduce 0%
17/04/04 14:18:36 INFO mapreduce.Job:  map 98% reduce 0%
17/04/04 14:18:39 INFO mapreduce.Job:  map 99% reduce 0%
17/04/04 14:18:42 INFO mapreduce.Job:  map 100% reduce 0%
17/04/04 14:18:44 INFO mapreduce.Job: Job job_1491310226923_0002 completed successfully
17/04/04 14:18:44 INFO mapreduce.Job: Counters: 31
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=499920
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=344
                HDFS: Number of bytes written=10000000000
                HDFS: Number of read operations=16
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=8
        Job Counters
                Launched map tasks=4
                Other local map tasks=4
                Total time spent by all maps in occupied slots (ms)=402802
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=402802
                Total vcore-seconds taken by all map tasks=402802
                Total megabyte-seconds taken by all map tasks=412469248
        Map-Reduce Framework
                Map input records=100000000
                Map output records=100000000
                Input split bytes=344
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=1247
                CPU time spent (ms)=149690
                Physical memory (bytes) snapshot=909225984
                Virtual memory (bytes) snapshot=6336397312
                Total committed heap usage (bytes)=884473856
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=214760662691937609
        File Input Format Counters
                Bytes Read=0
        File Output Format Counters
                Bytes Written=10000000000

## Generated Files
[vvaldevite@ip-172-31-8-114 ~]$ hdfs dfs -ls -h /user/vvaldevite/terasort-input
Found 5 items
-rw-r--r--   1 vvaldevite supergroup          0 2017-04-04 14:18 /user/vvaldevite/terasort-input/_SUCCESS
-rw-r--r--   1 vvaldevite supergroup      2.3 G 2017-04-04 14:18 /user/vvaldevite/terasort-input/part-m-00000
-rw-r--r--   1 vvaldevite supergroup      2.3 G 2017-04-04 14:18 /user/vvaldevite/terasort-input/part-m-00001
-rw-r--r--   1 vvaldevite supergroup      2.3 G 2017-04-04 14:18 /user/vvaldevite/terasort-input/part-m-00002
-rw-r--r--   1 vvaldevite supergroup      2.3 G 2017-04-04 14:18 /user/vvaldevite/terasort-input/part-m-00003

## Block Sizes
[hdfs@ip-172-31-8-114 centos]$ hadoop fsck /user/vvaldevite/terasort-input/part-m-00000 -files -blocks
DEPRECATED: Use of this script to execute hdfs command is deprecated.
Instead use the hdfs command for it.

Connecting to namenode via http://ip-172-31-8-114.us-west-2.compute.internal:50070
FSCK started by hdfs (auth:SIMPLE) from /172.31.8.114 for path /user/vvaldevite/terasort-input/part-m-00000 at Tue Apr 04 14:25:46 UTC 2017
/user/vvaldevite/terasort-input/part-m-00000 2500000000 bytes, 75 block(s):  OK
0. BP-1167505925-172.31.8.114-1491253844509:blk_1073743436_2612 len=33554432 Live_repl=1
1. BP-1167505925-172.31.8.114-1491253844509:blk_1073743438_2614 len=33554432 Live_repl=1
2. BP-1167505925-172.31.8.114-1491253844509:blk_1073743442_2618 len=33554432 Live_repl=1
3. BP-1167505925-172.31.8.114-1491253844509:blk_1073743446_2622 len=33554432 Live_repl=1
4. BP-1167505925-172.31.8.114-1491253844509:blk_1073743450_2626 len=33554432 Live_repl=1
5. BP-1167505925-172.31.8.114-1491253844509:blk_1073743454_2630 len=33554432 Live_repl=1
6. BP-1167505925-172.31.8.114-1491253844509:blk_1073743458_2634 len=33554432 Live_repl=1
7. BP-1167505925-172.31.8.114-1491253844509:blk_1073743462_2638 len=33554432 Live_repl=1
8. BP-1167505925-172.31.8.114-1491253844509:blk_1073743466_2642 len=33554432 Live_repl=1
9. BP-1167505925-172.31.8.114-1491253844509:blk_1073743469_2645 len=33554432 Live_repl=1
10. BP-1167505925-172.31.8.114-1491253844509:blk_1073743473_2649 len=33554432 Live_repl=1
11. BP-1167505925-172.31.8.114-1491253844509:blk_1073743477_2653 len=33554432 Live_repl=1
12. BP-1167505925-172.31.8.114-1491253844509:blk_1073743481_2657 len=33554432 Live_repl=1
13. BP-1167505925-172.31.8.114-1491253844509:blk_1073743485_2661 len=33554432 Live_repl=1
14. BP-1167505925-172.31.8.114-1491253844509:blk_1073743489_2665 len=33554432 Live_repl=1
15. BP-1167505925-172.31.8.114-1491253844509:blk_1073743493_2669 len=33554432 Live_repl=1
16. BP-1167505925-172.31.8.114-1491253844509:blk_1073743497_2673 len=33554432 Live_repl=1
17. BP-1167505925-172.31.8.114-1491253844509:blk_1073743501_2677 len=33554432 Live_repl=1
18. BP-1167505925-172.31.8.114-1491253844509:blk_1073743504_2680 len=33554432 Live_repl=1
19. BP-1167505925-172.31.8.114-1491253844509:blk_1073743508_2684 len=33554432 Live_repl=1
20. BP-1167505925-172.31.8.114-1491253844509:blk_1073743512_2688 len=33554432 Live_repl=1
21. BP-1167505925-172.31.8.114-1491253844509:blk_1073743516_2692 len=33554432 Live_repl=1
22. BP-1167505925-172.31.8.114-1491253844509:blk_1073743520_2696 len=33554432 Live_repl=1
23. BP-1167505925-172.31.8.114-1491253844509:blk_1073743524_2700 len=33554432 Live_repl=1
24. BP-1167505925-172.31.8.114-1491253844509:blk_1073743528_2704 len=33554432 Live_repl=1
25. BP-1167505925-172.31.8.114-1491253844509:blk_1073743531_2707 len=33554432 Live_repl=1
26. BP-1167505925-172.31.8.114-1491253844509:blk_1073743535_2711 len=33554432 Live_repl=1
27. BP-1167505925-172.31.8.114-1491253844509:blk_1073743539_2715 len=33554432 Live_repl=1
28. BP-1167505925-172.31.8.114-1491253844509:blk_1073743542_2718 len=33554432 Live_repl=1
29. BP-1167505925-172.31.8.114-1491253844509:blk_1073743546_2722 len=33554432 Live_repl=1
30. BP-1167505925-172.31.8.114-1491253844509:blk_1073743550_2726 len=33554432 Live_repl=1
31. BP-1167505925-172.31.8.114-1491253844509:blk_1073743552_2728 len=33554432 Live_repl=1
32. BP-1167505925-172.31.8.114-1491253844509:blk_1073743554_2730 len=33554432 Live_repl=1
33. BP-1167505925-172.31.8.114-1491253844509:blk_1073743556_2732 len=33554432 Live_repl=1
34. BP-1167505925-172.31.8.114-1491253844509:blk_1073743558_2734 len=33554432 Live_repl=1
35. BP-1167505925-172.31.8.114-1491253844509:blk_1073743560_2736 len=33554432 Live_repl=1
36. BP-1167505925-172.31.8.114-1491253844509:blk_1073743562_2738 len=33554432 Live_repl=1
37. BP-1167505925-172.31.8.114-1491253844509:blk_1073743564_2740 len=33554432 Live_repl=1
38. BP-1167505925-172.31.8.114-1491253844509:blk_1073743566_2742 len=33554432 Live_repl=1
39. BP-1167505925-172.31.8.114-1491253844509:blk_1073743568_2744 len=33554432 Live_repl=1
40. BP-1167505925-172.31.8.114-1491253844509:blk_1073743570_2746 len=33554432 Live_repl=1
41. BP-1167505925-172.31.8.114-1491253844509:blk_1073743572_2748 len=33554432 Live_repl=1
42. BP-1167505925-172.31.8.114-1491253844509:blk_1073743574_2750 len=33554432 Live_repl=1
43. BP-1167505925-172.31.8.114-1491253844509:blk_1073743576_2752 len=33554432 Live_repl=1
44. BP-1167505925-172.31.8.114-1491253844509:blk_1073743578_2754 len=33554432 Live_repl=1
45. BP-1167505925-172.31.8.114-1491253844509:blk_1073743580_2756 len=33554432 Live_repl=1
46. BP-1167505925-172.31.8.114-1491253844509:blk_1073743584_2760 len=33554432 Live_repl=1
47. BP-1167505925-172.31.8.114-1491253844509:blk_1073743588_2764 len=33554432 Live_repl=1
48. BP-1167505925-172.31.8.114-1491253844509:blk_1073743592_2768 len=33554432 Live_repl=1
49. BP-1167505925-172.31.8.114-1491253844509:blk_1073743596_2772 len=33554432 Live_repl=1
50. BP-1167505925-172.31.8.114-1491253844509:blk_1073743600_2776 len=33554432 Live_repl=1
51. BP-1167505925-172.31.8.114-1491253844509:blk_1073743604_2780 len=33554432 Live_repl=1
52. BP-1167505925-172.31.8.114-1491253844509:blk_1073743608_2784 len=33554432 Live_repl=1
53. BP-1167505925-172.31.8.114-1491253844509:blk_1073743612_2788 len=33554432 Live_repl=1
54. BP-1167505925-172.31.8.114-1491253844509:blk_1073743614_2790 len=33554432 Live_repl=1
55. BP-1167505925-172.31.8.114-1491253844509:blk_1073743619_2795 len=33554432 Live_repl=1
56. BP-1167505925-172.31.8.114-1491253844509:blk_1073743631_2807 len=33554432 Live_repl=1
57. BP-1167505925-172.31.8.114-1491253844509:blk_1073743662_2838 len=33554432 Live_repl=1
58. BP-1167505925-172.31.8.114-1491253844509:blk_1073743668_2844 len=33554432 Live_repl=1
59. BP-1167505925-172.31.8.114-1491253844509:blk_1073743671_2847 len=33554432 Live_repl=1
60. BP-1167505925-172.31.8.114-1491253844509:blk_1073743674_2850 len=33554432 Live_repl=1
61. BP-1167505925-172.31.8.114-1491253844509:blk_1073743677_2853 len=33554432 Live_repl=1
62. BP-1167505925-172.31.8.114-1491253844509:blk_1073743682_2858 len=33554432 Live_repl=1
63. BP-1167505925-172.31.8.114-1491253844509:blk_1073743684_2860 len=33554432 Live_repl=1
64. BP-1167505925-172.31.8.114-1491253844509:blk_1073743689_2865 len=33554432 Live_repl=1
65. BP-1167505925-172.31.8.114-1491253844509:blk_1073743693_2869 len=33554432 Live_repl=1
66. BP-1167505925-172.31.8.114-1491253844509:blk_1073743697_2873 len=33554432 Live_repl=1
67. BP-1167505925-172.31.8.114-1491253844509:blk_1073743701_2877 len=33554432 Live_repl=1
68. BP-1167505925-172.31.8.114-1491253844509:blk_1073743705_2881 len=33554432 Live_repl=1
69. BP-1167505925-172.31.8.114-1491253844509:blk_1073743709_2885 len=33554432 Live_repl=1
70. BP-1167505925-172.31.8.114-1491253844509:blk_1073743713_2889 len=33554432 Live_repl=1
71. BP-1167505925-172.31.8.114-1491253844509:blk_1073743717_2893 len=33554432 Live_repl=1
72. BP-1167505925-172.31.8.114-1491253844509:blk_1073743721_2897 len=33554432 Live_repl=1
73. BP-1167505925-172.31.8.114-1491253844509:blk_1073743725_2901 len=33554432 Live_repl=1
74. BP-1167505925-172.31.8.114-1491253844509:blk_1073743729_2905 len=16972032 Live_repl=1

Status: HEALTHY
 Total size:    2500000000 B
 Total dirs:    0
 Total files:   1
 Total symlinks:                0
 Total blocks (validated):      75 (avg. block size 33333333 B)
 Minimally replicated blocks:   75 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     1.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          3
 Number of racks:               1
FSCK ended at Tue Apr 04 14:25:46 UTC 2017 in 4 milliseconds


The filesystem under path '/user/vvaldevite/terasort-input/part-m-00000' is HEALTHY

#Terasort

## Command
time hadoop jar /opt/cloudera/parcels/CDH-5.10.1-1.cdh5.10.1.p0.10/jars/hadoop-examples.jar terasort /user/vvaldevite/terasort-input /user/vvaldevite/terasort-output > out_sort.txt 2>&1

## Execution Time
[vvaldevite@ip-172-31-8-114 ~]$ time hadoop jar /opt/cloudera/parcels/CDH-5.10.1-1.cdh5.10.1.p0.10/jars/hadoop-examples.jar terasort /user/vvaldevite/terasort-input /user/vvaldevite/terasort-output > out_sort.txt 2>&1

real    8m54.522s
user    0m8.790s
sys     0m0.426s

## Output
[vvaldevite@ip-172-31-8-114 ~]$ cat out_sort.txt
17/04/04 14:31:43 INFO terasort.TeraSort: starting
17/04/04 14:31:44 INFO input.FileInputFormat: Total input paths to process : 4
Spent 212ms computing base-splits.
Spent 4ms computing TeraScheduler splits.
Computing input splits took 217ms
Sampling 10 splits of 300
Making 6 from 100000 sampled records
Computing parititions took 615ms
Spent 835ms computing partitions.
17/04/04 14:31:45 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-8-114.us-west-2.compute.internal/172.31.8.114:8032
17/04/04 14:31:45 INFO mapreduce.JobSubmitter: number of splits:300
17/04/04 14:31:46 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1491310226923_0003
17/04/04 14:31:46 INFO impl.YarnClientImpl: Submitted application application_1491310226923_0003
17/04/04 14:31:46 INFO mapreduce.Job: The url to track the job: http://ip-172-31-8-114.us-west-2.compute.internal:8088/proxy/application_1491310226923_0003/
17/04/04 14:31:46 INFO mapreduce.Job: Running job: job_1491310226923_0003
17/04/04 14:31:52 INFO mapreduce.Job: Job job_1491310226923_0003 running in uber mode : false
17/04/04 14:31:52 INFO mapreduce.Job:  map 0% reduce 0%
17/04/04 14:32:01 INFO mapreduce.Job:  map 1% reduce 0%
17/04/04 14:32:06 INFO mapreduce.Job:  map 3% reduce 0%
17/04/04 14:32:08 INFO mapreduce.Job:  map 4% reduce 0%
17/04/04 14:32:17 INFO mapreduce.Job:  map 5% reduce 0%
17/04/04 14:32:19 INFO mapreduce.Job:  map 6% reduce 0%
17/04/04 14:32:20 INFO mapreduce.Job:  map 7% reduce 0%
17/04/04 14:32:25 INFO mapreduce.Job:  map 8% reduce 0%
17/04/04 14:32:32 INFO mapreduce.Job:  map 9% reduce 0%
17/04/04 14:32:33 INFO mapreduce.Job:  map 11% reduce 0%
17/04/04 14:32:41 INFO mapreduce.Job:  map 12% reduce 0%
17/04/04 14:32:45 INFO mapreduce.Job:  map 13% reduce 0%
17/04/04 14:32:46 INFO mapreduce.Job:  map 14% reduce 0%
17/04/04 14:32:49 INFO mapreduce.Job:  map 15% reduce 0%
17/04/04 14:32:56 INFO mapreduce.Job:  map 16% reduce 0%
17/04/04 14:32:58 INFO mapreduce.Job:  map 17% reduce 0%
17/04/04 14:32:59 INFO mapreduce.Job:  map 18% reduce 0%
17/04/04 14:33:02 INFO mapreduce.Job:  map 19% reduce 0%
17/04/04 14:33:08 INFO mapreduce.Job:  map 20% reduce 0%
17/04/04 14:33:10 INFO mapreduce.Job:  map 21% reduce 0%
17/04/04 14:33:15 INFO mapreduce.Job:  map 23% reduce 0%
17/04/04 14:33:22 INFO mapreduce.Job:  map 24% reduce 0%
17/04/04 14:33:24 INFO mapreduce.Job:  map 25% reduce 0%
17/04/04 14:33:29 INFO mapreduce.Job:  map 26% reduce 0%
17/04/04 14:33:31 INFO mapreduce.Job:  map 27% reduce 0%
17/04/04 14:33:36 INFO mapreduce.Job:  map 28% reduce 0%
17/04/04 14:33:37 INFO mapreduce.Job:  map 29% reduce 0%
17/04/04 14:33:42 INFO mapreduce.Job:  map 30% reduce 0%
17/04/04 14:33:44 INFO mapreduce.Job:  map 31% reduce 0%
17/04/04 14:33:48 INFO mapreduce.Job:  map 32% reduce 0%
17/04/04 14:33:50 INFO mapreduce.Job:  map 33% reduce 0%
17/04/04 14:33:55 INFO mapreduce.Job:  map 34% reduce 0%
17/04/04 14:33:57 INFO mapreduce.Job:  map 35% reduce 0%
17/04/04 14:34:01 INFO mapreduce.Job:  map 36% reduce 0%
17/04/04 14:34:04 INFO mapreduce.Job:  map 37% reduce 0%
17/04/04 14:34:09 INFO mapreduce.Job:  map 38% reduce 0%
17/04/04 14:34:10 INFO mapreduce.Job:  map 39% reduce 0%
17/04/04 14:34:14 INFO mapreduce.Job:  map 40% reduce 0%
17/04/04 14:34:19 INFO mapreduce.Job:  map 41% reduce 0%
17/04/04 14:34:21 INFO mapreduce.Job:  map 42% reduce 0%
17/04/04 14:34:24 INFO mapreduce.Job:  map 43% reduce 0%
17/04/04 14:34:27 INFO mapreduce.Job:  map 44% reduce 0%
17/04/04 14:34:31 INFO mapreduce.Job:  map 45% reduce 0%
17/04/04 14:34:35 INFO mapreduce.Job:  map 46% reduce 0%
17/04/04 14:34:36 INFO mapreduce.Job:  map 47% reduce 0%
17/04/04 14:34:40 INFO mapreduce.Job:  map 48% reduce 0%
17/04/04 14:34:47 INFO mapreduce.Job:  map 49% reduce 0%
17/04/04 14:34:49 INFO mapreduce.Job:  map 50% reduce 0%
17/04/04 14:34:50 INFO mapreduce.Job:  map 51% reduce 0%
17/04/04 14:34:55 INFO mapreduce.Job:  map 52% reduce 0%
17/04/04 14:34:58 INFO mapreduce.Job:  map 53% reduce 0%
17/04/04 14:35:01 INFO mapreduce.Job:  map 54% reduce 0%
17/04/04 14:35:04 INFO mapreduce.Job:  map 55% reduce 0%
17/04/04 14:35:08 INFO mapreduce.Job:  map 56% reduce 0%
17/04/04 14:35:11 INFO mapreduce.Job:  map 57% reduce 0%
17/04/04 14:35:14 INFO mapreduce.Job:  map 58% reduce 0%
17/04/04 14:35:17 INFO mapreduce.Job:  map 59% reduce 0%
17/04/04 14:35:22 INFO mapreduce.Job:  map 60% reduce 0%
17/04/04 14:35:24 INFO mapreduce.Job:  map 61% reduce 0%
17/04/04 14:35:26 INFO mapreduce.Job:  map 62% reduce 0%
17/04/04 14:35:31 INFO mapreduce.Job:  map 63% reduce 0%
17/04/04 14:35:35 INFO mapreduce.Job:  map 64% reduce 0%
17/04/04 14:35:38 INFO mapreduce.Job:  map 65% reduce 0%
17/04/04 14:35:40 INFO mapreduce.Job:  map 66% reduce 0%
17/04/04 14:35:42 INFO mapreduce.Job:  map 67% reduce 0%
17/04/04 14:35:48 INFO mapreduce.Job:  map 68% reduce 0%
17/04/04 14:35:50 INFO mapreduce.Job:  map 69% reduce 0%
17/04/04 14:35:52 INFO mapreduce.Job:  map 70% reduce 0%
17/04/04 14:35:54 INFO mapreduce.Job:  map 71% reduce 0%
17/04/04 14:35:59 INFO mapreduce.Job:  map 72% reduce 0%
17/04/04 14:36:04 INFO mapreduce.Job:  map 73% reduce 0%
17/04/04 14:36:07 INFO mapreduce.Job:  map 74% reduce 0%
17/04/04 14:36:10 INFO mapreduce.Job:  map 75% reduce 0%
17/04/04 14:36:14 INFO mapreduce.Job:  map 76% reduce 0%
17/04/04 14:36:16 INFO mapreduce.Job:  map 77% reduce 0%
17/04/04 14:36:20 INFO mapreduce.Job:  map 78% reduce 0%
17/04/04 14:36:23 INFO mapreduce.Job:  map 79% reduce 0%
17/04/04 14:36:27 INFO mapreduce.Job:  map 80% reduce 0%
17/04/04 14:36:29 INFO mapreduce.Job:  map 81% reduce 0%
17/04/04 14:36:33 INFO mapreduce.Job:  map 82% reduce 0%
17/04/04 14:36:36 INFO mapreduce.Job:  map 83% reduce 0%
17/04/04 14:36:41 INFO mapreduce.Job:  map 84% reduce 0%
17/04/04 14:36:49 INFO mapreduce.Job:  map 84% reduce 4%
17/04/04 14:36:50 INFO mapreduce.Job:  map 85% reduce 4%
17/04/04 14:36:51 INFO mapreduce.Job:  map 85% reduce 7%
17/04/04 14:36:54 INFO mapreduce.Job:  map 86% reduce 10%
17/04/04 14:36:55 INFO mapreduce.Job:  map 86% reduce 16%
17/04/04 14:36:57 INFO mapreduce.Job:  map 86% reduce 17%
17/04/04 14:37:00 INFO mapreduce.Job:  map 86% reduce 18%
17/04/04 14:37:01 INFO mapreduce.Job:  map 86% reduce 21%
17/04/04 14:37:03 INFO mapreduce.Job:  map 87% reduce 21%
17/04/04 14:37:04 INFO mapreduce.Job:  map 87% reduce 22%
17/04/04 14:37:06 INFO mapreduce.Job:  map 88% reduce 22%
17/04/04 14:37:07 INFO mapreduce.Job:  map 88% reduce 24%
17/04/04 14:37:12 INFO mapreduce.Job:  map 89% reduce 24%
17/04/04 14:37:13 INFO mapreduce.Job:  map 89% reduce 25%
17/04/04 14:37:17 INFO mapreduce.Job:  map 90% reduce 25%
17/04/04 14:37:23 INFO mapreduce.Job:  map 91% reduce 25%
17/04/04 14:37:25 INFO mapreduce.Job:  map 92% reduce 25%
17/04/04 14:37:31 INFO mapreduce.Job:  map 92% reduce 26%
17/04/04 14:37:32 INFO mapreduce.Job:  map 93% reduce 26%
17/04/04 14:37:36 INFO mapreduce.Job:  map 94% reduce 26%
17/04/04 14:37:40 INFO mapreduce.Job:  map 95% reduce 26%
17/04/04 14:37:46 INFO mapreduce.Job:  map 96% reduce 26%
17/04/04 14:37:49 INFO mapreduce.Job:  map 96% reduce 27%
17/04/04 14:37:51 INFO mapreduce.Job:  map 97% reduce 27%
17/04/04 14:37:58 INFO mapreduce.Job:  map 98% reduce 27%
17/04/04 14:38:02 INFO mapreduce.Job:  map 99% reduce 27%
17/04/04 14:38:07 INFO mapreduce.Job:  map 100% reduce 27%
17/04/04 14:38:08 INFO mapreduce.Job:  map 100% reduce 32%
17/04/04 14:38:11 INFO mapreduce.Job:  map 100% reduce 37%
17/04/04 14:38:13 INFO mapreduce.Job:  map 100% reduce 43%
17/04/04 14:38:14 INFO mapreduce.Job:  map 100% reduce 58%
17/04/04 14:38:17 INFO mapreduce.Job:  map 100% reduce 59%
17/04/04 14:38:19 INFO mapreduce.Job:  map 100% reduce 60%
17/04/04 14:38:20 INFO mapreduce.Job:  map 100% reduce 68%
17/04/04 14:38:23 INFO mapreduce.Job:  map 100% reduce 70%
17/04/04 14:38:25 INFO mapreduce.Job:  map 100% reduce 71%
17/04/04 14:38:26 INFO mapreduce.Job:  map 100% reduce 77%
17/04/04 14:38:29 INFO mapreduce.Job:  map 100% reduce 78%
17/04/04 14:38:31 INFO mapreduce.Job:  map 100% reduce 79%
17/04/04 14:38:32 INFO mapreduce.Job:  map 100% reduce 83%
17/04/04 14:38:33 INFO mapreduce.Job:  map 100% reduce 84%
17/04/04 14:38:38 INFO mapreduce.Job:  map 100% reduce 85%
17/04/04 14:38:44 INFO mapreduce.Job:  map 100% reduce 86%
17/04/04 14:38:50 INFO mapreduce.Job:  map 100% reduce 88%
17/04/04 14:38:56 INFO mapreduce.Job:  map 100% reduce 90%
17/04/04 14:39:02 INFO mapreduce.Job:  map 100% reduce 92%
17/04/04 14:39:14 INFO mapreduce.Job:  map 100% reduce 93%
17/04/04 14:39:31 INFO mapreduce.Job:  map 100% reduce 94%
17/04/04 14:39:44 INFO mapreduce.Job:  map 100% reduce 95%
17/04/04 14:39:56 INFO mapreduce.Job:  map 100% reduce 96%
17/04/04 14:40:02 INFO mapreduce.Job:  map 100% reduce 97%
17/04/04 14:40:14 INFO mapreduce.Job:  map 100% reduce 98%
17/04/04 14:40:20 INFO mapreduce.Job:  map 100% reduce 99%
17/04/04 14:40:32 INFO mapreduce.Job:  map 100% reduce 100%
17/04/04 14:40:36 INFO mapreduce.Job: Job job_1491310226923_0003 completed successfully
17/04/04 14:40:36 INFO mapreduce.Job: Counters: 50
        File System Counters
                FILE: Number of bytes read=4448645708
                FILE: Number of bytes written=8830137013
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=10000048900
                HDFS: Number of bytes written=10000000000
                HDFS: Number of read operations=918
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=12
        Job Counters
                Launched map tasks=300
                Launched reduce tasks=6
                Data-local map tasks=161
                Rack-local map tasks=139
                Total time spent by all maps in occupied slots (ms)=2863174
                Total time spent by all reduces in occupied slots (ms)=906764
                Total time spent by all map tasks (ms)=2863174
                Total time spent by all reduce tasks (ms)=906764
                Total vcore-seconds taken by all map tasks=2863174
                Total vcore-seconds taken by all reduce tasks=906764
                Total megabyte-seconds taken by all map tasks=2931890176
                Total megabyte-seconds taken by all reduce tasks=928526336
        Map-Reduce Framework
                Map input records=100000000
                Map output records=100000000
                Map output bytes=10200000000
                Map output materialized bytes=4342785901
                Input split bytes=48900
                Combine input records=0
                Combine output records=0
                Reduce input groups=100000000
                Reduce shuffle bytes=4342785901
                Reduce input records=100000000
                Reduce output records=100000000
                Spilled Records=200000000
                Shuffled Maps =1800
                Failed Shuffles=0
                Merged Map outputs=1800
                GC time elapsed (ms)=41209
                CPU time spent (ms)=1480110
                Physical memory (bytes) snapshot=152764715008
                Virtual memory (bytes) snapshot=482160971776
                Total committed heap usage (bytes)=172037767168
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=10000000000
        File Output Format Counters
                Bytes Written=10000000000
17/04/04 14:40:36 INFO terasort.TeraSort: done
