FROM fedora:25

RUN dnf -y install java-1.8.0-openjdk python hostname procps-ng && dnf clean all -y

# set Apache Spark version
ENV SPARK_VERSION 2.1.0
ENV HADOOP_VERSION 2.7

# download and extract Apache Spark
RUN curl -O https://archive.apache.org/dist/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz

RUN tar xvfz spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz -C /opt

ENV SPARK_HOME=/opt/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}

ADD log4j.properties $SPARK_HOME/conf/log4j.properties
ADD start-common.sh start-worker.sh start-master.sh /

ENV PATH $PATH:$SPARK_HOME/bin
