# Oracle

## 实验二

### 用户创建及角色分配
代码:

```SQL
SQL> CREATE ROLE cyz;
SQL> GRANT connect,resource,CREATE VIEW TO cyz;
SQL> CREATE USER wyz IDENTIFIED BY 123 DEFAULT TABLESPACE users TEMPORARY TABLESPACE temp;
SQL> ALTER USER wyz QUOTA 50M ON users;
SQL> GRANT cyz TO wyz;
```
结果:
![result](https://github.com/fishccc/Oracle/blob/master/test2/1.png)
用户名:wyz
角色:cyz
### 新用户wyz连接到pdborcl,创建表mytable和视图myview，插入数据，最后将myview的SELECT对象权限授予hr用户。

代码:
```SQL
show user;
SQL> CREATE TABLE mytable (id number,name varchar(50));
SQL> INSERT INTO mytable(id,name)VALUES(1,'zhang');
SQL> INSERT INTO mytable(id,name)VALUES (2,'wang');
SQL> CREATE VIEW myview AS SELECT name FROM mytable;
SELECT * FROM myview;
```
结果:
![result](https://github.com/fishccc/Oracle/blob/master/test2/2-1.png)
![result](https://github.com/fishccc/Oracle/blob/master/test2/2-2.png)

### 用户hr连接到pdborcl，查询wyz授予它的视图myview
代码:
```SQL
SQL> SELECT * FROM wyz.myview;
```
结果:
![result](https://github.com/fishccc/Oracle/blob/master/test2/33.png)

### 查看数据库的使用情况
结果:
![result](https://github.com/fishccc/Oracle/blob/master/test2/4.png)


