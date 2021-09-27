I am using ```fio``` workload generator to test my data on storage. 
I installed ``` https://github.com/axboe/fio``` for Centos 7 and upgraded GCC version to 4.9 to install it on Centos 7. 
Then I generated ``` ./fio --randrepeat=1 --direct=1 --name=test --filename=test --bs=4K --size=100M -readwrite=write --numjobs=5 ``` on /dev/sda1 storage to test 
SSD performance on client computes. 
Result data is displayed as : 
```
test: (groupid=0, jobs=1): err= 0: pid=10133: Mon Sep 27 12:49:28 2021
  write: IOPS=18, BW=74.5KiB/s (76.3kB/s)(100MiB/1374004msec); 0 zone resets
    clat (msec): min=9, max=1175, avg=53.67, stdev=48.33
     lat (msec): min=9, max=1175, avg=53.67, stdev=48.33
    clat percentiles (msec):
     |  1.00th=[   26],  5.00th=[   29], 10.00th=[   36], 20.00th=[   41],
     | 30.00th=[   42], 40.00th=[   44], 50.00th=[   46], 60.00th=[   50],
     | 70.00th=[   53], 80.00th=[   57], 90.00th=[   64], 95.00th=[   74],
     | 99.00th=[  342], 99.50th=[  414], 99.90th=[  558], 99.95th=[  802],
     | 99.99th=[  995]
   bw (  KiB/s): min=    8, max=  144, per=19.86%, avg=74.91, stdev=24.60, samples=2733
   iops        : min=    2, max=   36, avg=18.73, stdev= 6.15, samples=2733
  lat (msec)   : 10=0.01%, 20=0.01%, 50=63.80%, 100=33.69%, 250=1.02%
  lat (msec)   : 500=1.32%, 750=0.09%, 1000=0.05%, 2000=0.01%
  cpu          : usr=0.02%, sys=0.05%, ctx=25612, majf=0, minf=42
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,25600,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=10134: Mon Sep 27 12:49:28 2021
  write: IOPS=18, BW=74.5KiB/s (76.3kB/s)(100MiB/1374007msec); 0 zone resets
    clat (msec): min=8, max=1210, avg=53.66, stdev=48.33
     lat (msec): min=8, max=1210, avg=53.67, stdev=48.33
    clat percentiles (msec):
     |  1.00th=[   26],  5.00th=[   29], 10.00th=[   36], 20.00th=[   41],
     | 30.00th=[   42], 40.00th=[   44], 50.00th=[   46], 60.00th=[   50],
     | 70.00th=[   53], 80.00th=[   57], 90.00th=[   64], 95.00th=[   74],
     | 99.00th=[  342], 99.50th=[  414], 99.90th=[  527], 99.95th=[  818],
     | 99.99th=[ 1020]
   bw (  KiB/s): min=    8, max=  144, per=19.86%, avg=74.83, stdev=24.62, samples=2736
   iops        : min=    2, max=   36, avg=18.71, stdev= 6.16, samples=2736
  lat (msec)   : 10=0.01%, 20=0.02%, 50=63.96%, 100=33.48%, 250=1.08%
  lat (msec)   : 500=1.30%, 750=0.10%, 1000=0.04%, 2000=0.01%
  cpu          : usr=0.02%, sys=0.05%, ctx=25616, majf=0, minf=41
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,25600,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=10135: Mon Sep 27 12:49:28 2021
  write: IOPS=18, BW=74.5KiB/s (76.3kB/s)(100MiB/1374055msec); 0 zone resets
    clat (msec): min=9, max=1247, avg=53.67, stdev=48.51
     lat (msec): min=9, max=1247, avg=53.67, stdev=48.51
    clat percentiles (msec):
     |  1.00th=[   26],  5.00th=[   29], 10.00th=[   36], 20.00th=[   41],
     | 30.00th=[   42], 40.00th=[   44], 50.00th=[   46], 60.00th=[   50],
     | 70.00th=[   53], 80.00th=[   57], 90.00th=[   64], 95.00th=[   74],
     | 99.00th=[  351], 99.50th=[  422], 99.90th=[  531], 99.95th=[  818],
     | 99.99th=[ 1003]
   bw (  KiB/s): min=    8, max=  144, per=19.86%, avg=74.85, stdev=24.43, samples=2735
   iops        : min=    2, max=   36, avg=18.71, stdev= 6.11, samples=2735
  lat (msec)   : 10=0.01%, 20=0.02%, 50=64.14%, 100=33.34%, 250=1.03%
  lat (msec)   : 500=1.33%, 750=0.07%, 1000=0.05%, 2000=0.01%
  cpu          : usr=0.02%, sys=0.05%, ctx=25612, majf=0, minf=40
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,25600,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=10136: Mon Sep 27 12:49:28 2021
  write: IOPS=18, BW=74.5KiB/s (76.3kB/s)(100MiB/1374128msec); 0 zone resets
    clat (msec): min=9, max=1135, avg=53.67, stdev=48.29
     lat (msec): min=9, max=1135, avg=53.67, stdev=48.29
    clat percentiles (msec):
     |  1.00th=[   26],  5.00th=[   29], 10.00th=[   36], 20.00th=[   41],
     | 30.00th=[   42], 40.00th=[   44], 50.00th=[   46], 60.00th=[   50],
     | 70.00th=[   53], 80.00th=[   57], 90.00th=[   64], 95.00th=[   74],
     | 99.00th=[  338], 99.50th=[  422], 99.90th=[  550], 99.95th=[  751],
     | 99.99th=[  995]
   bw (  KiB/s): min=    8, max=  144, per=19.86%, avg=74.82, stdev=24.52, samples=2737
   iops        : min=    2, max=   36, avg=18.71, stdev= 6.13, samples=2737
  lat (msec)   : 10=0.01%, 20=0.02%, 50=63.99%, 100=33.48%, 250=1.02%
  lat (msec)   : 500=1.34%, 750=0.07%, 1000=0.05%, 2000=0.01%
  cpu          : usr=0.02%, sys=0.05%, ctx=25620, majf=0, minf=42
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,25600,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=10137: Mon Sep 27 12:49:28 2021
  write: IOPS=18, BW=74.5KiB/s (76.3kB/s)(100MiB/1374106msec); 0 zone resets
    clat (msec): min=12, max=1281, avg=53.67, stdev=48.43
     lat (msec): min=12, max=1281, avg=53.67, stdev=48.43
    clat percentiles (msec):
     |  1.00th=[   26],  5.00th=[   29], 10.00th=[   36], 20.00th=[   41],
     | 30.00th=[   42], 40.00th=[   44], 50.00th=[   46], 60.00th=[   50],
     | 70.00th=[   53], 80.00th=[   57], 90.00th=[   64], 95.00th=[   74],
     | 99.00th=[  342], 99.50th=[  414], 99.90th=[  558], 99.95th=[  810],
     | 99.99th=[ 1003]
   bw (  KiB/s): min=    8, max=  144, per=19.86%, avg=74.96, stdev=24.43, samples=2731
   iops        : min=    2, max=   36, avg=18.74, stdev= 6.11, samples=2731
  lat (msec)   : 20=0.02%, 50=64.07%, 100=33.40%, 250=1.04%, 500=1.33%
  lat (msec)   test: (groupid=0, jobs=1): err= 0: pid=10133: Mon Sep 27 12:49:28 2021
  write: IOPS=18, BW=74.5KiB/s (76.3kB/s)(100MiB/1374004msec); 0 zone resets
    clat (msec): min=9, max=1175, avg=53.67, stdev=48.33
     lat (msec): min=9, max=1175, avg=53.67, stdev=48.33
    clat percentiles (msec):
     |  1.00th=[   26],  5.00th=[   29], 10.00th=[   36], 20.00th=[   41],
     | 30.00th=[   42], 40.00th=[   44], 50.00th=[   46], 60.00th=[   50],
     | 70.00th=[   53], 80.00th=[   57], 90.00th=[   64], 95.00th=[   74],
     | 99.00th=[  342], 99.50th=[  414], 99.90th=[  558], 99.95th=[  802],
     | 99.99th=[  995]
   bw (  KiB/s): min=    8, max=  144, per=19.86%, avg=74.91, stdev=24.60, samples=2733
   iops        : min=    2, max=   36, avg=18.73, stdev= 6.15, samples=2733
  lat (msec)   : 10=0.01%, 20=0.01%, 50=63.80%, 100=33.69%, 250=1.02%
  lat (msec)   : 500=1.32%, 750=0.09%, 1000=0.05%, 2000=0.01%
  cpu          : usr=0.02%, sys=0.05%, ctx=25612, majf=0, minf=42
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,25600,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=10134: Mon Sep 27 12:49:28 2021
  write: IOPS=18, BW=74.5KiB/s (76.3kB/s)(100MiB/1374007msec); 0 zone resets
    clat (msec): min=8, max=1210, avg=53.66, stdev=48.33
     lat (msec): min=8, max=1210, avg=53.67, stdev=48.33
    clat percentiles (msec):
     |  1.00th=[   26],  5.00th=[   29], 10.00th=[   36], 20.00th=[   41],
     | 30.00th=[   42], 40.00th=[   44], 50.00th=[   46], 60.00th=[   50],
     | 70.00th=[   53], 80.00th=[   57], 90.00th=[   64], 95.00th=[   74],
     | 99.00th=[  342], 99.50th=[  414], 99.90th=[  527], 99.95th=[  818],
     | 99.99th=[ 1020]
   bw (  KiB/s): min=    8, max=  144, per=19.86%, avg=74.83, stdev=24.62, samples=2736
   iops        : min=    2, max=   36, avg=18.71, stdev= 6.16, samples=2736
  lat (msec)   : 10=0.01%, 20=0.02%, 50=63.96%, 100=33.48%, 250=1.08%
  lat (msec)   : 500=1.30%, 750=0.10%, 1000=0.04%, 2000=0.01%
  cpu          : usr=0.02%, sys=0.05%, ctx=25616, majf=0, minf=41
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,25600,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=10135: Mon Sep 27 12:49:28 2021
  write: IOPS=18, BW=74.5KiB/s (76.3kB/s)(100MiB/1374055msec); 0 zone resets
    clat (msec): min=9, max=1247, avg=53.67, stdev=48.51
     lat (msec): min=9, max=1247, avg=53.67, stdev=48.51
    clat percentiles (msec):
     |  1.00th=[   26],  5.00th=[   29], 10.00th=[   36], 20.00th=[   41],
     | 30.00th=[   42], 40.00th=[   44], 50.00th=[   46], 60.00th=[   50],
     | 70.00th=[   53], 80.00th=[   57], 90.00th=[   64], 95.00th=[   74],
     | 99.00th=[  351], 99.50th=[  422], 99.90th=[  531], 99.95th=[  818],
     | 99.99th=[ 1003]
   bw (  KiB/s): min=    8, max=  144, per=19.86%, avg=74.85, stdev=24.43, samples=2735
   iops        : min=    2, max=   36, avg=18.71, stdev= 6.11, samples=2735
  lat (msec)   : 10=0.01%, 20=0.02%, 50=64.14%, 100=33.34%, 250=1.03%
  lat (msec)   : 500=1.33%, 750=0.07%, 1000=0.05%, 2000=0.01%
  cpu          : usr=0.02%, sys=0.05%, ctx=25612, majf=0, minf=40
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,25600,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=10136: Mon Sep 27 12:49:28 2021
  write: IOPS=18, BW=74.5KiB/s (76.3kB/s)(100MiB/1374128msec); 0 zone resets
    clat (msec): min=9, max=1135, avg=53.67, stdev=48.29
     lat (msec): min=9, max=1135, avg=53.67, stdev=48.29
    clat percentiles (msec):
     |  1.00th=[   26],  5.00th=[   29], 10.00th=[   36], 20.00th=[   41],
     | 30.00th=[   42], 40.00th=[   44], 50.00th=[   46], 60.00th=[   50],
     | 70.00th=[   53], 80.00th=[   57], 90.00th=[   64], 95.00th=[   74],
     | 99.00th=[  338], 99.50th=[  422], 99.90th=[  550], 99.95th=[  751],
     | 99.99th=[  995]
   bw (  KiB/s): min=    8, max=  144, per=19.86%, avg=74.82, stdev=24.52, samples=2737
   iops        : min=    2, max=   36, avg=18.71, stdev= 6.13, samples=2737
  lat (msec)   : 10=0.01%, 20=0.02%, 50=63.99%, 100=33.48%, 250=1.02%
  lat (msec)   : 500=1.34%, 750=0.07%, 1000=0.05%, 2000=0.01%
  cpu          : usr=0.02%, sys=0.05%, ctx=25620, majf=0, minf=42
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,25600,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=10137: Mon Sep 27 12:49:28 2021
  write: IOPS=18, BW=74.5KiB/s (76.3kB/s)(100MiB/1374106msec); 0 zone resets
    clat (msec): min=12, max=1281, avg=53.67, stdev=48.43
     lat (msec): min=12, max=1281, avg=53.67, stdev=48.43
    clat percentiles (msec):
     |  1.00th=[   26],  5.00th=[   29], 10.00th=[   36], 20.00th=[   41],
     | 30.00th=[   42], 40.00th=[   44], 50.00th=[   46], 60.00th=[   50],
     | 70.00th=[   53], 80.00th=[   57], 90.00th=[   64], 95.00th=[   74],
     | 99.00th=[  342], 99.50th=[  414], 99.90th=[  558], 99.95th=[  810],
     | 99.99th=[ 1003]
   bw (  KiB/s): min=    8, max=  144, per=19.86%, avg=74.96, stdev=24.43, samples=2731
   iops        : min=    2, max=   36, avg=18.74, stdev= 6.11, samples=2731
  lat (msec)   : 20=0.02%, 50=64.07%, 100=33.40%, 250=1.04%, 500=1.33%
  lat (msec)   : 750=0.08%, 1000=0.05%, 2000=0.01%
  cpu          : usr=0.02%, sys=0.05%, ctx=25607, majf=0, minf=42
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,25600,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=373KiB/s (382kB/s), 74.5KiB/s-74.5KiB/s (76.3kB/s-76.3kB/s), io=500MiB (524MB), run=1374004-1374128msec: 750=0.08%, 1000=0.05%, 2000=0.01%
  cpu          : usr=0.02%, sys=0.05%, ctx=25607, majf=0, minf=42
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,25600,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=373KiB/s (382kB/s), 74.5KiB/s-74.5KiB/s (76.3kB/s-76.3kB/s), io=500MiB (524MB), run=1374004-1374128msec
```

