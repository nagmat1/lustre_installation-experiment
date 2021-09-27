I am using ```fio``` workload generator to test my data on storage. 
I installed ``` https://github.com/axboe/fio``` for Centos 7 and upgraded GCC version to 4.9 to install it on Centos 7. 
Then I generated ``` ./fio --name=test --filename=test --bs=4K --size=10M -readwrite=write --numjobs=10 ``` on /dev/sda1 storage to test 
SSD performance on client computes. 
Result data is displayed as : 
```
test: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=psync, iodepth=1
...
fio-3.28-35-g6e0ef
Starting 10 processes
Jobs: 4 (f=4): [_(3),f(1),W(1),_(2),W(1),_(1),f(1)][100.0%][w=13.5MiB/s][w=3457 IOPS][eta 00m:00s]
test: (groupid=0, jobs=1): err= 0: pid=12674: Mon Sep 27 13:12:50 2021
  write: IOPS=1066, BW=4265KiB/s (4367kB/s)(10.0MiB/2401msec); 0 zone resets
    clat (usec): min=9, max=574086, avg=896.92, stdev=17888.36
     lat (usec): min=9, max=574086, avg=897.49, stdev=17888.36
    clat percentiles (usec):
     |  1.00th=[    11],  5.00th=[    11], 10.00th=[    12], 20.00th=[    13],
     | 30.00th=[    13], 40.00th=[    13], 50.00th=[    14], 60.00th=[    14],
     | 70.00th=[    15], 80.00th=[    16], 90.00th=[    18], 95.00th=[    24],
     | 99.00th=[  1418], 99.50th=[ 10814], 99.90th=[400557], 99.95th=[459277],
     | 99.99th=[574620]
   bw (  KiB/s): min= 2144, max= 7224, per=17.70%, avg=4395.50, stdev=2565.94, samples=4
   iops        : min=  536, max= 1806, avg=1098.75, stdev=641.62, samples=4
  lat (usec)   : 10=0.74%, 20=92.34%, 50=5.47%, 100=0.39%, 250=0.04%
  lat (msec)   : 2=0.04%, 10=0.12%, 20=0.51%, 50=0.08%, 100=0.08%
  lat (msec)   : 250=0.04%, 500=0.12%, 750=0.04%
  cpu          : usr=0.75%, sys=1.21%, ctx=60, majf=0, minf=42
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12675: Mon Sep 27 13:12:50 2021
  write: IOPS=837, BW=3350KiB/s (3430kB/s)(10.0MiB/3057msec); 0 zone resets
    clat (usec): min=8, max=742751, avg=1188.19, stdev=23879.75
     lat (usec): min=8, max=742753, avg=1188.76, stdev=23879.77
    clat percentiles (usec):
     |  1.00th=[     9],  5.00th=[    11], 10.00th=[    12], 20.00th=[    12],
     | 30.00th=[    13], 40.00th=[    13], 50.00th=[    13], 60.00th=[    14],
     | 70.00th=[    14], 80.00th=[    15], 90.00th=[    16], 95.00th=[    20],
     | 99.00th=[   545], 99.50th=[ 23462], 99.90th=[633340], 99.95th=[641729],
     | 99.99th=[742392]
   bw (  KiB/s): min=  256, max= 6896, per=15.78%, avg=3918.20, stdev=2380.13, samples=5
   iops        : min=   64, max= 1724, avg=979.40, stdev=594.99, samples=5
  lat (usec)   : 10=4.34%, 20=90.82%, 50=3.32%, 100=0.47%, 250=0.04%
  lat (usec)   : 750=0.04%
  lat (msec)   : 4=0.12%, 10=0.12%, 20=0.16%, 50=0.16%, 100=0.16%
  lat (msec)   : 250=0.16%, 750=0.12%
  cpu          : usr=0.49%, sys=0.95%, ctx=58, majf=0, minf=42
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12676: Mon Sep 27 13:12:50 2021
  write: IOPS=4436, BW=17.3MiB/s (18.2MB/s)(10.0MiB/577msec); 0 zone resets
    clat (usec): min=9, max=288970, avg=218.18, stdev=6065.77
     lat (usec): min=10, max=288971, avg=218.76, stdev=6065.78
    clat percentiles (usec):
     |  1.00th=[    12],  5.00th=[    12], 10.00th=[    12], 20.00th=[    13],
     | 30.00th=[    13], 40.00th=[    13], 50.00th=[    13], 60.00th=[    14],
     | 70.00th=[    16], 80.00th=[    17], 90.00th=[    17], 95.00th=[    21],
     | 99.00th=[    45], 99.50th=[    79], 99.90th=[ 57410], 99.95th=[ 58983],
     | 99.99th=[287310]
   bw (  KiB/s): min= 5960, max= 5960, per=24.00%, avg=5960.00, stdev= 0.00, samples=1
   iops        : min= 1490, max= 1490, avg=1490.00, stdev= 0.00, samples=1
  lat (usec)   : 10=0.08%, 20=94.80%, 50=4.14%, 100=0.51%, 250=0.16%
  lat (msec)   : 10=0.04%, 20=0.12%, 100=0.12%, 500=0.04%
  cpu          : usr=2.43%, sys=6.08%, ctx=31, majf=0, minf=41
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12677: Mon Sep 27 13:12:50 2021
  write: IOPS=685, BW=2740KiB/s (2806kB/s)(10.0MiB/3737msec); 0 zone resets
    clat (usec): min=8, max=738274, avg=1424.34, stdev=25736.42
     lat (usec): min=8, max=738274, avg=1424.90, stdev=25736.43
    clat percentiles (usec):
     |  1.00th=[    10],  5.00th=[    11], 10.00th=[    12], 20.00th=[    13],
     | 30.00th=[    13], 40.00th=[    13], 50.00th=[    14], 60.00th=[    15],
     | 70.00th=[    16], 80.00th=[    17], 90.00th=[    18], 95.00th=[    22],
     | 99.00th=[   273], 99.50th=[ 33162], 99.90th=[641729], 99.95th=[708838],
     | 99.99th=[742392]
   bw (  KiB/s): min=  248, max= 5768, per=13.06%, avg=3243.00, stdev=2411.35, samples=6
   iops        : min=   62, max= 1442, avg=810.50, stdev=602.68, samples=6
  lat (usec)   : 10=2.27%, 20=91.33%, 50=5.00%, 100=0.31%, 250=0.08%
  lat (usec)   : 500=0.04%
  lat (msec)   : 10=0.12%, 20=0.20%, 50=0.23%, 100=0.04%, 250=0.23%
  lat (msec)   : 500=0.04%, 750=0.12%
  cpu          : usr=0.32%, sys=0.94%, ctx=71, majf=0, minf=42
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12678: Mon Sep 27 13:12:50 2021
  write: IOPS=620, BW=2484KiB/s (2543kB/s)(10.0MiB/4123msec); 0 zone resets
    clat (usec): min=8, max=636370, avg=1498.95, stdev=23445.26
     lat (usec): min=8, max=636371, avg=1499.54, stdev=23445.29
    clat percentiles (usec):
     |  1.00th=[     9],  5.00th=[    10], 10.00th=[    12], 20.00th=[    12],
     | 30.00th=[    13], 40.00th=[    13], 50.00th=[    13], 60.00th=[    14],
     | 70.00th=[    14], 80.00th=[    15], 90.00th=[    16], 95.00th=[    28],
     | 99.00th=[  4948], 99.50th=[ 84411], 99.90th=[541066], 99.95th=[624952],
     | 99.99th=[633340]
   bw (  KiB/s): min=    8, max= 4718, per=8.95%, avg=2223.57, stdev=1888.20, samples=7
   iops        : min=    2, max= 1179, avg=555.71, stdev=471.92, samples=7
  lat (usec)   : 10=5.51%, 20=88.55%, 50=4.41%, 100=0.35%, 250=0.04%
  lat (msec)   : 2=0.04%, 4=0.08%, 10=0.04%, 20=0.12%, 50=0.23%
  lat (msec)   : 100=0.23%, 250=0.23%, 500=0.04%, 750=0.12%
  cpu          : usr=0.39%, sys=0.73%, ctx=83, majf=0, minf=42
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12679: Mon Sep 27 13:12:50 2021
  write: IOPS=725, BW=2902KiB/s (2972kB/s)(10.0MiB/3528msec); 0 zone resets
    clat (usec): min=10, max=640944, avg=1372.69, stdev=22975.48
     lat (usec): min=10, max=640945, avg=1373.28, stdev=22975.49
    clat percentiles (usec):
     |  1.00th=[    12],  5.00th=[    12], 10.00th=[    12], 20.00th=[    13],
     | 30.00th=[    13], 40.00th=[    13], 50.00th=[    13], 60.00th=[    14],
     | 70.00th=[    14], 80.00th=[    14], 90.00th=[    16], 95.00th=[    25],
     | 99.00th=[   159], 99.50th=[ 55313], 99.90th=[404751], 99.95th=[608175],
     | 99.99th=[641729]
   bw (  KiB/s): min=    8, max= 7408, per=11.70%, avg=2906.43, stdev=3108.93, samples=7
   iops        : min=    2, max= 1852, avg=726.43, stdev=777.21, samples=7
  lat (usec)   : 20=94.22%, 50=3.98%, 100=0.55%, 250=0.27%, 750=0.04%
  lat (usec)   : 1000=0.04%
  lat (msec)   : 2=0.04%, 10=0.16%, 20=0.08%, 50=0.12%, 100=0.16%
  lat (msec)   : 250=0.12%, 500=0.16%, 750=0.08%
  cpu          : usr=0.26%, sys=1.02%, ctx=61, majf=0, minf=42
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12680: Mon Sep 27 13:12:50 2021
  write: IOPS=1478, BW=5912KiB/s (6054kB/s)(10.0MiB/1732msec); 0 zone resets
    clat (usec): min=9, max=696749, avg=669.32, stdev=16460.79
     lat (usec): min=9, max=696751, avg=669.88, stdev=16460.81
    clat percentiles (usec):
     |  1.00th=[    11],  5.00th=[    13], 10.00th=[    14], 20.00th=[    15],
     | 30.00th=[    16], 40.00th=[    16], 50.00th=[    16], 60.00th=[    17],
     | 70.00th=[    17], 80.00th=[    17], 90.00th=[    20], 95.00th=[    22],
     | 99.00th=[    57], 99.50th=[ 10552], 99.90th=[283116], 99.95th=[333448],
     | 99.99th=[700449]
   bw (  KiB/s): min= 1576, max=10364, per=23.73%, avg=5894.67, stdev=4395.94, samples=3
   iops        : min=  394, max= 2591, avg=1473.67, stdev=1098.98, samples=3
  lat (usec)   : 10=0.47%, 20=90.16%, 50=8.16%, 100=0.43%, 250=0.04%
  lat (usec)   : 500=0.04%
  lat (msec)   : 4=0.04%, 10=0.12%, 20=0.27%, 50=0.08%, 100=0.08%
  lat (msec)   : 500=0.08%, 750=0.04%
  cpu          : usr=1.10%, sys=2.02%, ctx=45, majf=0, minf=42
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12681: Mon Sep 27 13:12:50 2021
  write: IOPS=629, BW=2517KiB/s (2577kB/s)(10.0MiB/4069msec); 0 zone resets
    clat (usec): min=8, max=640566, avg=1532.39, stdev=22972.13
     lat (usec): min=9, max=640566, avg=1532.97, stdev=22972.14
    clat percentiles (usec):
     |  1.00th=[    11],  5.00th=[    12], 10.00th=[    12], 20.00th=[    13],
     | 30.00th=[    13], 40.00th=[    13], 50.00th=[    14], 60.00th=[    14],
     | 70.00th=[    15], 80.00th=[    15], 90.00th=[    17], 95.00th=[    22],
     | 99.00th=[ 10814], 99.50th=[116917], 99.90th=[404751], 99.95th=[624952],
     | 99.99th=[641729]
   bw (  KiB/s): min=   48, max= 6800, per=10.76%, avg=2673.00, stdev=2710.08, samples=7
   iops        : min=   12, max= 1700, avg=668.00, stdev=677.42, samples=7
  lat (usec)   : 10=0.98%, 20=93.44%, 50=3.75%, 100=0.66%
  lat (msec)   : 2=0.04%, 4=0.04%, 10=0.04%, 20=0.20%, 50=0.27%
  lat (msec)   : 100=0.08%, 250=0.35%, 500=0.08%, 750=0.08%
  cpu          : usr=0.27%, sys=0.86%, ctx=84, majf=0, minf=42
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12682: Mon Sep 27 13:12:50 2021
  write: IOPS=785, BW=3141KiB/s (3216kB/s)(10.0MiB/3260msec); 0 zone resets
    clat (usec): min=9, max=738293, avg=1262.18, stdev=23697.58
     lat (usec): min=9, max=738293, avg=1262.76, stdev=23697.58
    clat percentiles (usec):
     |  1.00th=[    10],  5.00th=[    11], 10.00th=[    11], 20.00th=[    12],
     | 30.00th=[    12], 40.00th=[    13], 50.00th=[    13], 60.00th=[    14],
     | 70.00th=[    14], 80.00th=[    15], 90.00th=[    17], 95.00th=[    28],
     | 99.00th=[    80], 99.50th=[ 23462], 99.90th=[517997], 99.95th=[616563],
     | 99.99th=[742392]
   bw (  KiB/s): min= 1176, max= 8976, per=16.39%, avg=4070.40, stdev=3256.26, samples=5
   iops        : min=  294, max= 2244, avg=1017.60, stdev=814.07, samples=5
  lat (usec)   : 10=2.03%, 20=91.48%, 50=4.92%, 100=0.59%, 250=0.08%
  lat (usec)   : 1000=0.04%
  lat (msec)   : 4=0.08%, 10=0.04%, 20=0.16%, 50=0.16%, 100=0.12%
  lat (msec)   : 250=0.12%, 500=0.08%, 750=0.12%
  cpu          : usr=0.49%, sys=0.89%, ctx=54, majf=0, minf=43
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12683: Mon Sep 27 13:12:50 2021
  write: IOPS=667, BW=2672KiB/s (2736kB/s)(10.0MiB/3833msec); 0 zone resets
    clat (usec): min=9, max=617463, avg=1421.28, stdev=22296.05
     lat (usec): min=10, max=617464, avg=1421.87, stdev=22296.22
    clat percentiles (usec):
     |  1.00th=[    12],  5.00th=[    12], 10.00th=[    12], 20.00th=[    13],
     | 30.00th=[    13], 40.00th=[    13], 50.00th=[    14], 60.00th=[    14],
     | 70.00th=[    15], 80.00th=[    15], 90.00th=[    17], 95.00th=[    30],
     | 99.00th=[   235], 99.50th=[ 52167], 99.90th=[408945], 99.95th=[541066],
     | 99.99th=[616563]
   bw (  KiB/s): min=   48, max= 6648, per=10.32%, avg=2564.71, stdev=2390.24, samples=7
   iops        : min=   12, max= 1662, avg=641.14, stdev=597.57, samples=7
  lat (usec)   : 10=0.04%, 20=92.81%, 50=5.20%, 100=0.70%, 250=0.27%
  lat (msec)   : 2=0.04%, 4=0.04%, 10=0.04%, 20=0.20%, 50=0.16%
  lat (msec)   : 100=0.08%, 250=0.20%, 500=0.16%, 750=0.08%
  cpu          : usr=0.29%, sys=0.99%, ctx=75, majf=0, minf=43
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=24.3MiB/s (25.4MB/s), 2484KiB/s-17.3MiB/s (2543kB/s-18.2MB/s), io=100MiB (105MB), run=577-4123msec
```

