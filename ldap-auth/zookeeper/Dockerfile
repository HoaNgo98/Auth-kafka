FROM centos:centos8
MAINTAINER seknop@gmail.com
ENV container docker

# 1. Adding Confluent repository
RUN rpm --import https://packages.confluent.io/rpm/5.5/archive.key
COPY confluent.repo /etc/yum.repos.d/confluent.repo
RUN yum clean all

# 2. Install zookeeper and kafka
RUN yum install -y java-11-openjdk
RUN yum install -y confluent-platform-2.12

# 3. Configure Kafka and zookeeper for Kerberos 
COPY zookeeper.properties /etc/kafka/zookeeper.properties
COPY zookeeper.sasl.jaas.config /etc/kafka/zookeeper_server_jaas.conf
COPY myid /var/lib/zookeeper/myid

EXPOSE 2181 2888 3888

CMD zookeeper-server-start /etc/kafka/zookeeper.properties 
