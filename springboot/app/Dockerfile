FROM maven:3.9.9-eclipse-temurin-17 AS build

WORKDIR /app

COPY pom.xml .
COPY src ./src
RUN mvn -B -DskipTests package

FROM eclipse-temurin:17-jre-alpine

VOLUME /tmp
EXPOSE 8081
COPY --from=build /app/target/demo-0.0.1.jar /app/app.jar
ENTRYPOINT ["java", "-jar", "/app/app.jar"]
