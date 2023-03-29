# Read Plotting Result

For Read Operation I've been running using configuration below here :
```
[global]
ioengine=io_uring
rw=read
runtime=60
direct=1 
bs=4k
numjobs=n(starting from 1,4,16,32,64,128,256)
threads=n(starting from 1,4,16,32,64,128,256)
time_based=1
thread
group_reporting
norandommap=1
randrepeat=0
size=1G

[nvme]
filename=/dev/nvme0n1 
```

# Result 

## QD=1 
```
read: (groupid=0, jobs=1): err= 0: pid=3312: Mon Mar 27 22:56:43 2023
  read: IOPS=74.9k, BW=293MiB/s (307MB/s)(17.1GiB/60001msec)
    slat (usec): min=6, max=7950, avg=12.72, stdev= 7.72
    clat (nsec): min=61, max=8261.5k, avg=150.04, stdev=8780.85
     lat (usec): min=9, max=8272, avg=12.99, stdev=11.70
    clat percentiles (nsec):
     |  1.00th=[   85],  5.00th=[   90], 10.00th=[   92], 20.00th=[   96],
     | 30.00th=[   98], 40.00th=[   99], 50.00th=[  100], 60.00th=[  103],
     | 70.00th=[  105], 80.00th=[  107], 90.00th=[  109], 95.00th=[  112],
     | 99.00th=[  126], 99.50th=[  175], 99.90th=[ 9920], 99.95th=[14400],
     | 99.99th=[20608]
   bw (  KiB/s): min=237080, max=304416, per=99.98%, avg=299486.89, stdev=9362.64, samples=119
   iops        : min=59270, max=76104, avg=74871.77, stdev=2340.65, samples=119
  lat (nsec)   : 100=43.87%, 250=55.72%, 500=0.06%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.09%, 10=0.16%, 20=0.09%, 50=0.01%
  lat (usec)   : 100=0.01%, 250=0.01%, 500=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=10.07%, sys=89.67%, ctx=11169, majf=0, minf=1
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=4493314,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=293MiB/s (307MB/s), 293MiB/s-293MiB/s (307MB/s-307MB/s), io=17.1GiB (18.4GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=4485602/0, merge=0/0, ticks=42390/0, in_queue=44, util=99.97%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067252/Research/IOUring/IOPS/read/read-1_hgmxft.jpg" alt="Read-1" width="600"/>
<br><br>

## QD=4 
```
read: (groupid=0, jobs=4): err= 0: pid=3318: Mon Mar 27 22:58:19 2023
  read: IOPS=284k, BW=1110MiB/s (1164MB/s)(65.0GiB/60002msec)
    slat (usec): min=8, max=12054, avg=13.39, stdev=11.16
    clat (nsec): min=65, max=8430.7k, avg=182.24, stdev=9014.25
     lat (usec): min=8, max=12055, avg=13.71, stdev=14.36
    clat percentiles (nsec):
     |  1.00th=[   82],  5.00th=[   86], 10.00th=[   87], 20.00th=[   89],
     | 30.00th=[   92], 40.00th=[   94], 50.00th=[   97], 60.00th=[  100],
     | 70.00th=[  103], 80.00th=[  151], 90.00th=[  153], 95.00th=[  153],
     | 99.00th=[  203], 99.50th=[ 4192], 99.90th=[ 9152], 99.95th=[14400],
     | 99.99th=[20608]
   bw (  MiB/s): min= 1001, max= 1128, per=100.00%, avg=1109.66, stdev= 4.22, samples=477
   iops        : min=256268, max=288948, avg=284073.53, stdev=1079.56, samples=477
  lat (nsec)   : 100=56.67%, 250=42.38%, 500=0.04%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.40%, 10=0.42%, 20=0.07%, 50=0.01%
  lat (usec)   : 100=0.01%, 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=9.70%, sys=89.90%, ctx=90967, majf=0, minf=4
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=17044358,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=1110MiB/s (1164MB/s), 1110MiB/s-1110MiB/s (1164MB/s-1164MB/s), io=65.0GiB (69.8GB), run=60002-60002msec

