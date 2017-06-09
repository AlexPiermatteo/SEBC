```
[ec2-user@ip-10-0-0-184 ~]$ kinit jeremy
Password for jeremy@ALEXPIERMATTEO.COM.UK:
[ec2-user@ip-10-0-0-184 ~]$ hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar pi  10 100
Number of Maps  = 10
Samples per Map = 100
Wrote input for Map #0
Wrote input for Map #1
Wrote input for Map #2
Wrote input for Map #3
Wrote input for Map #4
Wrote input for Map #5
Wrote input for Map #6
Wrote input for Map #7
Wrote input for Map #8
Wrote input for Map #9
Starting Job
17/06/09 06:39:47 INFO client.RMProxy: Connecting to ResourceManager at ip-10-0-0-124.eu-west-1.compute.internal/10.0.0.124:8032
17/06/09 06:39:48 INFO hdfs.DFSClient: Created token for jeremy: HDFS_DELEGATION_TOKEN owner=jeremy@ALEXPIERMATTEO.COM.UK, renewer=yarn, realUser=, issueDate=1497004788262, maxDate=1497609588262, sequenceNumber=2, masterKeyId=2 on 10.0.0.47:8020
17/06/09 06:39:48 INFO security.TokenCache: Got dt for hdfs://ip-10-0-0-47.eu-west-1.compute.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 10.0.0.47:8020, Ident: (token for jeremy: HDFS_DELEGATION_TOKEN owner=jeremy@ALEXPIERMATTEO.COM.UK, renewer=yarn, realUser=, issueDate=1497004788262, maxDate=1497609588262, sequenceNumber=2, masterKeyId=2)
17/06/09 06:39:48 INFO input.FileInputFormat: Total input paths to process : 10
17/06/09 06:39:49 INFO mapreduce.JobSubmitter: number of splits:10
17/06/09 06:39:49 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1497004674682_0002
17/06/09 06:39:49 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 10.0.0.47:8020, Ident: (token for jeremy: HDFS_DELEGATION_TOKEN owner=jeremy@ALEXPIERMATTEO.COM.UK, renewer=yarn, realUser=, issueDate=1497004788262, maxDate=1497609588262, sequenceNumber=2, masterKeyId=2)
17/06/09 06:39:50 INFO impl.YarnClientImpl: Submitted application application_1497004674682_0002
17/06/09 06:39:50 INFO mapreduce.Job: The url to track the job: http://ip-10-0-0-124.eu-west-1.compute.internal:8088/proxy/application_1497004674682_0002/
17/06/09 06:39:50 INFO mapreduce.Job: Running job: job_1497004674682_0002
17/06/09 06:40:05 INFO mapreduce.Job: Job job_1497004674682_0002 running in uber mode : false

17/06/09 06:40:05 INFO mapreduce.Job:  map 0% reduce 0%
17/06/09 06:40:18 INFO mapreduce.Job:  map 10% reduce 0%
17/06/09 06:40:19 INFO mapreduce.Job:  map 20% reduce 0%
17/06/09 06:40:21 INFO mapreduce.Job:  map 30% reduce 0%
17/06/09 06:40:22 INFO mapreduce.Job:  map 60% reduce 0%
17/06/09 06:40:29 INFO mapreduce.Job:  map 70% reduce 0%
17/06/09 06:40:33 INFO mapreduce.Job:  map 100% reduce 0%
17/06/09 06:40:40 INFO mapreduce.Job:  map 100% reduce 100%
17/06/09 06:40:41 INFO mapreduce.Job: Job job_1497004674682_0002 completed successfully
17/06/09 06:40:41 INFO mapreduce.Job: Counters: 50
        File System Counters
                FILE: Number of bytes read=87
                FILE: Number of bytes written=1390475
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=2960
                HDFS: Number of bytes written=215
                HDFS: Number of read operations=43
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=3
        Job Counters
                Launched map tasks=10
                Launched reduce tasks=1
                Data-local map tasks=9
                Rack-local map tasks=1
                Total time spent by all maps in occupied slots (ms)=61342
                Total time spent by all reduces in occupied slots (ms)=5347
                Total time spent by all map tasks (ms)=61342
                Total time spent by all reduce tasks (ms)=5347
                Total vcore-seconds taken by all map tasks=61342
                Total vcore-seconds taken by all reduce tasks=5347
                Total megabyte-seconds taken by all map tasks=62814208
                Total megabyte-seconds taken by all reduce tasks=5475328
        Map-Reduce Framework
                Map input records=10
                Map output records=20
                Map output bytes=180
                Map output materialized bytes=340
                Input split bytes=1780
                Combine input records=0
                Combine output records=0
                Reduce input groups=2
                Reduce shuffle bytes=340
                Reduce input records=20
                Reduce output records=0
                Spilled Records=40
                Shuffled Maps =10
                Failed Shuffles=0
                Merged Map outputs=10
                GC time elapsed (ms)=591
                CPU time spent (ms)=8540
                Physical memory (bytes) snapshot=4791894016
                Virtual memory (bytes) snapshot=17334300672
                Total committed heap usage (bytes)=5396496384
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=1180
        File Output Format Counters
                Bytes Written=97
Job Finished in 54.251 seconds
Estimated value of Pi is 3.14800000000000000000
```