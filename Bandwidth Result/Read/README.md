# Read Plotting Result

For Read Operation I've been running using configuration below here :
```
[global]
ioengine=io_uring
rw=read
runtime=60
direct=1 
bs=n(128k,256,512,1M)
numjobs=n(starting from 1,4,16,32)
threads=n(starting from 1,4,16,32)
time_based=1
thread
group_reporting
size=1G

[nvme]
filename=/dev/nvme0n1 
```
# Result 

# BlockSize=128k
## QD=1 
```
seq_read: (groupid=0, jobs=1): err= 0: pid=4571: Mon Mar 27 23:50:27 2023
  read: IOPS=26.8k, BW=3347MiB/s (3510MB/s)(196GiB/60001msec)
    slat (usec): min=13, max=14736, avg=15.29, stdev=28.38
    clat (nsec): min=87, max=9005.9k, avg=21424.91, stdev=14833.76
     lat (usec): min=28, max=14739, avg=36.82, stdev=32.00
    clat percentiles (nsec):
     |  1.00th=[16768],  5.00th=[17792], 10.00th=[18304], 20.00th=[19072],
     | 30.00th=[19328], 40.00th=[19840], 50.00th=[20096], 60.00th=[20352],
     | 70.00th=[20864], 80.00th=[21120], 90.00th=[21888], 95.00th=[23168],
     | 99.00th=[64256], 99.50th=[65280], 99.90th=[69120], 99.95th=[71168],
     | 99.99th=[82432]
   bw (  MiB/s): min= 1524, max= 3583, per=99.94%, avg=3345.21, stdev=403.69, samples=119
   iops        : min=12195, max=28670, avg=26761.66, stdev=3229.59, samples=119
  lat (nsec)   : 100=0.01%, 250=0.21%, 500=0.23%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.07%, 20=45.84%, 50=50.58%
  lat (usec)   : 100=3.06%, 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=6.91%, sys=51.33%, ctx=1599129, majf=0, minf=32
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=1606619,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=3347MiB/s (3510MB/s), 3347MiB/s-3347MiB/s (3510MB/s-3510MB/s), io=196GiB (211GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=1603687/0, merge=0/0, ticks=44934/0, in_queue=124, util=99.93%
```

### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070344/Research/IOUring/BW/read/128/read-128-1_oyjkub.jpg" alt="read-bs128-1" width="600"/>
<br><br>

