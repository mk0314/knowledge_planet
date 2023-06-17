<!--
 * @Author: mengkun822 1197235402@qq.com
 * @Date: 2023-06-14 11:32:22
 * @LastEditors: mengkun822 1197235402@qq.com
 * @LastEditTime: 2023-06-17 11:20:53
 * @FilePath: \knowledge_planet\docs\md\Mysql\Mysql.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->

数据库是实现数据持久化和数据管理

> ### 什么是数据持久化?

数据持久化 - 将数据从内存转移到能够长久保存数据的存储介质的过程

> ### 数据库分类

数据库分为关系型数据库和非关系型数据库

市场上流行的关系型数据库有：Mysql 、Oracle、 SQL serve

非关系型数据分为：MongoDB 、 Redis - 文档数据库/ KV 数据库

关系型数据库

-   理论基础： 关系代数和集合论
-   具体表象：用二维表保存数据
    -   行： 一条记录
    -   列： 某个属性
    -   主键列：能够唯一识别的这条记录的 id

学生（学号、姓名、性别、出生年月日， 地址）

学院（）

> ### 创建数据库

```sql
-- 如果存在名为school的数据库就删除它
drop database if exists school

-- 创建名为school的数据库
create database school charset utf8
-- 切换到school数据库环境下
use school

```

> ### 创建表

```sql
--创建student表
create table tb_student(
    stu_id int no null comment '学号',
    stu_name varchar(30) not null comment '姓名',
    stu_sex bit  default 0 comment '性别',
    stu_birth   date comment '出生年月',
    primary key (stu_id)
)
```

> ### 修改表

```sql
-- 添加列
alter table tb_student add column stu_addr varchar(255);
-- 删除列
alter table tb_student drop column stu_addr
```

> ### 插入数据

```sql

-- 插入数据
insert into tb_student values(1001, '张三', 1, '1998-08-23')
insert into st_student (stu_id, stu_name, stu_birth) values (1002, '李四', '2000-08-21')

```

> ### 删除数据

```sql
delete from tb_student where stu_id = 1001
```

> ### 更新数据

```sql
update tb_student set stu_name = '张晓', stu_sex = 0 where stu_id = 1001
```

> ### 查询数据

```sql
select * from tb_student where stu_id = 1001
```

> ### 筛选

```sql
select stu_name as 姓名, if(stu_sex, '男', '女') from tb_student where  stu_id in (1001, 1002)
```

> ### 模糊查询

```sql
select * from tb_student where stu_name like '张%'
```

> ### 除去空值

```sql
select stu_name from tb_student where stu_addr is not null
```

> ### 升降序

```sql
-- 升序
select stu_name from tb_student where stu_sex = 1 order by stu_birth asc

-- 降序
select stu_name from tb_student where stu_sex = 1 order by stu_birth desc
```

> ### 分组和聚合函数

分组：group by

avg: 平均值

count: 求和

统计女生人数

```sql
select count(*) from tb_student where stu_sex = 1
```

> ### 子查询

子查询是指在一个 SQL 语句中嵌套另一个 SQL 查询语句的方式来进行查询。子查询一般分为两类：标量子查询和表子查询。

标量子查询：
标量子查询返回的结果只有一行一列，一般用在 SELECT、WHERE、FROM 子句中。例如，查询员工表中所有薪资高于平均薪资的员工：

```sql
SELECT emp_name, salary
FROM employee
WHERE salary > (SELECT AVG(salary) FROM employee);
```

以上 SQL 语句中的子查询 (SELECT AVG(salary) FROM employee) 返回的结果是一个标量值，即员工表中所有员工的平均薪资。

表子查询：
表子查询返回的结果是一个表格，可以使用它来替代 FROM 子句中的表名。例如，查询员工表中所有薪资等于最高薪资的员工信息：

```sql
SELECT \*
FROM employee
WHERE salary = (SELECT MAX(salary) FROM employee);
```

以上 SQL 语句中的子查询 (SELECT MAX(salary) FROM employee) 返回的结果是一个表格，包含了员工表中薪资最高者的信息。

除了标量子查询和表子查询，SQL 中还有其他一些类型的子查询，例如 EXISTS 子查询、IN 子查询、ANY/SOME 子查询、ALL 子查询等等。子查询的灵活运用可以使得查询更加精确和高效，但也需要谨慎使用，避免因过度嵌套导致效率低下。

