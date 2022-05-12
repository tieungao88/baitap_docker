FROM "openjdk:8-jdk-alpine"

WORKDIR /app

# COPY . .
COPY target/*.jar obo.jar

# CMD ./mvnw spring-boot:run
CMD java -jar ./obo.jar
