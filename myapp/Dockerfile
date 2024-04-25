FROM openjdk:8-jdk as nightly

RUN apt-get update
RUN apt-get install -y maven
WORKDIR /okteto/src
COPY . .

RUN mvn install -f myapp/pom.xml -DgenerateBackupPoms=false


FROM mnevadom/mavenexample:latest as app

WORKDIR /usr/local/service
COPY . .

CMD mvn install -f myapp/pom.xml -DgenerateBackupPoms=false
