FROM centos

ENV PATH /usr/local/bin:$PATH

ENV LANG C.UTF-8

MAINTAINER Freeman Lo (aschenbach@gmail.com)

RUN set -eux; \
    yum update -y; \
    yum install -y wget; \
    yum install -y vim; \
    mkdir /opt/jdk14
    
COPY jdk-14.0.1_linux-x64_bin.tar.gz /var/tmp
COPY spark-2.4.5-bin-hadoop2.7.tgz /var/tmp

RUN set -eux; \
    tar xzf /var/tmp/jdk-14.0.1_linux-x64_bin.tar.gz -C /var/tmp; \
    cp -r /var/tmp/jdk-14.0.1/ /opt/jdk14/; \
    rm -fr /var/tmp/jdk-14.0.1; \
    rm -f /var/tmp/jdk-14.0.1_linux-x64_bin.tar.gz;\
    mkdir /usr/local/spark27; \
    # Forcing this to be a local file to be extracted rather than coming from internet over http
    # wget http://www.trieuvan.com/apache/spark/spark-2.4.5/spark-2.4.5-bin-hadoop2.7.tgz -P /var/tmp/; \
    tar xzf /var/tmp/spark-2.4.5-bin-hadoop2.7.tgz -C /var/tmp; \
    cp -r /var/tmp/spark-2.4.5-bin-hadoop2.7/ /usr/local/spark2.7/;\
    rm -fr /var/tmp/spark-2.4.5-bin-hadoop2.7/; \
    rm -f /var/tmp/spark-2.4.5-bin-hadoop2.7.tgz;\
    cd; \
    echo 'JAVA_HOME=/opt/jdk14_1' >> ~/.bash_profile; \
    echo 'export JAVA_HOME' >> ~/.bash_profile; \
    echo 'export PATH=$PATH:$JAVA_HOME/bin' >> ~/.bash_profile

RUN . ~/.bash_profile
    
ENTRYPOINT ["/usr/local/spark27/sbin/start-master.sh"]
EXPOSE 8080
