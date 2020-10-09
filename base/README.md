# React

这个是简单的入门文章啦。

`react` 的精髓：`虚拟dom` `函数式编程`；
 
<br>
<br>



## 什么是虚拟dom

我们的页面是由一个个 `html` 组合成的，如果用 `Javascript` 来描述的话，它会当作一个 `Json` 对象。

`虚拟Dom` 的思想就是将 `Html` 抽象成 `Javascript` 对象。


<br>
 
#### 传统dom更新

在传统的开发模式中，我们需要手动去操作 `dom` 来进行更新。那这样的操作成本是非常高的。以为在操作的过程当中，有可能去遍历了 `dom` 节点，可能造成 `重排` `重绘`，导致性能消耗过大。


<br>
<br>

#### 虚拟dom

`react` 把真实 `dom树` 转换成 `javascript对象书`，也就是 `virtual dom` 。`virtual dom` 的存在把以前多次操作 `dom` 的方式改为了一次，从而尽大的提高了页面的刷新效率，避免系统浪费。


<br>
<br>

## 函数式编程

<br>

#### 什么是函数式编程

`函数式编程` 是结构化编程的一种，主要的思想概念就是在代码结构中做了很多的 `function` 。

`react` 充分利用 `函数式` 编程的方法来减少冗余代码，`函数式` 编程也式 `react` 的精髓。

<br>

#### 函数式编程的好处

* 代码简介，清晰明了；
* 方便代码管理和维护；

<br>

>`函数式编程` 是 `react` 的精髓。

<br>
<br>


## JSX语法


#### 什么是JSX语法

`什么是JSX语法` 是 `javascript` 和 `xml` 相结合的一种格式。


* 当遇到 `<` 的时候就当 `html` 解析。
* 当遇到 `{` 的时候就当 `javascript` 解析。
* 小写首字母对应的是 `dom` 元素；
* 大写首字母对应的是 `组件`；
* 注释使用 `js` 的注释方法； 
* `class` 是 `js` 语法的关键字，所以需要将 `class` 改成 `className`；
* `for` 也是 `js` 语法的关键字，所以需要将 `for` 改成 `htmlFor`；
* `for` 也是 `js` 语法的关键字，所以需要将 `for` 改成 `htmlFor`；


<br>
<br>

## 组件

当我们想用组件描绘到我们的页面上，我们应该使用 `ReactDOM.render` 方法。


#### 组件的声明方式

我们可以使用函数来声明一个函数

```javascript
import React from 'react';

function Home(){                    //使用 `function` 来定义一个函数
    return <h1>hello world</h1>
}

export default Home;
```

<br>

或者你可以使用一个 `class` 来定义一个组件

```javascript
iomport React , {Component} from 'react';

class Home extends Component{           //使用一个 `class` 来定义一个函数
    render(){
        return(
            <h1>hello world</h1>
        )
    }
}

export default Home;
```

>原生的 `HTML` 是以小写字母开头的，为来避免冲突，我们在定义组件的时候一定以 `大写字母` 开头。

>组件只能包含一个顶级标签，不能同时出现多个，否则会报错。

<br>

以上两种方式都可以创建一个组件，那有什么区别呢？


<br>
<br>


#### 组件中的循环


首先定义一个 `data` 的文件夹，增加一个 `home.js` 文件，增加假数据，命名为 `home.js`。

<br>


* home.js
```javascript
let listData = [
    {name: 'peter', age: '12'},
    {name: 'anne', age: '14'},
    {name: 'ken', age: '25'},
    {name: 'osca', age: '23'},
    {name: 'olive', age: '16'}
]
export default listData；
```

<br>


* List 组件
```javascript
import React from 'react';
import Data from '../data/home'；
function List(){
  return <ul>
   {
      Data.map((items,index)=>{
      return <li>name: {items.name} + age: {items.age}</li>
      })
   }
  </ul>
}
```


<br>
<br>


#### 组件呈现在页面的方式

```javascript
ReactDOM.render   
    参数一：dom 对象            //这里是我们的 dom 对象，也可以是我们的组件
    参数二：注入点              //相当于容器，就是把上面的 dom 对象注入到这里面来
```

