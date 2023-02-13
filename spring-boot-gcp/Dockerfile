FROM maven:3.8-jdk-8 AS builder
COPY pom.xml /build/
COPY src /build/src
RUN mvn -f /build/pom.xml clean package

FROM openjdk:8-jre
COPY --from=builder /build/target/spring-boot-gcp-0.0.1-SNAPSHOT.jar /app/gcpproject.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/app/gcpproject.jar"]