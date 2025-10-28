# Step 1: Use Maven with Java 21 to build the app 
FROM maven:3.9.5-eclipse-temurin-21 AS builder
WORKDIR /app

COPY pom.xml .
RUN mvn dependency:go-offline

COPY src ./src
RUN mvn clean package -DskipTests

# Step 2: Use lightweight JDK 21 image to run
FROM eclipse-temurin:21-jdk-jammy
WORKDIR /app

COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]

