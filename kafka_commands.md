## KAFKA
```sh
root@da8499cb000f:/opt/kafka_2.11-0.10.1.0/bin# ./kafka-topics.sh --bootstrap-server localhost:9092 --list
```
### TOPICS
#### You can create a new Kafka topic named my-topic as follows:
```sh
./kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 3 --topic my-topic
```
#### You can verify that the my-topic topic was successfully created by listing all available topics:
```sh
./kafka-topics.sh --list --bootstrap-server localhost:9092
```
#### You can add more partitions as follows:
```sh
./kafka-topics.sh --bootstrap-server localhost:9092 --alter --topic my-topic --partitions 16
```
#### You can delete a topic named my-topic as follows:
```sh
./kafka-topics.sh --bootstrap-server localhost:9092 --delete --topic my-topic
```
#### You can find more details about a topic named cc_payments as follows:
```sh
./kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic cc_payments
```
#### You can see the under-replicated partitions for all topics as follows:
```sh
./kafka-topics.sh --bootstrap-server localhost:9092/kafka-cluster --describe --under-replicated-partitions
```
### PRODUCER
#### You can produce messages from standard input as follows:
```sh
./kafka-console-producer.sh --bootstrap-server localhost:9092 --topic my-topic
```
#### You can produce new messages from an existing file named messages.txt as follows:
```sh
./kafka-console-producer.sh --bootstrap-server localhost:9092 --topic test < messages.txt
```
### CONSUMER
#### You can begin a consumer from the beginning of the log as follows:
```sh
./kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic my-topic --from-beginning
```
#### You can consume a single message as follows:
```sh
./kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic my-topic  --max-messages 1
```
#### To list all the consumers
```sh
./kafka-consumer-groups.sh --bootstrap-server  localhost:9092 --list
```
#### To describe the consumer group
```sh
./kafka-consumer-groups.sh --bootstrap-server  localhost:9092 --describe --group usage-metrics
```
