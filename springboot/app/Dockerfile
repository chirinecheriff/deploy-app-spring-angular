# --- Stage 1: build the jar ---
FROM maven:3.9-eclipse-temurin-11 AS build
WORKDIR /app
COPY . .
RUN mvn -DskipTests package

# --- Stage 2: run the app ---
FROM eclipse-temurin:11
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8081
ENTRYPOINT ["java","-jar","app.jar"]