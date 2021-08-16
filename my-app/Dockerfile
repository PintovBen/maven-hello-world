FROM openjdk:8-jdk-alpine
COPY /target/my-app-1.0.0.jar /usr/app/my-app-1.0.0.jar 

# Set user as non-root
RUN addgroup -g 1001 -S appuser && adduser -u 1001 -S appuser -G appuser
RUN chown -R appuser:appuser /usr
USER appuser

# Run application
ENTRYPOINT ["java","-jar","/usr/app/my-app-1.0.0.jar"]