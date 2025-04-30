FROM maven:3.8.5-openjdk-17 AS build

# Set the working directory to where pom.xml is
WORKDIR /app

# Copy only the backend/skillbridge folder to /app
COPY backend/skillbridge/ /app

# Build the project
RUN mvn clean package -DskipTests

FROM openjdk:17-jdk-slim

# Copy the generated JAR file from the build stage
COPY --from=build /app/target/skillbridge-0.0.1-SNAPSHOT.jar skillbridge.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "skillbridge.jar"]