HAVING 是 SQL 中用于筛选分组数据的关键字。SQL 中的 GROUP BY 语句可以将数据按照指定的列进行分组，而 HAVING 语句可以在分组后的数据上进一步筛选。

具体来说，HAVING 语句可以配合 GROUP BY 语句来实现类似于 WHERE 语句的过滤效果，只不过 WHERE 语句是对原始数据进行筛选，而 HAVING 语句是对分组数据进行筛选。

以下是一个例子，假设我们有一个员工表 employee，其中包含了员工的姓名、所属部门和薪资信息。需要查询每个部门中薪资平均值大于 5000 的员工信息：

```sql
SELECT department, AVG(salary)
FROM employee
GROUP BY department
HAVING AVG(salary) > 5000;
```

> ### 内连接

内连接是 sql 中一种常见的关联查询方式，它可以在两个或多个表之间建立关联，并返回查询条件的记录。

内连接的基本语法如下：

```sql
select column1, column2, ……
from table1
inner join table2 ON condition
```

table1, table2 是要连接的表名，condition 是条件，可以是一个或多个等值比较。注意，ON 必须要跟在 inner join 之后

举个例子:

我们有一个存储了订单信息的 orders 表和一个存储了客户信息的 customers 表，它们之间通过 customer_id 字段建立了关联。如果需要查询所有包含客户信息的订单，可以使用内连接:

```sql
select orders.order_num, customers.customer_name
from orders
inner join customers
on orders.customer_id = customers.customer_id
```

> ### 外连接

外连接是 sql 中常见的关联查询方式，它可以在两个或多个表之间建立关联，并返回匹配和不匹配的记录，外连接包括左外连接、右外连接和全外连接三种类型

-   左外连接

左外连接是可以用来返回左边表中所有记录以及右边表中符合条件的记录。语法基本如下：

```sql
select column1, column2
from table1
left join table2
on condition
```

例子：
我们有一个存储了订单信息的 orders 表和一个存储了客户信息的 customers 表，它们之间通过 customer_id 字段建立了关联。如果需要查询包含客户信息以及未匹配的订单信息，可以使用左外连接:

```sql
select orders.order_num, customers.customer_name
from orders
left join customers
on orders.customer_id = customers.customer_id
```

-   右外连接

右外连接是可以用来返回右边表中所有记录以及左边表中符合条件的记录。语法基本如下：

```sql
select column1, column2
from table1
right join table2
on condition
```

例子：
我们有一个存储了订单信息的 orders 表和一个存储了客户信息的 customers 表，它们之间通过 customer_id 字段建立了关联。如果需要查询包含客户信息以及未匹配的订单信息，可以使用左外连接:

```sql
select orders.order_num, customers.customer_name
from orders
right join customers
on orders.customer_id = customers.customer_id
```

-   全外连接

全外连接是一种同时返回左边和右边表中全部记录的外连接方式，即左右连接结果拿到的并集，语法：

```sql
SELECT column1, column2, ...
FROM table1
FULL OUTER JOIN table2
ON condition;
```

> ### 分页查询

分页查询是将查询结果按照固定大小进行分割，每次返回部分数据的查询方式。语法如下：

```sql
select *
from table
limit offset, count

```

offset 表示查询结果的起始位置，count 表示每页返回的记录数。

例子：
我们有一个存储了商品信息的 products 表，如果要查询第 11 条到第 20 条记录信息，可以使用以下 SQL 语句：

```SQL
SELECT *
FROM products
LIMIT 10, 10;
```

> ### 用 exists 取代集合运算和去重操作

exists 子查询来避免使用集合运算和去重操作，从而提高查询效率

exists 子查询用于检查一个条件是否成立，通常与子查询结合使用，用于判断子查询是否返回数据，如果返回数据则 exists 返回 true 否则返回 false

```sql
select distinct e.stu_id
from enrollments e
where exists (
    select * from course c
    where c.course_id = e.course_id
    and c.course_name = '计算机网络'
)
```

以上 sql 语句中，使用 exists 子查询检查 enrollments 表中是否存在所选课程编号对应的课程名称为"计算机网络"的记录。如果存在，则将其对应的学生编号返回。使用 exists 子查询之后，可以避免使用集合运算和去重操作，从而提高效率。

注意：exists 子查询通常需要与主查询进行相关联，以确定子查询的条件所指代是主查询的哪个数据集。如果子查询中引用了主查询中的某列数据，则需要使用表别名或者完整限定列名来进行引用。

