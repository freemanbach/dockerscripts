# dockerscripts
location of my docker files \
-- experimenting with Spark DockerFiles \
-- if you wish to build your own spark 2.4.5 instance, you will have the following items \
mkdir $HOME/dockerimg \
-- download a version of JDK from either opensource JDK or from Oracle JDK and put it in this dockerimg folder \
-- paste either the spark version for centos or ubuntu into this dockerimg folder as well \
-- run this command in your Mac/Linux environment, but Choose one OS \
-- copy which ever one of the two flavor of spark into a file called Dockerfile
-- then run the following command
Example: docker build -t {centos||ubuntu_spark}:latest . \
docker build -t ubuntu_spark:latest . \
docker build -t centos_spark:latest .
