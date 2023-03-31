# Write Plotting Result

For write Operation I've been running using configuration below here :
```
[global]
ioengine=io_uring
rw=write
runtime=60
direct=1 
bs=n(128k,256,512,1M)
numjobs=n(starting from 1,4,16,32)
thwrites=n(starting from 1,4,16,32)
time_based=1
thwrite
group_reporting
size=1G

[nvme]
filename=/dev/nvme0n1 
```
# Result 

# BlockSize=128k
## QD=1 
```
seq_write: (groupid=0, jobs=1): err= 0: pid=3928: Mon Mar 27 23:11:08 2023
  write: IOPS=16.2k, BW=2026MiB/s (2125MB/s)(119GiB/60001msec); 0 zone resets
    slat (usec): min=14, max=9547, avg=25.97, stdev=33.23
    clat (nsec): min=113, max=7753.5k, avg=35050.88, stdev=32195.47
     lat (usec): min=34, max=9585, avg=61.16, stdev=47.99
    clat percentiles (usec):
     |  1.00th=[   25],  5.00th=[   27], 10.00th=[   28], 20.00th=[   29],
     | 30.00th=[   30], 40.00th=[   31], 50.00th=[   31], 60.00th=[   32],
     | 70.00th=[   32], 80.00th=[   33], 90.00th=[   38], 95.00th=[   73],
     | 99.00th=[   88], 99.50th=[  233], 99.90th=[  285], 99.95th=[  306],
     | 99.99th=[  363]
   bw (  MiB/s): min=  361, max= 2631, per=99.91%, avg=2024.44, stdev=391.75, samples=119
   iops        : min= 2888, max=21054, avg=16195.49, stdev=3134.00, samples=119
  lat (nsec)   : 250=0.05%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.10%, 50=93.00%
  lat (usec)   : 100=6.07%, 250=0.42%, 500=0.32%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=24.11%, sys=28.63%, ctx=972745, majf=0, minf=0
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,972585,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=2026MiB/s (2125MB/s), 2026MiB/s-2026MiB/s (2125MB/s-2125MB/s), io=119GiB (127GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=51/970738, merge=0/0, ticks=3/41100, in_queue=136, util=100.00%
```

### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070494/Research/IOUring/BW/write/128/Artboard_7_copy_al9iwu.png" alt="write-bs128-1" width="600"/>
<br><br>

