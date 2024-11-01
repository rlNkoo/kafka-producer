# Kafka Producer Application

This project contains a simple producer application for Apache Kafka, demonstrating how to set up and run Kafka locally. Apache Kafka is a distributed streaming platform that allows you to publish, subscribe to, store, and process data in real time.

## Introduction
Follow these instructions to set up Apache Kafka and run a producer and consumer application in your local environment.

## Starting Zookeeper and Kafka
Apache Kafka relies on Zookeeper to manage brokers and handle distributed synchronization. Start the Zookeeper server and Kafka server in separate terminal windows.

### 1. Start Zookeeper Server
Run the following command to start the Zookeeper server:
sh bin/zookeeper-server-start.sh config/zookeeper.properties

### 2. Start Kafka Server / Broker
In another terminal window, start the Kafka broker (server) with:
sh bin/kafka-server-start.sh config/server.properties

### 3. Create a Topic
To create a new Kafka topic, use the following command. Replace NewTopic with your desired topic name. This topic will have 3 partitions and a replication factor of 1:
sh bin/kafka-topics.sh --bootstrap-server localhost:9092 --create --topic NewTopic --partitions 3 --replication-factor 1

### 4. List All Topic Names
To view all existing Kafka topics, use:
sh bin/kafka-topics.sh --bootstrap-server localhost:9092 --list

### 5. Describe Topics
To get details about a specific topic (e.g., NewTopic), use:
sh bin/kafka-topics.sh --bootstrap-server localhost:9092 --describe --topic NewTopic

### 6. Produce a Message
You can produce messages to the NewTopic topic by using the console producer. After running this command, type messages and press Enter to send them:
sh bin/kafka-console-producer.sh --broker-list localhost:9092 --topic NewTopic

### 7. Consume Messages
To consume messages from the NewTopic topic, use the console consumer. This command will show messages from the beginning of the topic:
sh bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic NewTopic --from-beginning
