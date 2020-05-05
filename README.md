# Hdfs
Hdfs commands cheet sheet


### LOCAL FILE SYSTEM ###

	ls
	mkdir
	cp
	mv
	rm

### LISTING ROOT DIRECTORY ###

hadoop fs -ls /

### LISTING DEFAULT TO HOME DIRECTORY ###

hadoop fs -ls

hadoop fs -ls /user/cloudera

### CREATE A DIRECTORY IN HDFS ###

hadoop fs -mkdir hadoop-test1

### COPY FROM LOCAL FS TO HDFS ###

hadoop fs -copyFromLocal  /my_document/hdfs/commands/geologistics.csv hadoop-test1

### COPY TO HDFS TO LOCAL FS ###

hadoop fs -copyToLocal hadoop-test1/geologistics.csv .

hadoop fs -ls hadoop-test1

### CREATE 2 MORE DIRECTORIES ###

hadoop fs -mkdir hadoop-test2

hadoop fs -mkdir hadoop-test3

### COPY A FILE FROM ONE FOLDER TO ANOTHER ###

hadoop fs -cp hadoop-test1/geologistics.csv hadoop-test2

### MOVE A FILE FROM ONE FOLDER TO ANOTHER ###

hadoop fs -mv hadoop-test1/geologistics.csv hadoop-test3

### CHECK REPLICATION ###

hadoop fs -ls hadoop-test3

### CHANGE OR SET REPLICATION FACTOR ###

hadoop fs -Ddfs.replication=2 -cp hadoop-test2/geologistics.csv hadoop-test2/test_with_rep2.csv

hadoop fs -ls hadoop-test2

hadoop fs -ls hadoop-test2/test_with_rep2.csv

### CHANGING PERMISSIONS ###

hadoop fs -chmod 777 hadoop-test2/test_with_rep2.csv

sudo -u hdfs hadoop fs -chmod 777 /user/cloudera/test_with_rep2.csv

hdfs dfs -cp /tmp/sample.txt /data1

### FILE SYSTEM CHECK - REQUIRES ADMIN PREVILEGES ###

sudo -u hdfs hdfs fsck /user/cloudera/hadoop-test2 -files -blocks -locations 

sudo -u hdfs hdfs fsck /user/cloudera/hadoop-test3 -files -blocks -locations 

sudo -u hdfs hdfs fsck /user/cloudera/hadoop-test2/test_with_rep2.csv -files -blocks -locations 

vi /etc/hadoop/conf/hdfs-site.xml

/data/1/dfs/dn/current/BP-2125152513-172.31.45.216-1410037307133/current/finalized

### DELETE DIR/FILES IN HDFS ###

hadoop fs -rm hadoop-test2/test_with_rep2.csv

hadoop fs -rm -r hadoop-test1
hadoop fs -rm -r hadoop-test2
hadoop fs -rm -r hadoop-test3
