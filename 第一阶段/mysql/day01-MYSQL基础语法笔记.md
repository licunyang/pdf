# MYSQL基础语法
## 学习目标
1. 能够理解数据库的概念
2. 能够安装MySQL数据库
3. 能够启动,关闭及登录MySQL
4. 能够使用SQL语句操作数据库
5. 能够使用SQL语句操作表结构
6. 能够使用SQL语句进行数据的添加修改和删除的操作
7. 能够使用SQL语句简单查询数据


# 第1章 数据库的介绍
## 1.1 数据库概述
### 1.1.1 什么是数据库
​	存储数据的仓库. 其本质是一个文件系统，数据库按照特定的格式将数据存储起来，用户可以对数据库中的数据进行增加，修改，删除及查询操作。
### 1.1.2 数据的存储方式
1. **数据保存在内存**

   例如:数组,集合;new出来的对象存储在堆中.堆是内存中的一小块空间

   优点：内存速度快
   缺点：断电/程序退出,数据就清除了.内存价格贵

2. **数据保存在普通文件**
   优点：永久保存
   缺点：查找，增加，修改，删除数据比较麻烦，效率低

3. **数据保存在数据库**
   优点：永久保存,通过SQL语句比较方便的操作数据库

## 1.2 数据库的优点
​	数据库是按照特定的格式将数据存储在文件中，通过SQL语句可以方便的对大量数据进行增、删、改、查操作，数据库是对大量的信息进行管理的高效的解决方案。

## 1.3 数据库管理系统

​	数据库管理系统（DataBase Management System，**DBMS**）：指一种操作和管理数据库的大型软件，用于建立、使用和维护数据库，对数据库进行统一管理和控制，以保证数据库的安全性和完整性。用户通过数据库管理系统访问数据库中表内的数据

## 1.4 数据库管理系统、数据库和表的关系

​	数据库管理程序(DBMS)可以管理多个数据库，一般开发人员会针对每一个应用创建一个数据库。为保存应用中实体的数据，一般会在数据库创建多个表，以保存程序中实体的数据。数据库管理系统、数据库和表的关系如图所示：
![DBMS](image\DBMS.png)

先有数据库 → 再有表 → 再有数据
一个库包含多个表

## 1.5 实体类与表的对应关系

![实体类与表的对应关系](image\实体类与表的对应关系.png)

## 1.6 常见数据库

![常见数据库](image\常见数据库.PNG)
**MYSQL**：开源免费的数据库，小型的数据库.已经被Oracle收购了.MySQL6.x版本也开始收费。
**Oracle**：收费的大型数据库，Oracle公司的产品。Oracle收购SUN公司，收购MYSQL。
**DB2** ：IBM公司的数据库产品,收费的。常应用在银行系统中.
**SQLServer**：MicroSoft 公司收费的中型的数据库。C#、.net等语言常使用。
**SyBase**：已经淡出历史舞台。提供了一个非常专业数据建模的工具PowerDesigner。
**SQLite**: 嵌入式的小型数据库，应用在手机端。

**常用数据库**：**MYSQL**，**Oracle**
在web应用中，使用的最多的就是MySQL数据库，原因如下：

1. 开源、免费
2. 功能足够强大，足以应付web应用开发

# 第2章 MYSQL的安装,卸载与使用

## 2.1 MYSQL的安装和卸载

详见"MYSQL的安装和卸载.pdf"

## 2.2 数据库的启动
  MySQL启动方式和普通的windows程序双击启动方式不同，分为以下2种：

1. Windows服务方式启动
      操作步骤：
      ![mysql启动01](image\mysql启动01.png)
      ![mysql启动02](image\mysql启动02.png)
2. DOS命令方式启动
    操作步骤：
    ![mysql启动03](image\mysql启动03.png)
    ![mysql启动04](image\mysql启动04.png)

    启动MYSQL: `net start mysql`
    停止MYSQL: `net stop mysql`


