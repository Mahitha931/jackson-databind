# Use an official Maven image to build the application
FROM maven:3.8.6-openjdk-17-slim AS build

# Set the working directory inside the container
WORKDIR /app

# Clone the repository
RUN git clone https://github.com/Mahitha931/jackson-databind.git .

# Build the project using Maven
RUN mvn clean install -DskipTests

# Use a smaller base image for the runtime environment
FROM openjdk:17-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the built JAR file from the build stage
COPY --from=build /app/target/jackson-databind-*.jar /app/jackson-databind.jar

# Expose the port the application will run on
EXPOSE 8080

# Command to run the application
CMD ["java", "-jar", "jackson-databind.jar"]
