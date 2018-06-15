# 开始使用

​	

## 介绍

本文描述使用node.js在服务端连接mysql数据库的方法。开发环境如下：

win10 x64

node v6.10.0

​	

## 前置条件

电脑上已成功安装mysql数据库。

​	

## 创建数据库和表

打开workbench工具，执行以下sql命令：

```mysql
#创建数据库
create database testdb;

--创建表



```

​	

## 初始化项目

在磁盘上新建一个文件夹，进入该文件夹，打开命令行工具，并执行： 

```powershell
# 初始化项目
npm init -y

# 安装react和next
npm install --save react react-dom next

# 创建文件夹
mkdir pages
```

​	





## 编写页面

创建文件 `./pages/index.js` ，编写以下代码：

```jsx

```



## 创建server.js

创建文件 `./server.js` ，编写以下代码：

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



## 添加命令

打开 `package.json` ，对 `scripts` 部分进行修改，修改如下：

```json
"scripts": {
  "start": "next"
}
```

​		

## 运行项目

在项目根目录执行 `npm start` 命令：

```shell
# 启动项目
npm start
```

打开浏览器，输入 `http://localhost:3000/` ，可以看到提示"404 This page could not be found"，说明网站启动成功，但是目前找不到任何页面。





## 编写第一个页面

在 `pages` 文件夹里面添加 `index.js` 文件，并编写如下的代码：

```react
export default () => (
  <div>
    <p>Hello Next.js</p>
  </div>
)
```

保存文件，切换到浏览器，可以看到网页中成功显示 "Hello Next.js"。