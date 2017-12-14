[TOC]
#topic
  ```
topic3 //for test
topic0 //nothing (created dirty data)
rawdata //rawdata
  ```

## 创建topic

  ```
kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 2 --partitions 1 --topic test-topic
  ```


## 查看所有topic

  ```
kafka-topics.sh --zookeeper server18:2181 --list
  ```

## 查看创建的topic

  ```
kafka-topics.sh --describe --zookeeper localhost:2181 --topic test-topic
  ```

## 查看topic的offset值

  ```
kafka-run-class.sh kafka.tools.GetOffsetShell --topic rawData  --time -1 --broker-list server18:9092 --partitions 0
//time为-1时表示最大值，time为-2时表示最小值
  ```

##删除topic

```
kafka-topics --delete --zookeeper server18:2181 --topic topic0
```
##彻底删除topic方法0

```
bin/kafka-run-class.sh kafka.admin.DeleteTopicCommand --zookeeper node01:2181 --topic t_cdr
// 删除topic，慎用，只会删除zookeeper中的元数据，消息文件须手动删除
```

##彻底删除topic方法1

```shell
zkCli.sh
ls /brokers/topics
rmr /brokers/topics/[topic name] 
//删除后要重启kafka才能生效，否则仍然能从kafka中读取数据
```
# produce

##创建生产者

```c
kafka-console-producer.sh  --broker-list  localhost:9092 --topic test-topic

```
##从指定offset开始消费

```
kafka-console-consumer.sh --bootstrap-server server18:9092 --offset 19 --partition 0 --topic topic0
//此时必须制定partition
```
# consume

##创建消费者

```
kafka-console-consumer.sh  --bootstrap-server localhost:9092 --topic test-topic
```
# group 

##查看所有group

```
kafka-consumer-groups.sh --bootstrap-server server18:9092 --list
```
##查看offset

```
kafka-consumer-groups.sh --bootstrap-server server18:9092 --describe --group test
```

#version

##查看版本

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

# server.properties

```
log.retention.hours = 168
//kafka中消息保存的时间，默认为7天，这就是经常出现7天后无法消费的原因。
```

