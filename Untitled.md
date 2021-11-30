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

python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select ad_creative_id, ad_id, area, ut as dt, position, platform, format, media, appid, channel from (select ad_creative_id, ad_id, max(area) as area, max(dt) as ut, max(position) as position, max(platform) as platform, max(format) as format, max(media) as media, max(appid) as appid, max(channel) as channel from mt.ad_log where ad_id > {start_id} and ad_id <= {end_id} and dt between '2021-04-10' and '2021-04-20' group by ad_creative_id, ad_id)" --max_flush_cnt=1000 --querydims="select arrayJoin(range(toUInt32(ceil((1592461067-281736535) / 10000)))) as round, 281736535+round * 10000 as start_id, 281736535+(round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "2-3月同步任务结束"},"at": {"isAtAll": true}}'

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

python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select ad_creative_id, ad_id, area, ut as dt, position, platform, format, media, appid, channel from (select ad_creative_id, ad_id, max(area) as area, max(dt) as ut, max(position) as position, max(platform) as platform, max(format) as format, max(media) as media, max(appid) as appid, max(channel) as channel from mt.ad_log where ad_id > {start_id} and ad_id <= {end_id} and dt between '2020-05-01' and '2020-05-10' group by ad_creative_id, ad_id)" --max_flush_cnt=1000 --querydims="select arrayJoin(range(toUInt32(ceil((189895351) / 10000)))) as round, round * 10000 as start_id, (round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "5-10月同步任务结束"},"at": {"isAtAll": true}}'

python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select ad_creative_id, ad_id, area, ut as dt, position, platform, format, media, appid, channel from (select ad_creative_id, ad_id, max(area) as area, max(dt) as ut, max(position) as position, max(platform) as platform, max(format) as format, max(media) as media, max(appid) as appid, max(channel) as channel from mt.ad_log where ad_id > {start_id} and ad_id <= {end_id} and dt between '2020-05-10' and '2020-05-20' group by ad_creative_id, ad_id)" --max_flush_cnt=1000 --querydims="select arrayJoin(range(toUInt32(ceil((189895351) / 10000)))) as round, round * 10000 as start_id, (round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "5-20月同步任务结束"},"at": {"isAtAll": true}}'

python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select ad_creative_id, ad_id, area, ut as dt, position, platform, format, media, appid, channel from (select ad_creative_id, ad_id, max(area) as area, max(dt) as ut, max(position) as position, max(platform) as platform, max(format) as format, max(media) as media, max(appid) as appid, max(channel) as channel from mt.ad_log where ad_id > {start_id} and ad_id <= {end_id} and dt between '2020-05-20' and '2020-05-31' group by ad_creative_id, ad_id)" --max_flush_cnt=1000 --querydims="select arrayJoin(range(toUInt32(ceil((189895351) / 10000)))) as round, round * 10000 as start_id, (round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "5-31月同步任务结束"},"at": {"isAtAll": true}}'

117170000

python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select ad_creative_id, ad_id, area, ut as dt, position, platform, format, media, appid, channel from (select ad_creative_id, ad_id, max(area) as area, max(dt) as ut, max(position) as position, max(platform) as platform, max(format) as format, max(media) as media, max(appid) as appid, max(channel) as channel from mt.ad_log where ad_id > {start_id} and ad_id <= {end_id} and dt between '2020-10-11' and '2020-11-11' group by ad_creative_id, ad_id)" --max_flush_cnt=1000 --querydims="select arrayJoin(range(toUInt32(ceil((189895351- 117170000) / 10000)))) as round,  117170000+round * 10000 as start_id, 117170000+ (round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "10-11月同步任务结束"},"at": {"isAtAll": true}}'

126200000 

python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select ad_creative_id, ad_id, area, ut as dt, position, platform, format, media, appid, channel from (select ad_creative_id, ad_id, max(area) as area, max(dt) as ut, max(position) as position, max(platform) as platform, max(format) as format, max(media) as media, max(appid) as appid, max(channel) as channel from mt.ad_log where ad_id > {start_id} and ad_id <= {end_id} and dt between '2020-11-11' and '2020-12-11' group by ad_creative_id, ad_id)" --max_flush_cnt=1000 --querydims="select arrayJoin(range(toUInt32(ceil((189895351-126200000) / 10000)))) as round, 126200000+round * 10000 as start_id, 126200000+(round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "11-12月同步任务结束"},"at": {"isAtAll": true}}'


42050000

python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select ad_creative_id, ad_id, area, ut as dt, position, platform, format, media, appid, channel from (select ad_creative_id, ad_id, max(area) as area, max(dt) as ut, max(position) as position, max(platform) as platform, max(format) as format, max(media) as media, max(appid) as appid, max(channel) as channel from mt.ad_log where ad_id > {start_id} and ad_id <= {end_id} and dt between '2020-07-20' and '2020-08-11' group by ad_creative_id, ad_id)" --max_flush_cnt=1000 --querydims="select arrayJoin(range(toUInt32(ceil((189895351-42050000) / 10000)))) as round,42050000+round * 10000 as start_id, 42050000+(round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "7-20月同步任务结束"},"at": {"isAtAll": true}}'


64250000

python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select ad_creative_id, ad_id, area, ut as dt, position, platform, format, media, appid, channel from (select ad_creative_id, ad_id, max(area) as area, max(dt) as ut, max(position) as position, max(platform) as platform, max(format) as format, max(media) as media, max(appid) as appid, max(channel) as channel from mt.ad_log where ad_id > {start_id} and ad_id <= {end_id} and dt between '2020-08-11' and '2020-09-01' group by ad_creative_id, ad_id)" --max_flush_cnt=1000 --querydims="select arrayJoin(range(toUInt32(ceil((189895351-64250000) / 10000)))) as round, 64250000+round * 10000 as start_id, 64250000+(round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "8月-11同步任务结束"},"at": {"isAtAll": true}}'

 96950000
 
 python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select ad_creative_id, ad_id, area, ut as dt, position, platform, format, media, appid, channel from (select ad_creative_id, ad_id, max(area) as area, max(dt) as ut, max(position) as position, max(platform) as platform, max(format) as format, max(media) as media, max(appid) as appid, max(channel) as channel from mt.ad_log where ad_id > {start_id} and ad_id <= {end_id} and dt between '2020-06-16' and '2020-07-01' group by ad_creative_id, ad_id)" --max_flush_cnt=1000 --querydims="select arrayJoin(range(toUInt32(ceil((281638272-32757) / 10000)))) as round, round * 10000 as start_id, (round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "6-7-01月同步任务结束"},"at": {"isAtAll": true}}'
 
apt-get update && apt-get install vim -y && apt-get install screen -y && apt-get install less -y && screen -S job -s bash


python manage.py es_sync_river --sync_command=es_sync_ad_effect_snapshot --max_flush_cnt=1000 --db_dsn=alishh.ag-db-41.adData --query="select ad_id,action_last_day as action,impression_last_day as impression, impression_inc_2y from ad_effect_snapshot where ad_id=128081086"

python manage.py es_sync_river --sync_command=es_sync_ad_effect_snapshot --max_flush_cnt=1000 --db_dsn=alishh.ag-db-41.adData --query="select ad_id as _last_id, ad_id,action_last_day as action,impression_last_day as impression, impression_inc_2y from ad_effect_snapshot where ad_id>%s and ad_id> order by ad_id limit 1000"

