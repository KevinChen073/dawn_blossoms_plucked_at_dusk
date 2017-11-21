## WKWebview

[简书上的WKWebivew](http://www.jianshu.com/p/403853b63537)

IOS8后推出的webview组件。JS引擎使用`Nitro JavaScript`引擎。和UIWebview不一样，WK使用了JIT编译。详情可以[看这里](https://ariya.io/2012/06/nitro-javascriptcore-and-jit)。

>- UIWebView still uses who-can-remember-that-JavaScript-engine-without-JIT
>- Mobile Safari uses Nitro



PS:

渲染引擎和JS引擎

>最开始渲染引擎和 JS 引擎并没有区分的很明确，后来 JS 引擎越来越独立，**内核就倾向于只指渲染引擎**。

不同的浏览器有不同的渲染引擎，Firefox浏览器为Gecko引擎，Safari为WebKit引擎，Chrome为Blink引擎。常用的浏览器渲染引擎如下：Trident、Gecko、Blink、Webkit、Edge HTML（IE Edge后）

历史上，IE独大时期使用渲染引擎（内核）为Trident，然而后续因为一家独大，各种不跟随W3C标准。于是Firefox渐渐受到开发者的青睐，其内核为（Gecko)。而苹果的浏览器safari用的是源自linux浏览器的内核KHTML的分支webkit，08年出现的Chrome使用的则是fork并且改良webkit的Chromium内核，后续走向webkit的分支Blink，直接换名。

参考自[主流浏览器内核历史](http://web.jobbole.com/84826/)



JavaScript引擎的主要作用是，读取网页中的代码，对其处理后运行。

WebKit 的 JavaScriptCore （移动端Nitro)和 Google 的 V8

参考[javascript引擎指南](http://web.jobbole.com/84351/)

附：

各大渲染引擎和JS引擎的一些关注邮件