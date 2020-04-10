# mysql-final-test

2019-2020 mysql final test

姓名：竺雷
学号：17061636

说明1：考试为开卷，可以上网，自觉不要相互电话和QQ；

说明2：考试时间为：2020 年 4 月 10 日 8:10分-9:40分。

说明3：试题比较多，抓紧时间，超时提交的github commit不被接受。未避免完全超时提交，可以在做题过程中多 commit 几次。

说明4：结束后发邮件给 42225@hdu.edu.cn 标题为“MySQL期末考试,姓名+学号”，内容为github链接。


1 打印当前时间（例如 2020-04-07 13:41:42），写出SQL语句和结果
```sql
mysql> select now();
+---------------------+
| now()               |
+---------------------+
| 2020-04-10 08:02:48 |
+---------------------+
1 row in set (0.00 sec)
```

2 组合打印自己的姓名和学号(例如 张三+123456 或者 zhangsan+123456 显示需包含加号)，写出SQL语句和结果
```
mysql> SELECT 'zhulei+17061636';
+-----------------+
| zhulei+17061636 |
+-----------------+
| zhulei+17061636 |
+-----------------+
1 row in set (0.00 sec)
```

3 建立如下表1和表2，写出建表语句和插入语句。

表1：其中deptno为主键
```
deptno,dname,loc
(10, "ACCOUNTING", "NEW YORK"),
(20, "RESEARCH", "DALLAS"),
(30, "SALES", "CHICAGO"),
(40, "OPERATIONS", "BOSTON")
```
```
mysql> create table test1(deptno int NOT NULL,dname varchar(20),loc varchar(20),UNIQUE(deptno));
Query OK, 0 rows affected (0.04 sec)
mysql> insert into test1 values
    -> (10, "ACCOUNTING", "NEW YORK"),(20, "RESEARCH", "DALLAS"),(30, "SALES", "CHICAGO"),(40, "OPERATIONS", "BOSTON");
Query OK, 4 rows affected (0.01 sec)
mysql> select * from test1;
+--------+------------+----------+
| deptno | dname      | loc      |
+--------+------------+----------+
|     10 | ACCOUNTING | NEW YORK |
|     20 | RESEARCH   | DALLAS   |
|     30 | SALES      | CHICAGO  |
|     40 | OPERATIONS | BOSTON   |
+--------+------------+----------+
4 rows in set (0.00 sec)
```

表2：其中empno字段为主键
```
        empno, ename,    job,    MGR,   Hiredate,    sal,   comm, deptno
        (7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
	(7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
	(7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
	(7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
	(7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
	(7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
	(7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
	(7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
	(7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
	(7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
	(7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10)
```
```
mysql> create table test2(deptno int NOT NULL,empno int PRIMARY KEY,ename varchar(20),job varchar(20),MGR int,Hiredate date,sal float,comm float);
mysql> INSERT INTO test2 (empno, ename, job, MGR, Hiredate, sal, comm, deptno) VALUES
    -> (7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),(7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),(7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),(7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),(7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),(7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),(7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),(7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),(7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),(7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),(7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),(7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),(7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10);
Query OK, 13 rows affected (0.00 sec)
mysql> select * from test2;
+--------+-------+--------+-----------+------+------------+------+------+
| deptno | empno | ename  | job       | MGR  | Hiredate   | sal  | comm |
+--------+-------+--------+-----------+------+------------+------+------+
|     20 |  7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |
|     30 |  7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |
|     30 |  7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |
|     20 |  7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |
|     30 |  7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |
|     10 |  7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |
|     20 |  7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |
|     10 |  7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |
|     30 |  7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |
|     20 |  7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |
|     30 |  7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |
|     20 |  7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |
|     10 |  7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |
+--------+-------+--------+-----------+------+------------+------+------+
13 rows in set (0.00 sec)
```