> ### 执行计划

执行计划（Execution Plan）是指的是数据库系统根据查询语句优化器生成的一种查询操作的顺序和方式的计划，用于指导数据库系统如何进行查询操作，执行计划可以帮助我们了解查询的效率和瓶颈。从而对查询进行优化。

数据库系统会自动选择最佳的执行计划可以使用关键字 EXPLAIN 查看查询语句的执行计划，例如：

```sql
EXPLAIN select *
from orders
where customer_id = 123
order by order_date desc
limit 10
```

执行计划通常以树结构展示，每个节点表示一个查询操作，包括访问表、使用操作、使用索引、连接表和排序等操作。执行计划还会给出每个节点的重要属性，例如访问类型、行数估计、扫描的行数和过滤条件等。

注意：在生产环境中使用 EXPLAIN 语句时要谨慎使用，因为它会执行语句并暂停查询的执行，可能会影响其他用户的查询操作，因此，通常建议在开发环境中使用 explain 进行性能调优，然后将调整的查询语句部署到生产环境中。

> ### 索引

索引是一种提高查询效率的数据结构，用于快速定位表中的数据，索引可以理解为类似于书籍目录的数据结构，它将表中的数据按照某个列或者多个列的值进行排序，并建立映射关系，从而加快数据的访问速度。

在 mysql 中，可以使用 create index 语句来建立索引，例如

```sql
create index inx_customer_name on customers(customer_name)
```

上面的 sql 语句中建立了 inx_customer_name 的索引， 它是基于 customer_name 来创建的

注意：

-   索引应该建立在经常用于搜索和排序的列上，不宜滥用索引。

-   对于大规模数据的表，应该限制索引的数量，过多的索引会增加维护成本。

-   更新表中的数据时，需要同时更新索引中的数据，因此频繁的插入、更新和删除操作会影响索引的性能和效率

-   对于复合索引，如果查询中没有使用到所有列，将会浪费索引的空间，因此需要根据时机情况选择是否创建复合索引。

虽然索引可以提高查询效率，但是它也会增加数据存储的空间和维护成本。因此，在实际应用中需要根据数据量和查询操作的频率等因素进行综合考虑，选择合适的索引策略。

> ### 视图

视图是一种虚拟表，它不实际存数据，而是基于一个或多个表的查询结果生成一张表，视图可以简化复杂的查询操作，逻辑上将多个表连接起来，同时还可以保护敏感数据和限制用户的访问权限。

语句：

```sql
create view customer_orders as
select customers.customer_name, orders.order_date, orders.order_price
from customers
join orders on customers.customer_id = orders.customer_id
```

创建了 customer_orders 的视图，它基于 orders 和 customers 表查询结果生成，通过查询该视图，可以方便地获取每个客户的订单信息。

注意：

-   视图只是一个虚拟列表，它不实际存储数据，因此对视图进行的所有查询操作都会实时查询基础表

-   对视图进行的所有查询操作都必须与视图所基于的查询语句的约束一致，否则可能会产生意想不到的结果。

-   视图可以包含聚合函数和子查询等高级查询语句，从而实现更复杂的查询操作。

-   视图可以使用 GRANT 和 REVOKE 命令来控制用户对于视图的访问权限。

注意： 大量使用视图的情况下，可能会影响查询性能，因此需要根据实际情况进行综合考虑。同时，在使用视图时需要注意对基础表的修改可能会影响到视图的结果，因此需要谨慎使用。

> ### 存储过程

存储过程（Stored Produced）是一段预编译的程序代码，用于实现特定的操作或业务逻辑，他可以接受参数、执行操作、返回结果等，可以简化复杂的查询操作和提高查询效率。

在 mysql 中，可以使用 CREATE PRODUCED 语句来创建存储过程，例如：

```sql
create produced calculate_tax (in amount decimal(10, 2), out tax decimal(10,2))
begin
    set tax = amount * 10
end
```

以上的 sql 语句中，创建一个名为 exculate_tax 的存储过程，它接受一个名为 amount 的 decimal 的类型的值，并计算出税金，最后将结果赋值给名为 tax 的变量。

使用存储过程的时候需要注意以下几点：

-   存储过程可以包含条件语句、循环鱼护、异常处理等高等语句，从而实现复杂的逻辑操作。

-   存储过程可以使用参数进行灵活的数据传递，可以大大减少重复代码的编译。

