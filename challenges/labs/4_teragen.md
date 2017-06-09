## teragen command
```

time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Dmapredu ce.job.maps=6 -Ddfs.block.size=33554432 51200000 tgen512m

```

## teragen time output
```
real    1m12.115s
user    1m7.366s
sys     0m2.065s
```



## hdfs dfs -ls /user/theresa/tgen512m
```

[theresa@ip-10-0-0-47 ec2-user]$ hdfs dfs -ls /user/theresa/tgen512m
Found 2 items
-rw-r--r--   3 theresa supergroup          0 2017-06-09 06:11 /user/theresa/tgen512m/_SUCCESS
-rw-r--r--   3 theresa supergroup 5120000000 2017-06-09 06:11 /user/theresa/tgen512m/part-m-00000
```

```
[theresa@ip-10-0-0-47 ec2-user]$ hadoop fsck /user/theresa/tgen512m
DEPRECATED: Use of this script to execute hdfs command is deprecated.
Instead use the hdfs command for it.

Connecting to namenode via http://ip-10-0-0-47.eu-west-1.compute.internal:50070
FSCK started by theresa (auth:SIMPLE) from /10.0.0.47 for path /user/theresa/tgen512m at Fri Jun 09 06:13:52 EDT 2017 ..Status: HEALTHY
 Total size:    5120000000 B
 Total dirs:    1
 Total files:   2
 Total symlinks:                0
 Total blocks (validated):      153 (avg. block size 33464052 B)
 Minimally replicated blocks:   153 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          4
 Number of racks:               1
FSCK ended at Fri Jun 09 06:13:52 EDT 2017 in 6 milliseconds


The filesystem under path '/user/theresa/tgen512m' is HEALTHY
```