## QD=4
```
seq_read: (groupid=0, jobs=4): err= 0: pid=4578: Mon Mar 27 23:51:59 2023
  read: IOPS=41.7k, BW=5218MiB/s (5471MB/s)(306GiB/60001msec)
    slat (usec): min=6, max=10249, avg=15.59, stdev=29.97
    clat (nsec): min=77, max=14039k, avg=79550.46, stdev=51226.42
     lat (usec): min=24, max=14083, avg=95.28, stdev=58.64
    clat percentiles (usec):
     |  1.00th=[   27],  5.00th=[   43], 10.00th=[   44], 20.00th=[   46],
     | 30.00th=[   61], 40.00th=[   73], 50.00th=[   79], 60.00th=[   81],
     | 70.00th=[   85], 80.00th=[  106], 90.00th=[  116], 95.00th=[  131],
     | 99.00th=[  208], 99.50th=[  235], 99.90th=[  302], 99.95th=[  347],
     | 99.99th=[ 1467]
   bw (  MiB/s): min= 2701, max= 7143, per=99.96%, avg=5216.07, stdev=216.25, samples=476
   iops        : min=21614, max=57149, avg=41728.45, stdev=1730.03, samples=476
  lat (nsec)   : 100=0.01%, 250=0.02%, 500=0.03%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.03%, 50=25.77%
  lat (usec)   : 100=52.37%, 250=21.43%, 500=0.31%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.01%
  cpu          : usr=3.08%, sys=20.96%, ctx=2503801, majf=0, minf=128
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=2504692,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=5218MiB/s (5471MB/s), 5218MiB/s-5218MiB/s (5471MB/s-5471MB/s), io=306GiB (328GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=2500139/0, merge=0/0, ticks=210145/0, in_queue=364, util=99.93%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070344/Research/IOUring/BW/read/128/read-128-4_mvmyg2.jpg" alt="read-bs128-4" width="600"/>
<br><br>

## QD=16
```
seq_read: (groupid=0, jobs=16): err= 0: pid=4587: Mon Mar 27 23:54:10 2023
  read: IOPS=44.7k, BW=5594MiB/s (5865MB/s)(328GiB/60002msec)
    slat (usec): min=6, max=25391, avg=21.61, stdev=36.40
    clat (nsec): min=86, max=25594k, avg=334399.08, stdev=170001.08
     lat (usec): min=24, max=25733, avg=356.27, stdev=173.31
    clat percentiles (usec):
     |  1.00th=[   50],  5.00th=[  116], 10.00th=[  157], 20.00th=[  206],
     | 30.00th=[  251], 40.00th=[  293], 50.00th=[  334], 60.00th=[  371],
     | 70.00th=[  404], 80.00th=[  445], 90.00th=[  502], 95.00th=[  562],
     | 99.00th=[  709], 99.50th=[  775], 99.90th=[ 1074], 99.95th=[ 1483],
     | 99.99th=[ 5014]
   bw (  MiB/s): min= 4137, max= 6274, per=99.95%, avg=5590.72, stdev=25.59, samples=1905
   iops        : min=33096, max=50193, avg=44725.28, stdev=204.75, samples=1905
  lat (nsec)   : 100=0.01%, 250=0.01%, 500=0.08%, 750=0.04%, 1000=0.01%
  lat (usec)   : 2=0.01%, 10=0.01%, 20=0.03%, 50=0.85%, 100=2.68%
  lat (usec)   : 250=26.15%, 500=59.83%, 750=9.66%, 1000=0.53%
  lat (msec)   : 2=0.09%, 4=0.02%, 10=0.01%, 20=0.01%, 50=0.01%
  cpu          : usr=1.59%, sys=7.51%, ctx=2683135, majf=0, minf=512
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=2685013,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=5594MiB/s (5865MB/s), 5594MiB/s-5594MiB/s (5865MB/s-5865MB/s), io=328GiB (352GB), run=60002-60002msec

Disk stats (read/write):
  nvme0n1: ios=2679112/0, merge=0/0, ticks=756866/0, in_queue=1296, util=100.00%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070344/Research/IOUring/BW/read/128/read-128-16_u8qyud.jpg" alt="read-bs128-16" width="600"/>
<br><br>

