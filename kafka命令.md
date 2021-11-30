```shell
# 国内：
ssh -p36000 kafka-00.ag.alishh

#海外：
ssh -p36000 kafka-00.ag.awsor

# 国内

cd bin/kakfa


## 主题信息
bin/kafka-topics.sh --describe --zookeeper 172.19.33.30:2181 --topic binlog-pub-db-00-msp-org-brand

## 重置
./bin/kafka-consumer-groups.sh --bootstrap-server 172.19.33.10:9092 --group ag_ec_sync_product_qs --reset-offsets --to-latest --all-topics --execute

## 描述
./bin/kafka-consumer-groups.sh --describe --bootstrap-server 172.19.33.10:9092 --group ag_ec_sync_product_qs
./bin/kafka-consumer-groups.sh --describe --bootstrap-server 172.19.33.10:9092 --group test_ag_web_uni

## 查看消费组
kafka-consumer-groups.sh --bootstrap-server {kafka连接地址} --list

## 删除消费组
./bin/kafka-consumer-groups.sh --bootstrap-server {kafka连接地址} --delete --group {消费组}


## 消费消息
./bin/kafka-console-consumer.sh --bootstrap-server 172.19.33.10:9092 --topic binlog-db10-ecData-product-qs-growth --from-beginning

### 消费最多10个消息
./bin/kafka-console-consumer.sh --bootstrap-server 172.19.33.10:9092 --topic binlog-db10-ecData-product-qs-growth --max-messages 10

./bin/kafka-console-consumer.sh --bootstrap-server 172.19.33.10:9092 --topic binlog-ag-db-41-addata-advertisement --max-messages 10  --consumer-property group.id=es_sync_advertisement_uni

./bin/kafka-console-consumer.sh --bootstrap-server 172.20.20.50:9092 --topic binlog-ag-db-11-addata-ad-log-aggs --max-messages 1



## 偏移
./bin/kafka-consumer-groups.sh --bootstrap-server 172.19.33.10:9092 --group common --reset-offsets --shift-by -10 --topic binlog-db40-adData-ad-heat:0 --execute

./bin/kafka-consumer-groups.sh --bootstrap-server 172.19.33.10:9092 --group test_ag_web_uni --reset-offsets --shift-by -10 --topic binlog-db40-adData-ad-heat:0 --execute

./bin/kafka-consumer-groups.sh --bootstrap-server 172.19.33.10:9092 --group test_ag_web_uni --reset-offsets --to-latest --topic binlog-db40-adData-ad-heat --execute

./bin/kafka-consumer-groups.sh --bootstrap-server 172.20.20.50:9092 --group test-sync-ad-heat-overseas --reset-offsets --shift-by -10 --topic binlog-ag-db-11-addata-ad-heat:0 --execute

./bin/kafka-console-consumer.sh --bootstrap-server 172.20.20.50:9092 --topic binlog-ag-db-11-addata-ad-log-aggs  --max-messages 1  --consumer-property group.id=dj-ad-aggs-sync-oversea

./bin/kafka-consumer-groups.sh --bootstrap-server 172.20.20.50:9092 --group dj-ad-aggs-sync-oversea --reset-offsets --to-latest --topic binlog-ag-db-11-addata-ad-log-aggs --execute

./bin/kafka-console-consumer.sh --bootstrap-server 172.20.20.50:9092 --topic binlog-ag-db-11-addata-ad-log-aggs --from-beginning

### 查看kafka各个组的偏移量
./bin/kafka-run-class.sh --bootstrap-server 172.20.20.50:9092 -group test-sync-ad-heat-overseas

./bin/kafka-consumer-groups.sh --describe --bootstrap-server 172.20.20.50:9092 --group test-sync-ad-heat-overseas

./bin/kafka-consumer-groups.sh --bootstrap-server 172.20.20.50:9092 --group test-sync-ad-heat-overseas --reset-offsets --shift-by -1000000 --topic binlog-ag-db-11-addata-ad-heat:0 --execute


14137239132

145987062	
```

