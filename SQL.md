# 数据库的操作

## 创建数据库

- 基本语法

  ```sql
  CREATE DATABASE 数据库名 [CHARACTER SET 字符集] [COLLATE 校验规则]
  ```

  **在创建数据库、表的时候，为了规避关键字，可以使用反引号**

  ```sql
  CREATE DATABASE `CREATE`
  ```

- 字符集

  |  字符集   | 描述 |
  | :-------: | :--: |
  | utf8 默认 |      |
  |    gbk    |      |

- 排序规则/校对规则

  |  排序规则/校对规则   |     描述     |
  | :------------------: | :----------: |
  |       utf8_bin       |  区分大小写  |
  | utf8_general_ci 默认 | 不区分大小写 |

- 应用案例

  - 案例1：创建一个 mysql01 数据库

    ```sql
    CREATE DATABASE mysql01
    ```

  - 案例2：创建一个使用 utf8 字符集的 mysql01 数据库

    ```sql
    CREATE DATABASE mysql01 CHARACTER SET utf8
    ```

  - 案例3：创建一个使用 utf8 字符集，并带校验规则 utf8_bin 的 mysql01 数据库

    ```sql
    CREATE DATABASE mysql01 CHARACTER SET utf8 COLLATE utf8_bin
    ```

## 查看数据库

- 基本语法

  ```sql
  SHOW DATABASES
  ```

- 常用语法

  显示数据库创建语句

  ```sql
  SHOW CREATE DATABASE 数据库名
  ```

## 删除数据库

- 基本语法

  ```sql
  DROP DATABASE 数据库名
  ```
  

# 备份与恢复数据

## 备份数据库/表

- 基本语法

  - 备份数据库

    ```doc
    mysqldump -u 用户名 -p -B 数据库1 数据库2 数据库n > 路径/文件名.sql
    ```

  - 备份数据表

    ```sql
    mysqldump -u 用户名 -p 数据库 表1 表2 表n > 路径/文件名.sql
    ```
  
  mysqldump 指令在 mysql/bin/ 下
  
- 应用案例

  - 案例1：

    ```sql
    
    ```

  - 案例2：

    ```sql
    
    ```

## 恢复数据

- 方法1：

  ```sql
  srouce 路径/文件名.sql
  ```

- 方法2：图形化界面

# 基本数据类型

## 整数类型

| 整数类型  | 占用字节 | 表示范围 |
| :-------: | :------: | :------: |
|  TINYINT  |  1字节   |          |
| SMALLINT  |  2字节   |          |
| MEDIUMINT |  3字节   |          |
|    INT    |  4字节   |          |
|  BIGINT   |  8字节   |          |

## 浮点类型

|   浮点类型   | 占用字节 | 表示范围 |
| :----------: | :------: | :------: |
|    FLOAT     |  4字节   |          |
|    DOUBLE    |  8字节   |          |
| DECIMAL(m,d) |  不确定  |          |

## 字符串类型

| 字符串类型 |   长度   | 表示范围 |      |
| :--------: | :------: | :------: | ---- |
|    CAHR    | 固定长度 |          |      |
|  VARCHAR   | 可变长度 |          |      |
|    TEXT    | 可变长度 |          |      |
|  LONGTEXT  | 可变长度 |          |      |

## 日期类型

| 时间类型  | 描述 |
| :-------: | :--: |
|   DATE    |      |
|   TIME    |      |
| DATETIME  |      |
| TIMESTAMP |      |



## 二进制类型

| 二进制类型 |      | 描述 |
| :--------: | :--: | :--: |
|    BLOB    |      |      |
|  LONGBLOB  |      |      |

## 其他类型

# 表的操作

## 创建表

- 基本语法

  ```sql
  CREATE TABLE 表名(
      列名1 数据类型,
      列名2 数据类型,   
      列名n 数据类型	
  )[CHARACTER SET 字符集] [COLLATE 校对规则] [ENGINE 存储引擎]
  ```

  - table_name：表名，全部小写，多个单词分割用下划线_

  - engine：存储引擎，默认为 InnoDB

    **若字符集不指定和校对规则不指定，则视为数据库的字符集和校对规则**

- 应用案例：创建一个员工表 emp，选用适当的数据类型

  |    字段    |  数据类型   |
  | :--------: | :---------: |
  |     id     |     INT     |
  |    name    | VARCHAR(32) |
  |  Birthday  |    DATE     |
  | entry_time |  DATETIME   |
  |    job     | VARCHAR(32) |
  |   salary   |   DOUBLE    |
  |   resume   |    TEXT     |

  ```sql
  CREATE TABLE emp(
  	id INT,
  	`name` VARCHAR(32),
  	birthday DATE,
  	entry_time DATETIME,
  	job VARCHAR(32),
  	salary DOUBLE,
  	`resume` TEXT
  )CHARACTER SET utf8 COLLATE utf8_bin ENGINE INNODB;
  ```

## 删除表

- 基本语法

  ```sql
  DROP TABLE 表名
  ```

## 添加列