Shortly bw= 373KiB/s which is very slow. 

The same workload on /mnt/ folder where we mounted lustre file system generates : 
```
test: (groupid=0, jobs=1): err= 0: pid=11532: Mon Sep 27 13:05:40 2021
  write: IOPS=31, BW=126KiB/s (129kB/s)(100MiB/811367msec); 0 zone resets
    clat (msec): min=11, max=120, avg=31.68, stdev= 7.45
     lat (msec): min=11, max=120, avg=31.68, stdev= 7.45
    clat percentiles (msec):
     |  1.00th=[   19],  5.00th=[   24], 10.00th=[   25], 20.00th=[   25],
     | 30.00th=[   26], 40.00th=[   31], 50.00th=[   31], 60.00th=[   31],
     | 70.00th=[   36], 80.00th=[   37], 90.00th=[   43], 95.00th=[   44],
     | 99.00th=[   55], 99.50th=[   55], 99.90th=[   61], 99.95th=[   67],
     | 99.99th=[  103]
   bw (  KiB/s): min=   56, max=  160, per=19.99%, avg=126.22, stdev=11.23, samples=1622
   iops        : min=   14, max=   40, avg=31.55, stdev= 2.81, samples=1622
  lat (msec)   : 20=1.27%, 50=97.08%, 100=1.63%, 250=0.01%
  cpu          : usr=0.06%, sys=0.45%, ctx=28815, majf=0, minf=39
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,25600,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=11533: Mon Sep 27 13:05:40 2021
  write: IOPS=31, BW=126KiB/s (130kB/s)(100MiB/809700msec); 0 zone resets
    clat (usec): min=1345, max=120309, avg=31613.80, stdev=7307.92
     lat (usec): min=1346, max=120310, avg=31615.23, stdev=7307.94
    clat percentiles (usec):
     |  1.00th=[18482],  5.00th=[23987], 10.00th=[24249], 20.00th=[24511],
     | 30.00th=[25297], 40.00th=[30016], 50.00th=[30278], 60.00th=[30540],
     | 70.00th=[35914], 80.00th=[36439], 90.00th=[42730], 95.00th=[43254],
     | 99.00th=[54264], 99.50th=[54789], 99.90th=[60556], 99.95th=[66323],
     | 99.99th=[79168]
   bw (  KiB/s): min=   56, max=  160, per=19.99%, avg=126.48, stdev=11.15, samples=1619
   iops        : min=   14, max=   40, avg=31.62, stdev= 2.79, samples=1619
  lat (msec)   : 2=0.03%, 4=0.01%, 10=0.01%, 20=1.04%, 50=97.46%
  lat (msec)   : 100=1.45%, 250=0.01%
  cpu          : usr=0.06%, sys=0.47%, ctx=27383, majf=0, minf=39
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,25600,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=11534: Mon Sep 27 13:05:40 2021
  write: IOPS=31, BW=126KiB/s (129kB/s)(100MiB/812142msec); 0 zone resets
    clat (msec): min=11, max=141, avg=31.71, stdev= 7.47
     lat (msec): min=11, max=141, avg=31.71, stdev= 7.47
    clat percentiles (usec):
     |  1.00th=[18220],  5.00th=[23987], 10.00th=[24249], 20.00th=[24511],
     | 30.00th=[25297], 40.00th=[30016], 50.00th=[30278], 60.00th=[30540],
     | 70.00th=[35914], 80.00th=[36439], 90.00th=[42730], 95.00th=[43779],
     | 99.00th=[54264], 99.50th=[54789], 99.90th=[65274], 99.95th=[66847],
     | 99.99th=[95945]
   bw (  KiB/s): min=   64, max=  248, per=19.99%, avg=126.10, stdev=11.77, samples=1624
   iops        : min=   16, max=   62, avg=31.53, stdev= 2.94, samples=1624
  lat (msec)   : 20=1.15%, 50=97.14%, 100=1.71%, 250=0.01%
  cpu          : usr=0.06%, sys=0.47%, ctx=28321, majf=0, minf=38
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,25600,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=11535: Mon Sep 27 13:05:40 2021
  write: IOPS=31, BW=126KiB/s (129kB/s)(100MiB/811030msec); 0 zone resets
    clat (msec): min=11, max=102, avg=31.67, stdev= 7.39
     lat (msec): min=11, max=102, avg=31.67, stdev= 7.39
    clat percentiles (usec):
     |  1.00th=[18220],  5.00th=[23987], 10.00th=[24249], 20.00th=[24511],
     | 30.00th=[29492], 40.00th=[30016], 50.00th=[30278], 60.00th=[30540],
     | 70.00th=[35914], 80.00th=[36439], 90.00th=[42730], 95.00th=[43254],
     | 99.00th=[54264], 99.50th=[54789], 99.90th=[61080], 99.95th=[66847],
     | 99.99th=[79168]
   bw (  KiB/s): min=   64, max=  160, per=19.99%, avg=126.28, stdev=11.04, samples=1621
   iops        : min=   16, max=   40, avg=31.57, stdev= 2.76, samples=1621
  lat (msec)   : 20=1.36%, 50=97.02%, 100=1.61%, 250=0.01%
  cpu          : usr=0.06%, sys=0.46%, ctx=29384, majf=0, minf=39
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,25600,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1
test: (groupid=0, jobs=1): err= 0: pid=11536: Mon Sep 27 13:05:40 2021
  write: IOPS=31, BW=126KiB/s (129kB/s)(100MiB/811909msec); 0 zone resets
    clat (msec): min=11, max=120, avg=31.70, stdev= 7.47
     lat (msec): min=11, max=120, avg=31.70, stdev= 7.47
    clat percentiles (msec):
     |  1.00th=[   19],  5.00th=[   24], 10.00th=[   25], 20.00th=[   25],
     | 30.00th=[   26], 40.00th=[   31], 50.00th=[   31], 60.00th=[   31],
     | 70.00th=[   36], 80.00th=[   37], 90.00th=[   43], 95.00th=[   44],
     | 99.00th=[   55], 99.50th=[   55], 99.90th=[   62], 99.95th=[   68],
     | 99.99th=[  103]
   bw (  KiB/s): min=   56, max=  176, per=19.99%, avg=126.10, stdev=11.28, samples=1623
   iops        : min=   14, max=   44, avg=31.52, stdev= 2.82, samples=1623
  lat (msec)   : 20=1.29%, 50=97.07%, 100=1.62%, 250=0.02%
  cpu          : usr=0.06%, sys=0.45%, ctx=28593, majf=0, minf=38
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,25600,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=630KiB/s (646kB/s), 126KiB/s-126KiB/s (129kB/s-130kB/s), io=500MiB (524MB), run=809700-812142msec
```
The bandwidth on lustre client was : 630 KiB/s. 

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


