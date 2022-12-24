FROM ubuntu:latest as machine  
RUN  apt update &&  apt install openjdk-11-jdk -y && apt install  tar gzip -y \
     && apt install git -y \
     && apt install maven -y \
     && git clone https://github.com/openmrs/openmrs-core.git 
WORKDIR /openmrs-core 
RUN mvn clean package 
RUN mkdir /opt/tomcat
ADD https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.84/bin/apache-tomcat-8.5.84.tar.gz /opt/tomcat
RUN cd /opt/tomcat \
    && tar xzvf apache-tomcat-8.5.84.tar.gz && --from=machine /openmrs-core/webapp/target/openmrs.war  /opt/tomcat/apache-tomcat-8.5.84/webapps 
EXPOSE 8080 
CMD [ "/opt/tomcat/apache-tomcat-8.5.84/bin", "catalina.sh", "run" ]
