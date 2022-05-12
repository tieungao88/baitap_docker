# Stag1 - Build
FROM arm64v8/maven:3.8.5-ibm-semeru-11-focal as BUILD
WORKDIR /app
COPY . .
RUN mvn clean package -Dmaven.test.skip=true

# # Stag2 - Docker package
# FROM openjdk:8-alpine
# COPY --from=BUILD /app/target/websocket-demo-0.0.1-SNAPSHOT.jar .
# CMD java -Djava.security.egd=file:/dev/./urandom -jar websocket-demo-0.0.1-SNAPSHOT.jar