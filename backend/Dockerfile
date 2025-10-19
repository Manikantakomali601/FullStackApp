FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package

FROM eclipse-temurin:17.0.16_8-jre-ubi9-minimal
WORKDIR /app
COPY --from=builder /app/target/employee-backend-1.0.0.jar .
ENTRYPOINT ["java", "-jar", "employee-backend-1.0.0.jar"]
