# Randread Plotting Result

For Random Read Operation I've been running using configuration below here :
```
[global]
ioengine=io_uring
rw=randread
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
rand_read: (groupid=0, jobs=1): err= 0: pid=1736: Mon Mar 27 22:26:12 2023
  read: IOPS=63.1k, BW=246MiB/s (258MB/s)(14.4GiB/60000msec)
    slat (usec): min=8, max=21148, avg=14.98, stdev=27.33
    clat (nsec): min=74, max=6480.1k, avg=177.75, stdev=5896.20
     lat (usec): min=11, max=21153, avg=15.38, stdev=28.31
    clat percentiles (nsec):
     |  1.00th=[   96],  5.00th=[  115], 10.00th=[  153], 20.00th=[  155],
     | 30.00th=[  157], 40.00th=[  161], 50.00th=[  167], 60.00th=[  167],
     | 70.00th=[  169], 80.00th=[  169], 90.00th=[  171], 95.00th=[  173],
     | 99.00th=[  181], 99.50th=[  233], 99.90th=[  510], 99.95th=[ 3952],
     | 99.99th=[18304]
   bw (  KiB/s): min=240224, max=305448, per=99.99%, avg=252276.57, stdev=9302.67, samples=119
   iops        : min=60056, max=76362, avg=63069.17, stdev=2325.62, samples=119
  lat (nsec)   : 100=1.73%, 250=97.81%, 500=0.35%, 750=0.05%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.02%, 20=0.02%, 50=0.01%
  lat (usec)   : 100=0.01%, 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=10.30%, sys=89.53%, ctx=2371, majf=0, minf=1
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=3784496,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=246MiB/s (258MB/s), 246MiB/s-246MiB/s (258MB/s-258MB/s), io=14.4GiB (15.5GB), run=60000-60000msec

Disk stats (read/write):
  nvme0n1: ios=3778288/0, merge=0/0, ticks=40578/0, in_queue=184, util=99.92%
```

### Plotting Result 
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067184/Research/IOUring/IOPS/randread/randread-1_dsxk0l.jpg" alt="randread-1" width="600"/>
<br><br>

## QD=4 
```
rand_read: (groupid=0, jobs=4): err= 0: pid=1753: Mon Mar 27 22:30:01 2023
  read: IOPS=284k, BW=1110MiB/s (1164MB/s)(65.1GiB/60001msec)
    slat (usec): min=3, max=9736, avg=12.86, stdev= 9.12
    clat (nsec): min=63, max=7589.2k, avg=658.34, stdev=6607.06
     lat (usec): min=8, max=9739, avg=13.64, stdev=11.26
    clat percentiles (nsec):
     |  1.00th=[   89],  5.00th=[   98], 10.00th=[  101], 20.00th=[  105],
     | 30.00th=[  108], 40.00th=[  110], 50.00th=[  111], 60.00th=[  115],
     | 70.00th=[  117], 80.00th=[  119], 90.00th=[  126], 95.00th=[ 3280],
     | 99.00th=[14656], 99.50th=[15936], 99.90th=[20608], 99.95th=[23424],
     | 99.99th=[42752]
   bw (  MiB/s): min=  631, max= 1160, per=99.97%, avg=1110.10, stdev=21.09, samples=476
   iops        : min=161590, max=296975, avg=284184.50, stdev=5399.62, samples=476
  lat (nsec)   : 100=6.93%, 250=87.39%, 500=0.04%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=1.24%, 10=2.03%, 20=2.25%, 50=0.11%
  lat (usec)   : 100=0.01%, 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%
  cpu          : usr=10.81%, sys=86.99%, ctx=749283, majf=0, minf=4
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=17057184,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=1110MiB/s (1164MB/s), 1110MiB/s-1110MiB/s (1164MB/s-1164MB/s), io=65.1GiB (69.9GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=17025784/0, merge=0/0, ticks=168348/0, in_queue=172, util=99.92%
```

### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067183/Research/IOUring/IOPS/randread/randread-4_oqd5zr.jpg" alt="randread-4" width="600"/>
<br><br>

## QD=16
```
rand_read: (groupid=0, jobs=16): err= 0: pid=1763: Mon Mar 27 22:31:30 2023
  read: IOPS=281k, BW=1099MiB/s (1152MB/s)(64.4GiB/60011msec)
    slat (usec): min=2, max=41170, avg=23.36, stdev=432.84
    clat (nsec): min=61, max=36496k, avg=32476.04, stdev=496420.07
     lat (usec): min=8, max=41176, avg=56.08, stdev=659.88
    clat percentiles (nsec):
     |  1.00th=[      89],  5.00th=[      96], 10.00th=[     101],
     | 20.00th=[     133], 30.00th=[     135], 40.00th=[     139],
     | 50.00th=[     143], 60.00th=[     147], 70.00th=[     149],
     | 80.00th=[     183], 90.00th=[     187], 95.00th=[     274],
     | 99.00th=[  354304], 99.50th=[ 1122304], 99.90th=[ 8159232],
     | 99.95th=[11993088], 99.99th=[18743296]
   bw (  MiB/s): min=  856, max= 1312, per=99.98%, avg=1098.80, stdev= 5.73, samples=1909
   iops        : min=219266, max=336076, avg=281292.13, stdev=1466.03, samples=1909
  lat (nsec)   : 100=8.59%, 250=86.07%, 500=0.62%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.96%, 10=0.06%, 20=0.06%, 50=0.80%
  lat (usec)   : 100=0.74%, 250=0.86%, 500=0.45%, 750=0.17%, 1000=0.10%
  lat (msec)   : 2=0.17%, 4=0.13%, 10=0.16%, 20=0.06%, 50=0.01%
  cpu          : usr=2.69%, sys=22.26%, ctx=643727, majf=0, minf=16
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=16884088,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=1099MiB/s (1152MB/s), 1099MiB/s-1099MiB/s (1152MB/s-1152MB/s), io=64.4GiB (69.2GB), run=60011-60011msec

Disk stats (read/write):
  nvme0n1: ios=16847403/0, merge=0/0, ticks=170464/0, in_queue=248, util=100.00%
```

### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067183/Research/IOUring/IOPS/randread/randread-16_h8mbwe.jpg" alt="randread-16" width="600"/>
<br><br>

