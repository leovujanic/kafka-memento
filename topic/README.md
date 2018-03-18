# Topics

Automate deletion of multiple topics (e.g. for development purposes):

```bash
#!/usr/bin/env bash

TOPICS=(
    "my-topic-1"
    "my-topic-2"
    "my-topic-3"
)

deleteTopic() {
    $KAFKA_HOME/bin/kafka-topics.sh --zookeeper localhost:2181 --delete --topic $1;
}

for item in ${TOPICS[*]}
do
    deleteTopic $item;
done
```