python manage.py es_sync_river --sync_command=es_sync_ad_impression --max_flush_cnt=1000 --db_dsn="alishh.ag-db-test.adData" --query="select ad_id,impression_inc_2y from ad_impression_total where ad_id=21077042"


python manage.py es_sync_advertisement_uni --max_flush_cnt=1000 --db_dsn=alishh.ag-db-40.adData --query="select id as _last_id,id,updatedAt from advertisement where id>%s order by id limit 1000"

python manage.py es_sync_advertisement_uni --max_flush_cnt=1000 --db_dsn=alishh.ag-db-40.adData --query="select id,updatedAt from advertisement where id in ('42573277', '50390784', '11833765', '71441084', '71207757', '88427745', '89890371', '90979897', '90490550', '87590947', '88712705', '100837625', '103023855', '109026506', '109028090', '55616814', '105963696', '103019221', '103027688', '117611266', '113386252', '85323423', '122857372', '114018364', '101633184', '83074552', '113869822', '120209735', '126203624', '115235422', '130952908', '83075073', '134305473', '134800905', '134889827', '118017953', '134986414', '61993108', '136086834', '125837930', '136086737', '138021699', '138101842', '138814346', '136895976', '142172788', '143574769', '145185960', '145421416', '143768786', '147610460', '146444628', '148079666', '148477038', '148804893', '149703919', '150591655', '151194355', '151464452', '151532618', '151864645', '144744151', '149277709', '154295752', '151151703', '154591232', '155018983', '147393381', '155838555', '156628646', '157062645', '157398202', '100802265', '158209781', '158503456', '158525027', '158548738', '150315723', '159023638', '159536306', '156887404', '135976661', '159688659', '160921377', '130406681', '128512078', '148673792', '161782943', '161659432', '142827487', '132454562', '161726008', '157888538', '163013373', '114562700', '163399363', '39967869', '45513589', '163693260', '163726745', '144494420', '160406448', '140250131', '164831323', '164882465', '102059724', '149362643', '165945541', '166047310', '166073928', '166124537', '163314266', '166416395', '161311092', '103175571', '166480061', '72300928', '142657297', '167347198', '167497402', '133295256', '166554652', '167632483', '167676530', '167735586', '158599756', '167920656', '133650252', '72023873', '164287398', '166092218', '168286703', '168496395', '159225836', '168263362', '168750143', '99041149', '169120405', '146510209', '145688556', '167353315', '169875845', '169911725', '170328238', '169860938', '170568451', '157116903', '170172412', '170628489', '72654550', '170959239', '171019545', '170831278', '170845655', '171465927', '171372842', '128102662', '169293330', '167018492', '171566344', '171407473', '168304521', '170887080', '170242196', '171592067', '171746831', '171797401', '168598315', '171959274', '171839255', '172146408', '170207205', '172249363', '172462818', '172510411', '171643079', '172546207', '172639302', '172824468', '172953133', '172970005', '172600263', '173132395', '172579413', '80165216', '173203779', '173210026', '173285102', '173319137', '173397628', '173474557', '173021435', '172917945', '173560604', '173606725', '173626040', '173629566', '173652213', '160398933', '173786616', '173582034', '173877485', '173912911', '173913984', '172005406', '173929928', '173931533', '173881071', '174023184', '162608985', '174234724', '174283091', '174289113', '174334034', '174369757', '174382105', '174399352', '174399657', '148096509', '174404091', '174409161', '174411754', '174456113', '174468150', '174473038', '174478844', '174499540', '174503597', '174511786', '174305193', '173392067', '170232396', '174575595', '147911059', '174594620', '174599045', '170752603', '174641218', '174642610', '174662466', '174639673', '173638768', '173349517', '174764372', '174810447', '173628530', '174948589', '174962651', '174679937', '174978852', '174983095', '175031438', '173204587', '169649074', '175123492', '174921606', '174898269', '160601690', '175185303', '174320384', '175211033', '175215082', '175231678', '175331379', '175349542', '173563173', '175379014', '175391262', '175391293', '175394093', '175401740', '174509980', '175427977', '175452994', '175453693', '172342713', '175470481', '175486266', '175395356', '175530220', '175532467', '175021967', '174686283', '175539169', '175539937', '175515003', '173832524', '175391663', '175569504', '175381658', '175594390', '174087988', '175514144', '175649847', '175325037', '175675415', '175721142', '174543673', '106570598', '175787571', '175801615', '175803747', '175822992', '175829097', '175847620', '175386258', '169325074', '175375005', '175540580', '175704028', '175940494', '175469546', '175951550', '175565729', '175989348', '175190823', '175996145', '175316813', '175935686', '175400704', '176029381', '175162701', '174693459', '174986284', '176068465', '174421467', '151528044', '176099166', '175476458', '174046694', '175817572', '174950437', '176147069', '176158296', '176170156', '175786219', '146644268', '168699990', '176252340', '176287980', '176301099', '176304421', '176305546', '176308775', '176316869', '173306545', '175852787', '173551447', '176373273', '69790848', '116827633', '176422426', '176422383', '176429221', '176365462', '174409541', '175324986', '168947029', '176436052', '175438326', '176062765', '176462116', '176469829', '173416230', '174574415', '176430826', '170951371', '176582231', '176686918', '176686722', '176741726', '160796104', '167260103', '176249558', '154017791', '168697556', '177118293', '162466127', '177094769', '177295121', '157076171', '177344853', '143422142', '155402395', '165360806', '177296610', '166930562', '177458536', '177465931', '177405451', '174020232', '177153044', '174581129', '172016574', '175638697', '168376427', '177795633', '177803710', '177805335', '176316004', '177921120', '177921633', '177931537', '177948041', '178014499', '176874095', '174478665', '178092452', '168190543', '121971531', '176959751', '177277807', '178306941', '175570060', '159213877', '175656797', '175960554', '177322811', '177041970', '174664882', '178580947', '170030971', '178328465', '178333249', '174629167', '178665331', '178667362', '178713821', '178757852', '178781612', '111183279', '178795025', '178795565', '178807043', '178795102', '174398151', '178846422', '176370358', '178846979', '174130507', '178848535', '178850153', '178884313', '174693352', '178902283', '178934125', '178941902', '178942211', '177300760', '155868201', '178712168', '178995258', '179002330', '175593898', '179034481', '151623265', '179088548', '179125279', '179131459', '141330330', '178356420', '174979385', '179204937', '179237541', '179259058', '174844142', '179263419', '167765658', '179323016', '164144005', '178304936','179413453', '178399308', '179450861', '177006073', '179487941', '177208490', '175026428', '179544927', '176721913', '179584315', '179601946', '167010544', '179631007', '179639148', '179684130', '170409646', '172999848', '179798772', '179870988', '179932047', '179950519', '174633177', '143292456', '178982101', '176724280', '180040162', '165924556', '180127794', '180173589', '163635835', '177719346', '150725606', '180321042', '177864461', '175667660', '180511773', '180525187', '180529446', '177994648', '180603445', '180631152', '171344132', '180690386', '180773493', '180753248', '180790771', '170419460', '180842553', '180866157', '180888192', '180889377', '180931014', '174935829', '168162429', '181068574', '181075238', '161027075', '168591861', '181176910', '173631662', '179861447', '178097001', '181180268', '177342344', '180946563', '176623454', '179927823', '173098340', '181518757', '181528945', '181142266', '152329554', '181581256', '181622771', '181406938', '178992874', '181650259', '181665387', '179385431', '163336918', '177291976', '179795689', '178375853', '180085970', '181733336', '176540630', '181763641', '168590496', '181782838', '181761202', '181149592', '181837475', '178332945', '181842486', '135666035', '179363971', '179690096', '170635032', '182023603', '182027667', '172084309', '178127023', '175777646', '169557807', '181283822', '163317955', '182326943', '179361375', '179739069', '182431939', '171344039', '113570241', '173877886', '182605086', '182739346', '177310164', '182894802', '159678252', '180293844', '178532389', '159804306', '177125483', '174696832', '176216588', '180890092', '179468425', '148836589', '120738865', '183377682', '171375718', '167227279', '166909602', '183583049', '168576385', '181667015', '174737793', '176258566', '183793951', '176064634', '183244928', '183853336', '175926578', '176853017', '184052794', '179625572', '184175953', '132294477', '171595724', '184291569', '184315459', '184422969', '184467658', '172300232', '184443515', '170495861', '184646144', '184684725', '159173913','175539911', '184843334', '184851669', '167146960', '184949727', '185005947', '185072054', '168538853', '183813344', '172971670', '185208937', '185236109', '179055911', '185297333', '185490587', '185490679', '142797811', '185535188', '185549834', '185556986', '179056632', '184443783', '185675365', '185756584', '167965635', '185838516', '181649119', '185868341', '181622446', '135516899', '175376735', '184855616', '184701249', '185994665', '186073811', '186087780', '186134110', '184955239', '175441329', '186177277', '179835070', '173264699', '186183160', '176058797', '178341472', '186207873', '186211082', '171359878', '170642399', '171309543', '174371547', '178329044', '183685545', '186192788', '186266660', '171571491', '186272517', '174219282', '186300782', '181781073', '186347872', '151921923', '183979517', '181393051', '186398162', '177006894', '186497718', '161468450', '163414677', '175987006', '170449169', '186562854', '174023815', '186579570', '186582739', '162606350', '125155731', '167072737', '186642736', '177563313', '186743453', '185195520', '179867890', '125447869', '180569856', '186878426', '167445076', '186880578', '185038036', '177313924', '186908404', '185715920', '187010511', '187037825', '181018894', '187006662', '184605781', '182061044', '184854004', '185274673', '154557169', '186739246', '168140594', '186513626', '187243320', '187207229', '187301009', '187301500', '139438302', '185309288', '187348875', '187037289', '171761401', '171883971', '173461969', '187429929', '187454794', '167705356', '176253589', '164750540', '187526029', '139633938', '146325172', '187596748', '187644225', '178998891', '185439836', '187347198', '187690075', '187695595', '187697046', '187712449', '187697296', '185223988', '187749509', '184422699', '187808840', '187858928', '170537444', '187867722', '179964423', '156418161', '176463954', '187975333', '188015527', '178571086', '130088870', '186456456', '185052674', '186445894', '173156706', '184320770', '186478578', '174421383', '186386389', '176855182', '133555588', '84812898', '166163271', '188160531', '188195147', '188248454', '188269264', '187600325', '188265412', '188312855', '160846400', '188344824', '188321658', '183278673', '179733528', '171804240', '188381292', '181774602', '179594998', '177837279', '177190387', '170596359', '188463595', '188466761', '170497854', '188524020', '187336983', '187880822', '186203997', '188563740', '177975450', '188591169', '184843397', '176813897', '179579432', '188665789', '186491107', '188732791', '188739276', '177352351', '188743637', '179089019', '167599579', '158548964', '188787374', '188787288', '181538224', '188859027', '185260540', '163545402', '189019770', '189059300', '189132046', '188450091', '188261855', '177059196', '167442626', '175791570', '189342202', '189081045', '180268411', '189369828', '155001314', '93223590', '188831246', '189421229', '186551672', '189436510', '84462168', '189451108', '189287659', '188867112', '175813305', '167768155', '189527158', '189536859', '175404245', '187451120', '176258124', '188616468', '188828275', '187229864', '176240484', '189507437', '189613856', '173647579', '176351001', '173267238', '181544955', '169557684', '189731014', '169286669', '189762583', '189779556', '167145741', '189818621', '189819829', '167989701', '189775737', '186256539', '189896491', '189781055', '189913497', '179197378', '189944156', '189981765', '189986187', '189989324', '189991007', '189996027', '190004025', '182795313', '190031970', '176381730', '139868110', '190060607', '190061071', '180905334', '190062401', '189788765', '176781212', '179617004', '167593021', '190141353', '190119405', '190161478', '190172405', '190177460', '190191296', '174677752', '177556127', '190015810', '175008112', '190280489', '173351094', '190288444', '123440419', '186585264', '189287757', '190347097', '180878593', '174593181', '190379084', '180865985', '190384043', '190384053', '190387868', '190395448', '190413589', '190431796', '190466201', '185085854', '167103209', '190485330', '190493616', '190170880', '190508226', '157322724', '190359830', '190519657', '190522849', '190535349', '152664404', '190551252', '190553385', '156277484', '181901965', '181520628', '189468873', '179534944', '180686942', '186654767', '188281218', '189088798', '168168719', '190753257', '190750522', '190206065', '166921304', '171490017', '190798028', '190804240', '190824107', '171755982', '171802817', '166906523', '185680928', '190864946', '171429558', '167278608', '179617307', '178938977', '190939712', '190959485', '190981853', '181351051', '191045748', '191072275')"