- 基本语法

  ```sql
  ALTER TABLE 表名
  ADD 列名 数据类型 
  ```

- 应用案例：在 emp 表的基础之上添加 image 列，varchar 类型（要求在 resume 后面）

  ```sql
  ALTER TABLE emp
  ADD	image VARCHAR(32) NOT NULL DEFAULT ''
  AFTER `resume`
  ```

## 修改列

- 修改列属性
	
	- 基本语法
	
	  ```sql
	  ALTER TABLE 表名
	  MODIFY 表名 数据类型
	  ```
	
	- 应用案例：在 emp 表添加 image 列的基础之上，修改 image 列的数据类型为 varchar(60)
	
	  ```sql
	  ALTER TABLE emp
	  MODIFY job VARCHAR(60) NOT NULL DEFAULT ''
	  ```
	
- 修改列名

  - 基本语法
  
    ```sql
    ALTER TABLE 表名
    CHANGE 修改的列名 修改后的列名 数据类型
    ```
  
  - 应用案例：修改 emp 表的 name 为 user_name
  
    ```sql
    ALTER TABLE emp
    CHANGE `name` user_name VARCHAR(32)
    ```

## 修改表名

- 基本语法

  ```sql
  RENAME TABLE 原表名 TO 新表名
  ```

- 应用案例：将 emp 表表名改为 employee

  ```sql
  RENAME TABLE emp TO employee
  ```

## 修改字符集

- 基本语法

  ```sql
  ALTER TABLE 表名 CHARACTER SET 字符集
  ```

- 应用案例：在 employee 表的基础之上，修改 employee 表的字符集为 utf8

  ```sql
  ALTER TABLE employee CHARACTER SET utf8
  ```

## 删除列

- 基本语法

  ```sql
  ALTER TABLE 表名
  DROP 列名
  ```

- 应用案例：在 employee 表的基础之上，删除 sex 列

  ```sql
  ALTER TABLE employee
  DROP sex
  ```

# CRUD

## INSERT  语句

- 基本介绍

  

- 基本语法

  - 插入一条数据

    ```sql
    INSERT INTO 表名 [(列名1,列名2,列名n)]
    VALUES (列名1数据,列名2数据,列名n数据)
    ```

  - 插入多条数据

    ```sql
    INSERT INTO 表名 [(列名1,列名2,列名n)]
    VALUES (列名1数据,列名2数据,列名n数据),(列名1数据,列名2数据,列名n数据),(列名1数据,列名2数据,列名n数据)
    ```

  - 插入个别数据

    ```sql
    INSERT INTO 表名 (列名1,列名3)
    VALUES (列名1数据,列名3数据)
    ```

- 应用案例：创建一张 商品 good 表（id INT，goods_name VARCHAR(10)，price DOUBLE），price 默认值为 100，并添加两条数据

  ```sql
  # 创建 good 表
  CREATE TABLE good(
  		id INT,
  		goods_name VARCHAR(10),
  		price DOUBLE DEFAULT 100
  )
  
  # 添加数据
  # 注意：第二条数据插入的 '20' 可以插入数据，Mysql 底层会自动转化为 INT 
  INSERT INTO good (id,goods_name,price)
  VALUES (10,'华为手机',1000),('20','小米手机',2000)
  ```

- 注意事项

  - 不写列名默认为表的全部列并且按顺序，下面语句效果同上

    ```sql
    INSERT INTO good
    VALUES (30,'VIVO手机',1000)
    ```

  - 插入的数据可以为 NULL，前提是该列允许为空

    ```sql
    INSERT INTO good
    VALUES (40,'苹果手机',NULL)
    ```

  - 默认值的使用，如果不给某个字段复制时，如果有默认值会自动添加默认值，否则会报错

    ```sql
    INSERT INTO good (id,goods_name)
    VALUES (50,'oppo手机')
    ```

## UPDATE  语句

- 基本介绍

  

- 基本语法

  - 修改所有的列值

    ```sql
    UPDATE 表名
    SET 列名 = 数值
    ```
    
  - 修改特定要求的列值
  
    ```sql
    UPDATE 表名
    SET 列名 = 数值
    WHERE 查询条件
    ```
  
- 应用案例

  - 案例1：在 good 表的基础之上，将所有的 price 改为 2000

    ```sql
    UPDATE good
    SET price = 2000
    ```

  - 案例2：在案例1的基础之上，将华为手机的 price 改为 3000

    ```sql
    UPDATE good
    SET price = 3000
    WHERE goods_name = '华为手机'
    ```

  - 案例3：在案例2的基础之上，将华为手机 price + 2000，华为手机 id 改为 201

    ```sql
    UPDATE good
    SET price = price + 2000,id = 201
    WHERE goods_name = '华为手机'
    ```

## DELETE 语句

- 基本语法

  - 删除所有列的值

    ```sql
    DELETE FROM 表名
    ```

  - 删除特点要求的数据

    ```sql
    DELETE FROM 表名
    WHERE 查询条件
    ```

