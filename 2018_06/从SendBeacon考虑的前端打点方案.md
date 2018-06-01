## 从SendBeacon考虑的前端打点方案

### sendBeacon是啥

**参考**：MDN说明：https://developer.mozilla.org/zh-CN/docs/Web/API/Navigator/sendBeacon

**用处**：浏览器提供的post方式，即使在页面unload后也能够保障请求发送，用于解决打点场景问题。

**兼容性**：参考caniuse

![image-20180601231224509](/var/folders/gk/_wxqnhzd7y77mq00gz4p2q7m0000gn/T/abnerworks.Typora/image-20180601231224509.png)

> Beacon 不是烤肉的意思，是灯塔的意思（A signal fire to notify of the approach of an enemy, or to give any notice, commonly of warning.），

> 烤肉是 bacon (美 ['bekən] 杯啃) ；Beacon（美 ['bikən]  逼啃~~）

### 目前主流留恋其打点方案及其优劣

> 其中一种是通过在卸载事件处理器中创建一个图片元素并设置它的 src 属性的方法来延迟卸载以保证数据的发送。因为绝大多数用户代理会延迟卸载以保证图片的载入，所以数据可以在卸载事件中发送。
>
> 另一种技术是通过创建一个几秒钟的 no-op 循环来延迟卸载并向服务器发送数据。

1. Image方式：通过给服务器发送图片请求，把需要记录的信息通过参数记录，IE中会被abort
2. sendBeacon
3. 轮询发xhr：轮询发送请求

### 扩展一下，移动端打点方案

1. 需要考虑移动端场景的浏览器，例如UC这类型。
2. APP中可以考虑APP提供的打点能力，让APP记录打点，再统一发送。