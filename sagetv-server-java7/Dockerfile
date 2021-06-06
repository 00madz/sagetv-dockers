# BUILDING
# docker build -t 00madz/sagetv-server-java7:latest .

FROM 00madz/sagetv-base

# java 7 package is very difficult to find now so use pre-downloaded binaries from here: https://packages.debian.org/jessie/amd64/openjdk-7-jre-headless/download
# libjpeg62-turbo prereq is missing requires manual install from http://ftp.us.debian.org/debian/pool/main/libj/libjpeg-turbo/
# tzdata-java prereq is missing use alternate repo - see https://askubuntu.com/questions/795901/what-happened-to-tzdata-java-in-xenial-16-04

COPY java7/ /tmp 

RUN set -x

COPY java7/*.deb /var/cache/apt/archives/

RUN \  
  apt-add-repository ppa:justinludwig/tzdata && \
  apt-get update && \
  apt-get install -y tzdata-java java-common liblcms2-2 libnss3 libnspr4 libpcsclite1 libsctp1 && \
  dpkg -i /tmp/libjpeg62-turbo_1.5.2-2+deb10u1_amd64.deb && \
  apt install -y /tmp/openjdk-7-jre-headless_7u261-2.6.22-1~deb8u1_amd64.deb


# Define commonly used JAVA_HOME variable
ENV JAVA_HOME /usr/lib/jvm/openjdk-7-jdk 

RUN update-java-alternatives --jre-headless -s java-1.7.0-openjdk-amd64

RUN apt-get autoremove -y \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

