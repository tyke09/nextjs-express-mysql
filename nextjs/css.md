# 引用css文件

​	

## 介绍

本文介绍在next.js框架中使用css文件的步骤。

​	

## 准备条件

按照 [开始使用](start.md) 中的说明创建项目。

​	

## 编写_document.js

创建 `pages/_document.js` ，并编写如下代码：

```jsx
import Document, { Head, Main, NextScript } from 'next/document'

export default class MyDocument extends Document {
  render() {
    return (
      <html>
        <Head>
          <link rel="stylesheet" href="/_next/static/style.css" />
        </Head>
        <body>
          <Main />
          <NextScript />
        </body>
      </html>
    )
  }
}
```

​		

## 安装next-css

执行如下命令：

```shell
npm install --save @zeit/next-css
```

​	

## 编写next.config.js

创建 `./next.config.js` ，编写如下代码：

```jsx
const withCSS = require('@zeit/next-css')
module.exports = withCSS()
```

​	

## 编写css文件

创建 `css` 文件夹，创建 `css/style.css` ，编写如下代码：

```css
p {
  font-size:100px;
}
```

​	

## 引用css文件

修改 `pages/index.js` 如下：

```jsx
import '../css/style.css';

export default () => (
  <div>
    <p>Hello Next.js</p>
  </div>
)
```



## 测试

打开 `http://localhost:3000` ，可以看到样式生效了。