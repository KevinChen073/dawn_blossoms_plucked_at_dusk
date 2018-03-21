## 关于ES6继承以及继承的生命周期

#### ES6继承

首先，继承基于ES5的原型链机制。

babel中的继承方式实现方法：

1. 最基础的继承实现方法应该是`a.__proto__ =b`。因此也不会出现多重继承的菱形问题
2. 并且babel加上了对父类初始化的检测：`super(props)`,用`instanceOf`来检测新的父实例和function的关系



#### React中继承的生命周期

由于React `Component`类里面自带了生命周期，一般而言，如果后续有组件想继承基类A，同时这个基类A带了一些通用配置，那么较好的方法应该是让基类A把事情都放在constructor中做，然后继续暴露一些可供修改的方法给下一个子类用。对某些特殊的方法，要求子组件优先调用super.xxx();

`React.Component` -> `Base Component` -> `Biz Component`

其中，Base Component应该包含一些业务通用逻辑，如打点的初始化配置、通用环境变量（多语言、Platform）、通用方法暴露（如打点方法、通用逻辑方法等）



#### 参考文章

[ECMAScript 6入门](http://es6.ruanyifeng.com/#docs/class-extends)

[babel转化机制](https://github.com/lcxfs1991/blog/issues/9)

[ES6 class中的super](https://www.jianshu.com/p/1b7307201667?utm_campaign=maleskine&utm_content=note&utm_medium=seo_notes&utm_source=recommendation)