## 2.3 控制台连接数据库
​	MySQL是一个需要账户名密码登录的数据库，登陆后使用，它提供了一个默认的root账号，使用安装时设置的密码即可登录,常见的登录方式有以下几种:掌握其中一种即可
1. 登录格式1：`mysql -u用户名 -p密码`
   例如：`mysql –uroot -proot`
   ![MYSQL登录01](image\MYSQL登录01.png)
   后输入密码方式：

   `mysql -u用户名 -p回车`

   `密码`

   ![MYSQL登录04](image\MYSQL登录04.png)

2. 登录格式2：`mysql -hip地址 -u用户名 -p密码`
   例如：`mysql –h127.0.0.1 –uroot -proot`
   ​

3. 登录格式3：`mysql --host=ip地址 --user=用户名 --password=密码`
   例如：`mysql --host=localhost --user=root --password=root`
   ​

   退出MySQL：`exit`
   ![MYSQL登录03](image\MYSQL退出01.png)




# 第3章 SQL语句
## 3.1 SQL的概念
### 3.1.1 什么是SQL
​	结构化查询语言(Structured Query Language)简称SQL,SQL语句就是对数据库进行操作的一种语言。
### 3.1.2 SQL作用
​	通过SQL语句我们可以方便的操作数据库中的数据、表、数据库。
​	SQL是数据库管理系统都需要遵循的规范。不同的数据库生产厂商都支持SQL语句，但都有特有内容。
![SQL规范](image\SQL规范.png)

### 3.1.2 SQL语句分类
1. DDL(Data Definition Language)数据定义语言
   用来定义数据库对象：数据库，表，列等。关键字：create, drop,alter等

2. DML(Data Manipulation Language)数据操作语言
   用来对数据库中表的数据进行增删改。关键字：insert, delete, update等

3. DCL(Data Control Language)数据控制语言(了解)

   用来定义数据库的访问权限和安全级别，及创建用户。关键字：GRANT， REVOKE等

4. TCL(Transaction Control Language) 事务控制语言

​      用于控制数据库的事务操作，关键字; COMMIT，SAVEPOINT，ROLLBACK等

5. DQL(Data Query Language) 数据查询语言 (掌握)

   DQL语言并不是属于MYSQL官方的分类，但是对数据库的操作最多就是查询，所以

   我们的程序员把查询语句的语句称作为DQL语言

## 3.2 SQL通用语法
1. SQL语句可以单行或多行书写，以分号结尾。
2. 可使用空格和缩进来增强语句的可读性。
3. MySQL数据库的SQL语句不区分大小写，关键字建议使用大写。
   ```sql
   SELECT * FROM student;
   ```
4. 3种注释
   单行注释: -- 注释内容 或 # 注释内容(mysql特有)
   多行注释: /* 注释 */
## 3.3 DDL语句
### 3.3.1 DDL操作数据库
#### 3.3.1.1 创建数据库
1. 直接创建数据库
   `CREATE DATABASE 数据库名;`

2. 判断是否存在并创建数据库(了解)
   `CREATE DATABASE IF NOT EXISTS 数据库名;`

3. 创建数据库并指定字符集(了解)
   `CREATE DATABASE 数据库名 CHARACTER SET 字符集;`

4. 具体操作：
* 直接创建数据库db1
  ```sql
  CREATE DATABASE db1;
  ```
  ![直接创建数据库](image\直接创建数据库.png)

* 判断是否存在并创建数据库db2
  ```sql
  CREATE DATABASE IF NOT EXISTS db2;
  ```
  ![判断是否存在并创建数据库](image\判断是否存在并创建数据库.png)

* 创建数据库并指定字符集为gbk
  ```sql
  CREATE DATABASE db2 CHARACTER SET gbk;
  ```
  ![创建数据库并指定字符集](image\创建数据库并指定字符集.png)

#### 3.3.1.2 查看数据库
1. 查看所有的数据库
   `SHOW databases;`
   ![查看所有数据库](image\查看所有数据库.png)

2. 查看某个数据库的定义信息
   `SHOW CREATE DATABASE 数据库名;`
   ![查看某个数据库的定义信息](image\查看某个数据库的定义信息.png)

#### 3.3.1.3 修改数据库(了解)

修改数据库字符集格式

`ALTER DATABASE 数据库名 DEFAULT CHARACTER SET 字符集;`

