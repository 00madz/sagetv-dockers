# BUILDING
# docker build -t stuckless/sagetv-server-java8:latest .

FROM 00madz/sagetv-base:latest

RUN set -x

RUN mkdir -p /usr/lib/jvm && \
    cd /usr/lib/jvm/ && \
    wget https://download.java.net/openjdk/jdk8u41/ri/openjdk-8u41-b04-linux-x64-14_jan_2020.tar.gz && \
    tar -zxvf openjdk-8u41-b04-linux-x64-14_jan_2020.tar.gz && \
    rm -f openjdk-8u41-b04-linux-x64-14_jan_2020.tar.gz

# Define commonly used JAVA_HOME variable
ENV JAVA_HOME=/usr/lib/jvm/java-se-8u41-ri \
    PATH=/usr/lib/jvm/java-se-8u41-ri/bin:${PATH}

# Setup the /usr/bin/java alias (used by OpenDCT among other things)
RUN update-alternatives --install /usr/bin/java java /usr/lib/jvm/java-se-8u41-ri/bin/java 1
