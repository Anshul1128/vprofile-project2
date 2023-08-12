FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/Anshul1128/vprofile-project2.git
RUN cd vprofile-project2 && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL "Project"="Vprofile"  
LABEL "Author"="Anshul"
RUN rm -rf /user/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project2/target/vprofile-v2.war /user/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]