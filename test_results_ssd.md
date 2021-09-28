Writing phase : 
```
dd if=/dev/zero of=/mnt/1GB_2 bs=1M count=1000
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 3.11433 s, 337 MB/s
```

Reading phase : 
```
#dd if=/mnt/1GB of=/dev/null bs=1M count=1000
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 1.03792 s, 1.0 GB/s
```



