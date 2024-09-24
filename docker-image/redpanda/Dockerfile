FROM --platform=arm64 redpandadata/console

ENV KAFKA_BROKERS=kafka1:19091,kafka2:19092,kafka3:19093 \
    CONFIG_FILEPATH=/etc/redpanda/redpanda-console-config.yaml

COPY redpanda-console-config.yaml /etc/redpanda/redpanda-console-config.yaml
