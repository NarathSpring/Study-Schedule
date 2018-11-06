# Study Plan

- HTML
- ES6
- React
- React-router
- Vue
- Webpack
- Gatsby

## HTML

#### 标签的role属性

## ES6
## React
## React-router

#### 1、Usage 使用

```js
// index.js

import { Router, Route, hashHistory} from 'react-router'

render((
    <Router history = {hashHistory}>
        <Route path = '/' component = {App(根目录) />
        <Route path = '/others' component = {others} />
    </Router>
))
```

If you want to visit `/others`, make sure you have `#`. 

For example: **http://yourUrl/#/others**

#### 2、Navigating with Link 使用Link来做导航

> Perhaps the most used component in your app is Link. It's almost identical to the <a/> tag you're used to except that it's aware of the Router it was rendered in.

As far as I am concerned. You can use it as `<a>` tag. It has the almost the same function as `<a>`.


```js
// modules/App.js

import React from 'react'
import { Link } from 'react-router'

export default React.createClass({
  render() {
    return (
      <div>
        <h1>React Router Tutorial</h1>
        <ul role="nav">
          <li><Link to="/others">Others</Link></li>
        </ul>
      </div>
    )
  }
})
```

**Attention:** the path in `<Link>` must be exact the same as  `<Route>`

```js
// index.js

// ...

<Route path = '/others' component = {others} />

//...
```

#### 3、Nested Routes 鸟巢式的路由

`this.props.children`的使用 (暂时还没有理解，后面要回过头来看这个)

将所有元素以嵌套的方式放在一起, 使其他元素都成为`app`的子元素

```js
// index.js

// ...

render () {
    <Router history = {hashHistory}>
        <Route path = '/' component = {App}>
            <Route path = '/others' component = {Others} />
        </Route>
    </Router>,
    document.getElementById('app')
}
```

并在`App.js`中添加{`this.props.childre`}

```js
//App.js

//...

render () {
    // some tags here
    <div>
        // some tags here
    </div>
    
    {this.props.children}
}
```
#### 4、Link 的属性

We could use `activeStyle = {{color: 'red', //other properties here}}` or `activeClassName = 'className` to set up the active style.

```js
// App.js

//...

render(){
    return(
        ...
        <Link activeStyle = {{color: 'red'}} />
        <Link activeClassName = 'className' />
        ...
    )
}
```

> Nav Link Wrappers
> Most links in your site don't need to know they are active, usually just primary navigation links need to know. It's useful to wrap those so you don't have to remember what your activeClassName or activeStyle is everywhere.
> 
> We will use a spread operator here, the three dots. It clones our props and in this use case it clones activeClassName to our desired component for us to benefit from.
> 
> Create a new file at modules/NavLink.js that looks like this:
>
> ```js
> // modules/NavLink.js
> import React from 'react'
> import { Link } from 'react-router'
> 
> export default React.createClass({
>   render() {
>     return <Link {...this.props} activeClassName="active"/>
>   }
> })
>
> ```
> Now you can go change your links to NavLinks.
> 
> ```js
> // modules/App.js
> import NavLink from './NavLink'
> 
> // ...
> 
> <li><NavLink to="/about">About</NavLink></li>
> <li><NavLink to="/repos">Repos</NavLink></li>
> ```
> Oh, how beautiful upon the renders is the composability of components.

## Vue

## Webpack

#### Loaders 

First `npm install xxx-loader` in the commond line.

```
    npm install xxx-loader
```

then add the config in `webpack.config.js`

```(javascript)
//webpack.config.js

module.exports = {
    ...
    module:{
        loaders : [
            {
                test: /\.js/,
                // use `exclude` if you want to ignore some files
                // exclude: files,
                loader: 'xxx-loader'
            },
            {
                test: /\.css/,
                // use `exclude` if you want to ignore some files
                // exclude: files,
                loader: 'xxx-loader'
            }
        ]
}
```

#### Custom port 设置自定义端口

```(javascript)
//webpack.config.js

module.exports = {
    //other settings
    devServer: {
        host: '127.0.0.1',
        port: 'Any port you want it'
    }
}
```

## Gatsby