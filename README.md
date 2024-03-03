## Here are simplified commands for users to run Kafka locally, along with a brief description:

### Start Zookeeper Container
Start Zookeeper container and expose port 2181:
```bash
docker run -p 2181:2181 zookeeper
```

### Start Kafka Container
Start Kafka container, expose port 9092, and set up environment variables:
```bash
docker run -p 9092:9092 \
-e KAFKA_ZOOKEEPER_CONNECT=<PRIVATE_IP>:2181 \
-e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://<PRIVATE_IP>:9092 \
-e KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR=1 \
confluentinc/cp-kafka
```
Replace `<PRIVATE_IP>` with the private IP address of your machine.

### Create Kafka Topic
Create a Kafka topic named "rider-updates" with 2 partitions:
```bash
node admin.js
```

### Run Consumer
Run a Kafka consumer:
```bash
node consumer.js <GROUP_NAME>
```
Replace `<GROUP_NAME>` with the name of the consumer group.

### Run Producer
Run a Kafka producer:
```bash
node producer.js
```
Enter rider name and location as prompted, e.g., `tony south`, `tony north`.
