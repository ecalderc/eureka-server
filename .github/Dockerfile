FROM maven:3.8.5-openjdk-17-slim AS build
VOLUME /tmp
COPY .. ./
RUN mvn clean package -DskipTests

FROM openjdk:17
VOLUME /tmp
EXPOSE 8761
COPY --from=build /target/eureka-server-0.0.1-SNAPSHOT.jar ./eureka-server.jar
ENTRYPOINT ["java","-jar","/eureka-server.jar"]