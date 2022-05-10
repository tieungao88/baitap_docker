FROM "openjdk:8-jdk-alpine"

WORKDIR /app

# COPY . .
COPY target/*.jar hello.jar

# CMD ./mvnw spring-boot:run
CMD java -jar ./hello.jar
