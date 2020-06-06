FROM centos

ENV PATH /usr/local/bin:/bin:$PATH

ENV LANG C.UTF-8

MAINTAINER Freeman Lo (aschenbach@gmail.com)

RUN set -eux; \
    yum update -y; \
    yum install -y vim; \
    mkdir /opt/jdk14
    
COPY jdk-14.0.1_linux-x64_bin.tar.gz /var/tmp

RUN set -eux; \
    cd; \
    curl https://gist.githubusercontent.com/marioBonales/1637696/raw/93a33aa5f1893f46773483250214f8b8b496a270/.bashrc -o /root/.bashrc ; \
    tar xzf /var/tmp/jdk-14.0.1_linux-x64_bin.tar.gz -C /var/tmp; \
    # gunzip -c /var/tmp/jdk-14.0.1_linux-x64_bin.tar.gz | tar xf - ; \
    cp -r /var/tmp/jdk-14.0.1/ /opt/jdk14/ ; \
    rm -fr /var/tmp/jdk-14.0.1 ; \
    rm -f /var/tmp/jdk-14.0.1_linux-x64_bin.tar.gz ;\
    cd; \
    touch /root/.bash_profile ; \
    echo '[ -z "$PS1" ] && return' >> /root/.bash_profile; \
    echo $'\n\n' >> .bash_profile; \
    echo 'if [ -f /etc/bashrc ]; then' >> /root/.bash_profile; \
    echo ' . /etc/bashrc' >> /root/.bash_profile; \
    echo 'fi' >> /root/.bash_profile; \
    echo $'\n\n' >> /root/.bash_profile; \
    echo 'JAVA_HOME=/opt/jdk14' >> /root/.bash_profile; \
    echo 'export JAVA_HOME' >> /root/.bash_profile; \
    echo 'export PATH=$PATH:$JAVA_HOME/bin' >> /root/.bash_profile

RUN . /root/.bash_profile

ENTRYPOINT ["/bin/bash"]
