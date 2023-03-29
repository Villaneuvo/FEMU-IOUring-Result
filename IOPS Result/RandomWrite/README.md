# Randwrite Plotting Result

For Random Write Operation I've been running using configuration below here :
```
[global]
ioengine=io_uring
rw=randwrite
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
rand_write: (groupid=0, jobs=1): err= 0: pid=1847: Mon Mar 27 22:01:46 2023
  write: IOPS=62.7k, BW=245MiB/s (257MB/s)(14.3GiB/60001msec); 0 zone resets
    slat (usec): min=8, max=10755, avg=15.05, stdev=22.39
    clat (nsec): min=62, max=6297.8k, avg=162.97, stdev=4519.78
     lat (usec): min=10, max=10763, avg=15.44, stdev=22.89
    clat percentiles (nsec):
     |  1.00th=[  149],  5.00th=[  151], 10.00th=[  151], 20.00th=[  151],
     | 30.00th=[  151], 40.00th=[  153], 50.00th=[  153], 60.00th=[  153],
     | 70.00th=[  153], 80.00th=[  159], 90.00th=[  159], 95.00th=[  161],
     | 99.00th=[  165], 99.50th=[  171], 99.90th=[  294], 99.95th=[  572],
     | 99.99th=[18816]
   bw (  KiB/s): min=246280, max=264976, per=100.00%, avg=250750.32, stdev=2344.32, samples=119
   iops        : min=61570, max=66244, avg=62687.51, stdev=586.10, samples=119
  lat (nsec)   : 100=0.76%, 250=99.03%, 500=0.16%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.02%, 20=0.01%, 50=0.01%
  lat (usec)   : 100=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=11.67%, sys=88.26%, ctx=1141, majf=0, minf=0
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,3761259,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=245MiB/s (257MB/s), 245MiB/s-245MiB/s (257MB/s-257MB/s), io=14.3GiB (15.4GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=48/3753621, merge=0/0, ticks=1/39024, in_queue=244, util=99.99%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067164/Research/IOUring/IOPS/randwrite/randwrite-1_gystbc.jpg" alt="randwrite-1" width="600"/>
<br><br>

## QD=4 
```
rand_write: (groupid=0, jobs=4): err= 0: pid=1413: Mon Mar 27 21:38:02 2023
  write: IOPS=281k, BW=1097MiB/s (1150MB/s)(64.3GiB/60001msec); 0 zone resets
    slat (usec): min=6, max=11392, avg=13.12, stdev= 9.64
    clat (nsec): min=73, max=7418.9k, avg=487.10, stdev=5579.43
     lat (usec): min=8, max=11403, avg=13.78, stdev=11.11
    clat percentiles (nsec):
     |  1.00th=[   93],  5.00th=[   98], 10.00th=[  101], 20.00th=[  105],
     | 30.00th=[  108], 40.00th=[  111], 50.00th=[  114], 60.00th=[  117],
     | 70.00th=[  120], 80.00th=[  155], 90.00th=[  165], 95.00th=[  187],
     | 99.00th=[12992], 99.50th=[14784], 99.90th=[17536], 99.95th=[19328],
     | 99.99th=[25728]
   bw (  MiB/s): min=  713, max= 1197, per=99.98%, avg=1096.70, stdev=24.73, samples=476
   iops        : min=182602, max=306640, avg=280754.92, stdev=6332.06, samples=476
  lat (nsec)   : 100=6.70%, 250=88.60%, 500=0.05%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=1.41%, 10=2.06%, 20=1.13%, 50=0.04%
  lat (usec)   : 100=0.01%, 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=11.44%, sys=87.23%, ctx=542125, majf=0, minf=0
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,16849612,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=1097MiB/s (1150MB/s), 1097MiB/s-1097MiB/s (1150MB/s-1150MB/s), io=64.3GiB (69.0GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=51/16819079, merge=0/0, ticks=4/163018, in_queue=148, util=100.00%
```

### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067162/Research/IOUring/IOPS/randwrite/randwrite-4_uchiii.jpg" alt="randwrite-4" width="600"/>
<br><br>

## QD=16
```
rand_write: (groupid=0, jobs=16): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=1815: Mon Mar 27 22:00:05 2023
  write: IOPS=280k, BW=1095MiB/s (1148MB/s)(64.2GiB/60013msec); 0 zone resets
    slat (usec): min=2, max=40029, avg=17.67, stdev=265.68
    clat (nsec): min=57, max=36726k, avg=38648.24, stdev=467393.67
     lat (usec): min=9, max=40030, avg=56.51, stdev=538.09
    clat percentiles (nsec):
     |  1.00th=[      83],  5.00th=[      90], 10.00th=[      92],
     | 20.00th=[      98], 30.00th=[     102], 40.00th=[     105],
     | 50.00th=[     110], 60.00th=[     113], 70.00th=[     122],
     | 80.00th=[     155], 90.00th=[     169], 95.00th=[    3088],
     | 99.00th=[  733184], 99.50th=[ 2007040], 99.90th=[ 7372800],
     | 99.95th=[10289152], 99.99th=[16580608]
   bw (  MiB/s): min=  820, max= 1447, per=100.00%, avg=1095.73, stdev= 6.64, samples=1907
   iops        : min=210100, max=370568, avg=280507.69, stdev=1699.65, samples=1907
  lat (nsec)   : 100=23.99%, 250=70.41%, 500=0.12%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=1.51%, 10=0.04%, 20=0.01%, 50=0.55%
  lat (usec)   : 100=0.62%, 250=0.90%, 500=0.59%, 750=0.27%, 1000=0.16%
  lat (msec)   : 2=0.32%, 4=0.25%, 10=0.20%, 20=0.05%, 50=0.01%
  cpu          : usr=2.77%, sys=22.17%, ctx=673064, majf=0, minf=11
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,16825775,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=1095MiB/s (1148MB/s), 1095MiB/s-1095MiB/s (1148MB/s-1148MB/s), io=64.2GiB (68.9GB), run=60013-60013msec

Disk stats (read/write):
  nvme0n1: ios=51/16793831, merge=0/0, ticks=2/166640, in_queue=884, util=100.00%
```

### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067162/Research/IOUring/IOPS/randwrite/randwrite-16_dmhsgy.jpg" alt="randwrite-16" width="600"/>
<br><br>

## QD=32
```
rand_write: (groupid=0, jobs=32): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=1748: Mon Mar 27 21:55:11 2023
  write: IOPS=292k, BW=1140MiB/s (1196MB/s)(66.9GiB/60028msec); 0 zone resets
    slat (usec): min=2, max=123666, avg=24.69, stdev=572.49
    clat (nsec): min=60, max=75066k, avg=83918.55, stdev=896098.22
     lat (usec): min=8, max=123677, avg=108.81, stdev=1063.76
    clat percentiles (nsec):
     |  1.00th=[      82],  5.00th=[      84], 10.00th=[      89],
     | 20.00th=[      90], 30.00th=[      93], 40.00th=[      96],
     | 50.00th=[      98], 60.00th=[     101], 70.00th=[     104],
     | 80.00th=[     109], 90.00th=[     118], 95.00th=[    3312],
     | 99.00th=[ 1843200], 99.50th=[ 4620288], 99.90th=[14614528],
     | 99.95th=[19005440], 99.99th=[28180480]
   bw (  MiB/s): min=  916, max= 1522, per=100.00%, avg=1140.72, stdev= 2.83, samples=3820
   iops        : min=234506, max=389705, avg=292023.71, stdev=725.06, samples=3820
  lat (nsec)   : 100=54.81%, 250=39.06%, 500=0.06%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=1.57%, 10=0.01%, 20=0.01%, 50=0.20%
  lat (usec)   : 100=0.45%, 250=0.96%, 500=0.74%, 750=0.41%, 1000=0.26%
  lat (msec)   : 2=0.52%, 4=0.38%, 10=0.36%, 20=0.16%, 50=0.04%
  lat (msec)   : 100=0.01%
  cpu          : usr=1.34%, sys=11.11%, ctx=804814, majf=0, minf=15
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,17524654,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=1140MiB/s (1196MB/s), 1140MiB/s-1140MiB/s (1196MB/s-1196MB/s), io=66.9GiB (71.8GB), run=60028-60028msec

Disk stats (read/write):
  nvme0n1: ios=99/17479858, merge=0/0, ticks=4/174925, in_queue=772, util=100.00%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067163/Research/IOUring/IOPS/randwrite/randwrite-32_bakzsq.jpg" alt="randwrite-32" width="600"/>
<br><br>

## QD=64
```
rand_write: (groupid=0, jobs=64): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=1350: Mon Mar 27 22:16:41 2023
  write: IOPS=274k, BW=1072MiB/s (1124MB/s)(63.3GiB/60492msec); 0 zone resets
    slat (usec): min=2, max=196317, avg=86.15, stdev=2191.95
    clat (nsec): min=60, max=193155k, avg=141572.38, stdev=2056324.63
     lat (usec): min=9, max=196318, avg=228.61, stdev=3010.72
    clat percentiles (nsec):
     |  1.00th=[      75],  5.00th=[      80], 10.00th=[      82],
     | 20.00th=[      84], 30.00th=[      86], 40.00th=[      89],
     | 50.00th=[      90], 60.00th=[      91], 70.00th=[      94],
     | 80.00th=[     143], 90.00th=[     149], 95.00th=[     155],
     | 99.00th=[ 1318912], 99.50th=[ 6848512], 99.90th=[35389440],
     | 99.95th=[46399488], 99.99th=[67633152]
   bw (  MiB/s): min=  831, max= 1333, per=100.00%, avg=1080.96, stdev= 1.45, samples=7653
   iops        : min=212812, max=341346, avg=276723.86, stdev=372.05, samples=7653
  lat (nsec)   : 100=73.19%, 250=23.30%, 500=0.05%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.81%, 10=0.01%, 20=0.01%, 50=0.05%
  lat (usec)   : 100=0.15%, 250=0.59%, 500=0.35%, 750=0.21%, 1000=0.15%
  lat (msec)   : 2=0.31%, 4=0.21%, 10=0.21%, 20=0.17%, 50=0.20%
  lat (msec)   : 100=0.04%, 250=0.01%
  cpu          : usr=0.68%, sys=5.53%, ctx=470701, majf=0, minf=0
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,16604488,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=1072MiB/s (1124MB/s), 1072MiB/s-1072MiB/s (1124MB/s-1124MB/s), io=63.3GiB (68.0GB), run=60492-60492msec

Disk stats (read/write):
  nvme0n1: ios=102/16604430, merge=0/0, ticks=4/177299, in_queue=80, util=99.47%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067163/Research/IOUring/IOPS/randwrite/randwrite-64_dxuxbt.jpg" alt="randwrite-64" width="600"/>
<br><br>

## QD=128
```
rand_write: (groupid=0, jobs=128): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=1208: Mon Mar 27 22:20:42 2023
  write: IOPS=273k, BW=1068MiB/s (1120MB/s)(64.0GiB/61414msec); 0 zone resets
    slat (usec): min=2, max=292016, avg=63.06, stdev=2405.16
    clat (nsec): min=62, max=244329k, avg=392074.29, stdev=4077083.34
     lat (usec): min=8, max=292017, avg=455.51, stdev=4733.44
    clat percentiles (nsec):
     |  1.00th=[       80],  5.00th=[       84], 10.00th=[       86],
     | 20.00th=[       89], 30.00th=[       91], 40.00th=[       93],
     | 50.00th=[       95], 60.00th=[       96], 70.00th=[       99],
     | 80.00th=[      102], 90.00th=[      111], 95.00th=[   268288],
     | 99.00th=[  8847360], 99.50th=[ 23461888], 99.90th=[ 66322432],
     | 99.95th=[ 84410368], 99.99th=[121110528]
   bw (  MiB/s): min=  788, max= 1493, per=100.00%, avg=1093.01, stdev= 0.88, samples=15337
   iops        : min=201910, max=382253, avg=279807.37, stdev=224.47, samples=15337
  lat (nsec)   : 100=73.02%, 250=19.23%, 500=0.03%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=1.44%, 10=0.01%, 20=0.01%, 50=0.02%
  lat (usec)   : 100=0.07%, 250=1.00%, 500=1.57%, 750=0.45%, 1000=0.29%
  lat (msec)   : 2=0.70%, 4=0.63%, 10=0.60%, 20=0.35%, 50=0.39%
  lat (msec)   : 100=0.16%, 250=0.03%
  cpu          : usr=0.35%, sys=2.73%, ctx=1066559, majf=0, minf=30
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,16789337,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=1068MiB/s (1120MB/s), 1068MiB/s-1068MiB/s (1120MB/s-1120MB/s), io=64.0GiB (68.8GB), run=61414-61414msec

Disk stats (read/write):
  nvme0n1: ios=341/16789240, merge=0/0, ticks=12/255661, in_queue=904, util=97.88%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067163/Research/IOUring/IOPS/randwrite/randwrite-128_oxvbeu.jpg" alt="randwrite-128" width="600"/>
<br><br>


## QD=256
```
rand_write: (groupid=0, jobs=256): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=1375: Mon Mar 27 22:22:57 2023
  write: IOPS=253k, BW=987MiB/s (1035MB/s)(62.3GiB/64565msec); 0 zone resets
    slat (usec): min=2, max=693841, avg=243.77, stdev=7653.60
    clat (nsec): min=60, max=701993k, avg=686158.35, stdev=8364258.44
     lat (usec): min=9, max=706583, avg=932.16, stdev=11351.21
    clat percentiles (nsec):
     |  1.00th=[       83],  5.00th=[       91], 10.00th=[       94],
     | 20.00th=[       99], 30.00th=[      103], 40.00th=[      107],
     | 50.00th=[      110], 60.00th=[      116], 70.00th=[      135],
     | 80.00th=[      157], 90.00th=[      169], 95.00th=[   602112],
     | 99.00th=[ 11075584], 99.50th=[ 31064064], 99.90th=[143654912],
     | 99.95th=[191889408], 99.99th=[278921216]
   bw (  MiB/s): min=  427, max= 1731, per=100.00%, avg=1062.67, stdev= 0.87, samples=30675
   iops        : min=109528, max=443226, avg=272036.58, stdev=222.03, samples=30675
  lat (nsec)   : 100=20.08%, 250=72.05%, 500=0.11%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=1.09%, 10=0.03%, 20=0.01%, 50=0.01%
  lat (usec)   : 100=0.02%, 250=0.13%, 500=0.94%, 750=1.35%, 1000=0.64%
  lat (msec)   : 2=0.82%, 4=0.81%, 10=0.84%, 20=0.40%, 50=0.32%
  lat (msec)   : 100=0.18%, 250=0.16%, 500=0.02%, 750=0.01%
  cpu          : usr=0.18%, sys=1.32%, ctx=1107977, majf=0, minf=32
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,16320392,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=987MiB/s (1035MB/s), 987MiB/s-987MiB/s (1035MB/s-1035MB/s), io=62.3GiB (66.8GB), run=64565-64565msec

Disk stats (read/write):
  nvme0n1: ios=546/16320148, merge=0/0, ticks=20/390594, in_queue=4656, util=93.37%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067163/Research/IOUring/IOPS/randwrite/randwrite-256_pdoxci.jpg" alt="randwrite-256" width="600"/>
<br><br>