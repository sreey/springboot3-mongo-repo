FROM openjdk:17-jdk-slim AS build
COPY pom.xml mvnw ./
COPY .mvn .mvn
RUN ./mvnw dependency:resolve
COPY src src
RUN ./mvnw package
FROM openjdk:17-jdk-slim
WORKDIR /opt/sree
COPY --from=build target/*.jar sree-springboot-mongo.jar
ENTRYPOINT ["java", "-jar", "sree-springboot-mongo.jar"]