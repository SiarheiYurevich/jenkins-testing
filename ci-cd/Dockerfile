FROM maven:3.9.2 AS builder
WORKDIR /app
COPY . /app/.
RUN mvn -f /app/pom.xml clean package -DMaven.test.skip=true

FROM amazoncorretto:17.0.9
WORKDIR /app
COPY --from=builder app/target/*.jar app/app.jar
EXPOSE 8089
ENTRYPOINT ["java", "-jar", "app/app.jar"]