3.1 表2 中再插入一条记录：
(你的学号，你的姓名或者拼音， “CLERK”, 7782, 你的生日,  NULL, NULL, 10)
例如：(12345,  "Zhangsan", "sTUDENT", 7782, "2000-03-12", NULL, NULL, 10)
```
mysql> insert into test2 values
    -> (10,17061636,"zhulei","student",7782,"1998-11-25",NULL,NULL);
Query OK, 1 row affected (0.00 sec)
```

3.2 表中入职时间（Hiredate字段）最短的人。
```
--不考虑学生本人
mysql> select * from test2 where Year(Hiredate)>1981;
+--------+----------+--------+----------+------+------------+------+------+
| deptno | empno    | ename  | job      | MGR  | Hiredate   | sal  | comm |
+--------+----------+--------+----------+------+------------+------+------+
|     30 |     7499 | ALLEN  | SALESMAN | 7698 | 1982-03-12 | 1600 |  300 |
|     10 |     7698 | BLAKE  | MANAGER  | 7839 | 1985-03-12 | 2450 | NULL |
|     10 | 17061636 | zhulei | student  | 7782 | 1998-11-25 | NULL | NULL |
+--------+----------+--------+----------+------+------------+------+------+
3 rows in set (0.00 sec)
--可知入职最短的是BLAKE
```

3.3 有几种职位（job字段）？在关系代数中，本操作是什么运算？
答：不考虑学生本人的情况下，有CLERK,SALESMAN,MANAGER,ANALYST,PRESIDENT这几种职位。
在关系代数中，本操作是投影。

3.4 将 MILLER 的 comm 增加 100； 然后，找到 comm 比 MILLER 低的人；
```
mysql> update test2
    -> set comm = 1000
    -> where
    -> ename = 'MILLER';
Query OK, 1 row affected (0.01 sec)
mysql> select * from test2 WHERE comm < 1000;
+--------+-------+--------+----------+------+------------+------+------+
| deptno | empno | ename  | job      | MGR  | Hiredate   | sal  | comm |
+--------+-------+--------+----------+------+------------+------+------+
|     30 |  7499 | ALLEN  | SALESMAN | 7698 | 1982-03-12 | 1600 |  300 |
|     30 |  7521 | WARD   | SALESMAN | 7698 | 1838-03-12 | 1250 |  500 |
|     30 |  7844 | TURNER | SALESMAN | 7689 | 1981-03-12 | 1500 |    0 |
+--------+-------+--------+----------+------+------------+------+------+
3 rows in set (0.00 sec)
```

3.5 计算每个人的收入(ename, sal + comm)；计算总共有多少人；计算所有人的平均收入。 提示：计算时 NULL 要当做 0 处理； 
```

```


3.6 显示每个人的下属, 没有下属的显示 NULL。本操作使用关系代数中哪几种运算？

3.7 建立一个视图：每个人的empno, ename, job 和 loc。简述为什么要建立本视图。

3.8 为表2增加一个约束：deptno字段需要在表1中存在；这称做什么完整性？

3.9 为表2增加一个索引：ename 字段。简述为什么要在 ename 字段建立索引

3.10 将表2的 sal 字段改名为 salary
```
ALTER TABLE test2 CHANGE sal salary INT;
```

3.11 撰写一个函数 get_deptno_from_empno，输入 empno，输出对应的 deptno。 简述函数和存储过程有什么不同。

4 建立一个新用户，账号为自己的姓名拼音，密码为自己的学号；
```
mysql> create user 'zhulei'@'localhost' identified by '17061636';
Query OK, 0 rows affected (0.00 sec)
```

4.1 将表1的SELECT, INSERT, UPDATE(ename)权限赋给该账号。
```
--test为数据库名称
mysql> grant select on test.* to 'zhulei'@'localhost';
Query OK, 0 rows affected (0.00 sec)
mysql> grant insert on test.* to 'zhulei'@'localhost';
Query OK, 0 rows affected (0.00 sec)
mysql> grant update on test.* to 'zhulei'@'localhost';
Query OK, 0 rows affected (0.00 sec)
```

