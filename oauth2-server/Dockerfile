FROM openjdk:11-jdk as build
WORKDIR /workspace/app
COPY gradlew ./
COPY gradle ./gradle
COPY build.gradle.kts ./
COPY src ./src
RUN ./gradlew build

FROM openjdk:11-jdk
WORKDIR /workspace/app
COPY --from=build /workspace/app/build/libs/*.jar ./app.jar
EXPOSE 8080
ENTRYPOINT ["sh", "-c", "java ${JAVA_OPTS} -jar /workspace/app/app.jar ${0} ${@}"]
