# 获取后台数据

​	

## 介绍

本文介绍后去后台数据的方法。

​	

## 准备条件

按照 [开始使用](start.md) 中的说明创建项目。

​	

## 安装isomorphic-unfetch

安装第三方库 `isomorphic-unfetch` ，用于fetch数据。

```shell
# 安装isomorphic-unfetch
npm install --save isomorphic-unfetch
```

​	

## 修改index页面

将 `pages/indexjs` 进行如下修改：

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

​	

## 运行

执行 `npm start`，打开 `http://localhost:3000` ，可以看到从远程服务器获取的数据被成功显示在页面上。

注意，这里获取数据的任务是在服务端进行的，通过log信息可以验证这一点。