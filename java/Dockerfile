# Build

FROM maven:3.9.9-eclipse-temurin-8-alpine AS build

COPY src /usr/src/app/src

COPY pom.xml /usr/src/app

RUN mvn -f /usr/src/app/pom.xml clean package -DskipTests

# Execution

FROM eclipse-temurin:8-jre-alpine

WORKDIR /usr/src/app

LABEL maintainer "Maël KEHL"

COPY --from=build /usr/src/app/target/java-0.0.1-SNAPSHOT.jar .

CMD ["java", "-jar", "java-0.0.1-SNAPSHOT.jar"]
