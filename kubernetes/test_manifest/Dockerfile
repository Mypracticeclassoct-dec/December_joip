FROM ubuntu:latest as machine  
RUN  apt update &&  apt install openjdk-11-jdk -y && apt install  tar gzip -y \
     && apt install git -y \
     && apt install maven -y \
     && git clone https://github.com/openmrs/openmrs-core.git 
WORKDIR /openmrs-core 
RUN mvn clean package 
RUN cd openmrs-core/webapp  
EXPOSE 8080
CMD ["openmrs/startup.sh"]