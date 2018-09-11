FROM openjdk:8
VOLUME /tmp
ADD https://raw.githubusercontent.com/vishnubob/wait-for-it/master/wait-for-it.sh wait-for-it.sh
RUN bash -c 'chmod +x wait-for-it.sh'
RUN wget -O /dd-java-agent.jar 'https://search.maven.org/classic/remote_content?g=com.datadoghq&a=dd-java-agent&v=LATEST'
ARG ARTIFACT_NAME
ADD ${ARTIFACT_NAME}.jar /app.jar
ENV SPRING_PROFILES_ACTIVE docker,mysql
RUN bash -c 'touch /app.jar'
ENTRYPOINT ["java", "-javaagent:/dd-java-agent.jar", "-Xms256m", "-Xmx256m", "-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
