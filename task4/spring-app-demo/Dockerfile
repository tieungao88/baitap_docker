# Stag1 - Build
FROM maven:ibmjava-alpine as BUILD
WORKDIR /app
COPY . .
RUN ./mvnw clean package

# Stag2 - Docker package
FROM openjdk:8-alpine
COPY --from=BUILD /app/target/websocket-demo-0.0.1-SNAPSHOT.jar .
CMD java -Djava.security.egd=file:/dev/./urandom -jar websocket-demo-0.0.1-SNAPSHOT.jar
