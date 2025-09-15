FROM maven:3.9.9-eclipse-temurin-21-alpine AS build
WORKDIR /app
COPY . .
RUN ./mvnw package

FROM eclipse-temurin:21-jre-alpine
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["sh", "-c", "java $JAVA_OPTS -jar /app/app.jar"]

