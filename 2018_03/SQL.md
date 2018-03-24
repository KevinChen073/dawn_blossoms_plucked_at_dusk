## 日常使用SQL的一些经验

### 目录

- group by
- regexp_extract正则
- =,in,like的匹配
- case when条件选择
- union\join\mapjoin联表
- 常用函数



### 详解

`group by`：根据(by)一定的规则进行分组(Group)，例如常用的依据日期给所需要查询的数据进行分组、根据产品ID、根据进入页面给数据进行聚合。需要注意的是，在select中的项，如果不在聚合函数内，都需要进group by，否则会有多行相似数据。

http://www.w3school.com.cn/sql/sql_groupby.asp、http://www.cnblogs.com/wang-123/archive/2012/01/05/2312676.html

SQL中Group by的使用：http://www.cnblogs.com/rainman/archive/2013/05/01/3053703.html



小技巧：有时候可以预处理表来使得你的最终SQL不要那么累赘。例如

```sql
SELECT  pc.pc_detail_url
        ,pc.product_id
        ,count(DISTINCT m.cookie_id) as m_click_uv
FROM    (
            -- 为了把相同的产品不同entry_url去重 ，预处理表格
                        SELECT  REGEXP_EXTRACT(entry_url, 'product/([0-9]+)/\S*') AS product_id
                                ,cookie_id
                        FROM    <表格>
                        where ds >= 20180305
                        AND     refer_url LIKE <aaa>
                        AND     entry_url LIKE <bbb>
                        GROUP BY entry_url, cookie_id
        ) m
group by pc.pc_detail_url
        ,pc.product_id
```

---

`regexp_extract`：正则匹配，函数语法：`regexp_extract(string **\*subject***,  string **pattern**,  int **index**)`

可以以此来获得第1.2.3.4..n..个匹配字段

http://www.cnblogs.com/skyEva/p/5175377.html

---

```sql
SELECT <myColumnSpec> = 
CASE 
WHEN <A> THEN <somethingA> 
WHEN <B> THEN <somethingB> 
ELSE <somethingE> 
END 
```

http://www.cnblogs.com/qiantuwuliang/archive/2009/06/03/1495770.html

---

`=,in,like`：**等号**是用来查找与单个值匹配的所有数据；

**IN** 是 用来查找 与多个值匹配的所有数据；

而 **LIKE**用来查找与一个模式匹配的所有数据。

http://www.cnblogs.com/nucdy/p/5624843.html

---

`union`联表用法

`union all`可以阻止去重

https://segmentfault.com/a/1190000007926959

---

`join`，用join把多张表连起来，然后对这些表做where的判断。注意的是：`inner join on`和`where`的实际效果一致，只是效率不一样而已

left join on和where：http://www.cnblogs.com/hgwy/articles/1691689.html



`mapjoin`：hive的用法：对于多张表join，且其中有表的量不大，可以对其使用mapjoin，把其读到内存中。

`select /*+ mapjoin(t1)*/ t1.a,t1.b from table t1 join table2 t2  on ( t1.a=t2.a and f.ftime=20110802)  `

http://blog.csdn.net/liuj2511981/article/details/8616730

---

having

having和where类似，只是having可以在计算后再进行一次筛选，因此可以对别名进行筛选。

Having与Where的区别:http://www.cnblogs.com/rainman/archive/2013/05/01/3053703.html

---

常用函数：

聚合函数：count\max\average\min\....

正则函数：regexp_extract

去重关键字：distinct

选择：case when end