- 应用案例

  - 案例1：在 UPDATE 语句修改 good 表的基础之上，删除所有 VIVO 手机的所有数据

    ```sql
    DELETE FROM good
    WHERE goods_name = 'VIVO手机'
    ```

  - 案例2：在案例1的基础之上，删除 oppo手机的 price

    ```sql
    UPDATE good
    SET price = NULL;
    WHERE goods_name = 'oppo手机'
    ```

- 注意事项：DELETE 语句不能删除一条数据某列的数据，ALTER DROP 是删除表的列结构，要实现这个效果使用 UPDATE 语句


## SELECT 语句

- 基本语法

  - 单表查询

    ```sql
    SELECT [DISTINCT] [列名1,列名2,列名n] FROM 表名
    [WHERE 查询条件]
    [GROUP BY 列名1,列名2,列名n]
    [HAVING 查询条件]
    [ORDER BY 列名1 排序规则,列名2 排序规则] 
    [LIMIT (页号-1)*每页数据数,每页数据数]
    ```
    
    - DISTINCT：去除重复数据，去除全部查询相同的数据
    - DESC：排序规则，降序
    - ASC：排序规则，升序，默认
    
  - 使用表达式查询列

    ```sql
    SELECT 列名1,列名2,列名1 + 列名2 as `别名`
    FROM 表名
    ```
    
  - 查询加强

    - WHERE 子句

    - 模糊查询

      | 通配符 | 描述 |
      | :----: | :--: |
      |   %    |      |
      |   _    |      |

    - NULL

    - 表结构

    - ORDER BY 子句

    - LIMIT 子句，分页查询

      > **LIMIT (PAGENUMBER-1)*PAGESIZE,PAGESIZE**
      >
      > **（页号 - 1）* 每页显示条数，每页显示条数，不允许写表达式**

    - GROUP BY 子句，分组查询

    - HAVING 子句

    - 合并查询

  - 多表查询

    - 基本介绍

      多表查询是指基于两个和两个以上的表查询

      **多表查询的条件不能少于表的个数-1，否则会出现笛卡尔集**

    - 自连接

      自连接是指在同一张表的连接查询，将同一张表看做两张表

    - 子查询
    
      - 基本介绍
    
        子查询是指嵌入在其它 sql 语句中的 SELECT 语句，也叫嵌套查询
    
      - 单行子查询（单列）
    
        单行子查询是指只返回一行数据的子查询语句
    
      - 多行子查询（单列）
        多行子查询指返回多行数据的子查询，使用关键字in

      - 多列子查询

      - 多列子查序则是指查询返回多个列数据的子查询语句

