FROM eclipse-temurin:21.0.2_13-jdk-jammy AS builder
#WORKDIR /doc-app1
COPY .mvn/ .mvn
COPY mvnw pom.xml ./
RUN ./mvnw dependency:go-offline
COPY ./src ./src
#RUN ./mvnw clean install
RUN ./mvnw -Dmaven.test.skip=true clean install

FROM eclipse-temurin:21.0.2_13-jre-jammy AS final
#WORKDIR /doc-app1
COPY --from=builder target/*.war app_db.war
ENTRYPOINT ["java", "-jar", "app_db.war"]

