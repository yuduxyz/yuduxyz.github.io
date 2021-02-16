---
title: Next.js 路由
date: 2021-02-16 08:23:07
tags:
---

Next.js 提供了 Link 组件和 Router 对象。

Link的机制并不是在Button上增加了a标签实现的跳转，而是对其中的组件添加了click事件，然后在浏览器中创建一个路由，在最终渲染的结果上并不会对Button包裹任何元素，我们也可以看到点击Button页面也不会有刷新的情况。

还有一点需要说明的是,Link通过React.Children.only规定了它所包含的元素只能有一个，如果我们再并列Button写一个标签就会报错。
```js
<Link href="/a">
  <Button>跳转到A</Button>
  <Button>也跳转到A</Button>//报错
</Link>
```

如果我们有这种需求,可以将两个Button包裹在<div>中
```js
<div>
  <Button>跳转到A</Button>
  <Button>也跳转到A</Button>
</div>
```
复制代码此时点击两个按钮都会跳转到a页面，(知道事件冒泡的小伙伴可能对为什么都能跳转到a页面，不清楚的小伙伴可以去查查事件冒泡和捕获)

next.js为我们提供的并不只是Link组件，它还为我们提供了Router的方式 Tips: 这里的Router不是一个组件而是一个路由对象，Link的实现原理也是基于Router对象

浏览器路由 vs 服务器路由

https://juejin.cn/post/6844903827615776775

多级路由
如果路由有多级，直接在pages下创立父级目录，再把最终路由文件放入目录下即可实现多级路由。如在pages目录下创建user目录，user下再创建index.js和home.js，那么路由/user就对应index.js文件，/user/home就对应home.js文件

https://jspang.com/detailed?id=51

路由原理 https://www.codeleading.com/article/3908587604/