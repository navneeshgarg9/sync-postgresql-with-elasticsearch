#https://raw.githubusercontent.com/debezium/debezium-examples/master/unwrap-smt/debezium-jdbc-es/Dockerfile

FROM debezium/connect:1.0
ENV KAFKA_CONNECT_JDBC_DIR=$KAFKA_CONNECT_PLUGINS_DIR/kafka-connect-jdbc \
    KAFKA_CONNECT_ES_DIR=$KAFKA_CONNECT_PLUGINS_DIR/kafka-connect-elasticsearch

COPY kafka-connect-elasticsearch connect/kafka-connect-elasticsearch
ARG POSTGRES_VERSION=42.4.3
ARG KAFKA_JDBC_VERSION=10.7.4
ARG KAFKA_CONNECT_ES_VERSION=13.0.1
ARG ELASTICSEARCH_REST_CLIENT=7.17.25

# Deploy PostgreSQL JDBC Driver
RUN cd /kafka/libs && curl -sO https://jdbc.postgresql.org/download/postgresql-$POSTGRES_VERSION.jar

# Deploy Kafka Connect JDBC
RUN mkdir $KAFKA_CONNECT_JDBC_DIR && cd $KAFKA_CONNECT_JDBC_DIR &&\
	curl -sO http://packages.confluent.io/maven/io/confluent/kafka-connect-jdbc/$KAFKA_JDBC_VERSION/kafka-connect-jdbc-$KAFKA_JDBC_VERSION.jar