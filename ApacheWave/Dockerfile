#/usr/bin/docker build -t hcvst/wiab .
FROM stackbrew/ubuntu

MAINTAINER Hans Christian v. Stockhausen, hc@vst.io

# Install
RUN apt-get update
RUN apt-get install -y git 
RUN git clone https://github.com/apache/incubator-wave.git 
RUN apt-get install -y ant 
RUN apt-get install -y fakeroot 
RUN fakeroot apt-get install -y fuse
RUN apt-get install -y openjdk-7-jdk
RUN cd incubator-wave && ant get-third-party
ENV JAVA_HOME /usr/lib/jvm/java-1.7.0-openjdk-amd64
RUN cd incubator-wave && ant compile-gwt 
RUN cd incubator-wave && ant dist-server

# Config
RUN cd incubator-wave && ant -f server-config.xml -Dwave_server_domain=ubuntu.izazi.com -Dhttp_frontend_public_address=0.0.0.0:9898
#RUN cd incubator-wave && ant -f server-config.xml -Dhttp_frontend_public_address=0.0.0.0:9898

# Run
CMD cd incubator-wave && ant run-server
