# Base con Java
FROM eclipse-temurin:17-jre


ENV KAFKA_VERSION=3.7.0
ENV SCALA_VERSION=2.13
ENV KAFKA_HOME=/opt/kafka_${SCALA_VERSION}-${KAFKA_VERSION}
ENV PATH="$KAFKA_HOME/bin:$PATH"

RUN apt-get update && apt-get install -y curl unzip && rm -rf /var/lib/apt/lists/*

RUN curl -fSL "https://archive.apache.org/dist/kafka/3.7.0/kafka_2.13-3.7.0.tgz" -o /tmp/kafka.tgz && \
    tar -xzf /tmp/kafka.tgz -C /opt && \
    rm /tmp/kafka.tgz

RUN mkdir -p /usr/share/kafka/plugins
ENV KAFKA_CONNECT_PLUGINS=/usr/share/kafka/plugins


RUN apt-get update && apt-get install -y curl unzip

COPY connect-standalone.properties $KAFKA_HOME/config/connect-standalone.properties

EXPOSE 8083

ENTRYPOINT ["connect-standalone.sh", "/opt/kafka_2.13-3.7.0/config/connect-standalone.properties"]
