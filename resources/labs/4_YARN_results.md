# Results
## 8 Mappers, 1 Reducer, from 512 to 1024
```
[hdfs@ip-172-31-8-114 tmp]$ sh YARNtest.sh
Testing loop started on Tue Apr 4 19:35:01 UTC 2017

PARAMETERS
i = 8
j = 1
k = 512
MAP_MB = 409
RED_MB = 409

real    1m55.395s
user    0m6.013s
sys     0m0.297s

real    4m15.996s
user    0m8.920s
sys     0m0.426s
Deleted /results/tg-10GB-8-1-512
Deleted /results/ts-10GB-8-1-512

PARAMETERS
i = 8
j = 1
k = 1024
MAP_MB = 819
RED_MB = 819

real    1m49.720s
user    0m6.031s
sys     0m0.296s

real    6m12.568s
user    0m8.478s
sys     0m0.367s
Deleted /results/tg-10GB-8-1-1024
Deleted /results/ts-10GB-8-1-1024
Testing loop ended on Tue Apr 4 19:49:25 UTC 2017
```

## 12 Mappers, 6 Reducers, from 2048 to 4096
```
[hdfs@ip-172-31-8-114 tmp]$ sh YARNtest.sh
Testing loop started on Tue Apr 4 20:04:14 UTC 2017

PARAMETERS
i = 12
j = 6
k = 2048
MAP_MB = 1638
RED_MB = 1638

real    1m46.708s
user    0m5.990s
sys     0m0.306s

real    3m1.748s
user    0m7.971s
sys     0m0.352s
Deleted /results/tg-10GB-12-6-2048
Deleted /results/ts-10GB-12-6-2048

PARAMETERS
i = 12
j = 6
k = 4096
MAP_MB = 3276
RED_MB = 3276

real    1m57.621s
user    0m6.120s
sys     0m0.315s

real    5m31.341s
user    0m8.915s
sys     0m0.405s
Deleted /results/tg-10GB-12-6-4096
Deleted /results/ts-10GB-12-6-4096
Testing loop ended on Tue Apr 4 20:16:43 UTC 2017
```

# Comments
The best performance was actived with 12 mappers, 6 reducers and 1638 MB of memory. This is not the optimal configuration, since much more tests would be necessary to reach that conclusion.