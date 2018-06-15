# 页面间切换

​	

## 介绍

本文描述nextjs多个页面切换的方法。

​	

## 准备条件

按照 [开始使用](start.md) 中的说明创建项目。

​	

## 创建about页面

创建 `pages/about.js` ，编写如下代码

```react
export default () => (
  <div>
    <p>This is the about page</p>
  </div>
)
```

可以通过地址 http://localhost:3000/about 访问该页面。

​	

## 使用a标签跳转

将 `pages/index.js` 进行如下修改：

```react
export default () => (
  <div>
    <p>Hello Next.js</p>
    <a href="/about">about</a>
  </div>
)
```

现在可以从首页跳转到 `about` 页面了。

​	

## 使用Link跳转

将 `pages/index.js` 进行如下修改：

```react
import Link from 'next/link';

export default () => (
  <div>
    <p>Hello Next.js</p>
    <Link href="/about">
      <a>about</a>
    </Link>
  </div>
)
```

使用Link可以进行客户端跳转。