Disk stats (read/write):
  nvme0n1: ios=17015837/0, merge=0/0, ticks=168385/0, in_queue=148, util=99.93%
```

### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067252/Research/IOUring/IOPS/read/read-4_tkgdpm.jpg" alt="Read-4" width="600"/>
<br><br>

## QD=16
```
read: (groupid=0, jobs=16): err= 0: pid=3329: Mon Mar 27 22:59:47 2023
  read: IOPS=279k, BW=1088MiB/s (1141MB/s)(63.8GiB/60014msec)
    slat (usec): min=2, max=57477, avg=28.36, stdev=514.39
    clat (nsec): min=61, max=36473k, avg=27985.44, stdev=494512.82
     lat (usec): min=8, max=57482, avg=56.61, stdev=715.08
    clat percentiles (nsec):
     |  1.00th=[      87],  5.00th=[      93], 10.00th=[      97],
     | 20.00th=[     100], 30.00th=[     103], 40.00th=[     106],
     | 50.00th=[     107], 60.00th=[     111], 70.00th=[     114],
     | 80.00th=[     129], 90.00th=[     169], 95.00th=[     175],
     | 99.00th=[  109056], 99.50th=[  716800], 99.90th=[ 8093696],
     | 99.95th=[11993088], 99.99th=[18743296]
   bw (  MiB/s): min=  673, max= 1341, per=99.93%, avg=1087.49, stdev= 6.13, samples=1911
   iops        : min=172350, max=343434, avg=278396.47, stdev=1568.35, samples=1911
  lat (nsec)   : 100=18.44%, 250=78.43%, 500=0.13%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.62%, 10=0.07%, 20=0.04%, 50=0.61%
  lat (usec)   : 100=0.57%, 250=0.43%, 500=0.10%, 750=0.05%, 1000=0.04%
  lat (msec)   : 2=0.10%, 4=0.12%, 10=0.16%, 20=0.07%, 50=0.01%
  cpu          : usr=2.52%, sys=22.30%, ctx=434681, majf=0, minf=16
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=16719387,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=1088MiB/s (1141MB/s), 1088MiB/s-1088MiB/s (1141MB/s-1141MB/s), io=63.8GiB (68.5GB), run=60014-60014msec

Disk stats (read/write):
  nvme0n1: ios=16674410/0, merge=0/0, ticks=177050/0, in_queue=888, util=99.98%
```

### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067252/Research/IOUring/IOPS/read/read-16_o9ldyn.jpg" alt="Read-16" width="600"/>
<br><br>

## QD=32
```
read: (groupid=0, jobs=32): err= 0: pid=3350: Mon Mar 27 23:01:28 2023
  read: IOPS=274k, BW=1071MiB/s (1123MB/s)(62.8GiB/60019msec)
    slat (usec): min=2, max=113260, avg=68.82, stdev=1304.00
    clat (nsec): min=61, max=85917k, avg=45215.88, stdev=761161.85
     lat (usec): min=8, max=113262, avg=114.69, stdev=1514.12
    clat percentiles (nsec):
     |  1.00th=[      77],  5.00th=[      82], 10.00th=[      84],
     | 20.00th=[      87], 30.00th=[      90], 40.00th=[      92],
     | 50.00th=[      94], 60.00th=[      97], 70.00th=[     103],
     | 80.00th=[     165], 90.00th=[     171], 95.00th=[     187],
     | 99.00th=[  552960], 99.50th=[ 1548288], 99.90th=[10682368],
     | 99.95th=[19005440], 99.99th=[31326208]
   bw (  MiB/s): min=  835, max= 1370, per=99.93%, avg=1070.54, stdev= 3.14, samples=3830
   iops        : min=214000, max=350746, avg=274057.51, stdev=803.13, samples=3830
  lat (nsec)   : 100=65.34%, 250=30.75%, 500=0.59%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.33%, 10=0.05%, 20=0.02%, 50=0.26%
  lat (usec)   : 100=0.35%, 250=0.68%, 500=0.56%, 750=0.24%, 1000=0.16%
  lat (msec)   : 2=0.24%, 4=0.18%, 10=0.15%, 20=0.06%, 50=0.05%
  lat (msec)   : 100=0.01%
  cpu          : usr=1.23%, sys=11.25%, ctx=533734, majf=0, minf=31
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=16460618,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=1071MiB/s (1123MB/s), 1071MiB/s-1071MiB/s (1123MB/s-1123MB/s), io=62.8GiB (67.4GB), run=60019-60019msec