```javascript
ReactDOM.render(){
    <div>Hello world</div>,                 
    document.querySelector('#wrapper')      //将上面的 dom 对象注入到下面的 #wrapper 里来
}
```

<br>
<br>

#### 组件传参

```javascript
function Home(){
  return (
    <div>
      <Headline text="hello world this is bill" />
    </div>
  )
}

function Headline(props){
  return <h1>{props.text}</h1>
}
```


###### ES5的声明方式

```javascript
var Hello = React.createClass ({
    render:function(){
        return(
            <div>hello world</div>
        )
    }
})
```

<br>

###### ES6的声明方式


```javascript
class Hello extends React.Component {           //Hello 是我们的组件名字，记住要 `大写`,继承了 React.Component
    render(){                                   //同样里面是一个 render() 方法
        return (                                //return dom 元素
            <div>hello world</div>
        )
    }
}
```

<br>

>以前我们可以使用 `es5` 的生命方法，但是现在我们大部分都使用 `es6` 的方法。


<br>
<br>

#### 组件声明与描绘


###### 单个组件声明与描绘

基于上面，我们声明一个组件，并且使用它的话：

```javascript
class Hello extends React.Component{
    render(){
        return(
            <div>hello world</div>
        )
    }
}

ReactDOM.render(
    <div><Hello/></div>,
     document.querySelector('#wrapper')
)
```


<br>
<br>


###### 多个组件声明与描绘

```javascript
class Hello extends React.Component {
    render(){
        return (
            <div>hello world</div>
        )
    }
}

class Person extends React.Component {
    render(){
        return(
            <div>my name is perter</div>
        )
    }
}

ReactDOM.render(
    <div>
        <Hello/>
        <Person/>
    <div>,
    document.querySelector('#wrapper')
}
```


#### 属性




<br>
<br>


#### state


我们通过设置 `state` 来改变 `UI` 的状态；

```javascript
import React from 'react';

class Nav extends React.Component{
    constructor(){
        super()
        this.state = {
            swithch: true
        }
    }
}
```


## 你不知道的react

#### 如果本地打开打包后的文件

我们完成项目之后会将项目进行打包，但是打包之后的 `index.html` 在本地打开为空白页，无法预览。

我们只要在 `package.json` 中添加 

```javascript
"homepage":"./"
```

然后重新打包一次就好了。

<br>
<br>

#### react不要那么多嵌套

在我们做组件的时候，出现多个兄弟节点的时候我们需要一个父级节点包裹着，这样的话在渲染的时候就会多出很多 `<div></div>` 标签。

在 `vue` 里，我们可以使用 `<template></template>` 包裹子元素解决这个问题。

在 `react` 里，我们可以使用 `<React.Fragment></React.Fragment>` 包裹子元素解决这个问题。

<br>
<br>

#### 函数组件和类组件的区别

我们先来了解一下什么是 `函数组件`

**函数组件**

```javascript
function Button(props){
    return <button>submit</button>
}
```

<br>
<br>

那什么是 `类组件` 呢？



**类组件**

```javascript
class Button extends React.Component{
    render(){
        return(
            <button>submit</button>
        )
    }
}
```

<br>
<br>

**它们的区别是什么**

|区别|函数组件|类组建|
|:-|:-:|:-:|
|是否有this|No|Yes|
|是否有生命周期|No|Yes|
|是否有状态|No<br>全靠 `props` 传递进来|Yes<br>可以自己建立状态|



<br>
<br>


#### 使用css的几种方式

* 行内样式
* 声明样式
* 引入样式
* css Module 样式
* style-component


<br>

**行内样式**

```javascript
class example extends Component{
    render(){
        return(
            <div style={{background:'#fff';color:'#000'}}>This is an Example</div>
        )
    }
}
```

<br>
<br>

**声明样式**

```javascript
const boxOne = {
    background: 'black',
    color: 'white',
    fontSize: '20px'
}

class example extends Component{
    render(){
        return(
            <div style={boxOne}>hello world</div>
        )
    }
}
```

