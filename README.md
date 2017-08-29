# ansible-spark
Ansible playbook to spin up a basic Spark cluster using Apache Bigtop on OpenStack

NOTE: Not yet fully implemented or tested

## Dependencies

* Tested with OpenStack Ubuntu 17.04 image, Ansible 2.3.1.0, Python 2.7
* TODO: Client configuration

## Playbook

* TODO: write instructions for config & run project

# Example Map Reduce Job

curl http://www.gutenberg.org/ebooks/20417 --output outline_of_science_20417.txt
curl http://www.gutenberg.org/ebooks/5000 --output davinci_5000.txt
curl http://www.gutenberg.org/ebooks/4300 --output ulysses_4300.txt

sudo su hdfs -c "hdfs dfs -mkdir /data"
sudo su hdfs -c "hdfs dfs -mkdir /output"
sudo su hdfs -c "hdfs dfs -mkdir /tmp"
sudo su hdfs -c "hdfs dfs -chmod go+rwx /data"
sudo su hdfs -c "hdfs dfs -chmod go+rwx /output"
sudo su hdfs -c 'hdfs dfs -chmod go+rwx /tmp'

sudo su hdfs -c "hdfs dfs -copyFromLocal *.txt /data/"

sudo su yarn -c 'hadoop jar /usr/lib/hadoop-mapreduce/hadoop-mapreduce-examples-2.7.3.jar wordcount /data /output/run1'