## QD=4
```
seq_write: (groupid=0, jobs=4): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=3962: Mon Mar 27 23:12:48 2023
  write: IOPS=28.9k, BW=3611MiB/s (3786MB/s)(212GiB/60001msec); 0 zone resets
    slat (usec): min=7, max=23683, avg=24.15, stdev=49.58
    clat (nsec): min=128, max=23717k, avg=113440.52, stdev=100185.73
     lat (usec): min=30, max=23783, avg=137.79, stdev=115.81
    clat percentiles (usec):
     |  1.00th=[   31],  5.00th=[   53], 10.00th=[   60], 20.00th=[   68],
     | 30.00th=[   77], 40.00th=[   89], 50.00th=[  100], 60.00th=[  110],
     | 70.00th=[  128], 80.00th=[  151], 90.00th=[  176], 95.00th=[  210],
     | 99.00th=[  334], 99.50th=[  457], 99.90th=[  938], 99.95th=[ 1303],
     | 99.99th=[ 2999]
   bw (  MiB/s): min=  499, max= 5627, per=100.00%, avg=3610.65, stdev=244.20, samples=477
   iops        : min= 3994, max=45020, avg=28884.99, stdev=1953.58, samples=477
  lat (nsec)   : 250=0.01%, 500=0.01%, 750=0.02%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.02%, 50=4.32%
  lat (usec)   : 100=45.73%, 250=46.92%, 500=2.58%, 750=0.24%, 1000=0.05%
  lat (msec)   : 2=0.08%, 4=0.01%, 10=0.01%, 20=0.01%, 50=0.01%
  cpu          : usr=10.31%, sys=13.13%, ctx=1733212, majf=0, minf=1
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,1733135,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=3611MiB/s (3786MB/s), 3611MiB/s-3611MiB/s (3786MB/s-3786MB/s), io=212GiB (227GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=51/1730489, merge=0/0, ticks=3/202826, in_queue=776, util=100.00%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070494/Research/IOUring/BW/write/128/Artboard_3_wpvzva.png" alt="write-bs128-4" width="600"/>
<br><br>

## QD=16
```
seq_write: (groupid=0, jobs=16): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=3982: Mon Mar 27 23:15:11 2023
  write: IOPS=31.1k, BW=3892MiB/s (4081MB/s)(228GiB/60030msec); 0 zone resets
    slat (usec): min=8, max=28500, avg=37.93, stdev=44.77
    clat (nsec): min=162, max=21678k, avg=473558.87, stdev=217694.11
     lat (usec): min=36, max=21733, avg=511.85, stdev=219.83
    clat percentiles (usec):
     |  1.00th=[   93],  5.00th=[  163], 10.00th=[  215], 20.00th=[  293],
     | 30.00th=[  363], 40.00th=[  429], 50.00th=[  486], 60.00th=[  529],
     | 70.00th=[  578], 80.00th=[  627], 90.00th=[  709], 95.00th=[  775],
     | 99.00th=[  898], 99.50th=[  955], 99.90th=[ 1221], 99.95th=[ 2180],
     | 99.99th=[ 5669]
   bw (  MiB/s): min= 3268, max= 4815, per=100.00%, avg=3893.28, stdev=18.07, samples=1908
   iops        : min=26148, max=38522, avg=31145.75, stdev=144.55, samples=1908
  lat (nsec)   : 250=0.01%, 500=0.09%, 750=0.06%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.07%, 50=0.04%
  lat (usec)   : 100=1.01%, 250=12.96%, 500=38.98%, 750=40.46%, 1000=6.03%
  lat (msec)   : 2=0.24%, 4=0.03%, 10=0.02%, 20=0.01%, 50=0.01%
  cpu          : usr=3.48%, sys=6.87%, ctx=1867781, majf=0, minf=9
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,1869059,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=3892MiB/s (4081MB/s), 3892MiB/s-3892MiB/s (4081MB/s-4081MB/s), io=228GiB (245GB), run=60030-60030msec

Disk stats (read/write):
  nvme0n1: ios=51/1865446, merge=0/0, ticks=2/742717, in_queue=1308, util=100.00%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070494/Research/IOUring/BW/write/128/Artboard_2_nvie8l.png" alt="write-bs128-16" width="600"/>
<br><br>

