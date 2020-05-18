# FROM openjdk
# ADD target/account-service.jar account-service.jar
# ENTRYPOINT ["java", "-jar", "account-service.jar"]
# EXPOSE 2222
FROM maven:3.5.2-jdk-8-alpine AS MAVEN_BUILD
COPY pom.xml /build/
COPY src /build/src/
WORKDIR /build/
RUN mvn package
FROM openjdk:8-jre-alpine
WORKDIR /app
COPY --from=MAVEN_BUILD /build/target/account-service-1.0-SNAPSHOT.jar /app/
ENTRYPOINT ["java", "-jar", "account-service-1.0-SNAPSHOT.jar"]
