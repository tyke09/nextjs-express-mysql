# 修改head

​	

## 介绍

本文介绍在next.js框架中修改head的方法。

​	

## 准备条件

按照 [开始使用](start.md) 中的说明创建项目。

​	

## 修改index.js

将 `pages/index.js` 修改如下：

```jsx
import Head from 'next/head'

export default () => (
  <div>
    <Head>
      <title>My page title</title>
      <meta name="viewport" content="initial-scale=1.0, width=device-width" />
    </Head>
    <p>Hello Next.js</p>
  </div>
)
```

​	

## 测试

打开 `http://localhost:3000` ，可以看到 `<head>` 应用成功。