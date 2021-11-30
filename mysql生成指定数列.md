使用help_topic.help_topic_id

```mysql
select @s:=@s+30000 as order_date,mysql.help_topic.help_topic_id
from
  (( select @s := 47199) temp,mysql.help_topic)
where @s < 150000000
```