last_id=2918706


screen -S job -s bash（创建job的会话）


python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select ad_creative_id, ad_id, area, ut as dt, position, platform, format, media, appid, channel from (select ad_creative_id, ad_id, max(area) as area, max(dt) as ut, max(position) as position, max(platform) as platform, max(format) as format, max(media) as media, max(appid) as appid, max(channel) as channel from mt.ad_log where ad_id > {start_id} and ad_id <= {end_id} and dt between '2020-08-11' and '2020-09-01' group by ad_creative_id, ad_id)" --max_flush_cnt=1000 --querydims="select arrayJoin(range(toUInt32(ceil((189895351-90000000) / 10000)))) as round,90000000+round * 10000 as start_id, 90000000+(round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "90000000====9-01月同步任务结束"},"at": {"isAtAll": true}}'


98150000 and dt between '2020-09-01' and '2020-09-11' group by ad_creative_id, ad_id)


90000000

79510000

python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select ad_creative_id, ad_id, area, ut as dt, position, platform, format, media, appid, channel from (select ad_creative_id, ad_id, max(area) as area, max(dt) as ut, max(position) as position, max(platform) as platform, max(format) as format, max(media) as media, max(appid) as appid, max(channel) as channel from mt.ad_log where ad_id > {start_id} and ad_id <= {end_id} and dt between '2020-06-10' and '2020-06-19' group by ad_creative_id, ad_id)" --max_flush_cnt=1000 --querydims="select arrayJoin(range(toUInt32(ceil((189895351-79510000) / 10000)))) as round, 79510000+round * 10000 as start_id, 79510000+(round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "6-19月同步任务结束"},"at": {"isAtAll": true}}'

86790000

