FROM centos

ENV PATH /usr/local/bin:$PATH

ENV LANG C.UTF-8

MAINTAINER Freeman Lo (aschenbach@gmail.com)

RUN set -eux; \
    yum update -y; \
    yum install -y wget; \
    yum install -y vim; \
    mkdir /opt/jdk14 ; \
    mkdir /opt/tomcat8 ; \
    groupadd tomcat ; \
    useradd -s /bin/nologin -g tomcat -d /opt/tomcat tomcat
    
COPY jdk-14.0.1_linux-x64_bin.tar.gz /var/tmp
COPY apache-tomcat-8.0.33.tar.gz /var/tmp

RUN set -eux; \
    tar xzf /var/tmp/jdk-14.0.1_linux-x64_bin.tar.gz -C /opt/jdk14/ ; \
    rm -f /var/tmp/jdk-14.0.1_linux-x64_bin.tar.gz ; \
    tar xzf apache-tomcat-8.0.33.tar.gz -C /opt/tomcat ; \
    rm -f /var/tmp/apache-tomcat-8.033.tar.gz ; \
    cd /var/tmp ; \
    wget https://raw.githubusercontent.com/freemanbach/dockerscripts/master/tomcat/tomcat.service ; \
    mv tomcat.service /etc/systemd/system/

RUN set -eux; \
    cd /opt/tomcat8 ; \
    chgrp -R tomcat conf ;\
    chmod g+rwx conf ; \
    chmod g+r conf/* ; \
    chown -R tomcat logs/ temp/ webapps/ work/ ; \
    chgrp -R tomcat bin ; \
    chgrp -R tomcat lib ; \
    chmod g+rwx bin ; \
    chmod g+r bin/*


# systemctl start tomcat.service
# systemctl enable tomcat.service

# Testing Service
# http://192.168.1.X:8080
    
ENTRYPOINT ["/bin/bash"]
EXPOSE 8080