具体操作：
* 将db3数据库的字符集改成utf8
  ```sql
  ALTER DATABASE db3 DEFAULT CHARACTER SET utf8;
  ```
  ![修改数据库字符集](image\修改数据库字符集.png)
#### 3.3.1.4 删除数据库
`DROP DATABASE 数据库名;`

具体操作：
* 删除db2数据库
  ```sql
  DROP DATABASE db2;
  ```
  ![删除数据库](image\删除数据库.png)

#### 3.3.1.5 使用数据库
1. 查看正在使用的数据库
   `SELECT DATABASE();`
2. 使用/切换数据库
   `USE 数据库名;`

具体操作：
* 查看正在使用的数据库
  ```sql
  SELECT DATABASE();
  ```
  ![查看正在使用的数据库](image\查看正在使用的数据库.png)
* 使用db1数据库
  ```sql
  USE db1;
  ```
  ![使用db1数据库](image\使用db1数据库.png)

### 3.3.2 DDL操作表
>**前提先使用某个数据库**
#### 3.3.2.1 创建表
`CREATE TABLE 表名 (字段名1 字段类型1, 字段名2 字段类型2…);`

建议写成如下格式:
```sql
CREATE TABLE 表名 (
字段名1 字段类型1, 
字段名2 字段类型2
);
```
**MySQL数据类型**
MySQL中的我们常使用的数据类型如下：
![MYSQL常用数据类型](image\MYSQL常用数据类型.png)

详细的数据类型如下(不建议详细阅读！)
| 分类       | 类型名称         | 说明                                       |
| :------- | :----------- | :--------------------------------------- |
| 整数类型     | tinyInt      | 很小的整数                                    |
|          | smallint     | 小的整数                                     |
|          | mediumint    | 中等大小的整数                                  |
|          | int(integer) | 普通大小的整数                                  |
| 小数类型     | float        | 单精度浮点数                                   |
|          | double       | 双精度浮点数                                   |
|          | decimal（m,d） | 压缩严格的定点数                                 |
| 日期类型     | year         | YYYY  1901~2155                          |
|          | time         | HH:MM:SS  -838:59:59~838:59:59           |
|          | date         | YYYY-MM-DD 1000-01-01~9999-12-3          |
|          | datetime     | YYYY-MM-DD HH:MM:SS 1000-01-01 00:00:00~ 9999-12-31 23:59:59 |
|          | timestamp    | YYYY-MM-DD HH:MM:SS  1970~01~01 00:00:01 UTC~2038-01-19 03:14:07UTC |
| 文本、二进制类型 | CHAR(M)      | M为0~255之间的整数                             |
|          | VARCHAR(M)   | M为0~65535之间的整数                           |
|          | TINYBLOB     | 允许长度0~255字节                              |
|          | BLOB         | 允许长度0~65535字节                            |
|          | MEDIUMBLOB   | 允许长度0~167772150字节                        |
|          | LONGBLOB     | 允许长度0~4294967295字节                       |
|          | TINYTEXT     | 允许长度0~255字节                              |
|          | TEXT         | 允许长度0~65535字节                            |
|          | MEDIUMTEXT   | 允许长度0~167772150字节                        |
|          | LONGTEXT     | 允许长度0~4294967295字节                       |
|          | VARBINARY(M) | 允许长度0~M个字节的变长字节字符串                       |
|          | BINARY(M)    | 允许长度0~M个字节的定长字节字符串                       |


具体操作: 

创建student表包含id,name,birthday字段

```sql
CREATE TABLE student (
      id INT,
      name VARCHAR(20),
      birthday DATE
);
```

#### 3.3.2.2 查看表
1. 查看某个数据库中的所有表
   `SHOW TABLES;`

2. 查看表结构
   `DESC 表名;`

3. 查看创建表的SQL语句
   `SHOW CREATE TABLE 表名;`

  具体操作：
* 查看mysql数据库中的所有表
  ```sql
  SHOW TABLES;
  ```
  ![查看某个数据库中的所有表](image\查看某个数据库中的所有表.png)

* 查看student表的结构
  ```sql
  DESC student;
  ```
  ![查看student表的结构](image\查看student表的结构.png)
* 查看student的创建表SQL语句
  ```sql
  SHOW CREATE TABLE student;
  ```
  ![查看student的创建表SQL语句](image\查看student的创建表SQL语句.png)

