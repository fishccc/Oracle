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
代码:
```SQL
SQL>SELECT tablespace_name,FILE_NAME,BYTES/1024/1024 MB,MAXBYTES/1024/1024 MAX_MB,autoextensible FROM dba_data_files  WHERE  tablespace_name='USERS';

SQL> SELECT a.tablespace_name "表空间名",Total/1024/1024 "大小MB",
 free/1024/1024 "剩余MB",( total - free )/1024/1024 "使用MB",
 Round(( total - free )/ total,4)* 100 "使用率%"
 from (SELECT tablespace_name,Sum(bytes)free
        FROM   dba_free_space group  BY tablespace_name)a,
       (SELECT tablespace_name,Sum(bytes)total FROM dba_data_files
        group  BY tablespace_name)b
 where  a.tablespace_name = b.tablespace_name;
```
结果:

![result](https://github.com/fishccc/Oracle/blob/master/test2/4-1.png)
![result](https://github.com/fishccc/Oracle/blob/master/test2/4-2.png)


