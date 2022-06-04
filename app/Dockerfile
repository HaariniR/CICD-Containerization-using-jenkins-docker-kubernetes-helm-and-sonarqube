FROM tomcat:8-jre11
LABEL "name"="tomcat"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
CMD ["catalina.sh","run"]
WORKDIR /usr/local/tomcat
EXPOSE 8080
VOLUME /usr/local/tomcat/webapps
