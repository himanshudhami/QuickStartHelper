# Start Zookeeper and Kafka command

### Download it using wget
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
