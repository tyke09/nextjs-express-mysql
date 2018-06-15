# 创建组件

​	

## 介绍

本文介绍创建组件的方法。

​	

## 准备条件

按照 [开始使用](start.md) 中的说明创建项目。

​	

## 编写一个组件

创建 `components` 文件夹，并在其中创建 `Header.js`，编写如下代码：

```react
import Link from 'next/link'

const linkStyle = {
  marginRight: 15
}

const Header = () => (
  <div>
    <Link href="/">
      <a style={linkStyle}>Home</a>
    </Link>
    <Link href="/about">
      <a style={linkStyle}>About</a>
    </Link>
  </div>
)

export default Header
```

​	

## 修改index页面

将 `pages/indexjs` 进行如下修改：

```react
import Header from '../components/Header'

export default () => (
  <div>
    <Header />
    <p>Hello Next.js</p>
  </div>
)
```



## 创建about页面

在 `pages` 中创建 `about.js` ，编写如下代码

```react
import Header from '../components/Header'

export default () => (
  <div>
    <Header />
    <p>This is the about page</p>
  </div>
)
```

​			

## 测试

打开 `http://localhost:3000` ，可以看到组件 `Header` 被 index和about两个页面成功引用。