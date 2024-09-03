# Kafka connect

## Dependencies
### Need plugins

[debezium-mysql-connector](https://repo1.maven.org/maven2/io/debezium/debezium-connector-mysql/2.7.1.Final/debezium-connector-mysql-2.7.1.Final-plugin.tar.gz)


## How to use
### Docker compose up
```
cd docker-infra
docker compose up -d
```

### Register connector to connect
```
curl -X POST -H "Content-Type: application/json" --data @config.json http://localhost:8083/connectors
```

### config.json
```
{
    "name": "mysql-connect",
    "config": {
        "connector.class" : "io.debezium.connector.mysql.MySqlConnector",
        "database.hostname": "hansu-sandbox-db-instance-1.crcikgmci55c.ap-northeast-2.rds.amazonaws.com",
        "database.port": "3306",
        "database.user": "kafka_connect",
        "database.password": "KafkaConnect!",
        "database.server.id": "184054",
        "topic.prefix": "fullfillment",
        "table.include.list": "kafka_connect.outbox_debezium",
        "schema.history.internal.kafka.bootstrap.servers": "kafka1:19091,kafka2:19092,kafka3:19093",
        "schema.history.internal.kafka.topic": "schemahistory.fullfillment",
        "include.schema.changes": false,
        "transforms": "outbox",
        "transforms.outbox.type": "com.eunoia.transactionoutbox.smt.EunoiaTransformation",
        "transforms.outbox.table.expand.json.payload": true
    }
}
```

## Ref
[debezium mysql docs](https://debezium.io/documentation/reference/stable/connectors/mysql.html)