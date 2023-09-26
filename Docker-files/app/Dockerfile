FROM openjdk:11 AS BUILDIMAGE
RUN apt update && apt install maven -y
RUN git clone --branch docker https://github.com/TsiryTi/fork-vprofile-project.git
RUN cd fork-vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE fork-vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