## QD=32
```
rand_read: (groupid=0, jobs=32): err= 0: pid=1784: Mon Mar 27 22:33:06 2023
  read: IOPS=292k, BW=1141MiB/s (1197MB/s)(66.9GiB/60025msec)
    slat (usec): min=2, max=73824, avg=36.18, stdev=812.70
    clat (nsec): min=60, max=67377k, avg=71948.57, stdev=984026.67
     lat (usec): min=8, max=73829, avg=108.41, stdev=1276.72
    clat percentiles (nsec):
     |  1.00th=[      82],  5.00th=[      92], 10.00th=[      97],
     | 20.00th=[     101], 30.00th=[     104], 40.00th=[     106],
     | 50.00th=[     108], 60.00th=[     111], 70.00th=[     114],
     | 80.00th=[     115], 90.00th=[     127], 95.00th=[    3184],
     | 99.00th=[  831488], 99.50th=[ 3162112], 99.90th=[17432576],
     | 99.95th=[22675456], 99.99th=[32374784]
   bw (  MiB/s): min=  932, max= 1266, per=99.98%, avg=1141.27, stdev= 1.58, samples=3819
   iops        : min=238634, max=324264, avg=292164.76, stdev=405.68, samples=3819
  lat (nsec)   : 100=15.73%, 250=78.92%, 500=0.08%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=1.13%, 10=0.02%, 20=0.01%, 50=0.28%
  lat (usec)   : 100=0.66%, 250=1.16%, 500=0.65%, 750=0.29%, 1000=0.16%
  lat (msec)   : 2=0.27%, 4=0.20%, 10=0.21%, 20=0.15%, 50=0.07%
  lat (msec)   : 100=0.01%
  cpu          : usr=1.31%, sys=11.14%, ctx=746797, majf=0, minf=31
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=17540001,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=1141MiB/s (1197MB/s), 1141MiB/s-1141MiB/s (1197MB/s-1197MB/s), io=66.9GiB (71.8GB), run=60025-60025msec

Disk stats (read/write):
  nvme0n1: ios=17494271/0, merge=0/0, ticks=179855/0, in_queue=88, util=100.00%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067183/Research/IOUring/IOPS/randread/randread-32_wjxixr.jpg" alt="randread-32" width="600"/>
<br><br>

## QD=64
```
rand_read: (groupid=0, jobs=64): err= 0: pid=1836: Mon Mar 27 22:34:42 2023
  read: IOPS=282k, BW=1102MiB/s (1156MB/s)(64.6GiB/60037msec)
    slat (usec): min=2, max=165293, avg=50.50, stdev=1519.18
    clat (nsec): min=59, max=142814k, avg=174233.27, stdev=1760806.13
     lat (usec): min=8, max=165294, avg=225.18, stdev=2327.00
    clat percentiles (nsec):
     |  1.00th=[      87],  5.00th=[      94], 10.00th=[      98],
     | 20.00th=[     101], 30.00th=[     105], 40.00th=[     107],
     | 50.00th=[     110], 60.00th=[     113], 70.00th=[     115],
     | 80.00th=[     129], 90.00th=[  110080], 95.00th=[  370688],
     | 99.00th=[ 3129344], 99.50th=[ 7634944], 99.90th=[28180480],
     | 99.95th=[39059456], 99.99th=[60555264]
   bw (  MiB/s): min=  421, max= 1393, per=100.00%, avg=1102.20, stdev= 2.16, samples=7666
   iops        : min=107780, max=356715, avg=282162.76, stdev=551.85, samples=7666
  lat (nsec)   : 100=14.15%, 250=72.92%, 500=0.07%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=1.33%, 10=0.03%, 20=0.01%, 50=0.24%
  lat (usec)   : 100=0.98%, 250=3.76%, 500=2.60%, 750=1.11%, 1000=0.54%
  lat (msec)   : 2=0.89%, 4=0.54%, 10=0.44%, 20=0.22%, 50=0.15%
  lat (msec)   : 100=0.02%, 250=0.01%
  cpu          : usr=0.70%, sys=5.40%, ctx=1975457, majf=0, minf=62
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=16937340,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=1102MiB/s (1156MB/s), 1102MiB/s-1102MiB/s (1156MB/s-1156MB/s), io=64.6GiB (69.4GB), run=60037-60037msec

Disk stats (read/write):
  nvme0n1: ios=16888687/0, merge=0/0, ticks=334208/0, in_queue=2580, util=100.00%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067183/Research/IOUring/IOPS/randread/randread-64_nc5ija.jpg" alt="randread-64" width="600"/>
<br><br>

