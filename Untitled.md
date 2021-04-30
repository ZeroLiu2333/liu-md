```shell
python manage.py es_sync_ad_log_aggs_oversea --max_flush_cnt=1000 --db_dsn=awsor.ag-db-11.adData --querydims="select max(ad_id) as max_ad_id,min(ad_id) as min_ad_id,ad_id as _last_id from ad_log_aggs where dt='2021-04-07' and ad_id>%s order by ad_id limit 1000" --query="select ad_id ,ad_id,format,appid,media,area,dt from ad_log_aggs where dt='2021-04-07' and ad_id>={{min_ad_id}} and ad_id<={{max_ad_id}}"


python manage.py es_sync_ad_log_aggs_oversea --max_flush_cnt=1000 --db_dsn=awsor.ag-db-11.adData --query = "select ad_id ,ad_id,format,appid,media,area,dt from ad_log_aggs where dt='2021-04-07' and ad_id>=_last_id and ad_id<=max_ad_id"

python manage.py es_sync_ad_log_aggs_oversea --max_flush_cnt=1000 --db_dsn=awsor.ag-db-11.adData --query="select ad_id ,format,appid,media,area,dt from ad_log_aggs where dt='2021-04-07' limit 1"


select max(ad_id) as max_ad_id,min(ad_id) as min_ad_id,ad_id as _last_id from ad_log_aggs where dt='2021-04-09' and ad_id>%s order by ad_id limit 1000

python manage.py ch_sync_river --sync_command=ch_sync_product_category_relation --db_dsn=alishh.ag-db-10.ecData_v3 --query="select product_id, category_id from product_category_relation where product_id > {start_id} and product_id <= {end_id}" --max_flush_cnt=100000 --querydims="select arrayJoin(range(toUInt32(ceil((49840377) / 100000)))) as round, round * 100000 as start_id, (round + 1) * 100000 as end_id " --db_dim="clickhouse://ec-00.ag.alishh:9000/mt"


export LADDR=:8002;
python manage.py es_sync_material --db_dsn="clickhouse://ec-00.ag.alishh:9000/mt" --query="select * from ad_log where ad_id>={start_id} and ad_id<={end_id} and dt={dt}" --max_flush_cnt=10000 --querydims="select arrayJoin(range(toUInt32(ceil((183542326) / 10000)))) as round, round * 10000 as start_id, (round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt"

python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select * from mt.ad_log where ad_id=185914519" --max_flush_cnt=10000

select * from mt.ad_log where ad_id=185914519

python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select * from ad_log where ad_id>={start_id} and ad_id<={end_id} and dt between '2021-04-24' and '2021-04-26'" --max_flush_cnt=10000 --querydims="select arrayJoin(range(toUInt32(ceil((189062611) / 10000)))) as round, 32758 + round * 10000 as start_id, 32758 + (round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt"

python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select ad_creative_id, ad_id, area, dt, position, platform, format, media, appid, channel from ad_log where ad_id > {start_id} and ad_id <= {end_id} and dt between '2021-04-24' and '2021-04-28' group by ad_creative_id, ad_id, area, dt, position, platform, format, media, appid, channel" --max_flush_cnt=100000 --querydims="select arrayJoin(range(toUInt32(ceil((189895351) / 10000)))) as round, round * 10000 as start_id, (round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt"

python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select ad_creative_id, ad_id, area, ut as dt, position, platform, format, media, appid, channel from (select ad_creative_id, ad_id, max(area) as area, max(dt) as ut, max(position) as position, max(platform) as platform, max(format) as format, max(media) as media, max(appid) as appid, max(channel) as channel from mt.ad_log where ad_id > {start_id} and ad_id <= {end_id} and dt between '2021-02-22' and '2021-03-22' group by ad_creative_id, ad_id)" --max_flush_cnt=1000 --querydims="select arrayJoin(range(toUInt32(ceil((189895351) / 10000)))) as round, round * 10000 as start_id, (round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "2-3月同步任务结束"},"at": {"isAtAll": true}}'

python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select * from mt.ad_log where ad_id in (171605475,172782333,179044827)"

select ad_creative_id, ad_id, area, dt, position, platform, format, media, appid, channel from ad_log where ad_id > 113990000 and ad_id <= 114000000 and dt between '2021-04-24' and '2021-04-28' group by ad_creative_id, ad_id, area, dt, position, platform, format, media, appid, channel

es_sync_material
--kafka_group=test_es_sync_ad_log
--max_flush_cnt=1000
--max_flush_interval=1


https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c


echo 1; curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "3-4月同步任务结束"},"at": {"isAtAll": true}}'

134600000

190867543





```

![image-20210416152811013](/home/youmi/.config/Typora/typora-user-images/image-20210416152811013.png)

```mysql
select count(distinct material_id) as cnt
from ad_creative
where id in
    (select distinct ad_creative_id
     from ad_creative_rel
     where ad_id in
         (select distinct ad_id
          from ad_product
          where product_id in ({{product_id}})))
  and material_id>0
```

