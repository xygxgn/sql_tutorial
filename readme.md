SQL 基本语句

# DDL 语句 (用来定义数据库对象, 包括数据库、表、字段)
  <!-- 数据库操作 -->
  * 查询所有的数据库
  `SHOW DATABASES;`
  * 查看当前所在数据库名称
  `SELECT DATABASE();`
  * 选择使用某个数据库
  `USE 数据库名;`
  * 创建数据库
  `CREATE DATABASE [IF NOT EXISTS] 数据库名 [DEFAULT CHARSET 字符集] [COLLATE 排序规则];`
  * 删除数据库
  `DROP DATABASE [IF EXISTS] 数据库名;`
  <!-- 表操作 -->
  * 查询数据库中所有表
  `SHOW TABLES;`
  * 查询表结构
  `DESC 表名;`
  * 查询指定表的建表语句
  `SHOW CREATE TABLE 表名;`
  * 创建表
  `CREATE TABLE 表名(字段1 字段1类型 [COMMENT 字段1注释], 字段1 字段1类型 [COMMENT 字段1注释], ...) [COMMENT 表注释];`
  * 添加表中字段
  `ALTER TABLE 表名 ADD 字段名 类型(长度) [COMMENT 注释] [约束];`
  * 修改表中字段数据类型
  `ALTER TABLE 表名 MODIFY 字段名 新数据类型(长度);`
  * 修改表中字段名和数据类型
  `ALTER TABLE 表名 CHANGE 旧字段名 新字段名 类型(长度) [COMMENT 注释] [约束];`
  * 删除表中字段
  `ALTER TABLE 表名 DROP 字段名;`
  * 修改表名
  `ALTER TABLE 表名 RENAME TO 新表名;`
  * 删除表
  `DROP TABLE [IF EXISTS] 表名;`
  * 删除表并重新创建表
  `TRUNCATE TABLE 表名;`

# DML 语句 (用来对数据库中表的数据记录进行增删改操作)
  <!-- 添加数据 -->
  * 指定字段添加数据记录
  `INSERT INTO 表名(字段名1, 字段名2, ...) VALUES (值1, 值2, ...);`
  * 全部字段添加数据记录
  `INSERT INTO 表名 VALUES (值1, 值2, ...);`
  * 批量添加数据记录
  `INSERT INTO 表名(字段名1, 字段名2, ...) VALUES (值1, 值2, ...), (值1, 值2, ...), ...;`
  `INSERT INTO 表名 VALUES (值1, 值2, ...), (值1, 值2, ...), ...;`
  <!-- 修改数据 -->
  * 修改表中字段数据
  `UPDATE 表名 SET 字段名1=值1, 字段名2=值2, ... [WHERE 条件];`
  <!-- 删除数据 -->
  * 删除表中数据记录
  `DELETE FROM 表名 [WHERE 条件];`

# DQL 语句 (用来查询数据库中表的记录)
  <!-- 查询数据 -->
  * 编写顺序
  `SELECT 字段列表 FROM 表名列表 WHERE 条件列表 GROUP BY 分组字段列表 HAVING 分组后条件列表 ORDER BY 排序字段列表 LIMIT 分页参数;`
  *执行顺序
  `FROM 表名列表 WHERE 条件列表 GROUP BY 分组字段列表 HAVING 分组后条件列表 SELECT 字段列表 ORDER BY 排序字段列表 LIMIT 分页参数;`
  <!-- 基本查询 -->
  * 基本查询语法
  `SELECT [DISTINCT] 字段1 [[AS] 别名1], 字段2 [[AS] 别名2], ... FROM 表名;`
  * 查询所有字段
  `SELECT * FROM 表名;`
  * 查询多个字段并设置别名
  `SELECT 字段1 [AS] 别名1, 字段2 [AS] 别名2, ... FROM 表名;`
  * 去重查询多个字段
  `SELECT DISTINCT 字段列表 FROM 表名;`
  <!-- 条件查询 -->
  * 比较运算符
  `>, >=, <, <=, =, <>, !=, BETWEEN ... AND ..., IN(...), LIKE 占位符, IS NULL`  其中占位符'_'表示占一个字符, '%'表示占任意个字符
  * 逻辑运算符
  `AND, &&, OR, ||, NOT, !`
  * 条件查询语法
  `SELECT 字段列表 FROM 表名 WHERE 条件列表;`
  <!-- 聚合函数查询 -->
  * 聚合函数
  `count(), max(), min(), avg(), sum()`
  * 聚合函数查询语法
  `SELECT 聚合函数(字段列表) FROM 表名;`
  <!-- 分组查询 -->
  * 分组查询语法
  `SELECT 字段列表 FROM 表名 [WHERE 条件列表] GROUP BY 分组字段名 [HAVING 分组后过滤条件];`
  * WHERE 和 HAVING 的区别: 执行时机 WHERE 在分组之前, HAVING 在分组之后; 判断条件 WHERE 不能对聚合函数判断而 HAVING 可以
  <!-- 排序查询 -->
  `SELECT 字段列表 FROM 表名 ORDER BY 字段1 排序方式, 字段2 排序方式2, ...;` 排序方式: 升序 ASC (默认), 降序 DESC
  <!-- 分页查询 -->
  `SELECT 字段列表 FROM 表名 LIMIT 起始索引, 查询记录数;`

# DCL 语句 (用来创建数据库用户, 控制数据库的访问权限)
  <!-- 管理用户 -->
  * 查询用户
  `USE mysql;`
  `SELECT Host, User FROM user;`
  * 创建用户
  `CREATE USER '用户名'@'主机名' IDENTIFIED BY '密码';`
  * 修改用户密码
  `ALTER USER '用户名'@'主机名' IDENTIFIED WITH mysql_native_password BY '新密码';`
  * 删除用户
  `DROP USER '用户名'@'主机名';`
  <!-- 管理权限 -->
  * 常用权限
  `ALL, ALL PRIVILEGES, SELECT, INSERT, UPDATE, DELETE, ALTER, DROP, CREATE`
  * 查询权限
  `SHOW GRANTS FOR '用户名'@'主机名';`
  * 授予权限
  `GRANT 权限列表 ON 数据库.表名 TO '用户名'@'主机名';`
  * 撤销权限
  `REVOKE 权限列表 ON 数据库.表名 FROM '用户名'@'主机名';`

