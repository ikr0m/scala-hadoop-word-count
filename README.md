Scala Hadoop Word Count Example

### Install Hadoop
https://hadoop.apache.org/docs/r3.0.3/hadoop-project-dist/hadoop-common/SingleCluster.html

Java is required to run this project.

Download Hadoop from https://www-eu.apache.org/dist/hadoop/common/current/

Extract downloaded file:

> cd ~

> tar xf hadoop-3.1.1.tar.gz

> mv hadoop-3.1.1 hadoop

Edit hadoop-env.sh file
> vi etc/hadoop/hadoop-env.sh

Change following line to set to the root of your Java installation:

  export JAVA_HOME=/usr/java/latest

For example:

  export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-1.el7_6.x86_64/jre

You can find your java installation path with following command:

> update-alternatives --display java

This will display the usage documentation for the hadoop script
> bin/hadoop

### Run word counter on hadoop

> cd /path/to/scala-hadoop-word-count-project

> sbt clean compile assembly

> cd ~/hadoop

Create directory in HDFS with the following command:

> bin/hadoop fs -mkdir input_dir

> touch sample.txt

Fill this sample.txt with some text.

Insert some data in the newly created directory in HDFS by using the following command:
> bin/hadoop fs -put sample.txt input_dir

Now submit a job to Hadoop with the following command:
> bin/hadoop jar /path/to/scala-hadoop-word-count-project/target/scala-2.12/Scala_Hadoop-assembly-1.0.jar input_dir output_dir

You can see the output by using the following command:
> bin/hadoop fs -ls output_dir/
> less output_dir/part-00000

This project based on following nice tutorial https://dzone.com/articles/hadoop-word-count-program-innbspscala