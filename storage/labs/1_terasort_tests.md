## Create an end-user Linux account named with your GitHub handle

```
[ec2-user@ip-10-0-0-22 ~]$ sudo useradd alexpiermatteo
[ec2-user@ip-10-0-0-22 ~]$ sudo su - alexpiermatteo
```

I also changed the permissions of the hdfs directory /user/alexpiermatteo
```
[ec2-user@ip-10-0-0-22 ~]$ sudo -u hdfs hadoop fs -chown -R alexpiermatteo:alexpiermatte o /user/alexpiermatteo
```

## Create an end-user Linux account named with your GitHub handle
```
[alexpiermatteo@ip-10-0-0-22 ~]$ time hadoop jar /opt/cloudera/parcels/CDH-5.8.3-1.cdh5.
8.3.p0.2/jars/hadoop-examples.jar teragen -Dmapred.map.tasks=4 -Ddfs.block.size=33554432
 107374182 /user/alexpiermatteo/teragen_data_10g
17/06/06 06:15:38 INFO Configuration.deprecation: session.id is deprecated. Instead, use dfs.metrics.session-id
17/06/06 06:15:38 INFO jvm.JvmMetrics: Initializing JVM Metrics with processName=JobTracker, sessionId=
17/06/06 06:15:38 INFO terasort.TeraSort: Generating 107374182 using 1
17/06/06 06:15:38 INFO mapreduce.JobSubmitter: number of splits:1
17/06/06 06:15:38 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
17/06/06 06:15:38 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
17/06/06 06:15:38 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_local1055675522_0001
17/06/06 06:15:38 INFO mapreduce.Job: The url to track the job: http://localhost:8080/ 17/06/06 06:15:38 INFO mapreduce.Job: Running job: job_local1055675522_0001
17/06/06 06:15:38 INFO mapred.LocalJobRunner: OutputCommitter set in config null
17/06/06 06:15:38 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
17/06/06 06:15:38 INFO mapred.LocalJobRunner: OutputCommitter is org.apache.hadoop.mapreduce.lib.output.FileOutputCommitter
17/06/06 06:15:38 INFO mapred.LocalJobRunner: Waiting for map tasks
17/06/06 06:15:38 INFO mapred.LocalJobRunner: Starting task: attempt_local1055675522_0001_m_000000_0
17/06/06 06:15:38 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
17/06/06 06:15:38 INFO mapred.Task:  Using ResourceCalculatorProcessTree : [ ]
17/06/06 06:15:38 INFO mapred.MapTask: Processing split: org.apache.hadoop.examples.terasort.TeraGen$RangeInputFormat$RangeInputSplit@1b616dfe
17/06/06 06:15:39 INFO mapreduce.Job: Job job_local1055675522_0001 running in uber mode : false
17/06/06 06:15:39 INFO mapreduce.Job:  map 0% reduce 0%
17/06/06 06:15:44 INFO mapred.LocalJobRunner: map > map
17/06/06 06:15:45 INFO mapreduce.Job:  map 5% reduce 0%
17/06/06 06:15:47 INFO mapred.LocalJobRunner: map > map
17/06/06 06:15:48 INFO mapreduce.Job:  map 7% reduce 0%
17/06/06 06:15:50 INFO mapred.LocalJobRunner: map > map
17/06/06 06:15:51 INFO mapreduce.Job:  map 10% reduce 0%
17/06/06 06:15:53 INFO mapred.LocalJobRunner: map > map
17/06/06 06:15:54 INFO mapreduce.Job:  map 12% reduce 0%
17/06/06 06:15:56 INFO mapred.LocalJobRunner: map > map
17/06/06 06:15:57 INFO mapreduce.Job:  map 14% reduce 0%
17/06/06 06:15:59 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:00 INFO mapreduce.Job:  map 16% reduce 0%
17/06/06 06:16:02 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:03 INFO mapreduce.Job:  map 18% reduce 0%
17/06/06 06:16:05 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:06 INFO mapreduce.Job:  map 20% reduce 0%
17/06/06 06:16:08 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:09 INFO mapreduce.Job:  map 22% reduce 0%
17/06/06 06:16:11 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:12 INFO mapreduce.Job:  map 25% reduce 0%
17/06/06 06:16:14 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:15 INFO mapreduce.Job:  map 26% reduce 0%
17/06/06 06:16:17 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:23 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:24 INFO mapreduce.Job:  map 29% reduce 0%
17/06/06 06:16:26 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:27 INFO mapreduce.Job:  map 31% reduce 0%
17/06/06 06:16:29 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:30 INFO mapreduce.Job:  map 33% reduce 0%
17/06/06 06:16:32 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:33 INFO mapreduce.Job:  map 35% reduce 0%
17/06/06 06:16:35 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:36 INFO mapreduce.Job:  map 37% reduce 0%
17/06/06 06:16:38 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:39 INFO mapreduce.Job:  map 39% reduce 0%
17/06/06 06:16:41 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:42 INFO mapreduce.Job:  map 41% reduce 0%
17/06/06 06:16:44 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:45 INFO mapreduce.Job:  map 43% reduce 0%
17/06/06 06:16:47 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:53 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:54 INFO mapreduce.Job:  map 47% reduce 0%
17/06/06 06:16:56 INFO mapred.LocalJobRunner: map > map
17/06/06 06:16:57 INFO mapreduce.Job:  map 49% reduce 0%
17/06/06 06:16:59 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:00 INFO mapreduce.Job:  map 51% reduce 0%
17/06/06 06:17:02 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:03 INFO mapreduce.Job:  map 54% reduce 0%
17/06/06 06:17:05 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:06 INFO mapreduce.Job:  map 56% reduce 0%
17/06/06 06:17:08 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:09 INFO mapreduce.Job:  map 58% reduce 0%
17/06/06 06:17:11 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:12 INFO mapreduce.Job:  map 59% reduce 0%
17/06/06 06:17:14 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:15 INFO mapreduce.Job:  map 61% reduce 0%
17/06/06 06:17:17 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:18 INFO mapreduce.Job:  map 62% reduce 0%
17/06/06 06:17:20 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:21 INFO mapreduce.Job:  map 65% reduce 0%
17/06/06 06:17:23 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:24 INFO mapreduce.Job:  map 68% reduce 0%
17/06/06 06:17:26 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:27 INFO mapreduce.Job:  map 71% reduce 0%
17/06/06 06:17:29 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:30 INFO mapreduce.Job:  map 72% reduce 0%
17/06/06 06:17:32 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:33 INFO mapreduce.Job:  map 74% reduce 0%
17/06/06 06:17:35 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:36 INFO mapreduce.Job:  map 75% reduce 0%
17/06/06 06:17:38 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:39 INFO mapreduce.Job:  map 77% reduce 0%
17/06/06 06:17:41 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:42 INFO mapreduce.Job:  map 79% reduce 0%
17/06/06 06:17:44 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:45 INFO mapreduce.Job:  map 82% reduce 0%
17/06/06 06:17:47 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:48 INFO mapreduce.Job:  map 83% reduce 0%
17/06/06 06:17:50 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:51 INFO mapreduce.Job:  map 85% reduce 0%
17/06/06 06:17:53 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:54 INFO mapreduce.Job:  map 87% reduce 0%
17/06/06 06:17:56 INFO mapred.LocalJobRunner: map > map
17/06/06 06:17:57 INFO mapreduce.Job:  map 88% reduce 0%
17/06/06 06:17:59 INFO mapred.LocalJobRunner: map > map
17/06/06 06:18:00 INFO mapreduce.Job:  map 90% reduce 0%
17/06/06 06:18:02 INFO mapred.LocalJobRunner: map > map
17/06/06 06:18:03 INFO mapreduce.Job:  map 92% reduce 0%
17/06/06 06:18:05 INFO mapred.LocalJobRunner: map > map
17/06/06 06:18:06 INFO mapreduce.Job:  map 94% reduce 0%
17/06/06 06:18:08 INFO mapred.LocalJobRunner: map > map
17/06/06 06:18:09 INFO mapreduce.Job:  map 96% reduce 0%
17/06/06 06:18:11 INFO mapred.LocalJobRunner: map > map
17/06/06 06:18:12 INFO mapreduce.Job:  map 97% reduce 0%
17/06/06 06:18:14 INFO mapred.LocalJobRunner: map > map
17/06/06 06:18:15 INFO mapreduce.Job:  map 98% reduce 0%
17/06/06 06:18:17 INFO mapred.LocalJobRunner: map > map
17/06/06 06:18:18 INFO mapreduce.Job:  map 99% reduce 0%
17/06/06 06:18:19 INFO mapred.LocalJobRunner: map > map
17/06/06 06:18:19 INFO mapred.Task: Task:attempt_local1055675522_0001_m_000000_0 is done. And is in the process of committing
17/06/06 06:18:19 INFO mapred.LocalJobRunner: map > map
17/06/06 06:18:19 INFO mapred.Task: Task attempt_local1055675522_0001_m_000000_0 is allowed to commit now
17/06/06 06:18:19 INFO output.FileOutputCommitter: Saved output of task 'attempt_local1055675522_0001_m_000000_0' to hdfs://ip-10-0-0-22.eu-west-1.compute.internal:8020/user/alexpiermatteo/teragen_data_10g/_temporary/0/task_local1055675522_0001_m_000000
17/06/06 06:18:19 INFO mapred.LocalJobRunner: map
17/06/06 06:18:19 INFO mapred.Task: Task 'attempt_local1055675522_0001_m_000000_0' done.
17/06/06 06:18:19 INFO mapred.LocalJobRunner: Finishing task: attempt_local1055675522_0001_m_000000_0
17/06/06 06:18:19 INFO mapred.LocalJobRunner: map task executor complete.
17/06/06 06:18:19 INFO mapreduce.Job:  map 100% reduce 0%
17/06/06 06:18:19 INFO mapreduce.Job: Job job_local1055675522_0001 completed successfully
17/06/06 06:18:19 INFO mapreduce.Job: Counters: 21
        File System Counters
                FILE: Number of bytes read=276334
                FILE: Number of bytes written=576533
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=0
                HDFS: Number of bytes written=10737418200
                HDFS: Number of read operations=4
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=3
        Map-Reduce Framework
                Map input records=107374182
                Map output records=107374182
                Input split bytes=83
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=1342
                Total committed heap usage (bytes)=202899456
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=230593859918397906
        File Input Format Counters
                Bytes Read=0
        File Output Format Counters
                Bytes Written=10737418200

real    2m44.134s
user    2m14.907s
sys     0m3.976s
```

