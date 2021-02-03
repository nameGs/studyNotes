# MYSQL

1. ![image-20200917153001367](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200917153001367.png)

   员工表中部门以id的形式存在，为了解决数据冗余等问题。

2. 格式化日期使用`date_format((列名,'%Y-%m-%d %H:%i:%s'))`，将日期转换成字符串

   `str_to char()`将字符串转换成日期。

3. `DELETE`语句中不能使用别名。

4. `count(*)`java层返回的是lang型。

5. `SELECT 1 FROM 表`，其中的`1`表示临时得到一列数据，行数是表中的记录数，配合`EXISTS`可以快速查询结果是否存在，而结果的具体数据不涉及。在应用中速度比`SELECT *` 速度快。

6. 定义变量

   ```sql
   set @num_number = 0;
   select (@num_number := @num_number + 1) num ;
   ```

7. 时间函数：

   1. `SYSDATE()`：取的是动态的实时时间。
   2. `NOW()`：取的是语句开始执行的时间

   

   

