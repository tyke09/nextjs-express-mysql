# 整洁的url

​	

## 介绍

本文介绍使用整洁url路由的方式，类似 `https://book.douban.com/subject/30128172` ，在url中包含参数，但是直接将参数包含在url中，而不是使用问号 `?` 格式的查询字符串。

​	

## 准备条件

按照 [开始使用](start.md) 中的说明创建项目。

​	

## 创建server.js

在代码根目录创建 `server.js` ，编写如下代码：

```react
const express = require('express')
const next = require('next')

const dev = process.env.NODE_ENV !== 'production'
const app = next({ dev })
const handle = app.getRequestHandler()

app.prepare()
  .then(() => {
    const server = express()

    server.get('/subject/:id', (req, res) => {
      const actualPage = '/subject'
      const queryParams = { subjectId: req.params.id }
      app.render(req, res, actualPage, queryParams)
    })

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

​	

## 编写subject.js

在 `pages` 中创建 `pages/subject.js` ，编写如下代码

```react
export default (props) => (
  <div>
    <p>打开了subject页面，传入的id为{props.url.query.subjectId}.</p>
  </div>
)
```



## 修改index.js

将 `pages/index.js` 进行如下修改：

```react
export default () => (
  <div>
    <h1>书籍列表</h1>
    <ul>
      <li>
        <a href={'/subject/30128111'}>笑傲江湖</a>
      </li>
      <li>
        <a href={'/subject/30128333'}>神雕侠侣</a>
      </li>
      <li>
        <a href={'/subject/30128555'}>倚天屠龙记</a>
      </li>
    </ul>
  </div>
)
```

​			

## 修改scripts

对 `package.json` 中的 `scripts` 部分进行修改：

```json
"scripts": {
  "start": "node server.js"
}
```

​	

## 安装express

```shell
# 安装express
npm install --save express
```



## 测试

打开 `http://localhost:3000` ，依次点击不同的书名，可以看到正确加载了 `subject` 页面且成功获取传入的参数。