python manage.py es_sync_material --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select ad_creative_id, ad_id, area, ut as dt, position, platform, format, media, appid, channel from (select ad_creative_id, ad_id, max(area) as area, max(dt) as ut, max(position) as position, max(platform) as platform, max(format) as format, max(media) as media, max(appid) as appid, max(channel) as channel from mt.ad_log where ad_id > {start_id} and ad_id <= {end_id} and dt between '2020-07-20' and '2020-07-31' group by ad_creative_id, ad_id)" --max_flush_cnt=1000 --querydims="select arrayJoin(range(toUInt32(ceil((189895351-86790000) / 10000)))) as round,86790000 +round * 10000 as start_id, 86790000 +(round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "7-20月同步任务结束"},"at": {"isAtAll": true}}'


es_sync_ad_heat_oversea --max_flush_cnt=3000 --kafka_group=test-sync-ad-heat-overseas --max_flush_interval=60

138653762

python manage.py es_sync_ad_heat_oversea --max_flush_cnt=1000 --db_dsn=awsor.ag-db-11.adData --query="select ad_id as _last_id,ad_id,heat,created_time from ad_heat where ad_id>138653762 and ad_id>0 and created_time='2021-05-09' limit 1000"

python manage.py es_sync_ad_website_oversea --max_flush_cnt=1000 --db_dsn=awsor.ag-db-11.adData --query="select *, 'adData.ad_website_tag' as __table from ad_website_tag limit 10"

python manage.py es_sync_ad_heat_oversea --max_flush_cnt=1000 --db_dsn=awsor.ag-db-11.adData --query="select ad_id as _last_id, ad_id, heat, created_time, 'adData.ad_heat' as __

table from ad_heat  where ad_id = 129293367 and created_time = '2021-03-04' limit 3000"

python manage.py es_sync_ad_creative_oversea --max_flush_cnt=2000 --db_dsn="awsor.ag-db-11.adData" --query="select ad_id as _last_id,ad_creative_id from((select id ,id from ad_creative where modify_time between '2021-04-07 00:00:00' and '2021-04-08 10:50:00'  and id<=150044635 and id>=450829 and id>%s limit 10000) t1 left join(select ad_id,ad_creative_id from ad_creative_rel) t2 on t1.id=t2.ad_creative_id)"

python manage.py es_sync_ad_log_aggs_oversea --db_dsn="awsor.ag-db-11.adData" --query="select distinct ad_id, appid,ad_creative_id, channel, platform, format, media, area, dt from ad_log_aggs where ad_id > {start_id} and ad_id <= {end_id} and dt between '2021-05-11' and '2021-05-12' " --max_flush_cnt=1000 --querydims="select arrayJoin(range(toUInt32(ceil((189895351) / 10000)))) as round,round * 10000 as start_id, (round + 1) * 10000 as end_id" --db_dim="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt"

python manage.py es_sync_ad_log_aggs_oversea --max_flush_cnt=2000 --db_dsn="awsor.ag-db-11.adData" --query=""
EsSyncAdLogAggsOversea

python manage.py es_sync_ad_heat_oversea --max_flush_cnt=2000 --db_dsn="awsor.ag-db-11.adData" --query="select * from ad_heat where ad_id > {start_id} and ad_id <= {end_id} and created_time = '2021-05-25' " --querydims="select arrayJoin(range(toUInt32(ceil((189895351) / 10000)))) as round,round * 10000 as start_id, (round + 1) * 10000 as end_id order by round desc" --db_dim="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt"

python manage.py ad_aggs_sync_oversea --max_flush_cnt=2000 --db_dsn="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt" --query="select ad_id,area,ad_creative_id,dt,platform,format,media,appid,channel,'adData.ad_log_aggs' as __table from mt.ad_log where ad_id>{start_id} and ad_id<={end_id} and dt between '2020-08-10' and '2021-08-20' group by ad_id,area,ad_creative_id,dt,platform,format,media,appid,channel" --querydims="select arrayJoin(range(toUInt32(ceil((188486262) / 10000)))) as round,round * 10000 as start_id, (round + 1) * 10000 as end_id" --db_dim="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "8-10-20月同步任务结束"},"at": {"isAtAll": true}}'

python manage.py ad_aggs_sync_oversea --max_flush_cnt=2000 --db_dsn="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt" --query="select ad_id,area,ad_creative_id,dt,platform,format,media,appid,'adData.ad_log_aggs' as __table from mt.ad_log where ad_id>{start_id} and ad_id<={end_id} and dt between '2021-05-01' and '2021-05-10' group by ad_id,area,ad_creative_id,dt,platform,format,media,appid" --querydims="select arrayJoin(range(toUInt32(ceil((187897160-116749993) / 1000)))) as round,116749993+round * 1000 as start_id, 116749993+(round + 1) * 1000 as end_id" --db_dim="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "2105-01-10月同步任务结束"},"at": {"isAtAll": true}}'


python manage.py ad_aggs_sync_oversea --max_flush_cnt=5000 --db_dsn="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt" --query="select ad_id,area,ad_creative_id,dt,platform,format,media,'adData.ad_log_aggs' as __table from mt.ad_log where ad_id>{start_id} and ad_id<={end_id} and dt = '2021-09-01' group by ad_id,area,ad_creative_id,dt,platform,format,media" --querydims="select arrayJoin(range(toUInt32(ceil((269625301) / 10000)))) as round,round * 10000 as start_id, (round + 1) * 10000 as end_id order by round desc" --db_dim="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "2021-9月同步任务结束"},"at": {"isAtAll": true}}'

python manage.py ad_aggs_sync_oversea --max_flush_cnt=5000 --db_dsn="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt" --query="select ad_id,area,ad_creative_id,dt,platform,format,media,appid,channel,'adData.ad_log_aggs' as __table from mt.ad_log where dt between '2020-08-01'and '2020-08-10' and ad_id={start} " --db_dim="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt"


python manage.py ad_aggs_sync_oversea --max_flush_cnt=5000 --db_dsn="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt" --query="select ad_id,area,ad_creative_id,dt,platform,format,media,appid,channel,'adData.ad_log_aggs' as __table from mt.ad_log where dt between '2020-08-01' and '2020-08-10' and ad_id between 35541593 and 35543571 order by area limit 15 " --db_dim="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt"

media_list = get_oversea_adv_media(after["ad_id"])



197484000
215114039


01-04 92944900---
06-08 85143100---
09-12 91716500---
13-16 84049700--- 
17-21 68261200
22-25 95667700




"awsor.ag-db-test.adData":"mysql://ag_oversea:ag_overseaGie!R5@db-test.ag.awsor:3306/adData"



select ad_id,area,ad_creative_id,platform,format,media,appid from mt.ad_log where ad_id>191106796 and ad_id<=191107796 and dt between '2021-06-10' and '2021-06-20' group by ad_id,area,ad_creative_id,platform,format,media,appid


platform,format,media,appid,'adData.ad_log_aggs' as __table from mt.ad_log

-- 14301 --

select ad_id,area,ad_creative_id,platform,format,media,appid,'adData.ad_log_aggs' as __table from mt.ad_log where ad_id>191106796 and ad_id<=191107796 and dt between '2021-06-10' and '2021-06-20' group by ad_id,area,ad_creative_id,platform,format,media,appid


-- ad_creative_id 维度--


-- 完整 43470 --

select ad_id,area,ad_creative_id,platform,format,media,appid from mt.ad_log where ad_id>191107796 and ad_id<=191108796 and dt between '2021-06-01' and '2021-06-30' group by ad_id,area,ad_creative_id,platform,format,media,appid


-- 去掉appid 5953 --