Disk stats (read/write):
  nvme0n1: ios=16404309/0, merge=0/0, ticks=174138/0, in_queue=1360, util=99.97%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067252/Research/IOUring/IOPS/read/read-32_rvzlqk.jpg" alt="Read-32" width="600"/>
<br><br>

## QD=64
```
read: (groupid=0, jobs=64): err= 0: pid=3456: Mon Mar 27 23:04:05 2023
  read: IOPS=297k, BW=1159MiB/s (1216MB/s)(67.0GiB/60050msec)
    slat (usec): min=2, max=252011, avg=164.05, stdev=3146.05
    clat (nsec): min=62, max=144026k, avg=45805.01, stdev=1455864.44
     lat (usec): min=8, max=252012, avg=210.87, stdev=3474.09
    clat percentiles (nsec):
     |  1.00th=[      92],  5.00th=[      94], 10.00th=[      96],
     | 20.00th=[      99], 30.00th=[     101], 40.00th=[     102],
     | 50.00th=[     104], 60.00th=[     105], 70.00th=[     107],
     | 80.00th=[     109], 90.00th=[     112], 95.00th=[     115],
     | 99.00th=[     197], 99.50th=[     306], 99.90th=[15400960],
     | 99.95th=[40108032], 99.99th=[64225280]
   bw (  MiB/s): min=  927, max= 1374, per=99.94%, avg=1158.62, stdev= 1.28, samples=7657
   iops        : min=237492, max=351808, avg=296605.28, stdev=327.00, samples=7657
  lat (nsec)   : 100=22.63%, 250=76.79%, 500=0.12%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.24%, 10=0.01%, 20=0.01%, 50=0.01%
  lat (usec)   : 100=0.01%, 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.02%, 10=0.02%, 20=0.02%, 50=0.06%
  lat (msec)   : 100=0.03%, 250=0.01%
  cpu          : usr=0.59%, sys=5.66%, ctx=86430, majf=0, minf=62
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=17821718,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=1159MiB/s (1216MB/s), 1159MiB/s-1159MiB/s (1216MB/s-1216MB/s), io=67.0GiB (72.0GB), run=60050-60050msec

Disk stats (read/write):
  nvme0n1: ios=17818810/0, merge=0/0, ticks=170263/0, in_queue=588, util=99.94%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067252/Research/IOUring/IOPS/read/read-64_lq7qw4.jpg" alt="Read-64" width="600"/>
<br><br>

## QD=128
```
read: (groupid=0, jobs=128): err= 0: pid=3527: Mon Mar 27 23:05:36 2023
  read: IOPS=288k, BW=1124MiB/s (1179MB/s)(65.0GiB/60112msec)
    slat (usec): min=2, max=396492, avg=317.94, stdev=6441.41
    clat (nsec): min=60, max=396478k, avg=113737.36, stdev=3233543.10
     lat (usec): min=8, max=396494, avg=434.17, stdev=7226.24
    clat percentiles (nsec):
     |  1.00th=[       82],  5.00th=[       89], 10.00th=[       91],
     | 20.00th=[       96], 30.00th=[       99], 40.00th=[      101],
     | 50.00th=[      103], 60.00th=[      106], 70.00th=[      107],
     | 80.00th=[      111], 90.00th=[      116], 95.00th=[      125],
     | 99.00th=[      199], 99.50th=[     3216], 99.90th=[ 46923776],
     | 99.95th=[ 89653248], 99.99th=[133693440]
   bw (  MiB/s): min=  711, max= 1513, per=99.79%, avg=1121.88, stdev= 1.14, samples=15315
   iops        : min=182197, max=387336, avg=287199.51, stdev=290.78, samples=15315
  lat (nsec)   : 100=34.37%, 250=64.88%, 500=0.15%, 750=0.02%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.22%, 10=0.01%, 20=0.01%, 50=0.01%
  lat (usec)   : 100=0.02%, 250=0.05%, 500=0.03%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.02%, 10=0.02%, 20=0.02%, 50=0.05%
  lat (msec)   : 100=0.06%, 250=0.04%, 500=0.01%
  cpu          : usr=0.31%, sys=2.82%, ctx=113681, majf=0, minf=123
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=17300927,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=1124MiB/s (1179MB/s), 1124MiB/s-1124MiB/s (1179MB/s-1179MB/s), io=65.0GiB (70.9GB), run=60112-60112msec