## QD=32
```
seq_read: (groupid=0, jobs=32): err= 0: pid=4618: Mon Mar 27 23:57:47 2023
  read: IOPS=43.4k, BW=5426MiB/s (5690MB/s)(318GiB/60004msec)
    slat (usec): min=6, max=23698, avg=29.48, stdev=38.27
    clat (nsec): min=159, max=24143k, avg=705563.95, stdev=331091.02
     lat (usec): min=32, max=24227, avg=735.39, stdev=329.69
    clat percentiles (usec):
     |  1.00th=[   87],  5.00th=[  223], 10.00th=[  293], 20.00th=[  420],
     | 30.00th=[  537], 40.00th=[  644], 50.00th=[  725], 60.00th=[  791],
     | 70.00th=[  865], 80.00th=[  947], 90.00th=[ 1074], 95.00th=[ 1188],
     | 99.00th=[ 1401], 99.50th=[ 1516], 99.90th=[ 2507], 99.95th=[ 3392],
     | 99.99th=[ 7308]
   bw (  MiB/s): min= 4492, max= 6362, per=100.00%, avg=5429.91, stdev=10.28, samples=3811
   iops        : min=35944, max=50900, avg=43438.56, stdev=82.22, samples=3811
  lat (nsec)   : 250=0.01%, 500=0.52%, 750=0.20%, 1000=0.02%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.08%, 50=0.01%
  lat (usec)   : 100=0.29%, 250=5.63%, 500=19.81%, 750=27.21%, 1000=31.40%
  lat (msec)   : 2=14.63%, 4=0.14%, 10=0.03%, 20=0.01%, 50=0.01%
  cpu          : usr=1.00%, sys=4.79%, ctx=2587018, majf=0, minf=994
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=2604640,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=5426MiB/s (5690MB/s), 5426MiB/s-5426MiB/s (5690MB/s-5690MB/s), io=318GiB (341GB), run=60004-60004msec

Disk stats (read/write):
  nvme0n1: ios=2598726/0, merge=0/0, ticks=1406464/0, in_queue=1932, util=100.00%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070344/Research/IOUring/BW/read/128/read-128-32_yxx1ie.jpg" alt="read-bs128-32" width="600"/>
<br><br>

# BlockSize=256k
## QD=1
```
seq_read: (groupid=0, jobs=1): err= 0: pid=4658: Mon Mar 27 23:59:49 2023
  read: IOPS=16.8k, BW=4206MiB/s (4411MB/s)(246GiB/60001msec)
    slat (usec): min=17, max=8978, avg=18.98, stdev=36.40
    clat (nsec): min=123, max=8833.8k, avg=39798.31, stdev=24460.80
     lat (usec): min=49, max=8982, avg=58.91, stdev=43.70
    clat percentiles (usec):
     |  1.00th=[   34],  5.00th=[   35], 10.00th=[   36], 20.00th=[   36],
     | 30.00th=[   37], 40.00th=[   37], 50.00th=[   38], 60.00th=[   38],
     | 70.00th=[   38], 80.00th=[   39], 90.00th=[   41], 95.00th=[   44],
     | 99.00th=[  127], 99.50th=[  128], 99.90th=[  135], 99.95th=[  139],
     | 99.99th=[  194]
   bw (  MiB/s): min= 1686, max= 4560, per=99.97%, avg=4205.12, stdev=492.04, samples=119
   iops        : min= 6744, max=18240, avg=16820.49, stdev=1968.17, samples=119
  lat (nsec)   : 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.02%, 50=96.70%
  lat (usec)   : 100=0.39%, 250=2.85%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=4.22%, sys=39.06%, ctx=1009940, majf=0, minf=64
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=1009513,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=4206MiB/s (4411MB/s), 4206MiB/s-4206MiB/s (4411MB/s-4411MB/s), io=246GiB (265GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=1007723/0, merge=0/0, ticks=48001/0, in_queue=136, util=99.92%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070359/Research/IOUring/BW/read/256/read-256-1_qct60j.jpg" alt="read-bs256-1" width="600"/>
<br><br>

## QD=4
```
seq_read: (groupid=0, jobs=4): err= 0: pid=4691: Tue Mar 28 00:01:37 2023
  read: IOPS=17.6k, BW=4406MiB/s (4620MB/s)(258GiB/60001msec)
    slat (usec): min=7, max=23780, avg=25.07, stdev=65.98
    clat (nsec): min=87, max=13779k, avg=200722.95, stdev=160978.74
     lat (usec): min=38, max=23816, avg=226.03, stdev=184.08
    clat percentiles (usec):
     |  1.00th=[   60],  5.00th=[   97], 10.00th=[  106], 20.00th=[  110],
     | 30.00th=[  119], 40.00th=[  141], 50.00th=[  155], 60.00th=[  202],
     | 70.00th=[  243], 80.00th=[  265], 90.00th=[  322], 95.00th=[  379],
     | 99.00th=[  693], 99.50th=[  914], 99.90th=[ 1631], 99.95th=[ 2278],
     | 99.99th=[ 5538]
   bw (  MiB/s): min=  753, max= 7765, per=100.00%, avg=4406.79, stdev=421.74, samples=476
   iops        : min= 3014, max=31062, avg=17626.94, stdev=1686.97, samples=476
  lat (nsec)   : 100=0.01%, 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.01%, 50=0.60%
  lat (usec)   : 100=4.80%, 250=70.92%, 500=21.00%, 750=1.82%, 1000=0.40%
  lat (msec)   : 2=0.35%, 4=0.05%, 10=0.02%, 20=0.01%
  cpu          : usr=2.04%, sys=13.99%, ctx=1057871, majf=0, minf=256
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=1057493,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=4406MiB/s (4620MB/s), 4406MiB/s-4406MiB/s (4620MB/s-4620MB/s), io=258GiB (277GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=1055829/0, merge=0/0, ticks=216919/0, in_queue=944, util=99.97%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070359/Research/IOUring/BW/read/256/read-256-4_xvuyqt.jpg" alt="read-bs256-4" width="600"/>
<br><br>

## QD=16
```
seq_read: (groupid=0, jobs=16): err= 0: pid=4701: Tue Mar 28 00:03:15 2023
  read: IOPS=22.3k, BW=5580MiB/s (5851MB/s)(327GiB/60001msec)
    slat (usec): min=8, max=22824, avg=43.77, stdev=64.55
    clat (nsec): min=194, max=23318k, avg=670586.54, stdev=297719.78
     lat (usec): min=68, max=23349, avg=714.81, stdev=299.99
    clat percentiles (usec):
     |  1.00th=[  141],  5.00th=[  225], 10.00th=[  306], 20.00th=[  429],
     | 30.00th=[  537], 40.00th=[  619], 50.00th=[  693], 60.00th=[  758],
     | 70.00th=[  816], 80.00th=[  873], 90.00th=[  971], 95.00th=[ 1057],
     | 99.00th=[ 1287], 99.50th=[ 1401], 99.90th=[ 1795], 99.95th=[ 2409],
     | 99.99th=[ 8586]
   bw (  MiB/s): min= 4343, max= 6680, per=100.00%, avg=5584.70, stdev=27.11, samples=1908
   iops        : min=17372, max=26720, avg=22338.30, stdev=108.45, samples=1908
  lat (nsec)   : 250=0.01%, 500=0.01%, 750=0.02%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.01%, 50=0.01%
  lat (usec)   : 100=0.24%, 250=5.90%, 500=20.33%, 750=32.56%, 1000=32.94%
  lat (msec)   : 2=7.88%, 4=0.05%, 10=0.02%, 20=0.01%, 50=0.01%
  cpu          : usr=1.29%, sys=7.47%, ctx=1341084, majf=0, minf=1024
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=1339266,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=5580MiB/s (5851MB/s), 5580MiB/s-5580MiB/s (5851MB/s-5851MB/s), io=327GiB (351GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=1337033/0, merge=0/0, ticks=774745/0, in_queue=1136, util=100.00%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070359/Research/IOUring/BW/read/256/read-256-16_khth5f.jpg" alt="read-bs256-16" width="600"/>
<br><br>

## QD=32
```
seq_read: (groupid=0, jobs=32): err= 0: pid=4722: Tue Mar 28 00:04:42 2023
  read: IOPS=21.0k, BW=5255MiB/s (5511MB/s)(308GiB/60003msec)
    slat (usec): min=9, max=12965, avg=43.59, stdev=32.47
    clat (nsec): min=153, max=12955k, avg=1475675.70, stdev=608309.19
     lat (usec): min=61, max=13957, avg=1519.72, stdev=601.69
    clat percentiles (usec):
     |  1.00th=[  182],  5.00th=[  379], 10.00th=[  594], 20.00th=[  922],
     | 30.00th=[ 1156], 40.00th=[ 1352], 50.00th=[ 1549], 60.00th=[ 1729],
     | 70.00th=[ 1893], 80.00th=[ 2024], 90.00th=[ 2180], 95.00th=[ 2311],
     | 99.00th=[ 2540], 99.50th=[ 2638], 99.90th=[ 2999], 99.95th=[ 3785],
     | 99.99th=[ 7832]
   bw (  MiB/s): min= 4648, max= 5795, per=99.98%, avg=5254.26, stdev= 7.09, samples=3809
   iops        : min=18592, max=23182, avg=21014.82, stdev=28.37, samples=3809
  lat (nsec)   : 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.02%
  lat (usec)   : 2=0.30%, 4=0.01%, 10=0.01%, 20=0.06%, 50=0.01%
  lat (usec)   : 100=0.03%, 250=1.55%, 500=5.89%, 750=6.21%, 1000=9.11%
  lat (msec)   : 2=54.74%, 4=22.00%, 10=0.04%, 20=0.01%
  cpu          : usr=0.68%, sys=3.66%, ctx=1259240, majf=0, minf=2017
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=1261327,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=5255MiB/s (5511MB/s), 5255MiB/s-5255MiB/s (5511MB/s-5511MB/s), io=308GiB (331GB), run=60003-60003msec

Disk stats (read/write):
  nvme0n1: ios=1258307/0, merge=0/0, ticks=1570052/0, in_queue=1484, util=99.92%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070359/Research/IOUring/BW/read/256/read-256-32_j3ifp0.jpg" alt="read-bs256-32" width="600"/>
<br><br>

# BlockSize=512k
## QD=1
```
seq_read: (groupid=0, jobs=1): err= 0: pid=4769: Tue Mar 28 00:10:03 2023
  read: IOPS=9553, BW=4777MiB/s (5009MB/s)(280GiB/60001msec)
    slat (usec): min=20, max=19308, avg=23.91, stdev=45.21
    clat (nsec): min=149, max=4021.9k, avg=80028.30, stdev=29027.99
     lat (usec): min=90, max=19310, avg=104.06, stdev=56.35
    clat percentiles (usec):
     |  1.00th=[   73],  5.00th=[   74], 10.00th=[   75], 20.00th=[   76],
     | 30.00th=[   77], 40.00th=[   77], 50.00th=[   78], 60.00th=[   78],
     | 70.00th=[   79], 80.00th=[   80], 90.00th=[   81], 95.00th=[   83],
     | 99.00th=[  269], 99.50th=[  273], 99.90th=[  285], 99.95th=[  293],
     | 99.99th=[  355]
   bw (  MiB/s): min= 1410, max= 5072, per=99.95%, avg=4774.22, stdev=586.00, samples=119
   iops        : min= 2820, max=10144, avg=9548.41, stdev=1171.98, samples=119
  lat (nsec)   : 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.01%, 50=0.02%
  lat (usec)   : 100=98.45%, 250=0.09%, 500=1.41%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=2.60%, sys=28.22%, ctx=573658, majf=0, minf=128
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=573191,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=4777MiB/s (5009MB/s), 4777MiB/s-4777MiB/s (5009MB/s-5009MB/s), io=280GiB (301GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=572167/0, merge=0/0, ticks=50091/0, in_queue=76, util=99.94%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070373/Research/IOUring/BW/read/512/read-512-1_iyuhtw.jpg" alt="read-bs512-1" width="600"/>
<br><br>

## QD=4
```
seq_read: (groupid=0, jobs=4): err= 0: pid=4775: Tue Mar 28 00:11:34 2023
  read: IOPS=10.7k, BW=5350MiB/s (5610MB/s)(313GiB/60001msec)
    slat (usec): min=12, max=20125, avg=53.72, stdev=61.46
    clat (nsec): min=239, max=14894k, avg=318008.91, stdev=154112.30
     lat (usec): min=97, max=20166, avg=372.10, stdev=166.83
    clat percentiles (usec):
     |  1.00th=[   96],  5.00th=[  137], 10.00th=[  178], 20.00th=[  215],
     | 30.00th=[  229], 40.00th=[  260], 50.00th=[  289], 60.00th=[  343],
     | 70.00th=[  383], 80.00th=[  433], 90.00th=[  478], 95.00th=[  510],
     | 99.00th=[  701], 99.50th=[  799], 99.90th=[ 1057], 99.95th=[ 1745],
     | 99.99th=[ 4817]
   bw (  MiB/s): min= 3030, max= 8175, per=99.97%, avg=5348.73, stdev=287.62, samples=476
   iops        : min= 6060, max=16350, avg=10697.39, stdev=575.22, samples=476
  lat (nsec)   : 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 10=0.01%, 20=0.01%, 50=0.01%, 100=1.45%
  lat (usec)   : 250=34.07%, 500=58.35%, 750=5.36%, 1000=0.64%
  lat (msec)   : 2=0.07%, 4=0.03%, 10=0.01%, 20=0.01%
  cpu          : usr=2.17%, sys=18.01%, ctx=643231, majf=0, minf=512
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=642036,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=5350MiB/s (5610MB/s), 5350MiB/s-5350MiB/s (5610MB/s-5610MB/s), io=313GiB (337GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=640851/0, merge=0/0, ticks=205878/0, in_queue=456, util=99.93%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070373/Research/IOUring/BW/read/512/read-512-4_ipapyy.jpg" alt="read-bs512-4" width="600"/>
<br><br>

## QD=16
```
seq_read: (groupid=0, jobs=16): err= 0: pid=4784: Tue Mar 28 00:12:54 2023
  read: IOPS=10.6k, BW=5283MiB/s (5539MB/s)(310GiB/60002msec)
    slat (usec): min=13, max=24584, avg=67.46, stdev=101.70
    clat (nsec): min=196, max=26540k, avg=1442971.03, stdev=613918.77
     lat (usec): min=120, max=26595, avg=1511.01, stdev=612.30
    clat percentiles (usec):
     |  1.00th=[  204],  5.00th=[  482], 10.00th=[  709], 20.00th=[  938],
     | 30.00th=[ 1090], 40.00th=[ 1221], 50.00th=[ 1418], 60.00th=[ 1663],
     | 70.00th=[ 1844], 80.00th=[ 1991], 90.00th=[ 2147], 95.00th=[ 2245],
     | 99.00th=[ 2573], 99.50th=[ 2769], 99.90th=[ 4228], 99.95th=[ 5407],
     | 99.99th=[15270]
   bw (  MiB/s): min= 3599, max= 5976, per=99.96%, avg=5280.55, stdev=23.14, samples=1907
   iops        : min= 7197, max=11952, avg=10560.35, stdev=46.28, samples=1907
  lat (nsec)   : 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 20=0.01%, 50=0.01%, 100=0.02%
  lat (usec)   : 250=1.56%, 500=3.66%, 750=6.04%, 1000=12.44%
  lat (msec)   : 2=57.24%, 4=18.90%, 10=0.10%, 20=0.02%, 50=0.01%
  cpu          : usr=0.84%, sys=5.58%, ctx=635863, majf=0, minf=2048
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=633949,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=5283MiB/s (5539MB/s), 5283MiB/s-5283MiB/s (5539MB/s-5539MB/s), io=310GiB (332GB), run=60002-60002msec

Disk stats (read/write):
  nvme0n1: ios=632654/0, merge=0/0, ticks=829731/0, in_queue=2948, util=99.97%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070373/Research/IOUring/BW/read/512/read-512-16_lohuiq.jpg" alt="read-bs512-16" width="600"/>
<br><br>

## QD=32
```
seq_read: (groupid=0, jobs=32): err= 0: pid=4805: Tue Mar 28 00:14:17 2023
  read: IOPS=9367, BW=4684MiB/s (4911MB/s)(274GiB/60003msec)
    slat (usec): min=14, max=24857, avg=64.15, stdev=78.16
    clat (nsec): min=308, max=27317k, avg=3348094.52, stdev=1263942.40
     lat (usec): min=154, max=27369, avg=3412.85, stdev=1259.98
    clat percentiles (usec):
     |  1.00th=[ 1958],  5.00th=[ 2147], 10.00th=[ 2245], 20.00th=[ 2343],
     | 30.00th=[ 2409], 40.00th=[ 2507], 50.00th=[ 2606], 60.00th=[ 2868],
     | 70.00th=[ 4686], 80.00th=[ 4883], 90.00th=[ 5080], 95.00th=[ 5211],
     | 99.00th=[ 5604], 99.50th=[ 5800], 99.90th=[ 8160], 99.95th=[ 9503],
     | 99.99th=[19792]
   bw (  MiB/s): min= 3143, max= 6319, per=99.91%, avg=4679.43, stdev=21.32, samples=3816
   iops        : min= 6286, max=12638, avg=9357.35, stdev=42.65, samples=3816
  lat (nsec)   : 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 50=0.01%, 100=0.01%, 250=0.02%
  lat (usec)   : 500=0.02%, 750=0.04%, 1000=0.05%
  lat (msec)   : 2=1.15%, 4=63.52%, 10=35.14%, 20=0.04%, 50=0.01%
  cpu          : usr=0.38%, sys=2.21%, ctx=563400, majf=0, minf=4096
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=562057,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=4684MiB/s (4911MB/s), 4684MiB/s-4684MiB/s (4911MB/s-4911MB/s), io=274GiB (295GB), run=60003-60003msec

Disk stats (read/write):
  nvme0n1: ios=560453/0, merge=0/0, ticks=1690131/0, in_queue=776664, util=99.97%
```
### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070373/Research/IOUring/BW/read/512/read-512-32_axijtd.jpg" alt="read-bs512-1" width="600"/>
<br><br>

# BlockSize=1M
## QD=1
```
seq_read: (groupid=0, jobs=1): err= 0: pid=4844: Tue Mar 28 00:16:01 2023
  read: IOPS=4638, BW=4639MiB/s (4864MB/s)(272GiB/60001msec)
    slat (usec): min=29, max=10120, avg=36.23, stdev=92.20
    clat (nsec): min=186, max=6421.6k, avg=178560.26, stdev=64952.57
     lat (usec): min=187, max=10126, avg=214.91, stdev=118.15
    clat percentiles (usec):
     |  1.00th=[  161],  5.00th=[  163], 10.00th=[  165], 20.00th=[  165],
     | 30.00th=[  165], 40.00th=[  167], 50.00th=[  167], 60.00th=[  167],
     | 70.00th=[  169], 80.00th=[  172], 90.00th=[  174], 95.00th=[  178],
     | 99.00th=[  537], 99.50th=[  545], 99.90th=[  562], 99.95th=[  570],
     | 99.99th=[ 1012]
   bw (  MiB/s): min= 1536, max= 5082, per=99.94%, avg=4635.93, stdev=714.08, samples=119
   iops        : min= 1536, max= 5082, avg=4635.92, stdev=714.07, samples=119
  lat (nsec)   : 250=0.01%, 500=0.01%, 750=0.02%, 1000=0.01%
  lat (usec)   : 2=0.01%, 20=0.01%, 50=0.01%, 100=0.01%, 250=96.98%
  lat (usec)   : 500=0.03%, 750=2.93%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=1.36%, sys=20.15%, ctx=278707, majf=0, minf=256
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=278319,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=4639MiB/s (4864MB/s), 4639MiB/s-4639MiB/s (4864MB/s-4864MB/s), io=272GiB (292GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=277799/0, merge=0/0, ticks=52155/0, in_queue=204, util=99.95%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070323/Research/IOUring/BW/read/1m/read-1m-1_pehzxz.jpg" alt="read-bs1m-1" width="600"/>
<br><br>

## QD=4
```
seq_read: (groupid=0, jobs=4): err= 0: pid=4851: Tue Mar 28 00:17:44 2023
  read: IOPS=5573, BW=5574MiB/s (5844MB/s)(327GiB/60001msec)
    slat (usec): min=29, max=27151, avg=110.13, stdev=152.33
    clat (nsec): min=469, max=21897k, avg=604130.02, stdev=291141.47
     lat (usec): min=204, max=27161, avg=714.88, stdev=321.49
    clat percentiles (usec):
     |  1.00th=[  196],  5.00th=[  347], 10.00th=[  375], 20.00th=[  383],
     | 30.00th=[  392], 40.00th=[  400], 50.00th=[  545], 60.00th=[  619],
     | 70.00th=[  750], 80.00th=[  914], 90.00th=[  930], 95.00th=[  971],
     | 99.00th=[ 1319], 99.50th=[ 1598], 99.90th=[ 1876], 99.95th=[ 2114],
     | 99.99th=[ 6456]
   bw (  MiB/s): min= 3178, max= 8194, per=99.97%, avg=5571.99, stdev=323.94, samples=478
   iops        : min= 3178, max= 8194, avg=5571.81, stdev=323.95, samples=478
  lat (nsec)   : 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 50=0.01%, 100=0.01%, 250=4.47%
  lat (usec)   : 500=39.88%, 750=25.80%, 1000=25.59%
  lat (msec)   : 2=4.17%, 4=0.05%, 10=0.01%, 20=0.01%, 50=0.01%
  cpu          : usr=1.50%, sys=19.00%, ctx=335714, majf=0, minf=1024
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=334426,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=5574MiB/s (5844MB/s), 5574MiB/s-5574MiB/s (5844MB/s-5844MB/s), io=327GiB (351GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=333756/0, merge=0/0, ticks=204462/0, in_queue=560, util=99.93%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070324/Research/IOUring/BW/read/1m/read-1m-4_ekhsgv.jpg" alt="read-bs1m-4" width="600"/>
<br><br>

## QD=16
```
seq_read: (groupid=0, jobs=16): err= 0: pid=4864: Tue Mar 28 00:19:24 2023
  read: IOPS=4707, BW=4707MiB/s (4936MB/s)(276GiB/60004msec)
    slat (usec): min=25, max=19225, avg=109.65, stdev=62.65
    clat (nsec): min=381, max=14831k, avg=3284213.68, stdev=1234204.67
     lat (usec): min=296, max=22176, avg=3394.59, stdev=1228.20
    clat percentiles (usec):
     |  1.00th=[ 1696],  5.00th=[ 2147], 10.00th=[ 2212], 20.00th=[ 2376],
     | 30.00th=[ 2442], 40.00th=[ 2573], 50.00th=[ 2671], 60.00th=[ 2835],
     | 70.00th=[ 3425], 80.00th=[ 5014], 90.00th=[ 5145], 95.00th=[ 5342],
     | 99.00th=[ 5866], 99.50th=[ 6063], 99.90th=[ 7177], 99.95th=[ 7767],
     | 99.99th=[11338]
   bw (  MiB/s): min= 3275, max= 5915, per=99.94%, avg=4704.77, stdev=34.80, samples=1912
   iops        : min= 3275, max= 5915, avg=4704.08, stdev=34.80, samples=1912
  lat (nsec)   : 500=0.01%
  lat (usec)   : 2=0.01%, 250=0.02%, 500=0.06%, 750=0.04%, 1000=0.03%
  lat (msec)   : 2=2.37%, 4=68.12%, 10=29.33%, 20=0.02%
  cpu          : usr=0.45%, sys=3.78%, ctx=283942, majf=0, minf=4096
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=282463,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=4707MiB/s (4936MB/s), 4707MiB/s-4707MiB/s (4936MB/s-4936MB/s), io=276GiB (296GB), run=60004-60004msec

Disk stats (read/write):
  nvme0n1: ios=281784/0, merge=0/0, ticks=869036/0, in_queue=329312, util=99.95%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070324/Research/IOUring/BW/read/1m/read-1m-16_dxofl5.jpg" alt="read-bs1m-16" width="600"/>
<br><br>

## QD=32
```
seq_read: (groupid=0, jobs=32): err= 0: pid=4886: Tue Mar 28 00:20:59 2023
  read: IOPS=4435, BW=4436MiB/s (4651MB/s)(260GiB/60010msec)
    slat (usec): min=27, max=40979, avg=102.01, stdev=195.93
    clat (nsec): min=421, max=26819k, avg=7107244.94, stdev=2555885.04
     lat (usec): min=280, max=56998, avg=7209.87, stdev=2561.00
    clat percentiles (usec):
     |  1.00th=[ 5014],  5.00th=[ 5211], 10.00th=[ 5276], 20.00th=[ 5407],
     | 30.00th=[ 5538], 40.00th=[ 5604], 50.00th=[ 5735], 60.00th=[ 5932],
     | 70.00th=[ 6259], 80.00th=[10945], 90.00th=[11338], 95.00th=[11731],
     | 99.00th=[12387], 99.50th=[12649], 99.90th=[14746], 99.95th=[16712],
     | 99.99th=[23462]
   bw (  MiB/s): min= 2672, max= 5827, per=99.85%, avg=4428.81, stdev=26.87, samples=3826
   iops        : min= 2668, max= 5826, avg=4425.94, stdev=26.87, samples=3826
  lat (nsec)   : 500=0.01%, 750=0.01%
  lat (usec)   : 2=0.01%, 100=0.01%, 250=0.01%, 500=0.02%, 750=0.03%
  lat (usec)   : 1000=0.03%
  lat (msec)   : 2=0.06%, 4=0.16%, 10=74.03%, 20=25.63%, 50=0.02%
  cpu          : usr=0.19%, sys=1.56%, ctx=267420, majf=0, minf=8192
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=266178,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=4436MiB/s (4651MB/s), 4436MiB/s-4436MiB/s (4651MB/s-4651MB/s), io=260GiB (279GB), run=60010-60010msec

Disk stats (read/write):
  nvme0n1: ios=265189/0, merge=0/0, ticks=1770614/0, in_queue=1344208, util=99.94%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680070324/Research/IOUring/BW/read/1m/read-1m-32_kcb3hk.jpg" alt="read-bs1m-32" width="600"/>
<br><br>

### Explanation 
dari semua hasil diatas, dapat kita amati bahwa dengan menggunakan ioengine ```io_uring``` konsistensi performa yang didapat pada masing masing grafik dapat dikatakan cukup baik dikarenakan nilai yang diperoleh dari masing masing benchmarking konsisten diantara nilai 4000-5000 walaupun memang di beberapa kasus masih terjadi drop performa yang cukup signifikan seperti pada kasus QD=1 pada tiap tiap blocksize. Hal ini masih terkait dengan uji performa sebelumnya yang menggunakan ioengine ```psync``` yang dimana numjobs dan threads berperan penting dalam mepengaruhi fluktuasi performa benchmarking. 