select ad_id,area,ad_creative_id,platform,format,media from mt.ad_log where ad_id>191107796 and ad_id<=191108796 and dt between '2021-06-01' and '2021-06-30' group by ad_id,area,ad_creative_id,platform,format,media




100371966 3-5-9
95375962 4-10-20

210010673
191102796

203129788

116749993  5
187897160

165006762  4
24709962	

146045943  3
67403958

129495742   2
69529868

116147995   1
23230000

102388879   12
52819977

84760356    11
24409998

70532098     10
6169688

57771726     9
28447000	

31184378      8
27948952

25512236      7
25506739

80673962

06-01 190987000

06-08 193116000

06-15 202964000


## 2021-04-10 4月10号的数据没同步

python manage.py ad_aggs_oversea_sync --max_flush_cnt=2000 --db_dsn="awsor.ag-db-11.adData" --query="select *,'adData.ad_campaign' as __table from ad_campaign where ad_id=47191"

194918

python manage.py ad_aggs_oversea_sync --max_flush_cnt=2000 --db_dsn="awsor.ag-db-10.adData" --query="select *,'adData.ad_log_aggs' as __table from ad_log_aggs where ad_id=294558" 


python manage.py es_sync_shop_oversea --max_flush_cnt=2000 --db_dsn="awsor.ag-db-10.adData" --query="select id as _last_id, id,host,name,description,site_id,status from website where site_id>0 and status=0 and id>%s limit 1000"

python manage.py es_sync_river  --es_sync_command=es_sync_goods --max_flush_cnt=2000 --db_dsn="awsor.ag-db-10.adData" --query="select goods_id as _last_id, goods_id,name,website_id,description from goods where goods_id>%s limit 1000"

python manage.py ch_sync_river --sync_command=ch_sync_goods_category --db_dsn="awsor.ag-db-10.adData" --query="select goods_id,category_id,website_id from goods_category where website_id between {start_id} and {end_id}" --max_flush_cnt=2000 --querydims="select arrayJoin(range(toUInt32(ceil((14929073) / 100000)))) as round, round * 100000 as start_id, (round + 1) * 100000 as end_id" --db_dim="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt"

python manage.py ch_sync_river --sync_command=ch_sync_brands --db_dsn="alishh.pub-db-00.msp_org" --query="select id as _last_id, id,parent_id,level,deleted,ag_show from brands where id>%s limit 3000"


curl 0.0.0.0:35992/metrics

curl 0.0.0.0:8001/metrics

CONSUL=consul://consul-cluster.y.cn/sod/dj/aws_test/DEV/env?dc=awsjp&token=80b20a88-be89-0da6-f0df-c4b6a7c6b930
LADDR=:8001
AWSOR_DATABASE_AD_RO_DSN=mysql://dev_adm:dev_admHi2ohV)i@db-test.ag.awsor:3306/adData
AWSOR_DATABASE_AD_DSN=mysql://ag_oversea:zh97KpCX5RJ9FQ72@db-11.ag.awsor:3306/adData
AWSOR_DATABASE_ASO_RO_DSN=mysql://aso_www:BIMaJU1uV5VlbePh@db-11.ag.awsor:3306/asoData
AWSOR_DATABASE_ASO_DSN = mysql://aso_www:BIMaJU1uV5VlbePh@db-11.ag.awsor:3306/asoData
LOG_LEVEL=DEBUG

4742628	
16252468


python manage.py es_sync_ad_kv_oversea --max_flush_cnt=2000 --db_dsn="awsor.ag-db-10.adData" --query="select ad_id as _last_id,ad_id,k,v from ad_kv where k=75 and ad_id>%s and ad_id>188059703 and modify_time between '2021-06-01 07:00:00' and '2021-06-01 09:20:00' order by ad_id limit 1000"

python manage.py es_sync_ad_kv_oversea --max_flush_cnt=2000 --db_dsn="awsor.ag-db-10.adData" --query="select * from ad_kv where ad_id =7991342"


{'update': {'_index': 'ag_product_overseas', '_type': 'data', '_id': '8828240455', 'status': 400, 'error': {'type': 'mapper_parsing_exception', 'reason': 'failed to parse [id]', 'caused_by': {'type': 'json_parse_exception', 'reason': 'Numeric value (8828240455) out of range of int\n at [Source: org.elasticsearch.common.bytes.BytesReference$MarkSupportingStreamInputWrapper@2c31be45; line: 1, column: 17]'}}}}
NoneType: None


python manage.py ch_sync_river --db_dsn=awsor.ag-db-10.asoData --sync_command=ch_sync_app_style_tag --query="select app_id, platform,style_id from app_style_tag where app_id > {start_id} and app_id <= {end_id}" --max_flush_cnt=5000 --querydims="select arrayJoin(range(toUInt32(ceil((235964549) / 5000)))) as round, round * 5000 as start_id, (round + 1) * 5000 as end_id " --db_dim="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt"

4435587
python manage.py es_sync_ad_style --max_flush_cnt=5000 --db_dsn="alishh.ag-db-40.adData" --query="select adid as _last_id,adid,tagid,category from ad_industry_tag where category=2 and adid>8433610 and adid>%s order by adid limit 10000"

python manage.py es_sync_river --es_sync_command=es_sync_ad_industry_tag_final --max_flush_cnt=5000 --db_dsn="alishh.ag-db-40.adData" --query="select ad_id as _last_id,ad_id,tag_id from ad_industry_tag_final where ad_id>174806423 and ad_id>%s order by ad_id limit 10000"
174806423

python manage.py es_sync_test_log --db_dsn="alishh.ag-db-40.adData" --query="select ad_id,dt,ad_id as __deleted from ad_log_aggs where dt='2021-07-19' limit 10"

python manage.py es_sync_ad_effect --db_dsn="alishh.ag-db-40.adData" --query="select ad_id,stat_time,impression from ad_effect where ad_id between {start_id} and {end_id} and stat_time>='2019-07-30' and stat_time<='2019-08-30' group by ad_id,media_id,stat_time" --max_flush_cnt=5000 --querydims="select arrayJoin(range(toUInt32(ceil((235964549) / 10000)))) as round, round * 10000 as start_id, (round + 1) * 10000 as end_id " --db_dim="clickhouse://clickhouse-00.mt.alishh:9000/mt"

python manage.py es_sync_ad_effect --db_dsn="alishh.ag-db-40.adData" --query="select ad_id,stat_time,impression from ad_effect where ad_id between 20360041 and 20370000 and stat_time>='2019-07-30' and stat_time<='2019-08-30' group by ad_id,media_id,stat_time" --max_flush_cnt=5000 --querydims="select arrayJoin(range(toUInt32(ceil((235964549) / 10000)))) as round, round * 10000 as start_id, (round + 1) * 10000 as end_id " --db_dim="clickhouse://clickhouse-00.mt.alishh:9000/mt"

python manage.py es_sync_landpage_from_campaign --max_flush_cnt=3000 --db_dsn="alishh.ag-db-40.adData" --query="select ad_id,campaign_id,campaign_type from ad_campaign where ad_id=273974645"

python manage.py es_sync_landpage_from_ad_campaign --max_flush_cnt=3000 --db_dsn="alishh.ag-db-40.adData" --query="select ad_id,campaign_id,campaign_type from ad_campaign where ad_id between {start_id} and {end_id}" --querydims="select arrayJoin(range(toUInt32(ceil((274972984) / 10000)))) as round, round * 10000 as start_id, (round + 1) * 10000 as end_id " --db_dim="clickhouse://clickhouse-00.mt.alishh:9000/mt"

