# Oracle

## DML

### 算数运算符号

> #### +运算符
>
> ![image-20200923171914269](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923171914269.png)
>
> #### -运算符
>
> ![image-20200923171931138](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923171931138.png)
>
> #### *运算符
>
> ![image-20200923171949196](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923171949196.png)
>
> #### /运算符
>
> ![image-20200923171959995](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923171959995.png)
>
> #### || 运算符
>
> ![image-20200923172019891](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923172019891.png)
>
> #### 注意
>
> `select`关键字后要加`from`

### 关系运算符

> #### =
>
> #### <>
>
> #### \>
>
> #### \<
>
> #### \>=
>
> #### \<=
>
> #### IS NULL
>
> * 不是指空字符串，指的是没有值
>
> #### IS NOT NULL
>
> * 有值，可以是空字符串
>
> #### BETWEEN AND
>
> * 检索两个之间的，有先后顺序，比如`between 1 and 2`，等同于`>=1 && <=2`
>
> #### IN
>
> * 匹配列表中的值
>
> ![image-20200923172924018](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923172924018.png)
>
> #### LIKE
>
> * 检索匹配字符样式的数据
>
> ![image-20200923173040835](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923173040835.png)
>
> * `%`表示匹配任意的字符，`__`表示匹配单个字符

### 逻辑运算符

> #### AND
>
> * 都为真贼为真
>
> #### OR
>
> * 一个为假则为假
>
> #### NOT	
>
> * 取相反的

### SELECT语句

