## 连续登录7天用户数
```sql
# 找出连续登录7天的用户数  
select count(distinct name) num  
from (select name, base_dt, count(1)  
         from (select *, DATE_SUB(dt,INTERVAL rn DAY) as base_dt  
                 from ( select *, row_number() over(partition by a.name order by a.dt) as rn  
                         from( select name, date(dt) as dt from login_log group by name, date(dt)) a  
                         ) b  
                 ) c  
group by name,base_dt HAVING COUNT(1)>=7 ) d;  
  
# 找出连续登录7天的用户  
select name,  
       count(1)  
from ( select *, DATE_SUB(dt,INTERVAL rn DAY) as base_dt  
        from ( select *, row_number() over(partition by a.name order by a.dt) as rn  
                from ( select name, date(dt) as dt from login_log group by name, date(dt)) a  
                ) b  
        ) c  
group by name, base_dt HAVING COUNT(1)>=7;

```