## 关于UC的U4内核

以下资料和内容都是公网可以搜索得到的哈~再加上一些个人理解

网上能找到的关于UC内核的信息可谓少之又少……

[知乎上的UC浏览器专栏](https://zhuanlan.zhihu.com/ucbrowser?topic=pwa)

[UC开放平台官网](http://open-uc.uc.cn/solution/u4)

Web Push：基于Service Worker的Web推送能力。原理如下



embedView嵌入式View技术：在Web中嵌入来自Native的View。但讲道理而言，如果仅仅是在WebView中嵌入Native View，那么一般可用于一些高计算级别的页面。例如手机地图嵌入、内部动态图表、高能动画。这里面嵌入的方案如下：

而对于一些计算量不是特别多，而是交互性要求特别高的页面，例如沉浸式、手势滑动的Tab这一类的交互，则是需要Native View嵌入WebView的操作。一般Native中嵌入WebView的方案如下：



JS开发者的福音：[手势操作和JS阻塞](https://www.zhihu.com/question/24268253)



PWA技术（不是AMP噢）