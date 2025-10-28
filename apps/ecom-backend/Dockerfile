# Use official OpenJDK image
FROM eclipse-temurin:21-jdk

# Set working directory
WORKDIR /app

# Copy Maven/Gradle build files
COPY mvnw* pom.xml ./
COPY .mvn .mvn
COPY src src

# Package the application
RUN ./mvnw clean package -DskipTests

# Expose port
EXPOSE 8080

# Run the Spring Boot app
ENTRYPOINT ["java", "-jar", "target/*.jar"]