-   存储过程可以优化性能，因为它们是预编译的，而不必每次执行都编译一次。

-   存储过程可以使用 GRANT 和 REVOKE 命令来控制用户对于存储过程的访问权限。

注意：在使用存储过程时，需要注意安全性问题，例如防止 sql 主语攻击等。同时，在设计存储过程时需要注意遵循良好的编程规范和最佳实践，以保证存储过程的可读性、可维护型和性能优化性。

> ### 触发器

触发器（Trigger）是一种特殊的存储过程，它会在指定的表上自动执行，通常是插入、更新、删除数据时触发。触发器可以用于强制实施业务规则、保护数据完整性、记录日志等。

在 mysql 中可以使用 create trigger 语句来创建触发器

```sql
create trigger log_insert after insert on customer
for each row
begin
    insert into log (event_type, table_name, row_id) values ('insert',  'customer', new.customer_id)
```

以上 sql 语句中， 创建一个名为 log_insert 触发器，每次向 customer 表插入数据的时候，将事件类型、表名称和行记录到 log 表

使用触发器时注意以下几个点：

-   触发器可以对数据进行实时处理，可以用于入数据校验、数据转换等功能。

-   触发器可以保护数据库完整性，从而避免非法或重复数据的插入、更新和删除。

-   触发器可以记录日志、审计、跟踪修改等操作，有助于数据管理和监管。

-   触发器可以嵌套使用，可以互相引用和触发，从而实现复杂的逻辑

需要注意的是：在使用触发器时需要谨慎考虑其对性能的影响，因为触发器在每次数据操作时都会被执行。与此同时，在创建触发器的时候需要遵循良好的编程规范和最佳实践，以保证其可读性、可维护性和性能优化。

> ### 赋予权限和收回权限

在 mysql 中，可以使用 GRANT 命令来授权用户特定的权限，从而允许他们访问数据库对象或执行操作，语法如下：

```sql
grant privileges on database_name.object_name to user_name@host_name [with grant option]
```

其中，privileges 表示要授予的权限，如 select、insert、update、create、drop 等；database_name 和 object_name 表示数据库和表名，可以使用通配符\*表示所有数据或表；user_name 和 host_name 分别表示用户和主机名，可以使用通配符%表示所有主机。

现在对 user1 授予读取 customer 表的权限：

```sql
grant select on mydb.customers to user1@'localhost'
```

需要注意的是 grant 命令的执行者必须是具有 grant option 权限才能将授予的权限转移给其他用户，因此，如果不希望其他用户获得类似的权利，则可以忽略 with grant option 参数。

除了 grant 命令外，还可以使用 revoke 命令撤销用户的权限，语法如下：

```sql
revoke privileges on database_name.object_name from user_name@host_name
```

其中， privileges、 database_name、object_name、user_name、和 host_name 的含义用户 grant 命令相同。

注意:在授予或撤销用户权限时，应该根据时机需要来分配最低权限原则，以保证数据库的安全性和稳定性。

> ### 事务

事务是把多个增删改查的操作做成不可分割的原子性操作。要么全做，要么全都不做

事务是一组数据库操作，他们被视为一个单独的工作单元，并作为整体进行提交或回滚。使用事务可以确保数据的一致性和完整性，防止不完整或不正确的操作对数据库造成的影响。

在 Mysql 中，可以使用 BEGIN、COMMIT 和 ROLLBACK 语句来控制事务的开始、结束和回滚，例如：

```sql
BEFIN;
UPDATE account SET balance = balance - 100 where customer_id = 122;
update account set balance = balance + 100 where customer_id = 233;
commit;
```

以上 sql 中，使用 BEGIN 开始一个新事务，在该事务中一次执行两个 UPDATE 语句，最后使用 commit 提交事务。如果在事务执行期间发生错误或异常，可以使用 ROLLBACK 回滚事务，从而撤销先前的修改。

注意：mysql 支持四种事务隔离级别，分别为 read uncommitted、 read committed、 repeatable read 和 serializale。不同隔离级别具有不同的特点和应用场景，应根据实际需求进行选择和配置。

当使用事务时需要注意的是：

- 应该将事务操作限制在必要的范围内，以避免不必要的锁定和性能开销。

- 应该定期清理无用的事务内存或锁定，以减少资源占用和冲突。

- 应该避免长时间占用事务、不释放锁定和导致死锁等问题。
