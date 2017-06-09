```
[ec2-user@ip-10-0-0-124 ~]$ kinit theresa
Password for theresa@ALEXPIERMATTEO.COM.UK:
[ec2-user@ip-10-0-0-124 ~]$ hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar te rasort /user/theresa/tgen512m /user/theresa/tgen512m
17/06/09 06:38:48 INFO terasort.TeraSort: starting
17/06/09 06:38:50 INFO hdfs.DFSClient: Created token for theresa: HDFS_DELEGATION_TOKEN owner=theresa@ALEXPIERMATTEO.COM.UK, renewer=yarn, realUser=, issueDate=1497004730241, maxDate=1497609530241, sequenceNumber=1, masterKeyId=2 on 10.0.0.47:8020
17/06/09 06:38:50 INFO security.TokenCache: Got dt for hdfs://ip-10-0-0-47.eu-west-1.compute.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 10.0.0.47:8020, Ident: (token for theresa: HDFS_DELEGATION_TOKEN owner=theresa@ALEXPIERMATTEO.COM.UK, renewer=yarn, realUser=, issueDate=1497004730241, maxDate=1497609530241, sequenceNumber=1, masterKeyId=2)
17/06/09 06:38:50 INFO input.FileInputFormat: Total input paths to process : 1
Spent 343ms computing base-splits.
Spent 5ms computing TeraScheduler splits.
Computing input splits took 349ms
Sampling 10 splits of 153
Making 8 from 100000 sampled records
Computing parititions took 1193ms
Spent 1546ms computing partitions.
17/06/09 06:38:51 INFO client.RMProxy: Connecting to ResourceManager at ip-10-0-0-124.eu-west-1.compute.internal/10.0.0.124:8032
17/06/09 06:38:52 INFO mapreduce.JobSubmitter: number of splits:153
17/06/09 06:38:52 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1497004674682_0001
17/06/09 06:38:52 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 10.0.0.47:8020, Ident: (token for theresa: HDFS_DELEGATION_TOKEN owner=theresa@ALEXPIERMATTEO.COM.UK, renewer=yarn, realUser=, issueDate=1497004730241, maxDate=1497609530241, sequenceNumber=1, masterKeyId=2)
17/06/09 06:38:53 INFO impl.YarnClientImpl: Submitted application application_1497004674682_0001
17/06/09 06:38:53 INFO mapreduce.Job: The url to track the job: http://ip-10-0-0-124.eu-west-1.compute.internal:8088/proxy/application_1497004674682_0001/
17/06/09 06:38:53 INFO mapreduce.Job: Running job: job_1497004674682_0001
17/06/09 06:39:03 INFO mapreduce.Job: Job job_1497004674682_0001 running in uber mode : false

17/06/09 06:39:03 INFO mapreduce.Job:  map 0% reduce 0%
17/06/09 06:39:14 INFO mapreduce.Job:  map 2% reduce 0%
17/06/09 06:39:15 INFO mapreduce.Job:  map 3% reduce 0%
17/06/09 06:39:21 INFO mapreduce.Job:  map 6% reduce 0%
17/06/09 06:39:23 INFO mapreduce.Job:  map 7% reduce 0%
17/06/09 06:39:26 INFO mapreduce.Job:  map 8% reduce 0%
17/06/09 06:39:27 INFO mapreduce.Job:  map 9% reduce 0%
17/06/09 06:39:30 INFO mapreduce.Job:  map 10% reduce 0%
17/06/09 06:39:31 INFO mapreduce.Job:  map 12% reduce 0%
17/06/09 06:39:34 INFO mapreduce.Job:  map 13% reduce 0%
17/06/09 06:39:36 INFO mapreduce.Job:  map 14% reduce 0%
17/06/09 06:39:37 INFO mapreduce.Job:  map 15% reduce 0%
17/06/09 06:39:39 INFO mapreduce.Job:  map 16% reduce 0%
17/06/09 06:39:41 INFO mapreduce.Job:  map 17% reduce 0%
17/06/09 06:39:42 INFO mapreduce.Job:  map 18% reduce 0%
17/06/09 06:39:44 INFO mapreduce.Job:  map 19% reduce 0%
17/06/09 06:39:45 INFO mapreduce.Job:  map 20% reduce 0%
17/06/09 06:39:47 INFO mapreduce.Job:  map 21% reduce 0%
17/06/09 06:39:49 INFO mapreduce.Job:  map 22% reduce 0%
17/06/09 06:39:52 INFO mapreduce.Job:  map 24% reduce 0%
17/06/09 06:39:53 INFO mapreduce.Job:  map 25% reduce 0%
17/06/09 06:39:56 INFO mapreduce.Job:  map 26% reduce 0%
17/06/09 06:39:57 INFO mapreduce.Job:  map 27% reduce 0%
17/06/09 06:40:02 INFO mapreduce.Job:  map 28% reduce 0%
17/06/09 06:40:03 INFO mapreduce.Job:  map 29% reduce 0%
17/06/09 06:40:04 INFO mapreduce.Job:  map 30% reduce 0%
17/06/09 06:40:05 INFO mapreduce.Job:  map 31% reduce 0%
17/06/09 06:40:09 INFO mapreduce.Job:  map 33% reduce 0%
17/06/09 06:40:12 INFO mapreduce.Job:  map 34% reduce 0%
17/06/09 06:40:13 INFO mapreduce.Job:  map 35% reduce 0%
17/06/09 06:40:15 INFO mapreduce.Job:  map 37% reduce 0%
17/06/09 06:40:26 INFO mapreduce.Job:  map 38% reduce 0%
17/06/09 06:40:27 INFO mapreduce.Job:  map 39% reduce 0%
17/06/09 06:40:28 INFO mapreduce.Job:  map 41% reduce 0%
17/06/09 06:40:33 INFO mapreduce.Job:  map 42% reduce 0%
17/06/09 06:40:40 INFO mapreduce.Job:  map 43% reduce 0%
17/06/09 06:40:41 INFO mapreduce.Job:  map 44% reduce 0%
17/06/09 06:40:42 INFO mapreduce.Job:  map 46% reduce 0%
17/06/09 06:40:46 INFO mapreduce.Job:  map 47% reduce 0%
17/06/09 06:40:47 INFO mapreduce.Job:  map 48% reduce 0%
17/06/09 06:40:50 INFO mapreduce.Job:  map 49% reduce 0%
17/06/09 06:40:51 INFO mapreduce.Job:  map 50% reduce 0%
17/06/09 06:40:53 INFO mapreduce.Job:  map 52% reduce 0%
17/06/09 06:40:56 INFO mapreduce.Job:  map 53% reduce 0%
17/06/09 06:40:58 INFO mapreduce.Job:  map 54% reduce 0%
17/06/09 06:40:59 INFO mapreduce.Job:  map 55% reduce 0%
17/06/09 06:41:00 INFO mapreduce.Job:  map 56% reduce 0%
17/06/09 06:41:02 INFO mapreduce.Job:  map 57% reduce 0%
17/06/09 06:41:03 INFO mapreduce.Job:  map 58% reduce 0%
17/06/09 06:41:06 INFO mapreduce.Job:  map 59% reduce 0%
17/06/09 06:41:08 INFO mapreduce.Job:  map 60% reduce 0%
17/06/09 06:41:09 INFO mapreduce.Job:  map 61% reduce 0%
17/06/09 06:41:12 INFO mapreduce.Job:  map 62% reduce 0%
17/06/09 06:41:13 INFO mapreduce.Job:  map 64% reduce 0%
17/06/09 06:41:15 INFO mapreduce.Job:  map 65% reduce 0%
17/06/09 06:41:18 INFO mapreduce.Job:  map 66% reduce 0%
17/06/09 06:41:19 INFO mapreduce.Job:  map 67% reduce 0%
17/06/09 06:41:22 INFO mapreduce.Job:  map 68% reduce 0%
17/06/09 06:41:23 INFO mapreduce.Job:  map 69% reduce 0%
17/06/09 06:41:25 INFO mapreduce.Job:  map 70% reduce 0%
17/06/09 06:41:26 INFO mapreduce.Job:  map 71% reduce 0%
17/06/09 06:41:28 INFO mapreduce.Job:  map 72% reduce 0%
17/06/09 06:41:29 INFO mapreduce.Job:  map 73% reduce 0%
17/06/09 06:41:32 INFO mapreduce.Job:  map 74% reduce 0%
17/06/09 06:41:33 INFO mapreduce.Job:  map 75% reduce 0%
17/06/09 06:41:34 INFO mapreduce.Job:  map 76% reduce 0%
17/06/09 06:41:38 INFO mapreduce.Job:  map 78% reduce 0%
17/06/09 06:41:40 INFO mapreduce.Job:  map 80% reduce 0%
17/06/09 06:41:42 INFO mapreduce.Job:  map 81% reduce 0%
17/06/09 06:41:44 INFO mapreduce.Job:  map 82% reduce 0%
17/06/09 06:41:46 INFO mapreduce.Job:  map 83% reduce 0%
17/06/09 06:41:48 INFO mapreduce.Job:  map 84% reduce 0%
17/06/09 06:41:50 INFO mapreduce.Job:  map 85% reduce 0%
17/06/09 06:41:51 INFO mapreduce.Job:  map 86% reduce 0%
17/06/09 06:41:52 INFO mapreduce.Job:  map 88% reduce 0%
17/06/09 06:41:58 INFO mapreduce.Job:  map 89% reduce 0%
17/06/09 06:42:01 INFO mapreduce.Job:  map 90% reduce 0%
17/06/09 06:42:02 INFO mapreduce.Job:  map 91% reduce 4%
17/06/09 06:42:04 INFO mapreduce.Job:  map 91% reduce 8%
17/06/09 06:42:06 INFO mapreduce.Job:  map 92% reduce 8%
17/06/09 06:42:07 INFO mapreduce.Job:  map 92% reduce 11%
17/06/09 06:42:08 INFO mapreduce.Job:  map 93% reduce 15%
17/06/09 06:42:13 INFO mapreduce.Job:  map 95% reduce 15%
17/06/09 06:42:14 INFO mapreduce.Job:  map 96% reduce 16%
17/06/09 06:42:19 INFO mapreduce.Job:  map 97% reduce 16%
17/06/09 06:42:20 INFO mapreduce.Job:  map 99% reduce 16%
17/06/09 06:42:25 INFO mapreduce.Job:  map 100% reduce 16%
17/06/09 06:42:26 INFO mapreduce.Job:  map 100% reduce 17%
17/06/09 06:42:29 INFO mapreduce.Job:  map 100% reduce 21%
17/06/09 06:42:32 INFO mapreduce.Job:  map 100% reduce 25%
17/06/09 06:42:33 INFO mapreduce.Job:  map 100% reduce 33%
17/06/09 06:42:35 INFO mapreduce.Job:  map 100% reduce 35%
17/06/09 06:42:38 INFO mapreduce.Job:  map 100% reduce 56%
17/06/09 06:42:39 INFO mapreduce.Job:  map 100% reduce 60%
17/06/09 06:42:41 INFO mapreduce.Job:  map 100% reduce 62%
17/06/09 06:42:42 INFO mapreduce.Job:  map 100% reduce 75%
17/06/09 06:42:44 INFO mapreduce.Job:  map 100% reduce 90%
17/06/09 06:42:45 INFO mapreduce.Job:  map 100% reduce 94%
17/06/09 06:42:47 INFO mapreduce.Job:  map 100% reduce 96%
17/06/09 06:42:50 INFO mapreduce.Job:  map 100% reduce 99%
17/06/09 06:42:51 INFO mapreduce.Job:  map 100% reduce 100%
17/06/09 06:42:51 INFO mapreduce.Job: Job job_1497004674682_0001 completed successfully
17/06/09 06:42:51 INFO mapreduce.Job: Counters: 49
        File System Counters
                FILE: Number of bytes read=2271595752
                FILE: Number of bytes written=4515348542
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=5120023103
                HDFS: Number of bytes written=5120000000
                HDFS: Number of read operations=483
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=16
        Job Counters
                Launched map tasks=153
                Launched reduce tasks=8
                Data-local map tasks=153
                Total time spent by all maps in occupied slots (ms)=1134851
                Total time spent by all reduces in occupied slots (ms)=306975
                Total time spent by all map tasks (ms)=1134851
                Total time spent by all reduce tasks (ms)=306975
                Total vcore-seconds taken by all map tasks=1134851
                Total vcore-seconds taken by all reduce tasks=306975
                Total megabyte-seconds taken by all map tasks=1162087424
                Total megabyte-seconds taken by all reduce tasks=314342400
        Map-Reduce Framework
                Map input records=51200000
                Map output records=51200000
                Map output bytes=5222400000
                Map output materialized bytes=2223274240
                Input split bytes=23103
                Combine input records=0
                Combine output records=0
                Reduce input groups=51200000
                Reduce shuffle bytes=2223274240
                Reduce input records=51200000
                Reduce output records=51200000
                Spilled Records=102400000
                Shuffled Maps =1224
                Failed Shuffles=0
                Merged Map outputs=1224
                GC time elapsed (ms)=18589
                CPU time spent (ms)=757030
                Physical memory (bytes) snapshot=82080186368
                Virtual memory (bytes) snapshot=254226825216
                Total committed heap usage (bytes)=91523907584
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=5120000000
        File Output Format Counters
                Bytes Written=5120000000
17/06/09 06:42:51 INFO terasort.TeraSort: done
```