- 应用案例

  - 案例1：单表查询，查询 good 表

    ```sql
    SELECT * FROM good
    ```

  - 案例2：单表查询，查询 good 表的 id 和 goods_name 列

    ```sql
    SELECT id,goods_name FROM good
    ```

  - 案例3：单表查询，经过系列操作后 good 表内容如下表所示，统计手机的 price 总和为 sum

    ![image-20220719140208761](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220719140208761.png)

    ```sql
    SELECT id,goods_name,price + price_two AS `sum`
    FROM good
    ```
    
  - 案例4：查询增强，查找1992.1.1后入职的员工
  
    ```sql
    SELECT * FROM
    WHERE hiredate > '1992-01-01'
    ```
  
  - 案例5：查询增强，显示首字符为 S 的员工姓名和工资
  
    ```SQL
    SELECT ename,sal FROM emp
    WHERE enmae LIKE 'S%'
    ```
    
  - 案例6：查询增强，显示第三个字符为大写 O 的所有员工的姓名和工资
  
    ```sql
    SELECT ename,sal FROM emp
    WHERE ename LIKE '___O%'
    ```
  
  - 案例7：查询增强，显示没有上级的雇员的情况
  
    ```sql
    SELECT * FROM emp
    WHERE mgr IS NULL
    ```
  
  - 案例8：查询 emp 表的结构
  
    ```sql
    DESC emp
    ```
  
  - 案例9：查询增强，查询 emp 表的员工信息按照 sal 升序排序
  
    ```sql
    SELECT * FROM emp
    ORDER BY sal
    ```
  
  - 案例10：查询增强，查询 emp  表的部门号升序排序而员工的工资降序排序，显示员工信息
  
    ```sql
    SELECT * FROM emp
    ORDER BY deptno,sal DESC
    ```
    
  - 案例11：查询增强，查询 emp 表，根据员工的 empno 升序排序，每页显示 3 条记录
  
    ```sql
    # 第一页
    SELECT * FROM emp
    ORDER BY empno
    LIMIT 0,3;
    # 第二页
    SELECT * FROM emp
    ORDER BY empno
    LIMIT 3,3;
    # 第三页
    SELECT * FROM emp
    ORDER BY empno
    LIMIT 6,3;
    ```
  
  - 案例12：查询增强，显示每种岗位的员工总数、平均工资
  
    ```sql
    SELECT COUNT(*),AVG(sal),job FROM emp
    GROUP BY job
    ```
  
  - 案例13：查询增强，显示员工总数以及获得补助 comm 的员工数
  
    ```sql
    SELECT COUNT(*),COUNT(comm) FROM emp
    ```
  
  - 案例14：查询增强，查询 emp 表 显示员工总数以及未获得补助 comm 的员工数
  
    ```sql
    # 方法1
    SELECT COUNT(*),COUNT(COUNT(*) - COUNT(comm)) FROM emp
    # 方法2
    SELECT COUNT(*),COUNT(IF(comm IS NULL,1,NULL)) FROM emp
    ```
  
  - 案例15：查询增强，查询 emp 表，显示管理者 mgr 的总人数
  
    ```sql
    SELECT COUNT(DISTINCT mgr) FROM emp
    ```
  
  - 案例16：查询增强，查询 emp 表，查询员工工资的最大差额
  
    ```sql
    SELECT MAX(sal) - MIN(sal) FROM emp
    ```
  
  - 案例17：查询增强，统计各个部门的大于 1000 的平均工资，并且按照平均工资从高到低排序，取出前两行记录
  
    ```sql
    SELECT deptno,AVG(sal) AS avg_sal FROM emp
    GROUP BY deptno
    HAVING avg_sal > 1000
    ORDER BY avg_sal DESC
    LIMIT 0,2
    ```
  
  - 案例18：多表查询，查询 emp 表和 dept 表
  
    ```sql
    SELECT * FROM emp,dept
    WHERE emp.deptno = dept.deptno
    ```
  
  - 案例19：多表查询，显示员工名、员工工资及所在部门的名字
  
    ```sql
    SELECT ename,sal,dname FROM emp,dept
    WHERE emp.deptno = dept.deptno
    ```
  
  - 案例20：多表查询，显示部门号为 10 的部门名、员工名和工资
  
    ```sql
    SELECT ename,sal,dname FROM emp,dept
    WHERE emp.deptno = dept.deptno AND emp.deptno = 10
    ```
  
  - 案例21：显示各个员工的姓名，工资及其工资的级别
  
    ```sql
    SELECT ename,sal,grade FROM emp,salgrade
    WHERE sal BETWEEN losal AND hisal
    ```
  
  - 案例22：显示公司员工和他的上级名字
  
    AS 可以省略
  
    ```sql
    SELECT worker.ename AS '员工名',boss.ename AS '上级' FROM emp worker,emp boss
    WHERE worker.mgr = boss.empno
    ```
  
  - 案例23：单行子查询，显示与 SMITH 同一部门的所有员工
  
    ```sql
    # 方法一
    SELECT * FROM emp
    WHERE deptno = (
        SELECT deptno FROM emp
    	WHERE ename = 'SMITH'
    )
    # 方法二
    SELECT emp.* FROM emp sm,emp
    WHere sm.ename = 'SMITH' AND sm.deptno = emp.deptno
    ```
  
  - 案例24：多行子查询，查询和部门 10 号 的工作相同的员工的姓名、岗位、工资、部门号，但是不包含 10 号部门自己的员工
  
    ```sql
    SELECT ename,job,sal,deptno FROM emp
    WHERE job IN (
    	SELECT DISTINCT job FROM emp
    	WHERE deptno = 10
    ) AND deptno != 10
    ```
  
  - 案例25：多行子查询，显示工资比部门 30 号的所有员工的工资高的员工的姓名、工资和部门号
  
    ```sql
    # 方法一
    SELECT ename,sal,deptno FROM emp
    WHERE sal > ALL(
        SELECT sal FROM emp
        WHERE deptno = 30
    )
    
    # 方法二
    SELECT ename,sal,deptno FROM emp
    WHERE sal > (
        SELECT MAX(sal) FROM emp
        WHERE deptno = 30
    )
    ```
  
  - 案例26：多行子查询，查询工资比部门30的其中一个员工的工资高的员工的姓名、工资和部门号
  
    ```sql
    # 方法一
    SELECT ename,sal,deptno FROM emp
    WHERE sal > ANY(
        SELECT sal FROM emp
        WHERE deptno = 30
    )
    # 方法二
    SELECT ename,sal,deptno FROM emp
    WHERE sal > (
        SELECT MIN(sal) FROM emp
        WHERE deptno = 30
    )
    ```
  
  - 案例27：多列子查询，查询与 ALLEN 的部门和岗位完全相同的所有员工（并且不含 ALLEN 本人）
  
    ```sql
    SELECT * FROM emp
    WHERE (deptno, job) = (
        SELECT deptno,job FROM emp
        WHERE ename = 'ALLEN'
    ) AND ename != 'ALLEN'
    ```
  
  - 案例28：查找每个部门工资高于本部门平均工资的人的资料
  
    ```sql
    SELECT ename,sal,temp.avg_sal ,emp.deptno FROM emp,(
    		SELECT deptno,AVG(sal) AS avg_sal FROM emp
    		GROUP BY deptno
    ) temp
    WHERE emp.deptno = temp.deptno AND emp.sal > temp.avg_sal
    ```
  
  - 案例29：查找每个部门工资最高的人的详细资料
  
    ```sql
    SELECT ename,MAX(sal) FROM emp
    GROUP BY deptno
    ```
  
  - 案例30：查询每个部门的信息(包括：部门名，编号，地址)和人员数量
  
    ```sql
    SELECT dname,dept.deptno,tmp.person FROM dept,(
    		SELECT COUNT(*) AS person,deptno FROM emp
    		GROUP BY deptno
    		) tmp
    WHERE tmp.deptno = dept.deptno
    ```
    
  - 案例31：合并查询
  
    ```sql
    SELECT ename,sal,job FROM emp
    WHERE sal > 2500 #5 rows
    SELECT ename,sal,job FROM emp
    WHERE job = 'MANAGER' #3 rows
    
    # 合并查询 UNION ALL 8 rows，不会取消重复行
    SELECT ename,sal,job FROM emp
    WHERE sal > 2500 #5 rows
    UNION ALL
    SELECT ename,sal,job FROM emp
    WHERE job = 'MANAGER' #3 rows
    
    # 合并查询 UNION 8 rows，取消重复行
    SELECT ename,sal,job FROM emp
    WHERE sal > 2500 #5 rows
    UNION
    SELECT ename,sal,job FROM emp
    WHERE job = 'MANAGER' #3 rows
    ```
  