#### 3.3.2.3 快速创建一个表结构相同的表
`CREATE TABLE 新表名 LIKE 旧表名;`

具体操作：
* 创建s1表，s1表结构和student表结构相同
  ```sql
  CREATE TABLE s1 LIKE student;
  ```
  ![创建表结构相同的表](image\创建表结构相同的表.png)

#### 3.3.2.4 删除表
1. 直接删除表
   `DROP TABLE 表名;`
2. 判断表是否存在并删除表(了解)
   `DROP TABLE IF EXISTS 表名;`

具体操作：
* 直接删除表s1表
  ```sql
  DROP TABLE s1;
  ```
  ![直接删除表](image\直接删除表.png)
* 判断表是否存在并删除s1表
  ```sql
  DROP TABLE IF EXISTS s1;
  ```
  ![判断表存在并删除](image\判断表存在并删除.png)

#### 3.3.2.5 修改表结构
> 修改表结构使用不是很频繁，只需要知道下，等需要使用的时候再回来查即可
1. 添加表列
   `ALTER TABLE 表名 ADD 列名 类型;`

   具体操作：
   * 为学生表添加一个新的字段remark,类型为varchar(20)
     ```sql
     ALTER TABLE student ADD remark VARCHAR(20);
     ```
     ![添加字段](image\添加字段.png)

2. 修改列类型
   `ALTER TABLE 表名 MODIFY 列名 新的类型;`
   具体操作：
   * 将student表中的remark字段的改成varchar(100)
     ```sql
     ALTER TABLE student MODIFY remark VARCHAR(100);
     ```
     ![修改字段类型](image\修改字段类型.png)

3. 修改列名
   `ALTER TABLE 表名 CHANGE 旧列名 新列名 类型;`
   具体操作：
   * 将student表中的remark字段名改成intro，类型varchar(30)
     ```sql
     ALTER TABLE student CHANGE remark intro varchar(30);
     ```
     ![修改表字段名称](image\修改表字段名称.png)

4. 删除列
   `ALTER TABLE 表名 DROP 列名;`
   具体操作：
   * 删除student表中的字段intro
     ```sql
     ALTER TABLE student DROP intro;
     ```
     ![删除字段](image\删除字段.png)

5. 修改表名
   `RENAME TABLE 表名 TO 新表名;`
   具体操作：
   * 将学生表student改名成student2
     ```sql
      RENAME TABLE student TO student2;
     ```
     ![修改表名](image\修改表名.png)

6. 修改字符集
   `ALTER TABLE 表名 character set 字符集;`
   具体操作：
   * 将sutden2表的编码修改成gbk
     ```sql
     ALTER TABLE student2 character set gbk;
     ```
      ![修改字符集](image\修改字符集.png)

## 3.4 DML语句
### 3.4.1 插入记录
#### 3.4.1.1 插入全部字段
* 所有的字段名都写出来
  `INSERT INTO 表名 (字段名1, 字段名2, 字段名3…) VALUES (值1, 值2, 值3);`
* 不写字段名
  `INSERT INTO 表名 VALUES (值1, 值2, 值3…);`

#### 3.4.1.2 插入部分数据
   `INSERT INTO 表名 (字段名1, 字段名2, ...) VALUES (值1, 值2, ...);`
   没有添加数据的字段会使用NULL

1. 关键字说明
   ```sql
   INSERT INTO 表名 – 表示往哪张表中添加数据
   (字段名1, 字段名2, …)  --  要给哪些字段设置值
   VALUES (值1, 值2, …); -- 设置具体的值
   ```

2. 注意
   >* 值与字段必须对应，个数相同，类型相同
   >* 值的数据大小必须在字段的长度范围内
   >* 除了数值类型外，其它的字段类型的值必须使用引号引起。（建议单引号）
   >* 如果要插入空值，可以不写字段，或者插入null

