## Yarn Calculations

Tested values:
```
Worker vcores		20
Worker splindles	12
Worker RAM			128
Workload factor		1
Worker nodes		10
```

## Step2

The workload factor is the maximum number of map/reduce jobs to run on each node. With a workload factor of 1 is possible to execute only 1 map and only 1 reduce per-node. As well with a workload factor of 2 or 4 the maximum number of map/reduce tasks per-node will be respectively 2/4. 


You can modify the workload factor to increase the parallelism but if the result would change depends also from which value is set into YARN as maximum mapreduce tasks that can be executed on a cluster.