> * 用于查询表或视图。
> * 起别名可以用`AS`关键字，也可以省略直接写
>
> ![image-20200923173908978](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923173908978.png)
>
> ​		![image-20200923173957337](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923173957337.png)		
>
> #### TO_CHAR和TO_DATE
>
> `TO_DATE`：按照第二个参数的格式对第一个参数进行解析
>
> `TO_CHAR`：按照第二个参数的格式对第一个参数进行转换
>
> #### ORDER BY
>
> * 对数据进行排序。（ASC升序，DESC降序，默认ASC）
>
>   ![image-20200923174227257](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923174227257.png)
>
>   ![image-20200923174237306](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923174237306.png)
>
> #### DISTINCT
>
> * 去重
>
>   ![image-20200923174358504](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923174358504.png)
>
> #### WHERE
>
> * 查询条件，可以使用各种运算符
>
>   ![image-20200923174632970](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923174632970.png)
>
> #### AND
>
> * 连接多个查询，并且具有运算符的功能
>
>   ![image-20200923174941481](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923174941481.png)
>
> #### OR
>
> * 连接多个查询，并且具有运算符的功能
>
>   ![image-20200923175027520](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923175027520.png)
>
> * AND 和OR连用处理复杂条件时，要==使用括号==指明关系
>
>   ![image-20200923175215104](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923175215104.png)
>
> * IN和NOT IN
>
>   ![image-20200923175419225](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923175419225.png)
>
>   ![image-20200923175432842](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923175432842.png)
>
> #### BETWEEN
>
> * 连接，有顺序
>
>   ![image-20200923175538792](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923175538792.png)
>
>   ![image-20200923175613905](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923175613905.png)
>
> #### EXISTS和NOT EXISTS
>
> * 判断子查询是否有数据返回，有则为true，没有则为false，也可用于INSERT，UPDATE，DELETE
>
> * 跟在where后边
>
>   ![image-20200923180046615](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923180046615.png)
>
> #### ROW_NUMBER() OVER(PARTITION BY 分组列 ORDER BY 排序列 DESC)
>
> * 表示加入一列数据，表示行号
>
>   ![image-20201020153032328](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201020153032328.png)
>
>   * 根据分组列分组，根据排序列排序，最后生成的数据是每一组中的顺序。
>
>   ![image-20201109183017695](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201109183017695.png)
>
> #### GROUP BY
>
> * 根据指定的列分组并聚合，==结合聚合函数==使用。
>
> * 聚合函数：`count()`求和函数，`avg()`平均数函数，`sum()`求和函数，`max()`最大值函数，`min()`最小值函数。这几个可以在`select`查询中直接聚合而不使用`group by`，但是不能有其他列。
>
> * group by后边可以通过使用`having`对聚合结果进行再一次筛选。
>
> * `having`和`where`的区别：
>
>   * `where`后不能跟聚合函数
>   * `where`在``group by`之前执行，`having`在其后。
>   
>   ![image-20200924093629117](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924093629117.png)
>
> ### JOIN
>
> #### 多表联查
>
> * `CROSS JOIN`不在`WHERE`从句中指定关联条件，返回的记录数为各个表记录数的笛卡尔乘积，换而言之就是A和B表所有结合的可能。
>
>   * 语法中的`CROSS JOIN`可以省略。
>
>   ![image-20200924102449035](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924102449035.png)
>
> * `INNER JOIN`在`WHERE`从句中指定关联条件，返回符合指定关联条件的各个表记录数和各列值。
>
>   ![image-20200924101521704](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924101521704.png)
>
> * `OUT JOIN`在`WHERE`从句中指定表之间的关联，返回符合关联条件的指定的各个表记录数及各个列值，不符合的返回空。
>
>   * (+)标到哪个表的列后边，就表示查询另一个表的所有列，然后这个表和它进行匹配，如果没有则为空。（左连接或右连接）
>
>   ![image-20200924102002108](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924102002108.png)
>
>   * 可以可以写为：
>
>     ![image-20200924103015643](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924103015643.png)
>
> #### 三表联查
>
> * `OUT JOIN`
>
>   * 一个表最多外连接一个表。
>   * 使用(+)写法要用`WHERE`。
>
>   ![image-20200924103654403](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924103654403.png)

### 复合查询

> #### UNION（并集去重）
>
> * 把多个查询连接在一起，并且查询的结果**去重**
>
> ![image-20200924104504889](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924104504889.png)
>
> #### UNION ALL（并集不去重）
>
> * 把多个查询连接在一起，并且查询的结果**不去重***
>
>   ![image-20200924104630160](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924104630160.png)
>
> #### INTERSECT（交集）
>
> * 求多个查询语句的交集
>
>   ![image-20200924104855079](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924104855079.png)
>
> #### MINUS（减运算）
>
> * 求在第一个查询不在第二个查询的语句数据，参与`MINUS`的必须是相同数据类型。
>
>   ![image-20200924105023217](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924105023217.png)

### SUBQUERY子查询

> #### 概念
>
> * 在主语句中通过括号嵌套起来的查询语句叫做子查询。
>
> #### 分类
>
> * 相关子查询：子查询中引用外部表。
>
>   ![image-20200924105827000](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924105827000.png)
>
> * 非相关子查询：子查询不引用外部表。
>
>   ![image-20200924105757401](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924105757401.png)
>
> ![image-20200924110134264](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924110134264.png)

### LEVEL和CONNECT BY...START WITH...

> #### LEVEL
>
> * 标识树形结构的等级，`LEVEL`越大，层级越深。
>
> #### CONNECT BY...START WITH...
>
> * 用于查询树形结构

### ROWNUM和分页

> #### RUWNUM
>
> * 在`SELECT`语句中查询返回数据中表示是第几行。
>
>   ```sql
>   select * from (
>          select a.*, rownum as no from (
>                 select * from "admin" order by "id" asc
>         ) a
>   ) where no between 6 and 10;
>   ```
>   
>   表示从第六行查询到第10行。

## DML

### INSERT

> * 将指定的数据插入指定的表中
>
>   ![image-20200924112615238](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924112615238.png)
>
>   ![image-20200924112620531](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924112620531.png)

#### INSERT和SELECT

> * 将`SELECT`查询到的数据保存插入到指定表中，其中查询数据的顺序的数据类型必须和表的数据类型相同。
>
>   ![image-20200924113027556](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924113027556.png)
>
> * 

### UPDATE

> * 更新指定表的数据。
>
>   ![image-20200924113227163](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924113227163.png)

### DELETE

> * 将指定数据从指定的表中删除
>
>   ![image-20200924113352653](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924113352653.png)

### SELECT和DML

> `SELECT`可以以子查询的方式插入到DML语句中。

### WITH...AS...

> * 增加了sql的易读性，如果构造了多个子查询，结构会更清晰；
> * 更重要的是：“一次分析，多次使用”，这也是为什么会提供性能的地方，达到了“少读”的目标
> * 本质就是嵌套子查询

## DDL

> #### 表相关
>
> ##### CREATE
>
> * 创建表
>
> ![image-20200924113817476](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924113817476.png)
>
> ##### DROP
>
> * 删除数据库对象
>
>   ![image-20200924142248884](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924142248884.png)
>
> ##### TRUNCATE
>
> * 删除指定表的数据并且无法回滚
>
>   ![image-20200924141821243](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924141821243.png)
>
> ##### ALTER
>
> * 修改数据库对象
>
>   ![image-20200924142210204](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924142210204.png)
>
> ##### COMMENT
>
> * 给表、字段添加备注
>
>   ![image-20200924141629604](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924141629604.png)
>
> #### 视图相关
>
> ##### 视图与表的区别
>
> 1. 视图不需要占用磁盘内存
> 2. 视图不能添加索引
> 3. 使用视图可以简化查询
> 4. 有利于提高安全性
>
> ##### 创建
>
> ![image-20200924143650473](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924143650473.png)
>
> ##### 修改
>
> ![image-20200924143711090](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924143711090.png)
>
> ##### 删除
>
> ![image-20200924143725513](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924143725513.png)
>
> #### 同义词相关
>
> ##### 概念
>
> 1. 使用同义词可以屏蔽具体被映射对象的所属用户和真实数据库对象名称。
> 2. 同义词类似视图，但是视图只能映射查询SQL，同义词可以映射表、视图、存储过程、函数、包、序列等。
>
> ##### 创建
>
> ![image-20200924144021041](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924144021041.png)
>
> ##### 修改
>
> ![image-20200924144047050](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924144047050.png)
>
> ##### 删除
>
> ![image-20200924144107058](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924144107058.png)

## DCL

### Grant

>授权语句
>
>![image-20200924144406744](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924144406744.png)

### Revoke

>回收权限
>
>![image-20200924144328321](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924144328321.png)

## TL

### 事务的四大特性

1. A：原子性
2. C：一致性
3. I：隔离性
4. D：持久性

### COMMIT

> 

### ROLLBACK

> 

### SAVEPOINT

> 

## Oracle函数

### Ascii(char)

> 把指定的字符转换成Ascii码
>
> ![image-20200924144941519](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924144941519.png)
>
> ![image-20200924144949863](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924144949863.png)

### Asciistr(string)

> 如果指定的字符串在ascii码表中有，则转换为ascii码表中的，如果没有则转换成\\+utf16编码
>
> ![image-20200924145938607](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924145938607.png)
>
> ![image-20200924145953390](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924145953390.png)

### Chr(number)

> 根据数字返回ascii对应的字符
>
> ![image-20200924150043103](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924150043103.png)
>
> ![image-20200924150048871](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924150048871.png)

### Compose(string)

> 返回一个Unicode字符串
>
> ![image-20200924150304395](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924150304395.png)
>
> ![image-20200924150312159](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924150312159.png)

### Concat(string,string)

> 拼接字符串
>
> ![image-20200924150441607](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924150441607.png)
>
> ![image-20200924150449343](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924150449343.png)

### ||运算符

> 两个即以上进行拼接
>
> ![image-20200924150531656](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924150531656.png)
>
> ![image-20200924150539047](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924150539047.png)

### Convert

> 

### Dump

> 

### Initcap

> 

### Decode(条件,值1,返回值1,值2,返回值2,...值n,返回值n,缺省值)

> #### 含义  ---->   选择
>
> ```sql
> IF 条件=值1 THEN
> 　　　　RETURN(翻译值1)
> 	  ELSIF 条件=值2 THEN
> 　　　　RETURN(翻译值2)
> 　　　　......
> ELSIF 条件=值n THEN
> 　　　　RETURN(翻译值n)
> ELSE
> 　　　　RETURN(缺省值)
> END IF
> ```

### TRUNC(参数1,参数2)

> #### 含义  ---->  截断
>
> #### 用法
>
> 1. 截断数字：
>
>    * `TRUNC(n1,n2)`：n1表示被截断的数字，n2表示要截到哪一位。n2可以为负数，如果为负数，表示截断到小数点前。==不是四舍五入==
>
> 2. 截断日期：
>
>    * `TRUNC(n1,n2)`：n1表示日期，n2表示截取的内容。（具体如下表格）
>
>    |  属性  |               含义               |
>    | :----: | :------------------------------: |
>    |  year  |     截取到年（本年的第一天）     |
>    |   q    |   截取到季度（本季度的第一天）   |
>    | month  |     截取到月（本月的第一天）     |
>    |   ''   |               为空               |
>    |  不写  |            截取到今天            |
>    |  day   | 截取到周（本周第一天，及上周日） |
>    |   iw   |       本周第二天，即本周一       |
>    |  hh24  |      截取到小时（零分零秒）      |
>    |   mi   |             截取到分             |
>    | ~~ss~~ |  ~~报错（没有精确到秒的格式）~~  |