# 函数

## 聚合函数

- COUNT 函数

  - 基本介绍

    统计返回行的总数
    
    ![image-20220719142059947](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220719142059947.png)
    
  - 应用案例：分别统计 good 表的商品记录个数及价格数据记录

    ```sql
    SELECT COUNT(*) from good #5
    SELECT COUNT(price) from good #4
    ```

  - 注意事项

    COUNT(*)：返回满足条件的记录的个数

    COUNT(列名)：统计满足条件的某列有多少个，但是会返回 NULL 的情况

- SUM 函数

  - 基本介绍

    统计列数据的总数

  - 应用案例：统计所有手机的价格

    ```sql
    SELECT SUM(price) AS 总价 FROM good
    ```

  - 注意事项：SUM 函数仅对数值数据有效


- AVG 函数

  - 基本介绍

    统计列数据的平均数

  - 应用案例：统计所有手机平均价格

    ```sql
    SELECT AVG(price) AS 总价 FROM good
    ```
    


- MAX/MIN 函数

  - 统计列数据的最大/小值

  - 应用案例：统计所有手机的最大和最小价格

    ```sql
    SELECT MAX(price) AS 最大值,MIN(price) AS 最小值 FROM good
    ```


## 字符串函数

|             字符串函数              |                             描述                             |
| :---------------------------------: | :----------------------------------------------------------: |
|            CHARSET(str2)            |                        返回字串字符集                        |
|       CONCAT(str1,str2,strn)        |                           连接字串                           |
|       INSTR(string,substring)       |      返回 substring 在 string 中出现的位置，没有返回 0       |
|             UCASE(str)              |                          转换成大写                          |
|             LCASE(str)              |                          转换成小写                          |
|          LEFT(str,length)           |              从 str 中的左边起取 length 个字符               |
|          RIGHT(str,length)          |              从 str 中的右边起取 length 个字符               |
|             LENGTH(str)             |                        str 的字节长度                        |
| REPLACE(str,search_str,replace_str) |           在 str 中用 replace_str 替换 search_str            |
|         STRCMP(stri1,str2)          | 逐字符比较两字串大小,比较两个字符串，如果这两个字符串相等返回0，如果第一个参数是根据当前的排序小于第二个参数顺序返回-1，否则返回1。 |
|  SUBSTRING(str,position[,length])   |  从 str 的 position 开始（从1开始计算）[，取 length 个字符]  |
|             LTRIM(str)              |                         去除前端空格                         |
|             RTRIM(str2)             |                         去除后端空格                         |
|             TRIM(str2)              |               去除前后端空格（中间空格去不掉）               |

- 应用案例

  - 案例1：查询 emp 表的所有员工的姓名的字符集

    ```sql
    SELECT CHARSET(ename) FROM emp
    ```

  - 案例2：将 emp 表的员工名字和工作拼接到描述列

    ```sql
    SELECT CONCAT(ename,' job is ',job) AS 描述 FROM emp
    ```

  - 案例3：查询亚元里面字符串 “Uriku” 在 字符串 “IAMUriku” 中的位置

    ```sql
    SELECT INSTR('IAMUriku','Uriku') FROM DUAL #4
    ```

  - 案例4：将 emp 表的员工名字大写

    ```sql
    SELECT UCASE(ename) FROM emp
    ```

  - 案例5：将 emp 表的员工名字小写

    ```sql
    SELECT LCASE(ename) FROM emp
    ```

  - 案例6：将 emp 表的员工名字取前两个字符

    ```sql
    SELECT LEFT(ename,2) FROM emp
    ```

  - 案例7：查询字符串 ’Uriku‘ 的长度

    ```sql
    SELECT LENGTH('Uriku') FROM DUAL #5
    ```
  
  - 案例8：查询 emp 表中的 job 内容，将 MANAGER 替换成经理
  
    ```sql
    SELECT ename,REPLACE(job,'MANAGER','经理') FROM emp 
    ```
    
  - 案例9：比较 Uriku 和 Eugeo 的字符串大小
  
    ```sql
    SELECT STRCMP('Uriku','Eugeo') FROM DUAL #1
    ```
  
  - 案例10：截取字符串 Uriku 的前两个字符

    ```sql
    SELECT SUBSTRING('Uriku',1,2) FROM DUAL #Ur
    ```
    
  - 案例11：去除字符串 ’  U R IKU  ' 的前后空格 
  
    ```sql
    SELECT TRIM('  U R IKU  ') FROM DUAL #U R IKU
    ```

  - 案例12：以首字母小写的方式显示所有员工emp表的姓名
  
    ```sql
    SELECT CONCAT(LCASE(LEFT(ename,1)),RIGHT(ename,LENGTH(ename)-1)) FROM emp
    ```

    

