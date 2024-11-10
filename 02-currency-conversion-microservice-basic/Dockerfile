# Use a specific Maven image for the build stage
FROM maven:3.8.2-jdk-8-slim AS build
WORKDIR /home/app
COPY pom.xml .
RUN mvn dependency:go-offline

COPY src ./src
RUN mvn clean package -DskipTests

# Use a specific OpenJDK image for the runtime stage
FROM openjdk:8-jdk-alpine
WORKDIR /home/app
VOLUME /tmp
EXPOSE 8100
COPY --from=build /home/app/target/*.jar app.jar
ENTRYPOINT ["sh", "-c", "java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /home/app/app.jar"]
