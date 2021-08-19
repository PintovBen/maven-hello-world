# Build stage
FROM maven:3.8.2-openjdk-8 AS build
COPY src /usr/src/app/src
COPY pom.xml /usr/src/app
RUN mvn -f /usr/src/app/pom.xml clean package

# Run stage
FROM openjdk:8-jdk-alpine
COPY --from=build /usr/src/app/target/my-app-1.0.1.jar /usr/app/my-app-1.0.1.jar 

# Set user as non-root
RUN addgroup -g 1001 -S appuser && adduser -u 1001 -S appuser -G appuser
RUN chown -R appuser:appuser /usr
USER appuser

# Run application
ENTRYPOINT ["java","-jar","/usr/app/my-app-1.0.1.jar"]
