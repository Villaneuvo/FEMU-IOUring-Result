# Write Plotting Result

For Write Operation I've been running using configuration below here :
```
[global]
ioengine=io_uring
rw=write
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
write: (groupid=0, jobs=1): err= 0: pid=2567: Mon Mar 27 22:40:54 2023
  write: IOPS=60.8k, BW=238MiB/s (249MB/s)(13.9GiB/60001msec); 0 zone resets
    slat (usec): min=10, max=9060, avg=15.54, stdev=17.92
    clat (nsec): min=80, max=7477.2k, avg=169.35, stdev=8023.76
     lat (usec): min=11, max=9063, avg=15.93, stdev=19.66
    clat percentiles (nsec):
     |  1.00th=[  139],  5.00th=[  143], 10.00th=[  145], 20.00th=[  147],
     | 30.00th=[  149], 40.00th=[  151], 50.00th=[  153], 60.00th=[  153],
     | 70.00th=[  153], 80.00th=[  155], 90.00th=[  155], 95.00th=[  157],
     | 99.00th=[  163], 99.50th=[  171], 99.90th=[  274], 99.95th=[  596],
     | 99.99th=[19328]
   bw (  KiB/s): min=236928, max=247120, per=99.99%, avg=243250.43, stdev=1891.79, samples=119
   iops        : min=59232, max=61780, avg=60812.61, stdev=472.95, samples=119
  lat (nsec)   : 100=0.22%, 250=99.51%, 500=0.21%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.02%, 20=0.02%, 50=0.01%
  lat (usec)   : 100=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=11.33%, sys=88.57%, ctx=1263, majf=0, minf=0
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,3649283,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=238MiB/s (249MB/s), 238MiB/s-238MiB/s (249MB/s-249MB/s), io=13.9GiB (14.9GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=51/3643034, merge=0/0, ticks=2/39516, in_queue=164, util=100.00%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067270/Research/IOUring/IOPS/write/write-1_qq8dvi.jpg" alt="Write-1" width="600"/>
<br><br>

## QD=4 
```
write: (groupid=0, jobs=4): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=2581: Mon Mar 27 22:42:42 2023
  write: IOPS=227k, BW=886MiB/s (929MB/s)(51.9GiB/60005msec); 0 zone resets
    slat (usec): min=3, max=9911, avg=16.28, stdev=11.76
    clat (nsec): min=66, max=9863.7k, avg=734.06, stdev=11209.78
     lat (usec): min=9, max=9914, avg=17.15, stdev=16.26
    clat percentiles (nsec):
     |  1.00th=[   83],  5.00th=[   88], 10.00th=[   92], 20.00th=[   96],
     | 30.00th=[  100], 40.00th=[  103], 50.00th=[  107], 60.00th=[  112],
     | 70.00th=[  126], 80.00th=[  167], 90.00th=[  179], 95.00th=[ 3376],
     | 99.00th=[16320], 99.50th=[18304], 99.90th=[24704], 99.95th=[29056],
     | 99.99th=[50432]
   bw (  KiB/s): min=551976, max=1002032, per=99.96%, avg=907014.32, stdev=25630.55, samples=478
   iops        : min=137994, max=250508, avg=226753.53, stdev=6407.65, samples=478
  lat (nsec)   : 100=29.93%, 250=64.42%, 500=0.08%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=1.08%, 10=1.90%, 20=2.26%, 50=0.32%
  lat (usec)   : 100=0.01%, 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=9.92%, sys=88.04%, ctx=609431, majf=0, minf=2
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,13611364,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=886MiB/s (929MB/s), 886MiB/s-886MiB/s (929MB/s-929MB/s), io=51.9GiB (55.8GB), run=60005-60005msec

Disk stats (read/write):
  nvme0n1: ios=100/13581639, merge=0/0, ticks=3/158388, in_queue=276, util=100.00%
```

### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067270/Research/IOUring/IOPS/write/write-4_sl50we.jpg" alt="Write-4" width="600"/>
<br><br>

## QD=16
```
write: (groupid=0, jobs=16): err= 0: pid=2604: Mon Mar 27 22:44:17 2023
  write: IOPS=277k, BW=1082MiB/s (1135MB/s)(63.4GiB/60004msec); 0 zone resets
    slat (usec): min=2, max=55811, avg=21.04, stdev=349.28
    clat (nsec): min=62, max=32603k, avg=35865.90, stdev=513174.37
     lat (usec): min=8, max=55812, avg=57.07, stdev=620.96
    clat percentiles (nsec):
     |  1.00th=[      91],  5.00th=[      96], 10.00th=[     100],
     | 20.00th=[     104], 30.00th=[     107], 40.00th=[     111],
     | 50.00th=[     113], 60.00th=[     116], 70.00th=[     121],
     | 80.00th=[     127], 90.00th=[     135], 95.00th=[     193],
     | 99.00th=[  325632], 99.50th=[ 2007040], 99.90th=[ 8585216],
     | 99.95th=[11730944], 99.99th=[17694720]
   bw (  MiB/s): min=  726, max= 1363, per=100.00%, avg=1082.29, stdev= 5.08, samples=1913
   iops        : min=186024, max=349168, avg=277065.53, stdev=1300.83, samples=1913
  lat (nsec)   : 100=9.44%, 250=86.84%, 500=0.07%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=1.17%, 10=0.08%, 20=0.02%, 50=0.50%
  lat (usec)   : 100=0.44%, 250=0.37%, 500=0.18%, 750=0.11%, 1000=0.08%
  lat (msec)   : 2=0.20%, 4=0.21%, 10=0.21%, 20=0.07%, 50=0.01%
  cpu          : usr=2.82%, sys=22.06%, ctx=434911, majf=0, minf=0
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,16625495,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=1082MiB/s (1135MB/s), 1082MiB/s-1082MiB/s (1135MB/s-1135MB/s), io=63.4GiB (68.1GB), run=60004-60004msec

