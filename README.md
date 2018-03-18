# Kafka Memento



## Starting

### Start Zookeeper

`$KAFKA_HOME/bin/zookeeper-server-start.sh $KAFKA_HOME/config/zookeeper.properties`

### Start Kafka

`$KAFKA_HOME/bin/kafka-server-start.sh $KAFKA_HOME/config/server.properties`


**Aliases to start/stop Kafka (single local instance)**
```bash
alias zk-start="$KAFKA_HOME/bin/zookeeper-server-start.sh -daemon $KAFKA_HOME/config/zookeeper.properties"
alias zk-stop="$KAFKA_HOME/bin/zookeeper-server-stop.sh"

alias kafka-server-start="$KAFKA_HOME/bin/kafka-server-start.sh -daemon $KAFKA_HOME/config/server.properties"
alias kafka-server-stop="$KAFKA_HOME/bin/kafka-server-stop.sh"
```

## Topics API

### List topics

`$KAFKA_HOME/bin/kafka-topics.sh --list --zookeeper localhost:2181`

### Create topic

`$KAFKA_HOME/bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test`

### Topic info

`$KAFKA_HOME/bin/kafka-topics.sh --describe --zookeeper localhost:2181 --topic test`


## Topic configuration

To override default topic configuration use `--config <config.name>=<config.value>`

`$KAFKA_HOME/bin/kafka-topics.sh --zookeeper localhost:2181 --create --topic my-topic --partitions 1 --replication-factor 1 --config max.message.bytes=64000 --config flush.messages=1`

To modify topic config use config command with `--alter flag`

`$KAFKA_HOME/bin/kafka-configs.sh --zookeeper localhost:2181 --entity-type topics --entity-name my-topic --alter --add-config max.message.bytes=128000`

To remove override use config command with `--alter` and ``--delete-config

`$KAFKA_HOME/bin/kafka-configs.sh --zookeeper localhost:2181  --entity-type topics --entity-name my-topic --alter --delete-config max.message.bytes`

To check overrides set on the topic run

`$KAFKA_HOME/bin/kafka-configs.sh --zookeeper localhost:2181 --entity-type topics --entity-name my-topic --describe`

Full list of config options can be found [here](https://kafka.apache.org/documentation/#topicconfigs)


### Delete topic

`$KAFKA_HOME/bin/kafka-topics.sh --zookeeper localhost:2181 --delete --topic my-topic`

See [this](topic/README.md) for deleting multiple topics

### Purge topic
The following command will set topic retention to 1 second. Execute it and wait for 1 second then return to the old retention policy
`$KAFKA_HOME/bin/kafka-topics.sh --zookeeper localhost:2181 --alter --topic my-topic --config retention.ms=1000`

The following command will delete current retention policy and default will be used
`$KAFKA_HOME/bin/kafka-topics.sh --zookeeper localhost:2181 --alter --topic my-topic --delete-config retention.ms`



## Connect API

[File sink connector](connect-file-sink/README.md)

[File source connector](connect-file-source/README.md)

