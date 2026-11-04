FROM amazoncorretto:8-al2

WORKDIR /app

COPY . .

RUN ./mvnw package

CMD ["java", "-jar", "./target/docker-example-1.1.3.jar"]