## QD=32
```
seq_write: (groupid=0, jobs=32): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=4015: Mon Mar 27 23:16:50 2023
  write: IOPS=31.5k, BW=3939MiB/s (4130MB/s)(231GiB/60054msec); 0 zone resets
    slat (usec): min=7, max=64406, avg=40.12, stdev=83.60
    clat (nsec): min=180, max=23872k, avg=972025.00, stdev=441945.78
     lat (usec): min=37, max=23908, avg=1012.51, stdev=442.12
    clat percentiles (usec):
     |  1.00th=[  137],  5.00th=[  306], 10.00th=[  420], 20.00th=[  627],
     | 30.00th=[  783], 40.00th=[  914], 50.00th=[ 1012], 60.00th=[ 1090],
     | 70.00th=[ 1172], 80.00th=[ 1270], 90.00th=[ 1434], 95.00th=[ 1565],
     | 99.00th=[ 1811], 99.50th=[ 1909], 99.90th=[ 2474], 99.95th=[ 4146],
     | 99.99th=[14091]
   bw (  MiB/s): min= 3335, max= 4883, per=100.00%, avg=3941.77, stdev= 6.88, samples=3811
   iops        : min=26686, max=39068, avg=31533.24, stdev=55.00, samples=3811
  lat (nsec)   : 250=0.01%, 500=0.05%, 750=0.12%, 1000=0.17%
  lat (usec)   : 2=0.19%, 4=0.01%, 10=0.01%, 20=0.09%, 50=0.01%
  lat (usec)   : 100=0.11%, 250=2.34%, 500=10.67%, 750=13.81%, 1000=21.36%
  lat (msec)   : 2=50.81%, 4=0.21%, 10=0.03%, 20=0.02%, 50=0.01%
  cpu          : usr=2.00%, sys=3.46%, ctx=1885939, majf=0, minf=24
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,1892244,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=3939MiB/s (4130MB/s), 3939MiB/s-3939MiB/s (4130MB/s-4130MB/s), io=231GiB (248GB), run=60054-60054msec

Disk stats (read/write):
  nvme0n1: ios=51/1888226, merge=0/0, ticks=2/1448045, in_queue=2424, util=100.00%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070494/Research/IOUring/BW/write/128/Artboard_1_wj3oyz.png" alt="write-bs128-32" width="600"/>
<br><br>

# BlockSize=256k
## QD=1 
```
seq_write: (groupid=0, jobs=1): err= 0: pid=4092: Mon Mar 27 23:19:12 2023
  write: IOPS=9524, BW=2381MiB/s (2497MB/s)(140GiB/60001msec); 0 zone resets
    slat (usec): min=18, max=21283, avg=40.20, stdev=56.18
    clat (nsec): min=126, max=8119.4k, avg=63935.71, stdev=37950.91
     lat (usec): min=58, max=21291, avg=104.31, stdev=67.61
    clat percentiles (usec):
     |  1.00th=[   47],  5.00th=[   51], 10.00th=[   54], 20.00th=[   57],
     | 30.00th=[   58], 40.00th=[   59], 50.00th=[   59], 60.00th=[   60],
     | 70.00th=[   61], 80.00th=[   62], 90.00th=[   64], 95.00th=[  141],
     | 99.00th=[  147], 99.50th=[  151], 99.90th=[  161], 99.95th=[  172],
     | 99.99th=[ 1401]
   bw (  MiB/s): min= 1325, max= 3057, per=99.95%, avg=2380.05, stdev=291.55, samples=119
   iops        : min= 5300, max=12228, avg=9520.18, stdev=1166.20, samples=119
  lat (nsec)   : 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.01%, 50=3.97%
  lat (usec)   : 100=89.52%, 250=6.45%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=25.70%, sys=19.85%, ctx=572282, majf=0, minf=0
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,571484,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=2381MiB/s (2497MB/s), 2381MiB/s-2381MiB/s (2497MB/s-2497MB/s), io=140GiB (150GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=48/570202, merge=0/0, ticks=2/41399, in_queue=164, util=99.97%
```

### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070529/Research/IOUring/BW/write/256/Artboard_4_reahkd.png" alt="write-bs256-1" width="600"/>
<br><br>

## QD=4
```
seq_write: (groupid=0, jobs=4): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=4108: Mon Mar 27 23:21:28 2023
  write: IOPS=13.7k, BW=3421MiB/s (3587MB/s)(200GiB/60003msec); 0 zone resets
    slat (usec): min=11, max=22381, avg=45.29, stdev=62.22
    clat (nsec): min=162, max=12227k, avg=245827.28, stdev=166388.32
     lat (usec): min=64, max=22389, avg=291.34, stdev=189.50
    clat percentiles (usec):
     |  1.00th=[   74],  5.00th=[  100], 10.00th=[  125], 20.00th=[  139],
     | 30.00th=[  151], 40.00th=[  176], 50.00th=[  223], 60.00th=[  273],
     | 70.00th=[  306], 80.00th=[  326], 90.00th=[  375], 95.00th=[  420],
     | 99.00th=[  766], 99.50th=[  963], 99.90th=[ 1778], 99.95th=[ 2180],
     | 99.99th=[ 4555]
   bw (  MiB/s): min=  674, max= 5860, per=99.82%, avg=3414.34, stdev=296.74, samples=476
   iops        : min= 2696, max=23440, avg=13657.18, stdev=1186.99, samples=476
  lat (nsec)   : 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 20=0.01%, 50=0.09%, 100=4.89%
  lat (usec)   : 250=49.21%, 500=42.63%, 750=2.11%, 1000=0.57%
  lat (msec)   : 2=0.41%, 4=0.05%, 10=0.02%, 20=0.01%
  cpu          : usr=9.16%, sys=10.57%, ctx=822036, majf=0, minf=1
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,820968,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=3421MiB/s (3587MB/s), 3421MiB/s-3421MiB/s (3587MB/s-3587MB/s), io=200GiB (215GB), run=60003-60003msec

Disk stats (read/write):
  nvme0n1: ios=51/819124, merge=0/0, ticks=2/206015, in_queue=612, util=100.00%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070529/Research/IOUring/BW/write/256/Artboard_5_wqq4vq.png" alt="write-bs256-4" width="600"/>
<br><br>

## QD=16
```
seq_write: (groupid=0, jobs=16): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=3982: Mon Mar 27 23:15:11 2023
  write: IOPS=31.1k, BW=3892MiB/s (4081MB/s)(228GiB/60030msec); 0 zone resets
    slat (usec): min=8, max=28500, avg=37.93, stdev=44.77
    clat (nsec): min=162, max=21678k, avg=473558.87, stdev=217694.11
     lat (usec): min=36, max=21733, avg=511.85, stdev=219.83
    clat percentiles (usec):
     |  1.00th=[   93],  5.00th=[  163], 10.00th=[  215], 20.00th=[  293],
     | 30.00th=[  363], 40.00th=[  429], 50.00th=[  486], 60.00th=[  529],
     | 70.00th=[  578], 80.00th=[  627], 90.00th=[  709], 95.00th=[  775],
     | 99.00th=[  898], 99.50th=[  955], 99.90th=[ 1221], 99.95th=[ 2180],
     | 99.99th=[ 5669]
   bw (  MiB/s): min= 3268, max= 4815, per=100.00%, avg=3893.28, stdev=18.07, samples=1908
   iops        : min=26148, max=38522, avg=31145.75, stdev=144.55, samples=1908
  lat (nsec)   : 250=0.01%, 500=0.09%, 750=0.06%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.07%, 50=0.04%
  lat (usec)   : 100=1.01%, 250=12.96%, 500=38.98%, 750=40.46%, 1000=6.03%
  lat (msec)   : 2=0.24%, 4=0.03%, 10=0.02%, 20=0.01%, 50=0.01%
  cpu          : usr=3.48%, sys=6.87%, ctx=1867781, majf=0, minf=9
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,1869059,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=3892MiB/s (4081MB/s), 3892MiB/s-3892MiB/s (4081MB/s-4081MB/s), io=228GiB (245GB), run=60030-60030msec

Disk stats (read/write):
  nvme0n1: ios=51/1865446, merge=0/0, ticks=2/742717, in_queue=1308, util=100.00%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070529/Research/IOUring/BW/write/256/Artboard_7_f42d4w.png" alt="write-bs256-16" width="600"/>
<br><br>

## QD=32
```
seq_write: (groupid=0, jobs=32): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=4015: Mon Mar 27 23:16:50 2023
  write: IOPS=31.5k, BW=3939MiB/s (4130MB/s)(231GiB/60054msec); 0 zone resets
    slat (usec): min=7, max=64406, avg=40.12, stdev=83.60
    clat (nsec): min=180, max=23872k, avg=972025.00, stdev=441945.78
     lat (usec): min=37, max=23908, avg=1012.51, stdev=442.12
    clat percentiles (usec):
     |  1.00th=[  137],  5.00th=[  306], 10.00th=[  420], 20.00th=[  627],
     | 30.00th=[  783], 40.00th=[  914], 50.00th=[ 1012], 60.00th=[ 1090],
     | 70.00th=[ 1172], 80.00th=[ 1270], 90.00th=[ 1434], 95.00th=[ 1565],
     | 99.00th=[ 1811], 99.50th=[ 1909], 99.90th=[ 2474], 99.95th=[ 4146],
     | 99.99th=[14091]
   bw (  MiB/s): min= 3335, max= 4883, per=100.00%, avg=3941.77, stdev= 6.88, samples=3811
   iops        : min=26686, max=39068, avg=31533.24, stdev=55.00, samples=3811
  lat (nsec)   : 250=0.01%, 500=0.05%, 750=0.12%, 1000=0.17%
  lat (usec)   : 2=0.19%, 4=0.01%, 10=0.01%, 20=0.09%, 50=0.01%
  lat (usec)   : 100=0.11%, 250=2.34%, 500=10.67%, 750=13.81%, 1000=21.36%
  lat (msec)   : 2=50.81%, 4=0.21%, 10=0.03%, 20=0.02%, 50=0.01%
  cpu          : usr=2.00%, sys=3.46%, ctx=1885939, majf=0, minf=24
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,1892244,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=3939MiB/s (4130MB/s), 3939MiB/s-3939MiB/s (4130MB/s-4130MB/s), io=231GiB (248GB), run=60054-60054msec

Disk stats (read/write):
  nvme0n1: ios=51/1888226, merge=0/0, ticks=2/1448045, in_queue=2424, util=100.00%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070529/Research/IOUring/BW/write/256/Artboard_7_copy_2_xd6ov4.png" alt="write-bs256-32" width="600"/>
<br><br>

# BlockSize=512k
## QD=1 
```
seq_write: (groupid=0, jobs=1): err= 0: pid=4227: Mon Mar 27 23:27:08 2023
  write: IOPS=5111, BW=2556MiB/s (2680MB/s)(150GiB/60001msec); 0 zone resets
    slat (usec): min=27, max=11963, avg=69.39, stdev=68.87
    clat (nsec): min=146, max=6634.4k, avg=125521.67, stdev=48240.07
     lat (usec): min=115, max=11980, avg=195.04, stdev=89.38
    clat percentiles (usec):
     |  1.00th=[   96],  5.00th=[  104], 10.00th=[  110], 20.00th=[  115],
     | 30.00th=[  117], 40.00th=[  118], 50.00th=[  119], 60.00th=[  120],
     | 70.00th=[  121], 80.00th=[  123], 90.00th=[  125], 95.00th=[  133],
     | 99.00th=[  334], 99.50th=[  338], 99.90th=[  351], 99.95th=[  359],
     | 99.99th=[ 1385]
   bw (  MiB/s): min= 1193, max= 3728, per=100.00%, avg=2558.51, stdev=362.48, samples=119
   iops        : min= 2386, max= 7456, avg=5117.03, stdev=724.99, samples=119
  lat (nsec)   : 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 20=0.01%, 50=0.01%, 100=2.81%, 250=93.32%
  lat (usec)   : 500=3.83%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=25.94%, sys=13.68%, ctx=307846, majf=0, minf=0
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,306672,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=2556MiB/s (2680MB/s), 2556MiB/s-2556MiB/s (2680MB/s-2680MB/s), io=150GiB (161GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=48/306186, merge=0/0, ticks=2/41911, in_queue=120, util=99.97%
```

### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070562/Research/IOUring/BW/write/512/Artboard_5_1_tdlx0a.png" alt="write-512-1" width="600"/>
<br><br>

## QD=4
```
seq_write: (groupid=0, jobs=4): err= 0: pid=4242: Mon Mar 27 23:29:48 2023
  write: IOPS=7027, BW=3514MiB/s (3684MB/s)(206GiB/60001msec); 0 zone resets
    slat (usec): min=21, max=19265, avg=123.92, stdev=108.35
    clat (nsec): min=158, max=19785k, avg=442133.84, stdev=194651.08
     lat (usec): min=149, max=19900, avg=566.56, stdev=222.41
    clat percentiles (usec):
     |  1.00th=[  145],  5.00th=[  239], 10.00th=[  273], 20.00th=[  351],
     | 30.00th=[  375], 40.00th=[  392], 50.00th=[  404], 60.00th=[  420],
     | 70.00th=[  441], 80.00th=[  529], 90.00th=[  660], 95.00th=[  816],
     | 99.00th=[  988], 99.50th=[ 1074], 99.90th=[ 1287], 99.95th=[ 1385],
     | 99.99th=[ 3982]
   bw (  MiB/s): min= 2141, max= 4607, per=100.00%, avg=3515.36, stdev=120.52, samples=477
   iops        : min= 4282, max= 9214, avg=7030.50, stdev=241.03, samples=477
  lat (nsec)   : 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 20=0.01%, 50=0.01%, 100=0.01%, 250=6.44%
  lat (usec)   : 500=69.53%, 750=16.82%, 1000=6.28%
  lat (msec)   : 2=0.87%, 4=0.02%, 10=0.01%, 20=0.01%
  cpu          : usr=10.02%, sys=16.68%, ctx=423133, majf=0, minf=0
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,421662,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=3514MiB/s (3684MB/s), 3514MiB/s-3514MiB/s (3684MB/s-3684MB/s), io=206GiB (221GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=99/420679, merge=0/0, ticks=29/195190, in_queue=436, util=99.99%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070562/Research/IOUring/BW/write/512/Artboard_7_1_yi7txu.png" alt="write-512-4" width="600"/>
<br><br>

## QD=16
```
seq_write: (groupid=0, jobs=16): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=4263: Mon Mar 27 23:31:19 2023
  write: IOPS=8118, BW=4059MiB/s (4256MB/s)(238GiB/60032msec); 0 zone resets
    slat (usec): min=20, max=18011, avg=120.51, stdev=61.57
    clat (nsec): min=168, max=45175k, avg=1844754.38, stdev=698165.86
     lat (usec): min=152, max=45301, avg=1965.92, stdev=688.32
    clat percentiles (usec):
     |  1.00th=[  297],  5.00th=[  529], 10.00th=[  930], 20.00th=[ 1254],
     | 30.00th=[ 1450], 40.00th=[ 1663], 50.00th=[ 1909], 60.00th=[ 2114],
     | 70.00th=[ 2311], 80.00th=[ 2474], 90.00th=[ 2671], 95.00th=[ 2835],
     | 99.00th=[ 3130], 99.50th=[ 3261], 99.90th=[ 4015], 99.95th=[ 4555],
     | 99.99th=[ 8586]
   bw (  MiB/s): min= 3339, max= 4541, per=100.00%, avg=4061.06, stdev=12.22, samples=1909
   iops        : min= 6679, max= 9082, avg=8121.02, stdev=24.41, samples=1909
  lat (nsec)   : 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 50=0.01%, 100=0.01%, 250=0.66%, 500=3.65%
  lat (usec)   : 750=3.27%, 1000=3.81%
  lat (msec)   : 2=43.38%, 4=45.12%, 10=0.10%, 20=0.01%, 50=0.01%
  cpu          : usr=3.48%, sys=4.30%, ctx=490024, majf=0, minf=12
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,487384,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=4059MiB/s (4256MB/s), 4059MiB/s-4059MiB/s (4256MB/s-4256MB/s), io=238GiB (256GB), run=60032-60032msec

Disk stats (read/write):
  nvme0n1: ios=51/515222, merge=0/0, ticks=1/853788, in_queue=1564, util=99.97%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070562/Research/IOUring/BW/write/512/Artboard_7_copy_3_ioky18.png" alt="write-512-16" width="600"/>
<br><br>

## QD=32
```
seq_write: (groupid=0, jobs=32): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=4298: Mon Mar 27 23:34:00 2023
  write: IOPS=31.7k, BW=3960MiB/s (4153MB/s)(232GiB/60015msec); 0 zone resets
    slat (usec): min=8, max=36708, avg=40.00, stdev=62.15
    clat (nsec): min=168, max=24246k, avg=967218.32, stdev=427480.41
     lat (usec): min=42, max=24293, avg=1007.59, stdev=426.02
    clat percentiles (usec):
     |  1.00th=[  141],  5.00th=[  306], 10.00th=[  416], 20.00th=[  619],
     | 30.00th=[  775], 40.00th=[  906], 50.00th=[ 1004], 60.00th=[ 1090],
     | 70.00th=[ 1172], 80.00th=[ 1270], 90.00th=[ 1418], 95.00th=[ 1549],
     | 99.00th=[ 1795], 99.50th=[ 1909], 99.90th=[ 2606], 99.95th=[ 3720],
     | 99.99th=[11863]
   bw (  MiB/s): min= 3403, max= 4842, per=99.99%, avg=3959.88, stdev= 6.60, samples=3819
   iops        : min=27230, max=38740, avg=31677.86, stdev=52.81, samples=3819
  lat (nsec)   : 250=0.01%, 500=0.04%, 750=0.26%, 1000=0.13%
  lat (usec)   : 2=0.09%, 4=0.01%, 10=0.01%, 20=0.09%, 50=0.01%
  lat (usec)   : 100=0.10%, 250=2.32%, 500=11.00%, 750=14.14%, 1000=21.22%
  lat (msec)   : 2=50.33%, 4=0.24%, 10=0.03%, 20=0.01%, 50=0.01%
  cpu          : usr=2.01%, sys=3.46%, ctx=1894722, majf=0, minf=12
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,1901397,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=3960MiB/s (4153MB/s), 3960MiB/s-3960MiB/s (4153MB/s-4153MB/s), io=232GiB (249GB), run=60015-60015msec

Disk stats (read/write):
  nvme0n1: ios=51/1897121, merge=0/0, ticks=2/1448884, in_queue=1940, util=100.00%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070562/Research/IOUring/BW/write/512/Artboard_4_1_fmuezz.png" alt="write-512-32" width="600"/>
<br><br>

# BlockSize=1M
## QD=1 
```
seq_write: (groupid=0, jobs=1): err= 0: pid=4407: Mon Mar 27 23:38:28 2023
  write: IOPS=2658, BW=2659MiB/s (2788MB/s)(156GiB/60001msec); 0 zone resets
    slat (usec): min=50, max=11765, avg=131.07, stdev=93.88
    clat (nsec): min=200, max=3746.5k, avg=243975.90, stdev=68666.66
     lat (usec): min=225, max=12534, avg=375.23, stdev=126.97
    clat percentiles (usec):
     |  1.00th=[  192],  5.00th=[  217], 10.00th=[  223], 20.00th=[  229],
     | 30.00th=[  231], 40.00th=[  233], 50.00th=[  233], 60.00th=[  235],
     | 70.00th=[  237], 80.00th=[  239], 90.00th=[  243], 95.00th=[  247],
     | 99.00th=[  619], 99.50th=[  619], 99.90th=[  635], 99.95th=[  652],
     | 99.99th=[  709]
   bw (  MiB/s): min= 1302, max= 3050, per=99.98%, avg=2658.23, stdev=289.17, samples=120
   iops        : min= 1302, max= 3050, avg=2658.19, stdev=289.16, samples=120
  lat (nsec)   : 250=0.01%, 500=0.01%, 750=0.01%
  lat (usec)   : 20=0.01%, 100=0.01%, 250=95.55%, 500=1.22%, 750=3.21%
  lat (usec)   : 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%
  cpu          : usr=25.46%, sys=12.05%, ctx=159782, majf=0, minf=0
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,159529,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=2659MiB/s (2788MB/s), 2659MiB/s-2659MiB/s (2788MB/s-2788MB/s), io=156GiB (167GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=48/477433, merge=0/0, ticks=2/102357, in_queue=216, util=99.99%
```

### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070562/Research/IOUring/BW/write/512/Artboard_5_1_tdlx0a.png" alt="write-bs1M-1" width="600"/>
<br><br>

## QD=4
```
seq_write: (groupid=0, jobs=4): err= 0: pid=4462: Mon Mar 27 23:42:20 2023
  write: IOPS=3406, BW=3407MiB/s (3572MB/s)(200GiB/60001msec); 0 zone resets
    slat (usec): min=113, max=13034, avg=252.80, stdev=83.20
    clat (nsec): min=922, max=13127k, avg=913953.69, stdev=346937.18
     lat (usec): min=339, max=13353, avg=1168.17, stdev=365.42
    clat percentiles (usec):
     |  1.00th=[  249],  5.00th=[  297], 10.00th=[  457], 20.00th=[  603],
     | 30.00th=[  775], 40.00th=[  840], 50.00th=[  906], 60.00th=[ 1004],
     | 70.00th=[ 1074], 80.00th=[ 1221], 90.00th=[ 1336], 95.00th=[ 1467],
     | 99.00th=[ 1631], 99.50th=[ 1713], 99.90th=[ 2245], 99.95th=[ 2376],
     | 99.99th=[ 4686]
   bw (  MiB/s): min= 2510, max= 4618, per=100.00%, avg=3406.96, stdev=116.23, samples=479
   iops        : min= 2510, max= 4618, avg=3406.79, stdev=116.24, samples=479
  lat (nsec)   : 1000=0.01%
  lat (usec)   : 2=0.01%, 100=0.01%, 250=1.01%, 500=11.24%, 750=14.44%
  lat (usec)   : 1000=33.14%
  lat (msec)   : 2=39.95%, 4=0.20%, 10=0.01%, 20=0.01%
  cpu          : usr=13.30%, sys=13.17%, ctx=205878, majf=0, minf=0
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,204399,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=3407MiB/s (3572MB/s), 3407MiB/s-3407MiB/s (3572MB/s-3572MB/s), io=200GiB (214GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=96/248798, merge=0/0, ticks=3/238475, in_queue=220, util=99.99%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070562/Research/IOUring/BW/write/512/Artboard_7_1_yi7txu.png" alt="write-bs1M-4" width="600"/>
<br><br>

## QD=16
```
seq_write: (groupid=0, jobs=16): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=4486: Mon Mar 27 23:45:21 2023
  write: IOPS=4031, BW=4031MiB/s (4227MB/s)(236GiB/60018msec); 0 zone resets
    slat (usec): min=39, max=24886, avg=190.39, stdev=201.91
    clat (nsec): min=300, max=32813k, avg=3771813.53, stdev=1458744.62
     lat (usec): min=381, max=33009, avg=3962.99, stdev=1448.14
    clat percentiles (usec):
     |  1.00th=[  816],  5.00th=[ 1549], 10.00th=[ 2114], 20.00th=[ 2540],
     | 30.00th=[ 2835], 40.00th=[ 3130], 50.00th=[ 3556], 60.00th=[ 4178],
     | 70.00th=[ 4817], 80.00th=[ 5276], 90.00th=[ 5604], 95.00th=[ 5800],
     | 99.00th=[ 6456], 99.50th=[ 6980], 99.90th=[ 9503], 99.95th=[11600],
     | 99.99th=[23725]
   bw (  MiB/s): min= 3040, max= 4768, per=99.98%, avg=4030.12, stdev=20.30, samples=1915
   iops        : min= 3039, max= 4765, avg=4028.93, stdev=20.31, samples=1915
  lat (nsec)   : 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 10=0.01%, 50=0.01%, 250=0.01%, 500=0.25%
  lat (usec)   : 750=0.58%, 1000=0.83%
  lat (msec)   : 2=6.93%, 4=49.08%, 10=42.22%, 20=0.07%, 50=0.02%
  cpu          : usr=2.94%, sys=2.81%, ctx=243952, majf=0, minf=11
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,241951,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=4031MiB/s (4227MB/s), 4031MiB/s-4031MiB/s (4227MB/s-4227MB/s), io=236GiB (254GB), run=60018-60018msec

Disk stats (read/write):
  nvme0n1: ios=51/285017, merge=0/0, ticks=2/999389, in_queue=442592, util=99.98%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070562/Research/IOUring/BW/write/512/Artboard_7_copy_3_ioky18.png" alt="write-bs1M-16" width="600"/>
<br><br>

## QD=32
```
seq_write: (groupid=0, jobs=32): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=4518: Mon Mar 27 23:47:45 2023
  write: IOPS=3934, BW=3934MiB/s (4125MB/s)(231GiB/60060msec); 0 zone resets
    slat (usec): min=33, max=74588, avg=191.75, stdev=261.68
    clat (nsec): min=293, max=42983k, avg=7924408.20, stdev=2910770.23
     lat (usec): min=416, max=45601, avg=8116.63, stdev=2921.97
    clat percentiles (usec):
     |  1.00th=[ 5080],  5.00th=[ 5604], 10.00th=[ 5800], 20.00th=[ 5997],
     | 30.00th=[ 6128], 40.00th=[ 6259], 50.00th=[ 6390], 60.00th=[ 6587],
     | 70.00th=[ 7046], 80.00th=[12256], 90.00th=[12649], 95.00th=[13042],
     | 99.00th=[13698], 99.50th=[14746], 99.90th=[21103], 99.95th=[23725],
     | 99.99th=[31327]
   bw (  MiB/s): min= 2182, max= 5105, per=100.00%, avg=3937.81, stdev=25.54, samples=3812
   iops        : min= 2176, max= 5104, avg=3934.26, stdev=25.55, samples=3812
  lat (nsec)   : 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.04%, 4=0.21%, 10=73.77%, 20=25.81%, 50=0.12%
  cpu          : usr=1.51%, sys=1.19%, ctx=238463, majf=0, minf=27
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,236326,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=3934MiB/s (4125MB/s), 3934MiB/s-3934MiB/s (4125MB/s-4125MB/s), io=231GiB (248GB), run=60060-60060msec

Disk stats (read/write):
  nvme0n1: ios=51/249871, merge=0/0, ticks=2/1808933, in_queue=1372456, util=99.94%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070562/Research/IOUring/BW/write/512/Artboard_4_1_fmuezz.png" alt="write-bs1M-32" width="600"/>
<br><br>