## Run the `terasort` command on this file
```
[alexpiermatteo@ip-10-0-0-22 ~]$ time hadoop jar /opt/cloudera/parcels/CDH-5.8.3-1.cdh5.8.3.p0.2/jars/hadoop-examples.jar terasort /user/alexpiermatteo/teragen_data_10g /user/alexpiermatteo/terasort_data_10g
.
.
.
17/06/06 06:36:28 INFO mapred.LocalJobRunner: reduce > reduce
17/06/06 06:36:31 INFO mapred.LocalJobRunner: reduce > reduce
17/06/06 06:36:32 INFO mapreduce.Job:  map 100% reduce 94%
17/06/06 06:36:34 INFO mapred.LocalJobRunner: reduce > reduce
17/06/06 06:36:37 INFO mapred.LocalJobRunner: reduce > reduce
17/06/06 06:36:38 INFO mapreduce.Job:  map 100% reduce 95%
17/06/06 06:36:40 INFO mapred.LocalJobRunner: reduce > reduce
17/06/06 06:36:43 INFO mapred.LocalJobRunner: reduce > reduce
17/06/06 06:36:44 INFO mapreduce.Job:  map 100% reduce 96%
17/06/06 06:36:46 INFO mapred.LocalJobRunner: reduce > reduce
17/06/06 06:36:47 INFO mapreduce.Job:  map 100% reduce 97%
17/06/06 06:36:49 INFO mapred.LocalJobRunner: reduce > reduce
17/06/06 06:36:52 INFO mapred.LocalJobRunner: reduce > reduce
17/06/06 06:36:53 INFO mapreduce.Job:  map 100% reduce 98%
17/06/06 06:36:55 INFO mapred.LocalJobRunner: reduce > reduce
17/06/06 06:36:58 INFO mapred.LocalJobRunner: reduce > reduce
17/06/06 06:36:59 INFO mapreduce.Job:  map 100% reduce 99%
17/06/06 06:37:01 INFO mapred.LocalJobRunner: reduce > reduce
17/06/06 06:37:04 INFO mapred.LocalJobRunner: reduce > reduce
17/06/06 06:37:05 INFO mapreduce.Job:  map 100% reduce 100%
17/06/06 06:37:06 INFO mapred.Task: Task:attempt_local564886722_0001_r_000000_0 is done. And is in the process of committing
17/06/06 06:37:06 INFO mapred.LocalJobRunner: reduce > reduce
17/06/06 06:37:06 INFO mapred.Task: Task attempt_local564886722_0001_r_000000_0 is allowed to commit now
17/06/06 06:37:06 INFO output.FileOutputCommitter: Saved output of task 'attempt_local564886722_0001_r_000000_0' to hdfs://ip-10-0-0-22.eu-west-1.compute.internal:8020/user/alexpiermatteo/terasort_data_10g/_temporary/0/task_local564886722_0001_r_000000
17/06/06 06:37:06 INFO mapred.LocalJobRunner: reduce > reduce
17/06/06 06:37:06 INFO mapred.Task: Task 'attempt_local564886722_0001_r_000000_0' done.
17/06/06 06:37:06 INFO mapred.LocalJobRunner: Finishing task: attempt_local564886722_0001_r_000000_0
17/06/06 06:37:06 INFO mapred.LocalJobRunner: reduce task executor complete.
17/06/06 06:37:07 INFO mapreduce.Job: Job job_local564886722_0001 completed successfully 17/06/06 06:37:07 INFO mapreduce.Job: Counters: 35
        File System Counters
                FILE: Number of bytes read=33556925045
                FILE: Number of bytes written=1825729706061
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=1737303073300
                HDFS: Number of bytes written=10737418200
                HDFS: Number of read operations=111388
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=644
        Map-Reduce Framework
                Map input records=107374182
                Map output records=107374182
                Map output bytes=10952166564
                Map output materialized bytes=11166916848
                Input split bytes=53120
                Combine input records=0
                Combine output records=0
                Reduce input groups=107374182
                Reduce shuffle bytes=11166916848
                Reduce input records=107374182
                Reduce output records=107374182
                Spilled Records=319438188
                Shuffled Maps =320
                Failed Shuffles=0
                Merged Map outputs=320
                GC time elapsed (ms)=62699
                Total committed heap usage (bytes)=85608890368
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=10737418200
        File Output Format Counters
                Bytes Written=10737418200
17/06/06 06:37:07 INFO terasort.TeraSort: done

real    13m23.741s
user    15m31.810s
sys     1m17.138s
```
