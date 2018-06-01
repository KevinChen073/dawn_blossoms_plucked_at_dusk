### gulp问题

分类：技术领域 - 前端 - 工程构建

- 全局安装过gulp了，为什么运行gulp命令提示 Local gulp not found

为了控制依赖，package.json中使用的依赖，一般都要求局部安装，由项目自己去管理依赖版本。而命令行工具才会全局安装。



参考链接：

知乎：https://www.zhihu.com/question/36023122

SG：https://segmentfault.com/q/1010000002702134

SO：https://stackoverflow.com/questions/22115400/why-do-we-need-to-install-gulp-globally-and-locally

相关点：

- npm安装中的全局和局部安装关系
- gulp怎么做到必须全局和局部都安装



产生原因：

混淆了全局安装和项目依赖安装的意义。