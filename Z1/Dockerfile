FROM ubuntu:18.04

RUN apt update && apt install -y\
	wget\
	curl

#PORTS
EXPOSE 3000
EXPOSE 9000

#JAVA
RUN apt-get update &&\
	apt-get upgrade -y &&\
	apt-get install -y software-properties-common &&\
	add-apt-repository ppa:openjdk-r/ppa &&\
	apt-get update &&\
	apt-get -y install openjdk-8-jdk
ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64
ENV PATH $JAVA_HOME/bin:$PATH

#SCALA
RUN wget http://scala-lang.org/files/archive/scala-2.12.12.deb &&\
	dpkg -i scala-2.12.12.deb &&\
	apt-get update &&\
	apt-get install scala

#SBT
RUN echo "deb https://dl.bintray.com/sbt/debian /" | tee -a /etc/apt/sources.list.d/sbt.list &&\
	curl -sL "https://keyserver.ubuntu.com/pks/lookup?op=get&search=0x2EE0EA64E40A89B84B2DF73499E82A75642AC823" | apt-key add &&\
	apt-get update &&\
	apt-get install -y sbt 

#NODE+NPM
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash - 
RUN apt-get install -y nodejs &&\
	npm install npm@latest -g

RUN useradd -ms /bin/bash aszczepanczyk
RUN adduser aszczepanczyk sudo
USER aszczepanczyk
WORKDIR /home/aszczepanczyk/
RUN mkdir /home/aszczepanczyk/toshare/
VOLUME ["/home/aszczepanczyk/toshare/"]
