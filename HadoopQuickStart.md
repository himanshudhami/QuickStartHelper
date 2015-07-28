#Spark installation instructions on Ubuntu
======================

Pre-requisites: Java jdk,jre


##Scala
-------------

Terminal command:
'''unix
sudo apt-get install scala
'''

OR

Ubuntu Software Center:
search for scala and install.

##Hadoop
-------------


Terminal command:
'''
cd /
cd /usr/local
'''

http://hadoop.apache.org/releases.html

get the latest binary url, 
1. use wget to get the file
'''
wget http://ftp.wayne.edu/apache/hadoop/common/hadoop-2.7.1/hadoop-2.7.1.tar.gz
'''
2. extract files 
'''
sudo tar -xzf hadoop-2.7.1.tar.gz
'''
3. move files to hadoop generic directory
'''
mv hadoop-2.7.1.tar.gz hadoop
'''
4. check hadoop
'''
hadoop/bin/hadoop version
'''
**should give**
'''
Hadoop 2.7.1
Subversion https://git-wip-us.apache.org/repos/asf/hadoop.git -r 15ecc87ccf4a0228f35af08fc56de536e6ce657a
Compiled by jenkins on 2015-06-29T06:04Z
Compiled with protoc 2.5.0
From source with checksum fc0a1a23fc1868e4d5ee7fa2b28a58a
This command was run using /home/roshan/hadoop/share/hadoop/common/hadoop-common-2.7.1.jar
'''

if it fails with JAVA_HOME not available
set the JAVA_HOME at the *hadoop-env.sh* file under $HADOOP_HOME/conf or $HADOOP_HOME/etc/hadoop folder

5. set ssh
install openssh if not already available.
'''
sudo apt-get install openssh-server
'''
execute ssh at terminal to confirm.

setup ssh for hadoop
'''
ssh-keygen -t rsa -P ""
cat $HOME/.ssh/id_rsa.pub >> $HOME/.ssh/authorized_keys 
'''
6. configure hadoop
Once done, the next step is to configure Hadoop. All Hadoop configurations files are under $HADOOP_HOME/conf or $HADOOP_HOME/etc/hadoop folder. Hadoop configuration requires following three file configurations. A template file with the same name might be available.
1. *hadoop-env.sh* - In this file we need to set the JAVA_HOME. This file already contains place holder for JAVA_HOME which is commented out so you just need to search for that uncomment the code.

2. *core-site.xml* - This requires configurations about the HDFS. Here we need to configure minimum two configurations viz. hadoop.tmp.dir and fs.default.name as shown below
'''
<configuration>
<property>
</name>hadoop.tmp.dir</name>
<value>/app/hadoop/tmp</value>
<description>A base for other temporary directories.</description>
</property>
<property>
<name>fs.default.name</name>
<value>hdfs://localhost:54310</value>
<description>The name of the default file system. A URI whose scheme and authority determine the FileSystem implementation. The uri's scheme determines the config property (fs.SCHEME.impl) naming the FileSystem implementation class. The uri's authority is used to determine the host, port, etc. for a filesystem.
</description>
</property>
</configuration>
'''
3. *mapred-site.xml* - This file is specific to Job Tracker settings. We should set this file as follows.
'''
<configuration>
<property>
<name>
mapred.job.tracker</name>
<value>localhost:54311</value>
<description>
The host and port that the MapReduce job tracker runs at. If "local", then jobs are run in-process as a single map and reduce task.
</description>
</property>
</configuration>
'''
4. Now whatever folder we have specified in step 6.2, we should manually create that folder and give full rights to that folder. 
'''
cd ~
sudo mkdir -p /app/hadoop/tmp/
sudo chmod -R 777 /app
'''

7. add environment variables
Now it's time to export environment variables and add the entries in ~/.bashrc file. ~/.bashrc file is the script every time a user logs in. bashrc file is located under home directory of the user. To do so we have to do following. 
'''
sudo gedit ~/.bashrc
add the following lines
export JAVA_HOME=**java jre dir**
export HADOOP_HOME=/usr/local/hadoop
export PATH=$PATH:$JAVA_HOME/bin:$HADOOP_HOME/bin
'''
save and start a new terminal

8. create folder structure
'''
hadoop namenode -format 
'''
9. give permissions to folder
'''
sudo chown -R **user_name** /usr/local/hadoop
'''

10. start hadoop
'''
cd /usr/local/Hadoop/bin/
./start-all.sh
'''

##Spark
-------------
1. Get Apache Spark without hadoop Url
http://spark.apache.org/downloads.html
'''
cd /
cd /usr/local/
wget http://supergsego.com/apache/spark/spark-1.4.1/spark-1.4.1-bin-without-hadoop.tgz
'''
2. extract and move to folder
'''
wget http://supergsego.com/apache/spark/spark-1.4.1/spark-1.4.1-bin-without-hadoop.tgz
tar -xzf spark-1.4.1-bin-without-hadoop spark.tgz
sudo mv spark-1.4.1-bin-without-hadoop spark
'''
3. set environment variables
'''
sudo gedit ~/.bashrc
add the following lines
export JAVA_HOME=**java jre dir**
export SPARK_HOME=/usr/local/spark
export HADOOP_HOME=/usr/local/hadoop
export PATH=$PATH:$JAVA_HOME/bin:$HADOOP_HOME/bin:$SPARK_HOME/bin
'''


Resources
-------------

Spark install tutorial - [http://hadooptutorials.co.in/tutorials/spark/install-apache-spark-on-ubuntu.html](http://hadooptutorials.co.in/tutorials/spark/install-apache-spark-on-ubuntu.html)

Hadoop install tutorial - [http://hadooptutorials.co.in/tutorials/hadoop/install-hadoop-on-ubuntu.html](http://hadooptutorials.co.in/tutorials/hadoop/install-hadoop-on-ubuntu.html)

Scala install - [http://www.scala-lang.org/download/install.html](http://www.scala-lang.org/download/install.html)