## 数学函数

|          数学函数           |                      描述                       |
| :-------------------------: | :---------------------------------------------: |
|          ABS(num)           |                返回 num 的绝对值                |
|      BIN(decimal_num)       |             返回十进制数的二进制数              |
|        CEILING(num)         |                    向上取整                     |
|         FLOOR(num)          |                    向下取整                     |
| FORMAT(num,decimal_places)  |             保留小数位（四舍五入）              |
| CONV(num,from_base,to_base) | 将 num 的 from_base 进制数转化为 to_base 进制数 |
|                             |                                                 |
|                             |                                                 |
|                             |                                                 |
|                             |                                                 |
|                             |                                                 |
|                             |                                                 |

- 应用案例

  - 案例1：查询 -10 的绝对值

    ```sql
    SELECT ABS(-10) FROM DUAL #10
    ```

  - 案例2：查询 10 的二进制数

    ```sql
    SELECT BIN(10) FROM DUAL #1010
    ```
    
  - 案例3：查询 -1.1 大的最小整数
    
    ```sql
    SELECT CEILING(-1.1) FROM DUAL #-1
    ```
    
  - 案例4：将 8（十进制）转化为二进制
  
    ```sql
    SELECT CONV(8,10,2) FROM DUAL #1000
    ```
  
  - 案例5：查询 -1.1 小的最大整数
  
    ```sql
    SELECT FLOOR(-1.1) FROM DUAL #-2
    ```
    
  - 案例6：保留 867.3411 两位小数位
  
    ```sql
    SELECT FORMAT(867.3411,2) FROM DUAL #867.34
    ```
  
  - 案例7：
  
    ![image-20220720120649119](C:\Users\Uriku\Desktop\MySQL\image-20220720120649119.png)
  
    ```sql
    
    ```
  
  - 案例8：
  
    ![image-20220720120713025](C:\Users\Uriku\Desktop\MySQL\image-20220720120713025.png)
  
    ```sql
    ```
  
  - 案例9：
  
    ![image-20220720120730982](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720120730982.png)
  
    ```sql
    ```
  
  - 案例10：
  
    ![image-20220720121022329](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720121022329.png)
  
    ```sql
    
    ```

## 日期函数

|      日期函数       |        描述        |
| :-----------------: | :----------------: |
|   CURRENT_DATE()    |      当前日期      |
|   CURRENT_TIME()    |      当前时间      |
| CURRENT_TIMESTAMP() |     当前时间戳     |
|        NOW()        |   当前日期和时间   |
|       DATE()        |                    |
|     DATE_ADD()      |                    |
|     DATE_SUB()      |                    |
|      DATEDIFF       |                    |
|   YEAR(datetime)    |      返回年份      |
|  MONTH(datemtime)   |      返回月份      |
|         DAY         |                    |
|   UNIX_TIMESTAMP    |      返回秒数      |
|    FROM_UNIXTIME    | 把秒数转成指定日期 |

![image-20220720123605406](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720123605406.png)

![image-20220720123531596](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720123531596.png)

![image-20220720123822400](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720123822400.png)

- 应用案例

  ![image-20220720122149414](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720122149414.png)

  - 案例1：查询当前日期

    ![image-20220720121349702](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720121349702.png)

    ```sql
    SELECT CURRENT_DATE() FROM DUAL
    ```

  - 案例2：查询当前时间

    ![image-20220720121358494](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720121358494.png)

    ```sql
    SELECT CURRENT_TIME() FROM DUAL
    ```

  - 案例3：查询当前时间戳

    ![image-20220720121415396](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720121415396.png)

    ```sql
    SELECT CURRENT_TIMESTAMP() FROM DUAL
    ```

  - 案例4：查询当前日期和时间

    ![image-20220720122226324](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720122226324.png)

    ```sql
    ```

  - 案例5：查询 mes 表内在 10 分钟内发布的新闻

    ```sql
    # 方法1
    SELECT * FROM mes
    WHERE DATE_ADD(send_time,INTERVAL 10 MINUTE) >= NOW()
    
    # 方法2
    SELECT * FROM mes
    WHERE DATE_SUB(NOW(),INTERVAL 10 MINUTE) <= send_time
    ```

  - 案例6：求 2011-11-11 和 1990-1-1 相差多少天

    ```sql
    SELECT DATEDIFF('2011-11-11','1990-1-1') FROM DUAL #7984
    ```

  - 案例7：

    ![image-20220720123026127](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720123026127.png)

    ```sql
    
    ```

  - 案例8：假设你能活 80 岁，求出你还能活多少天

    ```sql
    SELECT DATEDIFF(DATE_ADD('2000-11-26',INTERVAL 80 YEAR),NOW()) FROM DUAL
    ```

  - 案例9：

    ![image-20220720124057588](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720124057588.png)

    ```sql
    
    ```

  - 案例10：

    ![image-20220720124239617](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720124239617.png)

    ```sql
    ```

  - 案例11：

    ![image-20220720124534615](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720124534615.png)

    ```sql
    ```

