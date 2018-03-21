## 日常使用SQL的一些经验

### 目录

- group by
- regexp_extract正则
- =,in,like的匹配
- case when条件选择
- union\join\mapjoin联表



### 详解

`group by`：根据(by)一定的规则进行分组(Group)，例如常用的依据日期给所需要查询的数据进行分组、根据产品ID、根据进入页面给数据进行分组等

http://www.w3school.com.cn/sql/sql_groupby.asp、http://www.cnblogs.com/wang-123/archive/2012/01/05/2312676.html



`regexp_extract`：正则匹配，函数语法：`regexp_extract(string **\*subject***,  string **pattern**,  int **index**)`

可以以此来获得第1.2.3.4..n..个匹配字段

http://www.cnblogs.com/skyEva/p/5175377.html



```sql
SELECT <myColumnSpec> = 
CASE 
WHEN <A> THEN <somethingA> 
WHEN <B> THEN <somethingB> 
ELSE <somethingE> 
END 
```

http://www.cnblogs.com/qiantuwuliang/archive/2009/06/03/1495770.html



`=,in,like`：**等号**是用来查找与单个值匹配的所有数据；

**IN** 是 用来查找 与多个值匹配的所有数据；

而 **LIKE**用来查找与一个模式匹配的所有数据。

http://www.cnblogs.com/nucdy/p/5624843.html



`union`联表用法

`union all`可以阻止去重

https://segmentfault.com/a/1190000007926959



`join`，用join把多张表连起来，然后对这些表做where的判断



`mapjoin`：hive的用法：对于多张表join，且其中有表的量不大，可以对其使用mapjoin，把其读到内存中。

`select /*+ mapjoin(t1)*/ t1.a,t1.b from table t1 join table2 t2  on ( t1.a=t2.a and f.ftime=20110802)  `

http://blog.csdn.net/liuj2511981/article/details/8616730