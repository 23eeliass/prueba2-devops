

FROM maven:3.8.5-openjdk-17 AS build
WORKDIR /app
COPY . .

WORKDIR /app/Springboot-API-REST
RUN mvn clean package -DskipTests


FROM eclipse-temurin:17-jre-alpine
WORKDIR /app

COPY --from=build /app/Springboot-API-REST/target/*.jar app.jar

RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]