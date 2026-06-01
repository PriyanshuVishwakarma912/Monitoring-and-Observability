# Getting the base image for java
# FROM eclipse-temurin:21-jdk-jammy
FROM maven:3.9-eclipse-temurin-21

# code in a working directory
WORKDIR /app

# copy all the code files
COPY . .

# Install the libraries witn maven

# RUN chmod +x mvnw && ./mvnw clean package -DskipTests
RUN mvn clean package -DskipTests
# RUN ls -la
# Expose the port
RUN cp target/*.jar app.jar
EXPOSE 8080

CMD ["java", "-jar", "app.jar"]

# ENTRYPOINT ["sh", "-c", "java -jar target/*.jar"]
