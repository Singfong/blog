## 背景

在编写组件化时，Vue提示报错：Error in v-on handler: "ReferenceError: state is not defined"

![pic](https://img-blog.csdnimg.cn/ad4572d8997c470ebb6f2dbdc7c4d6de.png)

## 解决报错思路

1.console控制台在index.js组件的第27行代码，还能输出语句：“mutations中的JIA被调用了”

2.故怀疑下一句代码有报错，注释掉，再观察控制台。此时无报错输出。index.js原代码如下：

![pic](https://img-blog.csdnimg.cn/ea3d877b9eda401eac57bab56fa46f6d.png)

3.注释掉第28行代码，console.log出来state的值，发现为undefined。

```javascript
`mutations:{`
        `JIA(store,value){`
            `console.log('mutations中的JIA被调用了',store,value);`
            `// state.sum += value;`
            `console.log(store.state);`
        `},`
`}`
```

 ![pic](https://img-blog.csdnimg.cn/bf0f4089108945a0bd43ac04fcd408c7.png)

4.奇怪？为什么会这样？开始检查配置项里面是否有写state，也有呀。

 ![pic](https://img-blog.csdnimg.cn/5925383194444b9381b80a559f023b33.png)

 5.最后检查一通发现：还是index.js第28行的错误引起的。JIA（）方法里面的参数，我写的是“store”,但是用来计算的时候，用的参数为“state”。难怪会报undefined的错。

## 反思

对于代码书写时候，要更加细致小心。