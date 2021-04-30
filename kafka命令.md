```shell
# 国内

cd bin/kakfa


## 主题信息
bin/kafka-topics.sh --describe --zookeeper 172.19.33.30:2181 --topic binlog-pub-db-00-msp-org-brand

## 重置
./bin/kafka-consumer-groups.sh --bootstrap-server 172.19.33.10:9092 --group ag_ec_sync_product_qs --reset-offsets --to-latest --all-topics --execute

## 描述
./bin/kafka-consumer-groups.sh --describe --bootstrap-server 172.19.33.10:9092 --group ag_ec_sync_product_qs
./bin/kafka-consumer-groups.sh --describe --bootstrap-server 172.19.33.10:9092 --group test_ag_web_uni

## 消费消息
./bin/kafka-console-consumer.sh --bootstrap-server 172.19.33.10:9092 --topic binlog-db10-ecData-product-qs-growth --from-beginning

### 消费最多10个消息
./bin/kafka-console-consumer.sh --bootstrap-server 172.19.33.10:9092 --topic binlog-db10-ecData-product-qs-growth --max-messages 10

./bin/kafka-console-consumer.sh --bootstrap-server 172.19.33.10:9092 --topic binlog-ag-db-41-addata-advertisement --max-messages 10  --consumer-property group.id=es_sync_advertisement_uni



## 偏移
./bin/kafka-consumer-groups.sh --bootstrap-server 172.19.33.10:9092 --group common --reset-offsets --shift-by -10 --topic binlog-db40-adData-ad-heat:0 --execute

./bin/kafka-consumer-groups.sh --bootstrap-server 172.19.33.10:9092 --group test_ag_web_uni --reset-offsets --shift-by -10 --topic binlog-db40-adData-ad-heat:0 --execute

./bin/kafka-consumer-groups.sh --bootstrap-server 172.19.33.10:9092 --group test_ag_web_uni --reset-offsets --to-latest --topic binlog-db40-adData-ad-heat --execute

118560000
```