## 加密函数

|   加密函数    |                         描述                          |
| :-----------: | :---------------------------------------------------: |
|    USER()     |                       返回用户                        |
|  DATABASE()   |                   返回当前数据名称                    |
|   MD5(str)    | 为字符串计算一个 MD5 32位的字符串，通常为用户密码加密 |
| PASSWORD(str) |                   mysql 8.0 移除了                    |
|               |                                                       |
|               |                                                       |
|               |                                                       |
|               |                                                       |
|               |                                                       |
|               |                                                       |

![image-20220720125812256](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720125812256.png)

SQL 注入在 JDBC 讲

- 应用案例

  - 案例1：

    ![image-20220720124924266](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720124924266.png)

    ```sql
    ```

  - 案例2：

    ![image-20220720125010484](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720125010484.png)

    ```sql
    SELECT DATABASE() FROM DUAL
    ```

  - 案例3：

    ![image-20220720125128442](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720125128442.png)

    ```sql
    SELECT MD5('ROOT') FROM DUAL
    SELECT LENGTH(MD5('ROOT')) FROM DUAL
    ```

  - 案例4：

    ![image-20220720130246340](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720130246340.png)

    ```sql
    
    ```

  - 案例5：

    ```sql
    
    ```

  - 案例6：

    ```sql
    
    ```

  - 案例7：

    ```sql
    
    ```

## 流程控制函数



![image-20220720130426152](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720130426152.png)

![image-20220720130709255](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720130709255.png)



![image-20220720131144134](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720131144134.png)

|     流程控制函数     |                        描述                        |
| :------------------: | :------------------------------------------------: |
| IF(expr1,exp2,expr3) |   如果 expr1为 True，则返回 expr2 否则返回 expr3   |
| IFNULL(expr1,expr2)  | 如果 expr1 不为 NULL，则返回 expr1，否则返回 expr2 |
|                      |                                                    |

- 应用案例

  - 案例1

    ```sql
    SELECT IF(FALSE,'北京','上海') FROM DUAL #上海
    ```
    
  - 案例2

    ![image-20220720130809887](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720130809887.png)

    ```sql
    ```
  
  - 案例3：

    ![image-20220720131538963](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720131538963.png)

    ```sql
    # 方法1
    SELECT ename,IF(comm IS NULL,0.0,comm) AS comm FROM emp
    # 方法2
    SELECT ename,IFNULL(comm,0.0) AS comm FROM emp
    ```
  
  - 案例4：

    ![image-20220720132039911](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720132039911.png)

    ```sql
    SELECT ename,(SELECT CASE
                    WHEN job = 'CLERK' THEN '职员'
                    WHEN job = 'MANGER' THEN '经理'
                    WHEN job = 'SALESMAN' THEN '销售人员'
                    ELSE job END) AS job,job
                    FROM emp
    ```

#  分组统计

## GROUP BY 字句

- 基本介绍

  对列进行分组

- 基本语法

  ```sql
  SELECT  FROM
  GROUP BY 分组条件
  ```

- 应用案例：

  ![image-20220720104803481](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220720104803481.png)
  
  - 案例1：查询 emp 表的每个部门的最高和最低工资
  
    ```sql
    SELECT MAX(sal),MIN(sal),deptno FROM emp
    GROUP BY deptno
    ```
  
  - 案例2：查询 emp 表的每个部门的每个岗位的最高和最低工资
  
    ```sql
    SELECT MAX(sal),MIN(sal),deptno,job FROM emp
    GROUP BY deptno,job
    ```
  
  - 案例3：查询 emp 表的平均工资低于 2000 的部门号和它的平均工资
  
    ```sql
    SELECT AVG(sal) AS 平均工资,deptno FROM emp
    GROUP BY deptno
    HAVING AVG(sal) < 2000
    ```
  

## HAVING 字句

- 基本介绍

  对分组后的数据进行筛选，GROUP BY 的 WHERE

- 基本语法


# 表的复制和去重

## 表的复制

- 应用案例

  - 案例1：把 emp 表的数据复制到 my_table01 表中

    ```sql
    INSERT INTO my_table01(id,`name`,sal,job,deptno)
    SELECT empno,ename,sal,job,deptno FROM emp
    ```

  - 案例2：自我复制

    ```sql
    INSERT INTO my_table01(id,`name`,sal,job,deptno)
    SELECT * FROM my_table01
    ```

