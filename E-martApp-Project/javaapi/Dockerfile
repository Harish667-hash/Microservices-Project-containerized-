FROM openjdk:8 AS JAVA_API_ARTIFACT
WORKDIR /usr/src/app/
RUN apt update && apt install maven -y
COPY ./ /usr/src/app/
RUN mvn install -DskipTests

# using base image
FROM openjdk:8

#copying build output and placing on container dir
WORKDIR /usr/src/app/
COPY --from=JAVA_API_ARTIFACT /usr/src/app/target/book-work-0.0.1-SNAPSHOT.jar ./book-work-0.0.1.jar

EXPOSE 9000
ENTRYPOINT ["java","-jar","book-work-0.0.1.jar"]
# Test