Shortly bw= 24.3 MiB/s which is slow. 

The same workload on /mnt/ folder where we mounted lustre file system generates : 
```  ./fio --name=test --filename=test --bs=4K --size=10M -readwrite=write --numjobs=10 ``` 
We get the result as : 

```
test: (g=0): rw=write, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=psync, iodepth=1
...
fio-3.28-35-g6e0ef
Starting 10 processes
Jobs: 8 (f=8)
test: (groupid=0, jobs=1): err= 0: pid=12545: Mon Sep 27 13:11:01 2021
  write: IOPS=2359, BW=9438KiB/s (9664kB/s)(10.0MiB/1085msec); 0 zone resets
    clat (usec): min=41, max=114416, avg=388.78, stdev=3450.82
     lat (usec): min=42, max=114417, avg=389.50, stdev=3450.82
    clat percentiles (usec):
     |  1.00th=[    62],  5.00th=[    64], 10.00th=[    65], 20.00th=[    66],
     | 30.00th=[    67], 40.00th=[    67], 50.00th=[    68], 60.00th=[    69],
     | 70.00th=[    71], 80.00th=[    80], 90.00th=[    84], 95.00th=[    93],
     | 99.00th=[ 10421], 99.50th=[ 13960], 99.90th=[ 29230], 99.95th=[100140],
     | 99.99th=[114820]
   bw (  KiB/s): min= 8501, max= 8501, per=9.55%, avg=8501.00, stdev= 0.00, samples=1
   iops        : min= 2125, max= 2125, avg=2125.00, stdev= 0.00, samples=1
  lat (usec)   : 50=0.27%, 100=96.17%, 250=0.90%, 500=0.04%, 750=0.04%
  lat (usec)   : 1000=0.04%
  lat (msec)   : 2=0.08%, 4=0.27%, 10=1.05%, 20=0.94%, 50=0.12%
  lat (msec)   : 250=0.08%
  cpu          : usr=2.40%, sys=15.77%, ctx=80, majf=0, minf=41
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12546: Mon Sep 27 13:11:01 2021
  write: IOPS=2306, BW=9225KiB/s (9447kB/s)(10.0MiB/1110msec); 0 zone resets
    clat (usec): min=49, max=112551, avg=404.20, stdev=3501.52
     lat (usec): min=50, max=112552, avg=409.64, stdev=3509.15
    clat percentiles (usec):
     |  1.00th=[    63],  5.00th=[    65], 10.00th=[    65], 20.00th=[    66],
     | 30.00th=[    67], 40.00th=[    67], 50.00th=[    68], 60.00th=[    68],
     | 70.00th=[    69], 80.00th=[    72], 90.00th=[    83], 95.00th=[    94],
     | 99.00th=[ 10421], 99.50th=[ 15008], 99.90th=[ 26608], 99.95th=[105382],
     | 99.99th=[112722]
   bw (  KiB/s): min= 7057, max= 7057, per=7.93%, avg=7057.00, stdev= 0.00, samples=1
   iops        : min= 1764, max= 1764, avg=1764.00, stdev= 0.00, samples=1
  lat (usec)   : 50=0.04%, 100=95.70%, 250=1.37%, 1000=0.12%
  lat (msec)   : 2=0.04%, 4=0.31%, 10=1.33%, 20=0.90%, 50=0.12%
  lat (msec)   : 250=0.08%
  cpu          : usr=1.98%, sys=16.23%, ctx=119, majf=0, minf=39
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12547: Mon Sep 27 13:11:01 2021
  write: IOPS=2226, BW=8904KiB/s (9118kB/s)(10.0MiB/1150msec); 0 zone resets
    clat (usec): min=34, max=122071, avg=409.49, stdev=3664.24
     lat (usec): min=34, max=122071, avg=429.16, stdev=3711.93
    clat percentiles (usec):
     |  1.00th=[    50],  5.00th=[    64], 10.00th=[    65], 20.00th=[    65],
     | 30.00th=[    66], 40.00th=[    67], 50.00th=[    67], 60.00th=[    68],
     | 70.00th=[    68], 80.00th=[    70], 90.00th=[    82], 95.00th=[    92],
     | 99.00th=[ 11338], 99.50th=[ 15139], 99.90th=[ 31327], 99.95th=[106431],
     | 99.99th=[122160]
   bw (  KiB/s): min= 6605, max=10328, per=9.51%, avg=8466.50, stdev=2632.56, samples=2
   iops        : min= 1651, max= 2582, avg=2116.50, stdev=658.32, samples=2
  lat (usec)   : 50=0.98%, 100=95.27%, 250=0.86%, 500=0.08%, 1000=0.04%
  lat (msec)   : 2=0.27%, 4=0.39%, 10=0.90%, 20=1.02%, 50=0.12%
  lat (msec)   : 250=0.08%
  cpu          : usr=1.39%, sys=15.40%, ctx=97, majf=0, minf=41
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12548: Mon Sep 27 13:11:01 2021
  write: IOPS=2229, BW=8920KiB/s (9134kB/s)(10.0MiB/1148msec); 0 zone resets
    clat (usec): min=41, max=114633, avg=413.92, stdev=3628.08
     lat (usec): min=41, max=114634, avg=424.84, stdev=3640.51
    clat percentiles (usec):
     |  1.00th=[    52],  5.00th=[    65], 10.00th=[    65], 20.00th=[    66],
     | 30.00th=[    67], 40.00th=[    67], 50.00th=[    68], 60.00th=[    68],
     | 70.00th=[    69], 80.00th=[    70], 90.00th=[    83], 95.00th=[    92],
     | 99.00th=[ 11731], 99.50th=[ 13698], 99.90th=[ 30016], 99.95th=[111674],
     | 99.99th=[114820]
   bw (  KiB/s): min= 6674, max=10138, per=9.44%, avg=8406.00, stdev=2449.42, samples=2
   iops        : min= 1668, max= 2534, avg=2101.00, stdev=612.35, samples=2
  lat (usec)   : 50=0.78%, 100=95.20%, 250=1.09%, 500=0.04%, 750=0.04%
  lat (msec)   : 2=0.31%, 4=0.27%, 10=0.86%, 20=1.25%, 50=0.08%
  lat (msec)   : 250=0.08%
  cpu          : usr=1.83%, sys=15.08%, ctx=104, majf=0, minf=41
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12549: Mon Sep 27 13:11:01 2021
  write: IOPS=7191, BW=28.1MiB/s (29.5MB/s)(10.0MiB/356msec); 0 zone resets
    clat (usec): min=40, max=52932, avg=129.41, stdev=1298.33
     lat (usec): min=40, max=52933, avg=129.95, stdev=1298.34
    clat percentiles (usec):
     |  1.00th=[   42],  5.00th=[   42], 10.00th=[   42], 20.00th=[   46],
     | 30.00th=[   46], 40.00th=[   48], 50.00th=[   54], 60.00th=[   66],
     | 70.00th=[   80], 80.00th=[   84], 90.00th=[   91], 95.00th=[   98],
     | 99.00th=[  172], 99.50th=[ 1029], 99.90th=[17957], 99.95th=[18220],
     | 99.99th=[52691]
  lat (usec)   : 50=46.76%, 100=48.71%, 250=3.87%, 500=0.12%, 750=0.04%
  lat (msec)   : 2=0.04%, 4=0.08%, 10=0.12%, 20=0.23%, 100=0.04%
  cpu          : usr=5.92%, sys=43.66%, ctx=30, majf=0, minf=40
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12550: Mon Sep 27 13:11:01 2021
  write: IOPS=2388, BW=9552KiB/s (9781kB/s)(10.0MiB/1072msec); 0 zone resets
    clat (usec): min=44, max=108220, avg=388.14, stdev=3394.14
     lat (usec): min=45, max=115070, avg=393.38, stdev=3536.76
    clat percentiles (usec):
     |  1.00th=[    58],  5.00th=[    65], 10.00th=[    65], 20.00th=[    66],
     | 30.00th=[    67], 40.00th=[    67], 50.00th=[    68], 60.00th=[    68],
     | 70.00th=[    69], 80.00th=[    77], 90.00th=[    83], 95.00th=[    92],
     | 99.00th=[ 10421], 99.50th=[ 14091], 99.90th=[ 30540], 99.95th=[103285],
     | 99.99th=[108528]
   bw (  KiB/s): min= 7440, max= 7440, per=8.36%, avg=7440.00, stdev= 0.00, samples=1
   iops        : min= 1860, max= 1860, avg=1860.00, stdev= 0.00, samples=1
  lat (usec)   : 50=0.55%, 100=95.62%, 250=1.21%, 1000=0.04%
  lat (msec)   : 4=0.31%, 10=1.13%, 20=0.98%, 50=0.08%, 250=0.08%
  cpu          : usr=1.87%, sys=16.43%, ctx=83, majf=0, minf=41
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12551: Mon Sep 27 13:11:01 2021
  write: IOPS=2361, BW=9446KiB/s (9673kB/s)(10.0MiB/1084msec); 0 zone resets
    clat (usec): min=41, max=130099, avg=400.22, stdev=3740.70
     lat (usec): min=42, max=130100, avg=400.98, stdev=3740.70
    clat percentiles (usec):
     |  1.00th=[    46],  5.00th=[    64], 10.00th=[    65], 20.00th=[    66],
     | 30.00th=[    67], 40.00th=[    67], 50.00th=[    68], 60.00th=[    69],
     | 70.00th=[    72], 80.00th=[    81], 90.00th=[    84], 95.00th=[    92],
     | 99.00th=[  9634], 99.50th=[ 15139], 99.90th=[ 28443], 99.95th=[104334],
     | 99.99th=[130548]
   bw (  KiB/s): min= 8553, max= 8553, per=9.61%, avg=8553.00, stdev= 0.00, samples=1
   iops        : min= 2138, max= 2138, avg=2138.00, stdev= 0.00, samples=1
  lat (usec)   : 50=1.80%, 100=94.73%, 250=0.74%, 750=0.04%, 1000=0.08%
  lat (msec)   : 2=0.12%, 4=0.43%, 10=1.17%, 20=0.59%, 50=0.23%
  lat (msec)   : 250=0.08%
  cpu          : usr=1.94%, sys=16.25%, ctx=90, majf=0, minf=41
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12552: Mon Sep 27 13:11:01 2021
  write: IOPS=2249, BW=8998KiB/s (9214kB/s)(10.0MiB/1138msec); 0 zone resets
    clat (usec): min=41, max=122964, avg=402.99, stdev=3686.79
     lat (usec): min=42, max=122965, avg=411.66, stdev=3708.00
    clat percentiles (usec):
     |  1.00th=[    58],  5.00th=[    64], 10.00th=[    65], 20.00th=[    66],
     | 30.00th=[    67], 40.00th=[    67], 50.00th=[    68], 60.00th=[    68],
     | 70.00th=[    69], 80.00th=[    71], 90.00th=[    83], 95.00th=[    93],
     | 99.00th=[ 10290], 99.50th=[ 14353], 99.90th=[ 36963], 99.95th=[108528],
     | 99.99th=[123208]
   bw (  KiB/s): min= 6973, max=10410, per=9.76%, avg=8691.50, stdev=2430.33, samples=2
   iops        : min= 1743, max= 2602, avg=2172.50, stdev=607.40, samples=2
  lat (usec)   : 50=0.43%, 100=95.82%, 250=0.98%, 500=0.04%
  lat (msec)   : 2=0.08%, 4=0.31%, 10=1.29%, 20=0.86%, 50=0.12%
  lat (msec)   : 250=0.08%
  cpu          : usr=1.67%, sys=15.39%, ctx=122, majf=0, minf=41
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12553: Mon Sep 27 13:11:01 2021
  write: IOPS=2241, BW=8967KiB/s (9182kB/s)(10.0MiB/1142msec); 0 zone resets
    clat (usec): min=48, max=119077, avg=426.97, stdev=3713.43
     lat (usec): min=49, max=119077, avg=427.70, stdev=3713.44
    clat percentiles (usec):
     |  1.00th=[    63],  5.00th=[    64], 10.00th=[    65], 20.00th=[    65],
     | 30.00th=[    66], 40.00th=[    67], 50.00th=[    67], 60.00th=[    68],
     | 70.00th=[    69], 80.00th=[    70], 90.00th=[    82], 95.00th=[    90],
     | 99.00th=[ 11731], 99.50th=[ 14877], 99.90th=[ 30278], 99.95th=[110625],
     | 99.99th=[119014]
   bw (  KiB/s): min= 6512, max=10651, per=9.64%, avg=8581.50, stdev=2926.71, samples=2
   iops        : min= 1628, max= 2662, avg=2145.00, stdev=731.15, samples=2
  lat (usec)   : 50=0.04%, 100=96.52%, 250=0.51%, 500=0.04%, 750=0.04%
  lat (usec)   : 1000=0.04%
  lat (msec)   : 2=0.16%, 4=0.27%, 10=0.98%, 20=1.17%, 50=0.16%
  lat (msec)   : 250=0.08%
  cpu          : usr=1.31%, sys=15.86%, ctx=113, majf=0, minf=42
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=12554: Mon Sep 27 13:11:01 2021
  write: IOPS=2997, BW=11.7MiB/s (12.3MB/s)(10.0MiB/854msec); 0 zone resets
    clat (usec): min=33, max=117574, avg=320.09, stdev=2811.50
     lat (usec): min=34, max=117575, avg=320.75, stdev=2811.50
    clat percentiles (usec):
     |  1.00th=[    35],  5.00th=[    36], 10.00th=[    37], 20.00th=[    65],
     | 30.00th=[    66], 40.00th=[    67], 50.00th=[    67], 60.00th=[    68],
     | 70.00th=[    69], 80.00th=[    72], 90.00th=[    83], 95.00th=[    92],
     | 99.00th=[  8291], 99.50th=[ 12518], 99.90th=[ 25560], 99.95th=[ 26084],
     | 99.99th=[117965]
   bw (  KiB/s): min= 7840, max= 7840, per=8.80%, avg=7840.00, stdev= 0.00, samples=1
   iops        : min= 1960, max= 1960, avg=1960.00, stdev= 0.00, samples=1
  lat (usec)   : 50=14.88%, 100=81.41%, 250=1.13%, 500=0.04%, 750=0.04%
  lat (msec)   : 2=0.08%, 4=0.31%, 10=1.33%, 20=0.59%, 50=0.16%
  lat (msec)   : 250=0.04%
  cpu          : usr=1.88%, sys=19.23%, ctx=80, majf=0, minf=41
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2560,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=87.0MiB/s (91.2MB/s), 8904KiB/s-28.1MiB/s (9118kB/s-29.5MB/s), io=100MiB (105MB), run=356-1150msec
```
The bandwidth on lustre client was : 87 MiB/s. 

On lustre file system : 
```
dd if=/dev/zero of=/mnt/1G bs=1M count=100 

100+0 records in
100+0 records out
104857600 bytes (105 MB) copied, 0.403955 s, 260 MB/s
```

On local storage : 
```
dd if=/dev/zero of=/test bs=1M count=100

100+0 records in
100+0 records out
104857600 bytes (105 MB) copied, 0.551001 s, 190 MB/s


```


