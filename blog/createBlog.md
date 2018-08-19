#### Vue + Github 快速生成博客
最近一直想撸个博客生成器，能力有限，刚入`vue` 不久，也是处于学习状态，于是就先用`github`撸了个简单的。 

目前初步工作大致完成，剩下就是修改样式。  
github地址:https://github.com/sallenhandong/vue-blog

#### 1. 首先创建 repo 名字就是 your_user_name.github.io
这是我创建好的
https://github.com/sallenhandong/sallenhandong.github.io  
 - 你可以修改 cofig.json  
 - Tags.type 和 d.type.需要一一对应  
```
{
  "d": [
    {
      "gitname": "ios.md",
      "type": 0,
      "title": "ios",
      "tags": ["文章", "JS"],
      "pic": " ",
      "info": "ios",
      "date": "2018/02/28"
    }
    
  ],
  "t": [
    {
      "tags": [{
        "name":"iOS",
        "count":1,
        "type":0
      }, 
        {
        "name":"JavaScript",
        "count":0,
        "type":0
      }]
    }
    
  ]
}

```
#### 2. clone this project and build 
-   需要安装node环境 然后安装yarn
#### Project setup
```
yarn install
```

#### Compiles and hot-reloads for development
```
yarn run serve
```

#### Compiles and minifies for production
```
yarn run build
```
#### To Do
- 增加模板
- 修改样式

#### Issue
 - vue如何动态去添加模板样式？
 - 归档功能暂未实现
 - 如何制作命令行工具，通过命令行创建博客以及发布？
 
欢迎交流讨论，互相学习。

#### 持续更新
> * Follow: https://github.com/sallenhandong
> * Source: slimsallen.com/#/detail/createBlog.md
