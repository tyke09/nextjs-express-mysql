#开始使用

​	

##介绍

本文描述使用node.js在服务端连接mysql数据库的方法。开发环境如下：

win10 x64

node v6.10.0

​	

##前置条件

电脑上已成功安装mysql数据库。

​	

##创建数据库和表

打开workbench工具，执行以下sql命令：

```mysql
#创建数据库
create database testdb;

#使用数据库
use testdb;

#创建表
create table testtable (
  `id` int auto_increment primary key,
  `name` varchar(45) default null,
  `age` int(11) default null
);

#加入数据
insert into testtable (name, age) values ('张三', 20);
insert into testtable (name, age) values ('李四', 30);
insert into testtable (name, age) values ('王五', 40);

#创建用户并授权
create user testuser@'localhost' identified by '123456';
grant select, insert, update, delete on testdb.* to testuser@'localhost';
flush privileges;
```


​    

​	

##初始化项目

在磁盘上新建一个文件夹，进入该文件夹，打开命令行工具，并执行： 

```shell
# 初始化项目
npm init -y

# 安装mysql
npm install --save mysql
```


​	

##创建server.js

创建文件 ./server.js ，编写以下代码：

```jsx
const express = require('express')
const next = require('next')
const mysql = require('mysql');

const dev = process.env.NODE_ENV !== 'production'
const app = next({ dev })
const handle = app.getRequestHandler()

const connection = mysql.createConnection({
  host: 'localhost',
  user: 'testuser',
  password: '123456',
  database: 'testdb'
});

connection.connect();

const sql = 'select * from testtable';

connection.query(sql, function (error, results, fields) {
  if (error) throw error;
  console.log(results);
});

connection.end();
```


 	

##运行

在项目根目录执行命令：

```shell
# 启动项目
node server.js
```

可以看到成功从mysql中查询到数据。



 