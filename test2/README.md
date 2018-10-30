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
结果:
```
![result](https://github.com/fishccc/Oracle/blob/master/test2/1.png)
用户名:wyz
角色:cyz
### 
![result](https://github.com/fishccc/Oracle/blob/master/test1/1.png)


![result](https://github.com/fishccc/Oracle/blob/master/test1/1.png)


![result](https://github.com/fishccc/Oracle/blob/master/test1/1.png)