Disk stats (read/write):
  nvme0n1: ios=96/16586765, merge=0/0, ticks=4/171178, in_queue=444, util=100.00%
```

### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067270/Research/IOUring/IOPS/write/write-16_dqi7ra.jpg" alt="Write-16" width="600"/>
<br><br>

## QD=32
```
write: (groupid=0, jobs=32): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=2656: Mon Mar 27 22:46:52 2023
  write: IOPS=272k, BW=1062MiB/s (1114MB/s)(62.3GiB/60033msec); 0 zone resets
    slat (usec): min=2, max=83431, avg=34.59, stdev=770.82
    clat (nsec): min=57, max=76738k, avg=81562.49, stdev=907565.36
     lat (usec): min=8, max=83444, avg=116.40, stdev=1191.31
    clat percentiles (nsec):
     |  1.00th=[      73],  5.00th=[      80], 10.00th=[      83],
     | 20.00th=[      87], 30.00th=[      90], 40.00th=[      94],
     | 50.00th=[      96], 60.00th=[      99], 70.00th=[     103],
     | 80.00th=[     109], 90.00th=[     123], 95.00th=[    2960],
     | 99.00th=[ 1925120], 99.50th=[ 5144576], 99.90th=[14483456],
     | 99.95th=[18481152], 99.99th=[28180480]
   bw (  MiB/s): min=  856, max= 1298, per=100.00%, avg=1063.16, stdev= 2.39, samples=3818
   iops        : min=219178, max=332291, avg=272167.50, stdev=612.03, samples=3818
  lat (nsec)   : 100=60.73%, 250=34.04%, 500=0.06%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=1.08%, 10=0.03%, 20=0.02%, 50=0.46%
  lat (usec)   : 100=0.57%, 250=0.88%, 500=0.42%, 750=0.20%, 1000=0.15%
  lat (msec)   : 2=0.37%, 4=0.36%, 10=0.41%, 20=0.17%, 50=0.04%
  lat (msec)   : 100=0.01%
  cpu          : usr=1.42%, sys=11.00%, ctx=695625, majf=0, minf=23
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,16321805,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=1062MiB/s (1114MB/s), 1062MiB/s-1062MiB/s (1114MB/s-1114MB/s), io=62.3GiB (66.9GB), run=60033-60033msec

Disk stats (read/write):
  nvme0n1: ios=51/16290031, merge=0/0, ticks=2/184549, in_queue=1832, util=100.00%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067270/Research/IOUring/IOPS/write/write-32_wthsqu.jpg" alt="Write-32" width="600"/>
<br><br>