## QD=128
```
rand_read: (groupid=0, jobs=128): err= 0: pid=1906: Mon Mar 27 22:36:12 2023
  read: IOPS=301k, BW=1174MiB/s (1231MB/s)(68.9GiB/60051msec)
    slat (usec): min=2, max=337466, avg=142.84, stdev=4109.16
    clat (nsec): min=65, max=281075k, avg=277514.99, stdev=4101458.30
     lat (usec): min=8, max=337467, avg=421.25, stdev=5809.21
    clat percentiles (nsec):
     |  1.00th=[       73],  5.00th=[       76], 10.00th=[       78],
     | 20.00th=[       80], 30.00th=[       82], 40.00th=[       83],
     | 50.00th=[       85], 60.00th=[       86], 70.00th=[       88],
     | 80.00th=[       90], 90.00th=[       93], 95.00th=[      108],
     | 99.00th=[  2408448], 99.50th=[ 13697024], 99.90th=[ 71827456],
     | 99.95th=[ 93847552], 99.99th=[137363456]
   bw (  MiB/s): min=  797, max= 1530, per=99.95%, avg=1173.74, stdev= 1.03, samples=15324
   iops        : min=204189, max=391699, avg=300475.00, stdev=264.34, samples=15324
  lat (nsec)   : 100=94.31%, 250=2.29%, 500=0.06%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=1.06%, 10=0.01%, 20=0.01%, 50=0.01%
  lat (usec)   : 100=0.01%, 250=0.22%, 500=0.49%, 750=0.17%, 1000=0.08%
  lat (msec)   : 2=0.22%, 4=0.23%, 10=0.25%, 20=0.18%, 50=0.23%
  lat (msec)   : 100=0.14%, 250=0.04%, 500=0.01%
  cpu          : usr=0.31%, sys=2.80%, ctx=439070, majf=0, minf=124
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=18052642,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=1174MiB/s (1231MB/s), 1174MiB/s-1174MiB/s (1231MB/s-1231MB/s), io=68.9GiB (73.9GB), run=60051-60051msec

Disk stats (read/write):
  nvme0n1: ios=17994624/0, merge=0/0, ticks=206081/0, in_queue=2580, util=99.90%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067183/Research/IOUring/IOPS/randread/randread-128_c5dy8f.jpg" alt="randread-128" width="600"/>
<br><br>


## QD=256
```
rand_read: (groupid=0, jobs=256): err= 0: pid=2039: Mon Mar 27 22:37:42 2023
  read: IOPS=275k, BW=1075MiB/s (1127MB/s)(63.1GiB/60103msec)
    slat (usec): min=2, max=717428, avg=186.47, stdev=6623.40
    clat (nsec): min=59, max=629797k, avg=733970.28, stdev=7266982.32
     lat (usec): min=8, max=717432, avg=922.18, stdev=9844.00
    clat percentiles (nsec):
     |  1.00th=[       68],  5.00th=[       69], 10.00th=[       71],
     | 20.00th=[       73], 30.00th=[       74], 40.00th=[       76],
     | 50.00th=[       77], 60.00th=[       78], 70.00th=[       86],
     | 80.00th=[      137], 90.00th=[   370688], 95.00th=[  1744896],
     | 99.00th=[ 13303808], 99.50th=[ 30539776], 99.90th=[117964800],
     | 99.95th=[160432128], 99.99th=[250609664]
   bw (  MiB/s): min=  298, max= 1857, per=100.00%, avg=1075.37, stdev= 0.98, samples=30676
   iops        : min=76474, max=475611, avg=275284.35, stdev=250.52, samples=30676
  lat (nsec)   : 100=73.04%, 250=14.34%, 500=0.08%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=1.40%, 10=0.02%, 20=0.01%, 50=0.03%
  lat (usec)   : 100=0.06%, 250=0.34%, 500=1.42%, 750=1.71%, 1000=0.94%
  lat (msec)   : 2=2.01%, 4=1.99%, 10=1.37%, 20=0.54%, 50=0.41%
  lat (msec)   : 100=0.18%, 250=0.12%, 500=0.01%, 750=0.01%
  cpu          : usr=0.18%, sys=1.34%, ctx=1868729, majf=0, minf=256
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=16541724,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=1075MiB/s (1127MB/s), 1075MiB/s-1075MiB/s (1127MB/s-1127MB/s), io=63.1GiB (67.8GB), run=60103-60103msec

Disk stats (read/write):
  nvme0n1: ios=16516469/0, merge=0/0, ticks=908001/0, in_queue=29728, util=99.87%
```
### Plotting Result
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1680067183/Research/IOUring/IOPS/randread/randread-256_xeynek.jpg" alt="randread-256" width="600"/>
<br><br>