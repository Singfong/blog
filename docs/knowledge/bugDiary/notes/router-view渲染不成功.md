## 背景

在div中引入router-link标签实现路由的切换后，再在指定的位置使用router-view显示与 url 对应的组件，发现页面无法正常渲染。

```javascript
<div class="list-group">
 
          <!-- Vue中借助router-link标签实现路由的切换 -->
          <router-link class="list-group-item" active-class="active" to="/about.html">About</router-link>
          <router-link class="list-group-item" active-class="active" to="/home.html">Home</router-link>
        </div>
```

```javascript
<div class="panel-body">
            <!-- 指定组件的呈现位置 -->
			      <router-view></router-view>
          </div>
```

![pic](https://img-blog.csdnimg.cn/5381dce5b9224a2088151b5253027691.png)

## 思路
1.检查路由的配置，先看下路由配置。路径和组件名看起来没有什么大问题，网上其他帖子需要注意的routes拼写问题也检查好几遍，也没有问题。

![pic](https://img-blog.csdnimg.cn/2a2561a0904345d59772097d3c25bd5d.png)

 2.于是转换思路，最终检查一通下来，发现<router-link class="list-group-item" active-class="active" to="/about.html">About</router-link>有问题。

里面to是用来：传递指定链接，这个值可以是一个字符串或者是描述目标位置的对象。

不应该是xxxx.html。

![pic](https://img-blog.csdnimg.cn/3ea2cd874f51463080ff55a38b4a7de9.png)

 3.将.html删除之后，保存即可显示router-view所渲染的内容。

## 总结
对<router-link to></router-link>使用及传参不熟悉，导致页面渲染不成功。引以为鉴。