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
grant all on localhost.testdb to 'testuser'@'localhost';
flush privileges;
```


​    

​	

##初始化项目

在磁盘上新建一个文件夹，进入该文件夹，打开命令行工具，并执行： 

```shell
# 初始化项目
npm init -y

# 安装react和next
npm install --save react react-dom next

# 安装mysql
npm install --save mysql

# 创建文件夹
mkdir pages
```


​	





##编写页面

创建文件 ./pages/index.js ，编写以下代码：

```jsx
import fetch from 'isomorphic-unfetch'

const Index = (props) => (
  <div>
    <h1>Batman TV Shows</h1>
    <ul>
      {props.shows.map(({ show }) => (
        <li key={show.id}>
          {show.name}
        </li>
      ))}
    </ul>
  </div>
)

Index.getInitialProps = async function () {
  const res = await fetch('https://api.tvmaze.com/search/shows?q=batman')
  const data = await res.json()

  console.log(`Show data fetched. Count: ${data.length}`)

  return {
    shows: data
  }
}

export default Index
```



##创建server.js

创建文件 ./server.js ，编写以下代码：

```jsx
const express = require('express')
const next = require('next')

const dev = process.env.NODE_ENV !== 'production'
const app = next({ dev })
const handle = app.getRequestHandler()

app.prepare()
  .then(() => {
    const server = express()
     
    server.get('*', (req, res) => {
      return handle(req, res)
    })

    server.listen(3000, (err) => {
      if (err) throw err
      console.log('> Ready on http://localhost:3000')
    })
  })
  .catch((ex) => {
    console.error(ex.stack)
    process.exit(1)
  })
```



##添加命令

打开 package.json ，对 scripts 部分进行修改，修改如下：

    "scripts": {
      "start": "next"
    }


​		

##运行项目

在项目根目录执行 npm start 命令：

    # 启动项目
    npm start

打开浏览器，输入 http://localhost:3000/ ，可以看到提示"404 This page could not be found"，说明网站启动成功，但是目前找不到任何页面。



 