Disk stats (read/write):
  nvme0n1: ios=17297802/0, merge=0/0, ticks=173229/0, in_queue=660, util=99.90%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067252/Research/IOUring/IOPS/read/read-128_vwip5v.jpg" alt="Read-128" width="600"/>
<br><br>


## QD=256
```
read: (groupid=0, jobs=256): err= 0: pid=3660: Mon Mar 27 23:07:16 2023
  read: IOPS=285k, BW=1113MiB/s (1167MB/s)(65.4GiB/60166msec)
    slat (usec): min=2, max=1061.8k, avg=406.28, stdev=10213.75
    clat (nsec): min=61, max=775358k, avg=475024.94, stdev=7956868.66
     lat (usec): min=8, max=1085.2k, avg=884.95, stdev=12980.76
    clat percentiles (nsec):
     |  1.00th=[       83],  5.00th=[       89], 10.00th=[       92],
     | 20.00th=[       97], 30.00th=[       99], 40.00th=[      102],
     | 50.00th=[      104], 60.00th=[      106], 70.00th=[      109],
     | 80.00th=[      111], 90.00th=[      118], 95.00th=[      127],
     | 99.00th=[     3216], 99.50th=[ 25034752], 99.90th=[141557760],
     | 99.95th=[193986560], 99.99th=[274726912]
   bw (  MiB/s): min=  448, max= 1789, per=98.99%, avg=1101.81, stdev= 0.94, samples=30607
   iops        : min=114828, max=458113, avg=281993.07, stdev=241.07, samples=30607
  lat (nsec)   : 100=31.67%, 250=67.11%, 500=0.11%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.22%, 10=0.01%, 20=0.01%, 50=0.01%
  lat (usec)   : 100=0.01%, 250=0.03%, 500=0.02%, 750=0.02%, 1000=0.01%
  lat (msec)   : 2=0.04%, 4=0.03%, 10=0.04%, 20=0.11%, 50=0.28%
  lat (msec)   : 100=0.13%, 250=0.13%, 500=0.02%, 750=0.01%, 1000=0.01%
  cpu          : usr=0.15%, sys=1.41%, ctx=185594, majf=0, minf=254
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=17142985,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=1113MiB/s (1167MB/s), 1113MiB/s-1113MiB/s (1167MB/s-1167MB/s), io=65.4GiB (70.2GB), run=60166-60166msec

Disk stats (read/write):
  nvme0n1: ios=17115078/0, merge=0/0, ticks=188183/0, in_queue=6564, util=99.87%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067252/Research/IOUring/IOPS/read/read-256_h7lzpr.jpg" alt="Read-256" width="600"/>
<br><br>