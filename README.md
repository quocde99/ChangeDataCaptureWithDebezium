# ChangeDataCaptureWithDebezium
Change data capture with debezium
### Introduction
Debezium is a distributed platform that converts information from your existing databases into event streams, enabling applications to detect, and immediately respond to row-level changes in the databases.
Using Debezium requires three separate services: ZooKeeper, Kafka, and the Debezium connector service.

docker compose --env-file .env up
curl -i -X POST -H "Accept:application/json" -H "Content-Type:application/json" localhost:8083/connectors/ -d '@./connect/connect.json'