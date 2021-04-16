```shell
python manage.py es_sync_ad_log_aggs_oversea --max_flush_cnt=1000 --db_dsn=awsor.ag-db-11.adData --querydims="select max(ad_id) as max_ad_id,min(ad_id) as min_ad_id,ad_id as _last_id from ad_log_aggs where dt='2021-04-07' and ad_id>%s order by ad_id limit 1000" --query="select ad_id ,ad_id,format,appid,media,area,dt from ad_log_aggs where dt='2021-04-07' and ad_id>={{min_ad_id}} and ad_id<={{max_ad_id}}"


python manage.py es_sync_ad_log_aggs_oversea --max_flush_cnt=1000 --db_dsn=awsor.ag-db-11.adData --query = "select ad_id ,ad_id,format,appid,media,area,dt from ad_log_aggs where dt='2021-04-07' and ad_id>=_last_id and ad_id<=max_ad_id"

python manage.py es_sync_ad_log_aggs_oversea --max_flush_cnt=1000 --db_dsn=awsor.ag-db-11.adData --query="select ad_id ,format,appid,media,area,dt from ad_log_aggs where dt='2021-04-07' limit 1"






```

![image-20210416152811013](/home/youmi/.config/Typora/typora-user-images/image-20210416152811013.png)