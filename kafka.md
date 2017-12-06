[TOC]
#topic
- ```
  topic3 //for test
  topic0 //nothing (created dirty data)
  rawdata //rawdata
  ```

- 创建topic

  ```
  kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 2 --partitions 1 --topic test-topic
  ```


- 查看所有topic

  ```
  kafka-topics.sh --zookeeper server18:2181 --list
  ```

- 查看创建的topic

  ```
  kafka-topics.sh --describe --zookeeper localhost:2181 --topic test-topic
  ```

- 删除topic

  ```
  kafka-topics --delete --zookeeper server18:2181 --topic topic0
  ```

  ​

- 彻底删除topic

  ```shell
  zkCli.sh
  ls /brokers/topics
  rmr /brokers/topics/[topic name] 
  //删除后要重启kafka才能生效，否则仍然能从kafka中读取数据
  ```

# produce

- 创建生产者

  ```c
  kafka-console-producer.sh  --broker-list  localhost:9092 --topic test-topic

  ```

- 从指定offset开始消费（此时必须制定partition）

  ```
  kafka-console-consumer.sh --bootstrap-server server18:9092 --offset 19 --partition 0 --topic topic0
  ```
# consume

- 创建消费者

  ```
  kafka-console-consumer.sh  --bootstrap-server localhost:9092 --topic test-topic
  ```
# group 

- 查看所有group

  ```
  kafka-consumer-groups.sh --bootstrap-server server18:9092 --list
  ```

- 查看offset

  ```
  kafka-consumer-groups.sh --bootstrap-server server18:9092 --describe --group test
  ```



#version

- 查看版本

  ```
  cd /usr/local/kafka
  find ./libs/ -name \*kafka_\* | head -1 | grep -o '\kafka[^\n]*'
  ```

# stream

- The *Kafka Streams DSL* (**Domain Specific Language**) is built on top of the Streams Processor API. It is the recommended for most users, especially beginners.

# API

## producer

```java
new ProducerRecord<String, String>(topicName, Integer.toString(i++), record)
//如果topicName不存在，会自动创建，但消费者要重启才能发现新创建的topic
```