3. 具体操作:
   * 插入部分数据，往学生表中添加 id, name, age, sex数据
   ```sql
   INSERT INTO student (id, NAME, age, sex) VALUES (1, '张三', 20, '男');
   ```
   ![添加部分数据](image\添加部分数据.png)

   * 向表中插入所有字段
     * 所有的字段名都写出来
     ```sql
      INSERT INTO student (NAME, id, age, sex, address) VALUES ('李四', 2, 23, '女', '广州');
     ```
     ![所有字段都添加数据](image\所有字段都添加数据.png)

     * 不写字段名
     ```sql
     INSERT INTO student VALUES (3, '王五', 18, '男', '北京');
     ```
     ![添加所有字段数据](image\添加所有字段数据.png)

#### 3.4.1.3 DOS命令窗口操作数据乱码问题的解决
>当我们使用DOS命令行进行SQL语句操作如有有中文会出现乱码，导致SQL执行失败
>![DOS中文乱码01](image\DOS中文乱码01.png)
>错误原因:因为MySQL的客户端设置编码是utf8,而系统的DOS命令行编码是gbk，编码不一致导致的乱码
>![DOS中文乱码02](image\DOS中文乱码02.png)

查看 MySQL 内部设置的编码
`show variables like 'character%';`
![DOS中文乱码03](image\DOS中文乱码03.png)

解决方案：修改client、connection、results的编码为GBK，保证和DOS命令行编码保持一致
1. 单独设置
   ```sql
   set character_set_client=gbk; 
   set character_set_connection=gbk;
   set character_set_results=gbk;
   ```
2. 快捷设置
   ```sql
   set names gbk;
   ```
   > 注意：以上2种方式为临时方案，退出DOS命令行就失效了，需要每次都配置

3. 修改MySQL安装目录下的my.ini文件，重启服务所有地方生效。此方案将所有编码都修改了
   ![DOS中文乱码04](image\DOS中文乱码04.png)

#### 3.4.1.4 蠕虫复制
什么是蠕虫复制：在已有的数据基础之上，将原来的数据进行复制，插入到对应的表中
语法格式：`INSERT INTO 表名1 SELECT * FROM 表名2;`
作用:将`表名2`中的数据复制到`表名1`中

具体操作:
* 创建student2表，student2结构和student表结构一样
```sql
CREATE TABLE student2 LIKE student;
```
* 将student表中的数据添加到student2表中
```sql
INSERT INTO student2 SELECT * FROM student;
```
>注意：如果只想复制student表中name,age字段数据到student2表中使用如下格式
>`INSERT INTO student2(NAME, age) SELECT NAME, age FROM student;`
>![蠕虫复制](image\蠕虫复制.png)

### 3.4.2 更新表记录
1. 不带条件修改数据
   `UPDATE 表名 SET 字段名=值;`
2. 带条件修改数据
   `UPDATE 表名 SET 字段名=值 WHERE 字段名=值;`

3. 关键字说明
   ```sql
   UPDATE: 修改数据
   SET: 修改哪些字段
   WHERE: 指定条件
   ```
4. 具体操作：
   * 不带条件修改数据，将所有的性别改成女
     ```sql
     UPDATE student SET sex='女';
     ```
     ![修改所有数据](image\修改所有数据.png)

   * 带条件修改数据，将id号为2的学生性别改成男
     ```sql
     UPDATE student SET sex='男' WHERE id=2;
     ```
     ![带条件修改](image\带条件修改.png)

   * 一次修改多个列，把id为3的学生，年龄改成26岁，address改成北京
     ```sql
     UPDATE student SET age=26, address='北京' WHERE id=3;
     ```
     ![一次性修改2个字段](image\一次性修改2个字段.png)

### 3.4.3 删除表记录
1. 不带条件删除数据
   `DELETE FROM 表名;`

2. 带条件删除数据
   `DELETE FROM 表名 WHERE 字段名=值;`

3. truncate删除表记录
   `TRUNCATE TABLE 表名;`
   >truncate和delete的区别：
   >* delete是将表中的数据一条一条删除
   >* truncate是将整个表摧毁，重新创建一个新的表,新的表结构和原来表结构一模一样
   >  ![truncate](image\truncate.png)

4. 具体操作：
   * 带条件删除数据，删除id为3的记录
     ```sql
     DELETE FROM student WHERE id=3;
     ```

     ![删除满足条件的记录](image\删除满足条件的记录.png)

   * 不带条件删除数据,删除表中的所有数据
     ```sql
     DELETE FROM student;
     ```
     ![删除所有记录](image\删除所有记录.png)

