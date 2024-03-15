FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/walsoulconsut/vprofile-project1.git
RUN cd vprofile-project1 && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="kumar"

RUN rm -rf /usr/local/tomcat/webapps/*
copy --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]