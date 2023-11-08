# Build Stage
FROM adoptopenjdk/openjdk11:alpine-slim AS builder
WORKDIR /app
COPY build.gradle .
COPY settings.gradle .
COPY gradlew .
COPY gradle/ gradle/
COPY src/ src/
RUN ./gradlew clean build -x test

# Final Stage
FROM adoptopenjdk/openjdk11:alpine-slim
WORKDIR /app
COPY --from=builder /app/build/libs/jeongspring.jar jeongspring.jar
ENTRYPOINT ["java", "-jar", "jeongspring.jar"]