FROM bellsoft/liberica-openjdk-alpine-musl:latest
WORKDIR /opt
RUN apk add --no-cache unzip wget
RUN wget https://it-expertise.ru/pusk/ite-pusk-1.0.228.tar.gz && tar xvzf ite-pusk-1.0.228.tar.gz
WORKDIR /opt/pusk
RUN wget https://fserver.1c.ru/its/files/public/1cits/exe/java-api-8.3.11/java-api-8.3.11.zip && unzip java-api-8.3.11.zip && unzip ./java-api-8.3.11/java-api-1.6.7.zip && unzip ./java-api-1.6.7/com._1c.v8.ibis.admin-1.6.7.zip && cp ./com._1c.v8.ibis.admin-1.6.7/lib/*.jar ./lib
EXPOSE 8181
ENTRYPOINT exec java -cp ./bin/ite-pusk.jar:./lib/* -Dloader.main=com.ite.utils.pusk.Application org.springframework.boot.loader.PropertiesLauncher --spring.config.import=optional:./data/application.properties
