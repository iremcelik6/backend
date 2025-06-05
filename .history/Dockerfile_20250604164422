# 1. aşama: Maven ile build
FROM maven:3.8.5-eclipse-temurin-17 AS build

WORKDIR /app

COPY pom.xml .
COPY src ./src

RUN mvn clean package -DskipTests

# 2. aşama: Uygulama çalıştırma
FROM eclipse-temurin:17-jdk-alpine

WORKDIR /app

COPY --from=build /app/target/moviehub-backend-1.0.0.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]

