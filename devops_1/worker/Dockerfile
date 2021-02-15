FROM maven:3.5-jdk-8-alpine as builder

COPY . /worker

WORKDIR /worker

RUN mvn dependency:resolve

RUN mvn package


FROM openjdk:8-jre-alpine

COPY --from=builder /worker/target/ /worker

WORKDIR /worker

CMD [ "java", "-jar", "worker-jar-with-dependencies.jar"]