12430123

sum(increase(dj_total{k8s_cluster="awsor-production", app="dj-es-sync-ad-heat-oversea", exported_name="ad_heat_oversea_skip_for_time"}[10m]))


select ad_id,campaign_type,campaign_id from ad_campaign where  ad_id in (select ad_id from ad_campaign where campaign_type=401 and campaign_id=4799 and ad_id between {start_id} and {end_id}) 


select ad_id,campaign_type,campaign_id,ad_id as _last_id from ad_campaign where ad_id in (select ad_id from ad_campaign where campaign_type=401 and campaign_id=4799 and ad_id > %s order by ad_id limit 2000) order by ad_id


python manage.py ad_aggs_sync_from_ad_campaign_oversea --db_dsn="awsor.ag-db-11.adData" --query="select ad_id,campaign_type,campaign_id from ad_campaign where  ad_id=47177 and campaign_type=201 and campaign_id=200503" --max_flush_cnt=2000 

python manage.py ad_aggs_sync --db_dsn="alishh.ag-db-40.adData" --query="select ad_id,campaign_type,campaign_id from ad_campaign where  ad_id in (select ad_id from ad_campaign where campaign_type=401 and campaign_id=4799 and ad_id between {start_id} and {end_id})" --max_flush_cnt=2000 --querydims="select arrayJoin(range(toUInt32(ceil((236644337) / 100000)))) as round, 1022+round * 100000 as start_id, 1022+(round + 1) * 100000 as end_id " --db_dim="clickhouse://clickhouse-00.mt.alishh:9000/mt"

python manage.py ad_aggs_sync --db_dsn="alishh.ag-db-40.adData" --query="select ad_id,campaign_type,campaign_id,'adData.ad_campaign' as __table from ad_campaign where  ad_id in (select ad_id from ad_campaign where campaign_type=401 and campaign_id=4799 and ad_id between {start_id} and {end_id})" --max_flush_cnt=2000 --querydims="select arrayJoin(range(toUInt32(ceil((236644337) / 100000)))) as round, 1022+round * 100000 as start_id, 1022+(round + 1) * 100000 as end_id " --db_dim="clickhouse://clickhouse-00.mt.alishh:9000/mt"

--db_dsn="awsor.ag-db-10.adData" --query="select goods_id,category_id,website_id from goods_category where website_id between {start_id} and {end_id}" --max_flush_cnt=2000 --querydims="select arrayJoin(range(toUInt32(ceil((14929073) / 100000)))) as round, round * 100000 as start_id, (round + 1) * 100000 as end_id" --db_dim="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt"

python manage.py ad_aggs_sync_oversea --max_flush_cnt=3000 --db_dsn="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt" --query="select ad_id,area,ad_creative_id,dt,platform,format,media,'adData.ad_log_aggs' as __table from mt.ad_log where dt between '2021-09-05' and '2021-09-06' and ad_id between {start_id} and {end_id} group by ad_id,area,ad_creative_id,dt,platform,format,media" --querydims="select arrayJoin(range(toUInt32(ceil((274552154) / 10000)))) as round,round * 10000 as start_id, (round + 1) * 10000 as end_id order by round desc" --db_dim="clickhouse://default:6t4kRK4S@clickhouse-00.ag.awsor:9000/mt";curl 'https://oapi.dingtalk.com/robot/send?access_token=d2e2d41e851e934cac52eacbad0f1a43086a57b74d9698b82df8e91d8921293c' -H 'Content-Type: application/json' -d '{"msgtype": "text","text": {"content": "2021-6月同步任务结束"},"at": {"isAtAll": true}}'


apt-get update && apt-get install vim -y && apt-get install screen -y && apt-get install less -y && screen -S job -s bash


python manage.py sync_command=


python manage.py es_sync_landpage_from_ad_log_aggs --max_flush_cnt=5000 --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select area,ad_id,dt,channel,appid,media_v2,'adData.ad_log_aggs' as __table from mt.ad_log where ad_id>{start_id} and ad_id<={end_id} and dt between '2021-09-20' and '2021-09-28' group by area,ad_id,dt,channel,appid,media_v2" --querydims="select arrayJoin(range(toUInt32(ceil((274552154) / 100000)))) as round,round * 100000 as start_id,(round + 1) * 100000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt"

python manage.py es_sync_material_from_ad_link --max_flush_cnt=3000 --db_dsn="alishh.ag-db-40.adData" --query="select adid as _last_id, adid, lp_id from ad_link where adid>%s order by adid limit 3000" --querydims="select arrayJoin(range(toUInt32(ceil((274552154) / 10000)))) as round,round * 10000 as start_id, (round + 1) * 10000 as end_id" --db_dim="clickhouse://ec-00.ag.alishh:9000/mt"

python manage.py es_sync_landpage_from_ad_log_aggs --max_flush_cnt=3000 --db_dsn="clickhouse://default:6t4kRK4S@172.19.30.10:9000/mt" --query="select area,ad_id,dt,channel,appid,media_v2,'adData.ad_log_aggs' as __table from mt.ad_log where ad_id>=248233600 and ad_id<=248243600"


python manage.py es_sync_ad_campaign --max_flush_cnt=3000 --db_dsn="alishh.ag-db-40.adData" --query="select ad_id,campaign_id,campaign_type from ad_campaign where campaign_type=400 and campaign_id=8146808982456239086"

python manage.py ad_aggs_sync --max_flush_cnt=3000 --db_dsn="alishh.ag-db-40.adData" --query="select ad_id,campaign_id,campaign_type,'adData.ad_campaign' as __table from ad_campaign where campaign_type=400 and campaign_id=8146808982456239086"

ad_aggs_sync

$YUGONG \
-src "$DB40_AD_DSN?direct=false&usetx=true&maxflushcount=5000" \
-dst "$ALI_AG_DB_TEST/test_adData?direct=false&usetx=true&maxflushcount=5000" \
-query "
insert into ad_effect(ad_id,media_id,platform,format,impression,click,action,budget,stat_time,modify_time) values (%d,%d,%d,%d,%d,%d,%d,%d,%d,%d)
select ad_id,media_id,platform,format,impression,click,action,budget,stat_time,modify_time from ad_effect where stat_time = date_format(date_sub(now(), interval 2 year), '%Y-%m-%d')"






```

![image-20210416152811013](/home/youmi/.config/Typora/typora-user-images/image-20210416152811013.png)

```mysql
class EsSyncAdIndustryTag(BinlogSyncCommand):
    """从ad_industry_tag同步广告行业与风格广告index"""

    topic = ["binlog-ag-db-41-addata-ad-industry-tag-final", "binlog-ag-db-41-addata-ad-industry-tag"]

    def handle_row(self, table, before, after):
        if table == "adData.ad_industry_tag":
            if not after:
                # 删除操作
                self.buffer[before["adid"]] = None
                return
            self.buffer[after["adid"]] = None
        else:
            if not after:
                # 删除操作
                self.buffer[before["ad_id"]] = None
                return
            self.buffer[after["ad_id"]] = None

    def flush(self):
        ad_ids = list(self.buffer.keys())
        if not ad_ids:
            return
        # 因为广告标签是一对多，所以重新获取广告的所有标签，然后再同步ES
        tag_dict = get_tag_from_ad_final(ad_ids)
        data = {
            ad_id: {"tag_list": [{"tagid": i, "method": 1, "proba": 95} for i in tag_dict.get(ad_id, [])]}
            for ad_id in ad_ids
        }
        write_to_es(ES_DSN, ES_INDEX_AD, data, upsert=True)
        self.buffer = {}