## QD=64
```
write: (groupid=0, jobs=64): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=2706: Mon Mar 27 22:49:09 2023
  write: IOPS=284k, BW=1109MiB/s (1163MB/s)(65.5GiB/60491msec); 0 zone resets
    slat (usec): min=2, max=248020, avg=95.94, stdev=2231.75
    clat (nsec): min=61, max=153202k, avg=124117.52, stdev=2004031.78
     lat (usec): min=9, max=248042, avg=220.70, stdev=3002.68
    clat percentiles (nsec):
     |  1.00th=[      79],  5.00th=[      82], 10.00th=[      85],
     | 20.00th=[      87], 30.00th=[      89], 40.00th=[      91],
     | 50.00th=[      93], 60.00th=[      95], 70.00th=[      97],
     | 80.00th=[      99], 90.00th=[     103], 95.00th=[     110],
     | 99.00th=[  242688], 99.50th=[ 5406720], 99.90th=[35913728],
     | 99.95th=[46923776], 99.99th=[66322432]
   bw (  MiB/s): min=  868, max= 1344, per=100.00%, avg=1118.47, stdev= 1.28, samples=7651
   iops        : min=222367, max=344195, avg=286326.18, stdev=326.57, samples=7651
  lat (nsec)   : 100=81.25%, 250=16.42%, 500=0.09%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.67%, 10=0.02%, 20=0.01%, 50=0.09%
  lat (usec)   : 100=0.12%, 250=0.34%, 500=0.16%, 750=0.06%, 1000=0.03%
  lat (msec)   : 2=0.09%, 4=0.10%, 10=0.16%, 20=0.16%, 50=0.18%
  lat (msec)   : 100=0.04%, 250=0.01%
  cpu          : usr=0.65%, sys=5.56%, ctx=305413, majf=0, minf=0
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,17175800,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=1109MiB/s (1163MB/s), 1109MiB/s-1109MiB/s (1163MB/s-1163MB/s), io=65.5GiB (70.4GB), run=60491-60491msec

Disk stats (read/write):
  nvme0n1: ios=102/17175743, merge=0/0, ticks=6/185458, in_queue=1804, util=99.52%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067270/Research/IOUring/IOPS/write/write-64_r6dosf.jpg" alt="Write-64" width="600"/>
<br><br>

## QD=128
```
write: (groupid=0, jobs=128): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=2792: Mon Mar 27 22:50:49 2023
  write: IOPS=267k, BW=1041MiB/s (1092MB/s)(62.9GiB/61875msec); 0 zone resets
    slat (usec): min=2, max=400059, avg=69.73, stdev=2490.20
    clat (nsec): min=62, max=380748k, avg=392900.90, stdev=4703799.95
     lat (usec): min=8, max=400064, avg=463.12, stdev=5324.24
    clat percentiles (nsec):
     |  1.00th=[       81],  5.00th=[       82], 10.00th=[       83],
     | 20.00th=[       86], 30.00th=[       87], 40.00th=[       87],
     | 50.00th=[       88], 60.00th=[       88], 70.00th=[       88],
     | 80.00th=[       90], 90.00th=[       96], 95.00th=[      116],
     | 99.00th=[  7766016], 99.50th=[ 28442624], 99.90th=[ 78118912],
     | 99.95th=[ 95944704], 99.99th=[132644864]
   bw (  MiB/s): min=  686, max= 1385, per=100.00%, avg=1073.43, stdev= 0.88, samples=15312
   iops        : min=175634, max=354606, avg=274794.26, stdev=224.08, samples=15312
  lat (nsec)   : 100=91.90%, 250=4.87%, 500=0.03%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=1.16%, 10=0.01%, 20=0.01%, 50=0.02%
  lat (usec)   : 100=0.06%, 250=0.15%, 500=0.15%, 750=0.11%, 1000=0.06%
  lat (msec)   : 2=0.14%, 4=0.16%, 10=0.25%, 20=0.26%, 50=0.41%
  lat (msec)   : 100=0.20%, 250=0.04%, 500=0.01%
  cpu          : usr=0.33%, sys=2.75%, ctx=355996, majf=0, minf=29
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,16493006,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=1041MiB/s (1092MB/s), 1041MiB/s-1041MiB/s (1092MB/s-1092MB/s), io=62.9GiB (67.6GB), run=61875-61875msec

Disk stats (read/write):
  nvme0n1: ios=249/16492888, merge=0/0, ticks=11/190936, in_queue=648, util=97.15%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067271/Research/IOUring/IOPS/write/write-128_lvu53d.jpg" alt="Write-128" width="600"/>
<br><br>


## QD=256
```
write: (groupid=0, jobs=256): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=2961: Mon Mar 27 22:53:33 2023
  write: IOPS=256k, BW=999MiB/s (1047MB/s)(63.0GiB/64627msec); 0 zone resets
    slat (usec): min=2, max=781936, avg=92.55, stdev=4188.62
    clat (nsec): min=62, max=676778k, avg=832354.20, stdev=8665263.93
     lat (usec): min=8, max=781947, avg=925.30, stdev=9628.54
    clat percentiles (nsec):
     |  1.00th=[       80],  5.00th=[       85], 10.00th=[       86],
     | 20.00th=[       88], 30.00th=[       90], 40.00th=[       92],
     | 50.00th=[       94], 60.00th=[       95], 70.00th=[       97],
     | 80.00th=[       99], 90.00th=[      104], 95.00th=[      112],
     | 99.00th=[ 26607616], 99.50th=[ 52166656], 99.90th=[137363456],
     | 99.95th=[173015040], 99.99th=[250609664]
   bw (  MiB/s): min=  481, max= 1614, per=100.00%, avg=1071.20, stdev= 0.70, samples=30652
   iops        : min=123229, max=413189, avg=274175.45, stdev=179.12, samples=30652
  lat (nsec)   : 100=81.48%, 250=15.54%, 500=0.04%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.87%, 10=0.01%, 20=0.01%, 50=0.01%
  lat (usec)   : 100=0.01%, 250=0.01%, 500=0.02%, 750=0.02%, 1000=0.01%
  lat (msec)   : 2=0.05%, 4=0.10%, 10=0.21%, 20=0.35%, 50=0.73%
  lat (msec)   : 100=0.33%, 250=0.18%, 500=0.01%, 750=0.01%
  cpu          : usr=0.16%, sys=1.35%, ctx=354866, majf=0, minf=32
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,16524392,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=999MiB/s (1047MB/s), 999MiB/s-999MiB/s (1047MB/s-1047MB/s), io=63.0GiB (67.7GB), run=64627-64627msec

Disk stats (read/write):
  nvme0n1: ios=597/16524148, merge=0/0, ticks=20/178566, in_queue=1572, util=93.31%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067270/Research/IOUring/IOPS/write/write-256_m0z0of.jpg" alt="Write-256" width="600"/>
<br><br>