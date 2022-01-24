# hadoop3centos7
-------------------- Update Server Repo --------------------
sudo yum update -y

cat /etc/os-release

cat /etc/passwd
cat /etc/group
-------------------- Add User --------------------
sudo adduser hdadmin
sudo passwd hdadmin
sudo usermod -aG wheel hdadmin
-------------------- Download Wget--------------------
sudo yum install wget -y
-------------------- Centos7 ----------------- 
#imran chaush
#+918237267747

sudo yum update -y
java -version
sudo yum install java-1.8.0-openjdk -y
************************************************************
jps
-bash: jps: command not found
************************************************************

sudo yum install java-1.8.0-openjdk-devel -y
java -version

-------------------- Switch User --------------------
su - hdadmin
************************************************************
whoami
pwd
************************************************************
-------------------- Hadoop3 Download --------------------
wget --no-check-certificate  https://dlcdn.apache.org/hadoop/common/hadoop-3.3.1/hadoop-3.3.1.tar.gz
ls -lrth
tar -zxvf hadoop-3.3.1.tar.gz  #Do It In Forground
tar xzf hadoop-3.3.1.tar.gz #Do It In Background
mv hadoop-3.3.1 hdp3
ls

-------------------- bashrc file configration --------------------
sudo yum install nano -y
nano ~/.bashrc

export HADOOP_HOME=/home/hdadmin/hdp3/
export HADOOP_INSTALL=$HADOOP_HOME
export HADOOP_MAPRED_HOME=$HADOOP_HOME
export HADOOP_COMMON_HOME=$HADOOP_HOME
export HADOOP_HDFS_HOME=$HADOOP_HOME
export YARN_HOME=$HADOOP_HOME
export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
export PATH=$PATH:$HADOOP_HOME/sbin:$HADOOP_HOME/bin
export JAVA_HOME=/usr/lib/jvm/jre-1.8.0-openjdk
export PATH=$PATH:$JAVA_HOME

source ~/.bashrc
-------------------- hadoop-env.sh --------------------
nano /home/hdadmin/hdp3/etc/hadoop/hadoop-env.sh

export JAVA_HOME=/usr/lib/jvm/jre-1.8.0-openjdk
export HADOOP_OPTS=-Djava.net.preferIPV4Stack=true

-------------------- core-site.xml --------------------
nano /home/hdadmin/hdp3/etc/hadoop/core-site.xml

<property>
  <name>fs.default.name</name>
    <value>hdfs://localhost:9000</value>
</property>

-------------------- hdfs-site.xml --------------------
nano /home/hdadmin/hdp3/etc/hadoop/hdfs-site.xml

<property>
 <name>dfs.replication</name>
 <value>1</value>
</property>

<property>
  <name>dfs.name.dir</name>
    <value>file:///home/hdadmin/hdp3/hadoopdata/hdfs/namenode</value>
</property>

<property>
  <name>dfs.data.dir</name>
    <value>file:///home/hdadmin/hdp3/hadoopdata/hdfs/datanode</value>
</property>

-------------------- yarn-site.xml --------------------
nano /home/hdadmin/hdp3/etc/hadoop/yarn-site.xml

<property>
  <name>yarn.nodemanager.aux-services</name>
    <value>mapreduce_shuffle</value>
 </property>
-------------------- mapred-site.xml --------------------
nano /home/hdadmin/hdp3/etc/hadoop/mapred-site.xml

<property>
  <name>mapreduce.framework.name</name>
   <value>yarn</value>
 </property>
 
 -------------------- format namenode --------------------
 hdfs namenode -format
 
 start-all.sh
 
 jps

------------------------------------------------------------
NameNode			23.22.18.181:9870
SecondaryNameNode 	23.22.18.181:9868
DataNode 			23.22.18.181:9864

ResourceManager		23.22.18.181:8088
NodeManager			23.22.18.181:8042

NameNode
SecondaryNameNode
DataNode
ResourceManager
NodeManager
------------------------------------------------------------
