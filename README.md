# ChangeDataCaptureWithDebezium
Change data capture with debezium
### Introduction
Debezium is a distributed platform that converts information from your existing databases into event streams, enabling applications to detect, and immediately respond to row-level changes in the databases.
Using Debezium requires three separate services: ZooKeeper, Kafka, and the Debezium connector service.
### start docker compose 
docker compose --env-file .env up

### connector from kafka connect to debezium connector
curl -i -X POST -H "Accept:application/json" -H "Content-Type:application/json" localhost:8083/connectors/ -d '@./connect/connect.json'

curl -i -X POST -H "Accept:application/json" -H "Content-Type:application/json" localhost:8083/connectors/ -d '@./connect/connect_arvo.json'

### schema registry data chage 
curl -X GET http://localhost:8081/subjects/dbserver1.inventory.customers-value/versions/1

schema registry api:
https://docs.confluent.io/platform/current/schema-registry/develop/api.html

Document flink debezium:
https://nightlies.apache.org/flink/flink-docs-master/docs/connectors/table/formats/debezium/

/kafka/bin/kafka-console-consumer.sh \
      --bootstrap-server kafka:9092 \
      --property print.key=true \
      --formatter io.confluent.kafka.formatter.AvroMessageFormatter \
      --property schema.registry.url=http://schema-registry:8081 \
      --topic dbserver1.inventory.addresses