GET ag_shop_overseas/data/_search
{
  "query": {
    "function_score": {
      "query": {
        "bool": {
          "must": [
            {
                  "multi_match": {
                      "slop":0,
                      "operator":"or",
                      "query": "Encontre",
                      "type": "best_fields", 
                      "fields": ["host.zh^96","shop_name^128","description^64"],
                      "tie_breaker": 0.3,
                      "minimum_should_match":"2<60% 5<70%"
    }

            }
          ]
        }
      }
    }
    },
    "size": 1000,
    "from": 0,
    "min_score":0,
      "highlight": {
    "number_of_fragments": 0,
    "pre_tags": ["<em class='highlight'>"], 
    "post_tags": ["</em>"],
    "fields": {
      "host.zh": {},
      "shop_name": {}
    }
  }
}

GET ag_shop_overseas/data/_search
{
  "query": {
    "function_score": {
      "query": {
        "bool": {
          "must": [
            {
              "multi_match": {
                "slop":0,
                "query":"Encontre",
                "type": "best_fields", 
                "operator":"or",
                "fields": ["host.zh^96","shop_name^128","decription^64"],
                "tie_breaker": 0.3,
                "minimum_should_match":"2<60% 5<70%"
              }
            }
          ]
        }
      }
    }
    
  },
  "size": 1000,
  "from": 0,
  "min_score":0,
  "highlight": {
    "number_of_fragments": 0,
    "pre_tags": ["<em class='highlight'>"], 
    "post_tags": ["</em>"],
    "fields": {
      "host.zh": {},
      "shop_name": {}
    }
  }
}



{
    "filter":[{"terms":{"shop_id":[1289914,7359219,117647,229559,1373911,895922,1985362,547157,1219072,946424]}}],
    "scrpt_score":{
        "script":{
            "params":{
                "set":{1289914:588,7359219:585,117647:574,229559:570,1373911:531,895922:524,1985362:516,547157:467,1219072:451,946424:375},
                "field":"shop_id"
            },
            "id":"field-score"
        }
    }
}


{
    "query":{
        "function_score":{
            "funcations" :[{
    "filter":[{"terms":{"shop_id":[1289914,7359219,117647,229559,1373911,895922,1985362,547157,1219072,946424]}}],
    "scrpt_score":{
        "script":{
            "params":{
                "set":{1289914:588,7359219:585,117647:574,229559:570,1373911:531,895922:524,1985362:516,547157:467,1219072:451,946424:375},
                "field":"shop_id"
            },
            "id":"field-score"
        }
    }
}],
            "query":{
                "bool":{
                    "must":{
                        "bool":{
                            "should":[{
  "query": {
    "function_score": {
      "query": {
        "bool": {
          "must": [
            {
                  "multi_match": {
      "slop":0,
      "operator":"or",
      "query": "Pocket",
      "type": "best_fields", 
      "fields": ["product_title^128","description^96"],
      "tie_breaker": 0.3,
      "minimum_should_match":"2<60% 5<70%"
    }

            }
          ]
        }
      }
    }
    },
    "size": 1000,
    "from": 0,
    "min_score":0,
      "highlight": {
    "number_of_fragments": 0,
    "pre_tags": ["<em class='highlight'>"], 
    "post_tags": ["</em>"],
    "fields": {
      "product_title": {}
    }
  }
},{"terms":{"shop_id":[1289914,7359219,117647,229559,1373911,895922,1985362,547157,1219072,946424]}}]
                        }
                    }
                }
            },
            "score_mode":"max",
            "boost_mode":"sum",
        }
    }
}
}


1289914:588,7359219:585,117647:574,229559:570,1373911:531,895922:524,1985362:516,547157:467,1219072:451,946424:375


CREATE TABLE _ad_aggs_by_day_aggs (`ad_id_bm` AggregateFunction(groupBitmap, UInt32) COMMENT '广告内部id位图', `campaign_type` UInt16 COMMENT '推广目标类型', `campaign_id` UInt32 COMMENT '推广目标id', `media_id` UInt32 COMMENT '媒体id', `channel_id` UInt32 COMMENT '渠道id', `ad_format` UInt8 COMMENT '广告形式', `application` UInt8 COMMENT '爬虫应用id', `creative_type` UInt8 COMMENT '创意类型', `platform` UInt8 COMMENT '投放平台', `developer_id` UInt32 COMMENT '开发者id', `area` String COMMENT '投放地区代码', `purpose` UInt8 COMMENT '推广目的', `genre_id` UInt32 COMMENT 'ag应用分类id', `dt` Date COMMENT '广告抓取日期', `is_created_day` UInt8 COMMENT '该日期是否是广告的新投放日期: 1/0。TODO: 待补充ad_aggs的ad_month第32位新投放的同步') ENGINE = MergeTree() PARTITION BY dt ORDER BY (ad_format, application, creative_type, platform, campaign_type, campaign_id, area, media_id, purpose) TTL dt + toIntervalDay(701) SETTINGS index_granularity = 8192


    select
        toString(addDays(today(), - number)) as dt
    from
        system.numbers limit $LAST_DAY
        
        
rename 

$YUGONG2 \
-src "$CH_AG_DSN" \
-querydims "
select arrayJoin(range(toUInt32(ceil((11159376) / 1000)))) as round,round * 1000 as start_id, (round + 1) * 1000 as end_id,arrayJoin(['AU','BR','DE','FR', 'GB', 'ID','IN', 'JP', 'KR', 'MY', 'RU','SG', 'TH','US','VN', 'CA', 'TW','AE']) as cc
" \
-dst "$AWSOR_DATABASE_AD_DSN?batchinsert=true&maxflushcount=10000" \
-query "
insert into campaign_record_v2 (campaign_id, campaign_type, area, first_date, last_date) values (%d, %d, %s, %s, %s)
select campaign_id,
    campaign_type,
    area,
    MIN(dt) as first_date,
    MAX(dt) as last_date
from mt.ad_aggs_by_day
    where campaign_id > {{start_id}} and campaign_id<= {{end_id}} and campaign_type > 0 and area = '{{cc}}'
    group by campaign_id, campaign_type, area 
on duplicate key update first_date= least(first_date, values(first_date))
"





826594




数据同步
1. 修改海外同步数据的方式，改用监听binlog同步数据，实时更新海外es数据
2. 迁移海外同步es的脚本到rancher，统一国内和海外的同步es的姿势
  这个任务主要是想使es的数据同步更实时，之前通过baton跑同步脚本的方式需要通过modify_time的变更进行通过，这个过程需要频繁查询数据库获取变更，如果一些关联属性表发生变更，就有可能会丢失更新数据。改用监听binlog的方式，通过kafka获取变更的数据，并且细分各个字段来源，根据具体来源来同步数据，不容易丢失更新，并且数据更加实时。

