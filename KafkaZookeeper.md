# Start _Zookeeper_ and _Kafka_ command

### Download  _Zookeeper_ using wget
 wget http://mirrors.ukfast.co.uk/sites/ftp.apache.org/zookeeper/stable/zookeeper-3.4.6.tar.gz
### Extract it to the folder
 tar -xvf zookeeper-3.4.6.tar.gz
### Move to the folder
 cd zookeeper-3.4.6/
### Copy sample config
 cp conf/zoo_sample.cfg conf/zoo.cfg
### Start using the command
 bin/zkServer.sh start
JMX enabled by default
Using config: /home/ubuntu/zookeeper-3.4.6/bin/../conf/zoo.cfg
Starting zookeeper ... STARTED


### Download _Kafka_ using wget
wget http://supergsego.com/apache/kafka/0.8.2.1/kafka_2.10-0.8.2.1.tgz
### Extract it to the folder
tar xvzf kafka_2.10-0.8.2.1.tgz
### Move to the folder
 cd kafka_2.10-0.8.2.1/
### Start using the command
bin/kafka-server-start.sh config/server.properties

### set JAVA8 and home variable

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer

### Set latest JAVA to be the default one 

sudo apt-get install oracle-java8-set-default

###_Restart Machine_
