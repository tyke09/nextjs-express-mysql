# 加载图片

​	

## 介绍

本文介绍在next.js框架中在页面中引用图片的步骤。

​	

## 准备条件

按照 [开始使用](start.md) 中的说明创建项目。

​	

## 创建static文件夹

在根目录创建 `static` 文件夹，用于存放图片，将图片文件 `image.jpg` 放在里面。

​			

## 修改index.js

将 `pages/index.js` 修改如下：

```jsx
export default () => (
  <div>
    <p>Hello Next.js</p>
    <img src="static/image.jpg"/>
  </div>
)
```

​	

## 测试

打开 `http://localhost:3000` ，可以看到图片显示成功。