## 3.5 DQL
>查询不会对数据库中的数据进行修改.只是一种显示数据的方式
### 3.5.1 简单查询
#### 3.5.1.1 查询表所有数据
1. 使用*表示所有列
   `SELECT * FROM 表名;`
   具体操作：
   ```sql
   SELECT * FROM student;
   ```
   ![查询所有列](image\查询所有列.png)

2. 写出查询每列的名称
   `SELECT 字段名1, 字段名2, 字段名3, ... FROM 表名;`
   具体操作：
   ```sql
   SELECT id, NAME ,age, sex, address FROM student;
   ```
   ![查询所有列](image\查询所有列.png)

#### 3.5.1.2 查询指定列
查询指定列的数据,多个列之间以逗号分隔
`SELECT 字段名1, 字段名2... FROM 表名;`

具体操作：
查询student表中的name 和 age 列
```sql
SELECT NAME, age FROM student;
```
![查询指定字段](image\查询指定字段.png)

#### 3.5.1.3 别名查询
1. 查询时给列、表指定别名需要使用AS关键字
2. 使用别名的好处是方便观看和处理查询到的数据
   `SELECT 字段名1 AS 别名, 字段名2 AS 别名... FROM 表名;`
   `SELECT 字段名1 AS 别名, 字段名2 AS 别名... FROM 表名 AS 表别名;`
   注意:
   >查询给表取别名目前还看不到效果，需要到多表查询的时候才能体现出好处
   >AS关键字可以省略

3. 具体操作：
   * 查询sudent表中name 和 age 列，name列的别名为”姓名”，age列的别名为”年龄”
   ```sql
   SELECT NAME AS 姓名, age AS 年龄 FROM student;
   ```
   ![查询字段别名](image\查询字段别名.png)
   * 查询sudent表中name和age列，student表别名为s
   ```sql
   SELECT NAME, age FROM student AS s;
   ```
   ![查询表别名](image\查询表别名.png)
   >查询给表取别名目前还看不到效果，需要到多表查询的时候才能体现出好处

#### 3.5.1.4 清除重复值
1. 查询指定列并且结果不出现重复数据
   `SELECT DISTINCT 字段名 FROM 表名;`
2. 具体操作：
   * 查询name，age列并且结果不出现重复name和age
   ```sql
   SELECT DISTINCT NAME, age FROM student;
   ```
   ![取出重复数据](image\取出重复数据.png)

#### 3.5.1.5 查询结果参与运算
1. 某列数据和固定值运算
   `SELECT 列名1 + 固定值 FROM 表名;`
2. 某列数据和其他列数据参与运算
   `SELECT 列名1 + 列名2 FROM 表名;`
   >注意: 参与运算的必须是数值类型

3. 需求：
   * 添加数学，英语成绩列,给每条记录添加对应的数学和英语成绩
   * 查询的时候将数学和英语的成绩相加

4. 实现：

* 修改student表结构,添加数学和英语成绩列
  ```sql
  ALTER TABLE student ADD math INT;
  ALTER TABLE student ADD english INT;
  ```
* 给每条记录添加对应的数学和英语成绩
     ![添加数学和英语成绩](image\添加数学和英语成绩.png)
* 查询math + english的和
  ```sql
  SELECT math + english FROM student;
  ```
  ![查询math和english的和](image\查询math和english的和.png)
  >结果确实将每条记录的math和english相加，但是效果不好看

* 查询math + english的和使用别名”总成绩”
  ```sql
  SELECT math + english 总成绩 FROM student;
  ```
  ![组合查询结果取别名](image\组合查询结果取别名.png)

* 查询所有列与math + english的和并使用别名”总成绩”
  ```sql
  SELECT *, math + english 总成绩 FROM student;
  ```
  ![查询所有列数据和参与运算](image\查询所有列数据和参与运算.png)

* 查询姓名、年龄，将每个人的年龄增加10岁
  ```sql
  SELECT name, age + 10 FROM student;
  ```
  ![查询后年龄增加10岁](image\查询后年龄增加10岁.png)