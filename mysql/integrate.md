# 和前端集成

​	

## 介绍

本文介绍将数据库与前台框架next.js集成的方法，在服务端渲染页面时，从数据库查询数据，完成渲染。

​	

## 前置条件

已按照[开始使用](start.md)中的步骤准备好mysql数据库以及表和数据。

​	

## 创建项目

在磁盘上新建一个文件夹 `next-study1` ，进入该文件夹，打开命令行工具，并执行： 

```sh
# 初始化项目
npm init -y

# 安装next和mysql包
npm install --save react react-dom next mysql

# 创建文件夹
mkdir pages
```

​	

## 封装查询模块

创建文件 `dao.js` ，编写以下代码：

```jsx

const mysql = eval("require('mysql')");

const query = function (sql) {
  return new Promise((resolve, reject) => {
    const connection = mysql.createConnection({
      host: 'localhost',
      user: 'testuser',
      password: '123456',
      database: 'testdb'
    });

    connection.connect();
    connection.query(sql, function (error, results, fields) {
      if (error) {
        reject(error);
      } else {
        resolve(results);
      }
    });

    connection.end();
  })
}

const dao = {
  getData: function () {
    const sql = 'select * from testtable';
    return query(sql);
  }
};

module.exports = dao;
```

​	

## 编写页面

创建文件 `pages/index.js` ，编写以下代码：

```jsx


const Index = (props) => (
  <div>
    <h1>从数据库中获得的数据</h1>
    <table>
      <thead>
        <tr>
          <th>姓名</th>
          <th>年龄</th>
        </tr>
      </thead>
      <tbody>
        {
          (props.data || []).map((item, index) => {
            return (
              <tr key={index}>
                <td>{item.name}</td>
                <td>{item.age}</td>
              </tr>
            )
          })
        }
      </tbody>
    </table>
  </div>
)

Index.getInitialProps = async function () {
  const dao = require('../dao');
  const data = await dao.getData();
  return { data: data };
}

export default Index
```

​	

## 修改脚本

对 `package.json` 进行如下修改：

```json

```



## 运行

在项目根目录执行命令：

```shell
# 启动项目
node server.js
```

可以看到成功从mysql中查询到数据，且显示到页面中。



 