数据同步
1. 优化海外同步热度脚本
2. 熟悉granfan的使用和学习通过指标观察同步脚本的性能问题
  产品经常发现当天的热度数据与数据库的数据会有差异，所以我去查了广告热度脚本消费的数据，发现当天的数据总是消费不完，并且会出现乱序消费的情况-先写入热度又更新为0，原因是热度一天会更新三次，且全量更新导致数据写入过多导致延迟。由于热度数据对实时，顺序消费要求较高，我便只更新变更的数据，减少写入数据量和kafka只设置一个分区，保证消费顺序。
  
数据同步
1. 修改海外同步ad_aggs的方式，迁移海外ad_aggs同步脚本到rancher
  目前海外想统一同步数据的姿势，并且之前ad_aggs的表结构设置得和业务有出入，数据也有些缺失。所以要重构ad_aggs表结构，并且修改同步数据的姿势，避免出现漏数据的情况。但是由于添加了几个一对多维度的字段，导致新ad_aggs表的数据增加了10倍，业务查询方面出现问题，目前正在优化ad_aggs表结构，以及同步ad_aggs的方式。
  
  
业务 AG
1. 开发店铺排行版的导出功能
2. 开发商品和店铺的品类筛选
3. 开发店铺下的商品排行榜，修改通用版的查询方式，使用redapi查询
  通用版需要做店铺下的商品展示，在做这个需求的时候，需要修改业务上使用orm来查询数据，改连接redapi，通过redash来保存sql查询语句，便于管理和修改sql，并且可以更好的优化sql查询性能。
  在做店铺排行榜的导出功能时，熟悉了导出功能部分的代码架构，但是测试方面，由于测试环境的导出队列有问题，导致每次导出时间都很长，比较影响开发效率和测试效率。
业务 AG
1. 开发素材视图增加各个维度的同步脚本
  这个需求主要时在各个维度下都有各自独立的素材视图，便于客户的查看素材。在开发过程中，了解到es的index修改特性，不能修改字段只能重建并重新同步数据，所以这个需求主要是在同步数据的过程耗时较长，需要考虑到换表的同时也不能影响线上使用。
业务 gpi
1. 完成gpi的店铺搜索和商品搜索的开发
  这个需求是要修改gpi的搜索方式，之前在sql语句进行关键词查询，修改后通过es搜索，搜索数据快且更准确。目前gpi在es的查询方面采用search template的方式，在yapi设置查询接口，然后通过传递es查询模板和查询相关参数来查询。这种方式减少了python组装查询语句的步骤，也学习到了seach template的使用和es查询相关方式的知识。

业务 管理后台
1. 解决银联网页版重复支付报错问题
因为银联方面只要跳到支付页面，就算不支付他也认为你创建了订单并且有了特定的流水号，导致返回页面想支付会报错，所以这边我们对流水号做了一些处理，用订单号加时间戳的方式生成流水号，处理不能重复支付的问题。
2. 移除ycms管理后台废弃功能和通用版应用商店的废弃代码
ycms要废弃优惠小券和销售订单的功能并迁移到业务中台处理，通用版的应用商店也已经废弃。


上半年主要的工作都是数据同步方面，由于一开始对数据同步的姿势不太熟悉，导致了在迁移海外同步脚本的开发时间较长。通过同步脚本开发过程中，开阔了自己的技能点，更加熟悉kafka，binlog以及不同的同步脚本框架，以及同步数据方面的工作，提高了后续同步脚本开发任务的速率，能够有制定数据同步方案的能力。
业务方面的开发通过半年业务开发的积累，开发速率也得到了提升，数据链路也比较熟悉，主要是一些细节和边界值需要多加注意，减少程序因为一些细节问题导致出bug，写业务代码需要细心思考。























曝光数
1.最新曝光数
2.最近两年总曝光数



变更情况：
1.新增当天数据




LAST_DAY=${LAST_DAY:-701}
$YUGONG \
-src "$CH_AG_DSN" \
-dst "$TEST_CH_AG_DSN" \
-querydims "
    select toString(addDays(today(), - number)) as dt
    from system.numbers limit $LAST_DAY
" \
-prepare "
    ALTER TABLE _ad_aggs_by_day_app_shadow drop PARTITION '{{dt}}'
" \
-query "
insert into _ad_aggs_by_day_app_shadow(ad_id_bm, campaign_type, campaign_id, purpose, media_id, ad_format, creative_type, area, genre_id, dt, is_created_day)
select toTypeName(groupBitmapOrState(ad_id_bm)),
       campaign_type,
       campaign_id,
       purpose,
       media_id,
       ad_format,
       creative_type,
       area,
       genre_id,
       dt,
       is_created_day
from
  (select ad_id_bm,
          campaign_type,
          campaign_id,
          purpose,
          media_id,
          ad_format,
          creative_type,
          area,
          genre_id,
          dt,
          is_created_day
   from mt.ad_aggs_by_day
   where dt = '2021-08-02' and purpose in (1,
                     2) and campaign_id=1576705341
   group by campaign_type,
            campaign_id,
            purpose,
            media_id,
            ad_format,
            creative_type,
            area,
            genre_id,
            dt,
            is_created_day,ad_id_bm)tmp
group by campaign_type,
         campaign_id,
         purpose,
         media_id,
         ad_format,
         creative_type,
         area,
         genre_id,
         dt,
         is_created_day
" \
-after "ALTER TABLE ad_aggs_by_day_app REPLACE PARTITION '{{dt}}' from _ad_aggs_by_day_app_shadow" \
-after "ALTER TABLE ad_aggs_by_day_app drop PARTITION '{{dt}}'"


insert into _ad_aggs_by_day_app_shadow(ad_id_bm, campaign_type, campaign_id, purpose, media_id, ad_format, creative_type, area, genre_id, dt, is_created_day)
select groupBitmapOrState(ad_id_bm) as ad_id_bm,
       campaign_type,
       campaign_id,
       purpose,
       media_id,
       ad_format,
       creative_type,
       area,
       genre_id,
       dt,
       is_created_day
from
  (select ad_id_bm,
          campaign_type,
          campaign_id,
          purpose,
          media_id,
          ad_format,
          creative_type,
          area,
          genre_id,
          dt,
          is_created_day
   from mt.ad_aggs_by_day
   where dt = '2021-07-01' and purpose in (1,
                     2)
   group by campaign_type,
            campaign_id,
            purpose,
            media_id,
            ad_format,
            creative_type,
            area,
            genre_id,
            dt,
            is_created_day,ad_id_bm)tmp
  group by campaign_type,
         campaign_id,
         purpose,
         media_id,
         ad_format,
         creative_type,
         area,
         genre_id,
         dt,
         is_created_day












国内ch：
memory：15.4GB
Swap：947.2MB
CPUs: 4 x 2.50 GHz
海外ch：
Memory (RAM): 15.19 GB
Swap: Using 0.0 of 0.0 MB swap.
CPUs: 4 x 3.10 GHz





    if user_group not in settings.INTERNAL_USER_GROUP:
        # 非内部用户仅显示对外品牌
        where_sql_dict["ag_show_outer"] = 0
    else:
        # 内部用户能筛选 对内对外品牌 ag_show 0 / 1 内部用户默认看所有品牌及不用传ag_show字段
        if not data.get("show") or {0, 1} == set(data["show"]):
            # 默认查询和全选都是不加筛选条件
            pass
        elif 0 in data["show"]:
            where_sql_dict["ag_show_inner"] = 0
        elif 1 in data["show"]:
            where_sql_dict["ag_show_outer"] = 0
            
            
            
            
            
            
            
  
```