4.2 显示该账号权限
```
mysql> show grants for 'zhulei'@'localhost';
+------------------------------------------------------------------+
| Grants for zhulei@localhost                                      |
+------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'zhulei'@'localhost'                       |
| GRANT SELECT, INSERT, UPDATE ON `test`.* TO 'zhulei'@'localhost' |
+------------------------------------------------------------------+
2 rows in set (0.00 sec)
```

4.3 `with grant option` 是什么意思。
答：权限传递，使用这个子句时将允百许用户将其权限分配给度他人。

5 表 1 和表 2 这样设计是否符合第一范式，是否符合第二范式，为什么？
答：表1符合第一范式也符合第二范式，因为表内无重复，各数据可被唯一区分。表2符合第一范式但不符合第二范式，因为表内无重复，但没有存储各个数据的唯一标识。

6 画出表 1 和表 2 所对应的 E-R 图


7 什么是外模式，什么是内模式。为什么要分成这几层？
答：外模式又称子模式或用户模式，对应于用户级。它是某个或某几个用户所看到的数据库的数据视图，是与某一应用有关的数据的逻辑表示。外模式是从模式导出的一个子集，包含模式中允许特定用户使用的那部分数据。用户可以通过外模式描述语言来描述、定义对应于用户的数据记录(外模式)，也可以利用数据操纵语言(Data Manipulation Language，DML)对这些数据记录进行操作。外模式反映了数据库系统的用户观。
内模式又称存储模式，对应于物理级。它是数据库中全体数据的内部表示或底层描述，是数据库最低一级的逻辑描述，它描述了数据在存储介质上的存储方式和物理结构，对应着实际存储在外存储介质上的数据库。内模式由内模式描述语言来描述、定义的。内模式反映了数据库系统的存储观。
数据库领域公认的标准结构是三级模式结构，它包括外模式、概念模式、内模式。三级模式结构有效地组织、管理数据，提高了数据库的逻辑独立性和物理独立性。用户级对应外模式，概念级对应概念模式，物理级对应内模式，使不同级别的用户对数据库形成不同的视图。

8 什么是ACID？
答：ACID，指数据库事务正确执行的四个基本要素的缩写。包含：原子性（Atomicity）、一致性（Consistency）、隔离性（Isolation）、持久性（Durability）。一个支持事务（Transaction）的数据库，必须要具有这四种特性，否则在事务过程（Transaction processing）当中无法保证数据的正确性，交易过程极可能达不到交易方的要求。

8.1 编写一个事务，“将 MILLER 的 comm 增加 100，如果增加后的 comm 大于 1000 则回滚”；
```
DELIMITER $$
CREATE FUNCTION func_test2_comm (comm INT)
RETURNS DOUBLE
BEGIN
update test2 set comm = comm + 100 where (SELECT comm FROM test2 WHERE test2.ename = 'MILLER') < 1000;
END$$
DELIMITER ;
```

8.2 如何查看 MySQL 当前的隔离级别？
答：show variables like 'transaction_isolation';或者select @@transaction_isolation;

8.3 如果隔离级别为 READ-UNCOMMITED, 完成 “MILLER 的 comm 增加 100” 事务操作完成后，可能读到的结果有哪些，原因是什么？
答：结果1:读到comm增加100。创建了事务，未提交或者已提交都可能出现这个结果。
结果2:读到没有增加100的comm。创建了事务，但是回滚了。
根本原因是隔离级别为 只读-不写 ，无权限操作数据。

9 有哪些场景不适合用关系型数据库？为什么？
答：关系型数据库的缺点：1）不擅长大量数据的写入处理2）不擅长为有数据更新的表做索引或表结构（schema）变更3）不擅长对简单查询需要快速返回结果的处理
所以不适合场景：1）海量数据存储；2）多格式的数据存储；
