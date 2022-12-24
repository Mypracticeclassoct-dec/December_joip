FROM ubuntu:latest as machine  
RUN  apt update &&  apt install openjdk-11-jdk -y && apt install  tar gzip -y \
     && apt install git -y \
     && apt install maven -y && mkdir test
ADD  https://github.com/openmrs/openmrs-core.git  /test
WORKDIR /test/openmrs-core 
RUN mvn  package 
