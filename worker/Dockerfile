FROM maven:3.5-jdk-8-alpine as builder

ADD .  .

WORKDIR .

RUN mvn dependency:resolve \
&& mvn package

FROM openjdk:8-jre-alpine

COPY --from=builder ./target/worker-jar-with-dependencies.jar .

CMD java -jar worker-jar-with-dependencies.jar
