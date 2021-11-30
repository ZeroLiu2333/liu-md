### 重建索引
1. 在已有的索引上定个别名，并指向别名
2. 建个新索引，并写入数据
3. 将别名指向新索引，取消旧索引对别名的指向

##### 查询索引别名

````elm
GET material/_alias

{
  "material_v1": {
    "aliases": {
      "material": {}
    }
  }
}
````

##### 创建新索引
````elm
PUT material_v2
{
  "mappings": {
      "data": {
        "dynamic": "strict",
        "_size": {
          "enabled": true
        },
        "properties": {
          "ads": {
            "type": "integer",
            "index": false
          },
          "seller_company_name": {
            "type": "text",
            "term_vector": "with_positions_offsets",
            "fields": {
              "raw": {
                "type": "text",
        }
      }
    }
}

````
##### 同步数据到新索引
同步旧数据到新索引



##### - 注意：重跑旧数据到新索引前要先把同步脚本的任务给停调，不然会出现数据丢失问题。

跑完数据后重启同步脚本任务即可

````shell
ssh alishh-ag-ma 

ssh ag-wb-01

/home/ymserver/bin/dump_data/node_modules/.bin/elasticdump --type=data --concurrency=8 --searchBody='{"query": {"bool": {"filter": {"range": {"min_dt": {"gte": "2019-09-06"}}}}}}' --input=http://elastic:nZ3gpnW47PGp@es-cn-v0h0ly9io00071cps.elasticsearch.aliyuncs.com:9200/landpage --output=http://elastic:nZ3gpnW47PGp@es-cn-v0h0ly9io00071cps.elasticsearch.aliyuncs.com:9200/landpage_v1 --limit=3000
--input 源数据
--output 目的数据

/home/ymserver/bin/dump_data/node_modules/.bin/elasticdump --type=data --concurrency=8 --searchBody='{"query": {"bool": {"filter": {"range": {"min_dt": {"gte": "2019-09-06"}}}}}}' --input=http://elastic:nZ3gpnW47PGp@es-cn-v0h0ly9io00071cps.elasticsearch.aliyuncs.com:9200/landpage --output=http://ag-pgm:l0ng-r4nd0m@es-cn-7pp29nzdq001dccjy.elasticsearch.aliyuncs.com:9200/landpage --limit=3000
--input 源数据
--output 目的数据

http://ag-pgm:l0ng-r4nd0m@es-cn-7pp29nzdq001dccjy.elasticsearch.aliyuncs.com:9200

$DJ_SCRIPT/yugong/ag/ad_aggs_outer_shop.sh

4265000
````
#####  检验新索引的数据和旧索引的是否一样

##### 将新索引指向别名，并取消旧索引对别名的指向
````elm
POST _aliases
{
  "actions": [
    {
      "remove": {
        "index": "material_v1",
        "alias": "material"
      }
    },
    {
      "add": {
        "index": "material_v2",
        "alias": "material"
      }
    }
  ]
}
````


