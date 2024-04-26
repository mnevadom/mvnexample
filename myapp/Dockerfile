FROM openjdk:8-jdk as nightly

RUN apt-get update
RUN apt-get install -y maven
WORKDIR /okteto/src
COPY . .

RUN mvn install -f pom.xml -DgenerateBackupPoms=false


FROM mnevadom/mavenexample:latest as testing
EXPOSE 8080
WORKDIR /usr/local/service
COPY . .

RUN mvn install -f pom.xml -DgenerateBackupPoms=false

CMD java -jar target/*.jar

FROM mnevadom/mavenexample:latest as app
EXPOSE 8080
WORKDIR /okteto/src
COPY . .

RUN mvn install -f pom.xml -DgenerateBackupPoms=false

CMD java -jar target/*.jar