## 表的去重

- 应用案例：

  ```sql
  # 把 emp 的表结构（列），复制到 my_table02
  CREATE TABLE my_table02 LIKE emp
  INSERT INTO  my_table02
  SELECT * FROM emp
  # 去重
  # 1.先创建一张临时表 my_tmp,该表的结构和 my_tab02 一样
  # 2.把 my_tmp 的记录通过 DISTINCT 关键字处理后把记录复制到 my_tmp
  # 3.把 my_tmp 表记录复制到 my_table02
  # 4.drpo 掉临时表
  CREATE TABLE my_tmp LIKE my_table01
  INSERT INTO my_tmp
  SELECT DISTINCT * FROM my_table01
  DELETE FROM my_table01
  INSERT INTO my_table01
  SELECT * FROM my_tmp
  DROP TABLE my_tmp
  ```
  

# 外连接

  	前面我们学习的查询，是利用where子句对两张表或者多张表，形成的笛卡尔积进行筛选，根据关联条件，显示所有匹配的记录，匹配不上的，不
显示

​		列出部门名称和这些部门的员工名称和工作，同时要求显示出那些没有员工的部门，做不到，匹配不到

```sql
SELECT ename,job,dNAME FROM emp,dept
WHERE emp.deptno = dept.deptno
ORDER BY dname
```

![image-20220721124320772](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220721124320772.png)

![image-20220721124336543](C:\Users\Uriku\AppData\Roaming\Typora\typora-user-images\image-20220721124336543.png)

## 左外连接

- 基本介绍

  左侧的表完全显示我们就说是左外连接（stu 全显示）

- 应用案例：显示所有人的成绩，如果没有成绩，也要显示该人的姓名和 id 成绩显示为空

  ```sql
  SELECT `name`,stu.id,grade FROM stu LEFT JOIN exam
  ON stu.id = exam.id
  ```

## 右外连接

- 基本介绍

  右侧的表完全显示我们就说是右外连接

- 应用案例：显示所有成绩，如果没有名字匹配，显示空

  ```sql
  SELECT `name`,stu.id,grade FROM stu RIGHT JOIN exam
  ON stu.id = exam.id
  ```

## 综合案例

列出部门名称和这些部门的员工信息（名字和工作），同时列出那些没有员工的部门名

```sql
SELECT * FROM emp RIGHT JOIN dept
ON emp.deptno = dept.deptno
```

# SQL  约束

- 基本介绍

  约束用于确保数据库的数据满足特定的商业规则。在 MySQL 中，约束包括：NOT NULL、UNIQUE、PRIMARY KEY、FOREIGN KEY、CHECK 五种

## 主键 PRIMARY KEY

- 基本介绍

  用于唯一的标示表行的数据，当定义主键约束后，该列不能重复、不能为空、唯一。一张表最多只能有一个主键，但可以是复合主键

- 基本语法

  ```sql
  列名 数据类型 PRIMARY KEY
  ```

- 注意事项

  1. 主键对应的列不能重复、不能为空、唯一
  2. 一张表最多只能有一个主键，但可以是复合主键

  ```sql
  # 多个主键错误
  id INT PRIMARY KEY,
  `name` VARCHAR(32) PRIMARY KEY,
  email VARCHAR(32)
  
  # 复合键，只有 id 和 name 完全相同才报错
  id INT,
  `name` VARCHAR(32) ,
  email VARCHAR(32),
  PRIMARY KEY (id,`name`)
  ```

## 非空  NOT NULL

- 基本介绍

  如果在列上定义了 NOT NULL，那么当插入数据时，必须为列提供数据

## 唯一  UNIQUE

- 基本介绍

  当定义了唯一约束后，该列值是不能重复的

- 注意事项
  1. 如果没有指定 NOT NULL，则 UNIQUE 字段可以有多个 NULL
  2. 一张表可以有多个 UNIQUE 字段
  3. 如果一个列，是 UNIQUE NOT NULL 使用效果类似 PRIMARY KEY

## 外键  FOREIGN KEY

- 基本介绍

  用于定义主表和从表之间的关系：外键约束要定义在从表上，主表则必须具有主键约束或是 UNIQUE 约束。当定义外键约束后，要求外键列数据必须在主表的主键列存在或是为 NULL

- 基本语法

  ```sql
  列名 数据类型 FOREIGN KEY () REFERENCES 约束列名
  ```

- 应用案例

  ```sql
  # 创建主表
  CREATE TABLE clazz(
  	cid INT PRIMARY KEY,
      `name` VARCHAR(32) NOT NULL DEFAULT ''
  )
  # 创建从表
  CREATE TABLE ny_stu(
  	id INT PRIMARY KEY,
      `name` VARCHAR(32) NOT NULL DEFAULT ''
      clazz_id INT,
      FOREIGN KEY (clazz_id) REFERENCES clazz(cid)
  )
  ```
  
  

