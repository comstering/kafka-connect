FROM --platform=arm64 confluentinc/cp-kafka-connect:7.7.0

ENV CONNECT_BOOTSTRAP_SERVERS=kafka1:19091,kafka2:19092,kafka3:19093 \
    CONNECT_REST_PORT=8083 \
    CONNECT_GROUP_ID=kafka-connect \
    CONNECT_CONFIG_STORAGE_TOPIC=_connect-configs \
    CONNECT_OFFSET_STORAGE_TOPIC=_connect-offsets \
    CONNECT_STATUS_STORAGE_TOPIC=_connect-status \
    CONNECT_KEY_CONVERTER=org.apache.kafka.connect.json.JsonConverter \
    CONNECT_VALUE_CONVERTER=org.apache.kafka.connect.json.JsonConverter \
    CONNECT_INTERNAL_KEY_CONVERTER=org.apache.kafka.connect.json.JsonConverter \
    CONNECT_INTERNAL_VALUE_CONVERTER=org.apache.kafka.connect.json.JsonConverter \
    CONNECT_REST_ADVERTISED_HOST_NAME=kafka-connect \
    CONNECT_PLUGIN_PATH=/usr/share/java/kafka,/usr/share/confluent-hub-components,/data/connect-jars,/usr/share/java/kafka/debezium-connector-mysql

ADD https://repo1.maven.org/maven2/io/debezium/debezium-connector-mysql/2.7.1.Final/debezium-connector-mysql-2.7.1.Final-plugin.tar.gz /usr/share/java/kafka/
