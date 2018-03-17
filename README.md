# Kafka Memento



## Starting

Start Zookeeper:

`$KAFKA_HOME/bin/zookeeper-server-start.sh $KAFKA_HOME/config/zookeeper.properties`

Start Kafka:

`$KAFKA_HOME/bin/kafka-server-start.sh $KAFKA_HOME/config/server.properties`


**Aliases to start/stop Kafka (single local instance)**
```bash
alias zk-start="$KAFKA_HOME/bin/zookeeper-server-start.sh -daemon $KAFKA_HOME/config/zookeeper.properties"
alias zk-stop="$KAFKA_HOME/bin/zookeeper-server-stop.sh"

alias kafka-server-start="$KAFKA_HOME/bin/kafka-server-start.sh -daemon $KAFKA_HOME/config/server.properties"
alias kafka-server-stop="$KAFKA_HOME/bin/kafka-server-stop.sh"
```



## Connect API

[File sink connector](connect-file-sink/README.md)

[File source connector](connect-file-source/README.md)

