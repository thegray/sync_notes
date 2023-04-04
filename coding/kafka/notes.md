---

Tags : 
Back Links :
Date : {{05-05-2022}} 21:07

---

# Kafka Notes

### Kafka server config
- **broker.id**
set unique each kafka server
- **log.dirs**
location of kafka data
- **num.partitions**
default number of log partitions per topic that will be used if not specified
- **zookeeper.connect**
zookeeper address

### Create topics
**Unix:**
``{kafka-dir}/bin/kafka-topics.sh --create --bootstrap-server {address}:9092 --replication-factor {n} --partitions {x} --topic {name}

**Windows:**
``{kafka-dir}/bin/windows/kafka-topics.bat --create --bootstrap-server {address}:9092 --replication-factor {n} --partitions {x} --topic {name}

- kafka-dir : location of kafka installation
- address : kafka host address
- n : number represents how many replications the data will have in across all kafka servers
- x : number represents how many partitions the topics will have
- name : represents name of the topic

### Send message to a topic
**Unix:**
``{kafka-dir}/bin/kafka-console-producer.sh --broker-list {address}:9092 --topic {name}
then, type message to send

**Windows:**
``./kafka_2.12-2.8.1/bin/windows/kafka-console-producer.bat --broker-list localhost:9092 --topic my-topic
then, type message to send

### Check Topic's Config
**Use --describe option:**
``{kafka-dir}/bin/kafka-topics.sh --bootstrap-server {address}:9092 --describe --topic {topic}

#### Alter Topic
**Use --alter option:**
- Add:
``{kafka-dir}/bin/kafka-configs.sh --bootstrap-server {address}:9092 --alter --entity-type topics --entity-name {topic_name} --add-config {config_options}
- Delete:
``{kafka-dir}/bin/kafka-configs.sh --bootstrap-server {address}:9092 --alter --entity-type topics --entity-name {topic_name} --delete-config {config_options}

##### Config Options:
- `min.insync.replicas={n}`
  Specify number of replicas needed to complete in-sync process. If the number of in-sync replicas drops below this number, Kafka stops accepting writes with -1 (or all).
- `retention.ms={x}
  The maximum time a log is retained before old log segments are discarded. This only applies if the “delete” retention policy is used.
- `retention.bytes={n}
  The maximum size a log partition can grow to before old log segments are discarded to free up space. This only applies if the “delete” retention policy is used.
- and many more...

##### Add Partition count
``{kafka-dir}/bin/kafka-topics.bat --bootstrap-server {address}:9092 --alter --topic {topic_name} --partitions {new_partition_count}

### Get Messages as Consumers
**Unix:**
``{kafka-dir}/bin/kafka-console-consumer.sh --bootstrap-server {address}:9092 --topic {name}

**Windows:**
``./kafka_2.12-2.8.1/bin/windows/kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic access_log

#### Options
``--from-beginning
-> consume all messages from start

### Behavior
#### Broadcast
- Consumers on *different groups* but on the *same topic* will receive *same messages*.

illustration:
producer ('message1') -> kafka -> consumer ["group1"], receive ('message1')
							                         -> consumer ["group2"], receive ('message1')

#### Queue
- Deliver messages **exactly once** to only one consumer. Must use *more than one partitions*, and consumers has to be in *same group*.

illustration:
producer ('msg1') -> kafka {partition 0} -> consumer 1 ["grp"], receive ('msg1')
producer ('msg2') -> kafka {partition 1} -> consumer 2 ["grp"], receive ('msg2')
producer ('msg3') -> kafka {partition 2} -> consumer 3 ["grp"], receive ('msg3')

**Cases:**
- Partitions count (*p*) is **lower** than Consumers count (*c*) in same group: excess Consumers **will not receive message**, only *p* Consumers that will receive message.
- Partitions count (p) is **same** with Consumers count (c) in same group: each Consumers will receive message **once** per p messages produced.
- Partitions count (p) is **bigger** than Consumers count (c) in same group: some Consumers will receive **more than one message** per p messages produced. Order of delivery depends on consumers' *rebalance strategy*.

### Rebalance (Consumer)
Mechanism to update message delivery to the Consumers at the event of Consumers count is changing.
https://stackoverflow.com/questions/59578378/sarama-partition-consumer-with-consumergroup

