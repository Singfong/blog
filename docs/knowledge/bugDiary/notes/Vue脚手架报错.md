## 背景
运行命令行：npm run serve时，提示报错：

error  Component name "School" should always be multi-word  vue/multi-word-component-names（组件名称“School”应始终为多字vue/多字组件名称）

![pic](https://img-blog.csdnimg.cn/4a65bf5da87f40f58ab25b1f956d570d.png)

## 解决方法
打开文件夹中 vue.config.js，配置命令行lintOnSave:false，

这个命令行目的是，关闭自动语法检查，使得代码中闲置代码不被检查到，导致报错

![pic](https://img-blog.csdnimg.cn/6b2e25012e884cba886d473cc7380819.png)

 最后 再次运行命令行npm run serve，即可成功运行。