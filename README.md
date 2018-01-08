# waterfall-layout

## 多图片瀑布布局法

瀑布流布局的原理是分栏装载图片，如果是横排横排的加载，就得考虑怎样实现参差不齐的效果。而用分栏的瀑布去解决就很简单了，根本不需要什么样式。

#### 瀑布流思想：

    首屏加载的时候，根据浏览器宽度以及每列宽度计算出列表个数，然后根据内容区的高度offsetHeight和clientHeight判断，如果clientHeight大于offsetHeight(document.documentElement.clientHeight > document.documentElement.offsetHeight-4)，则继续append一张新图片。
    
    当滚动的时候，对每一列的底部位置做检测，如果在屏幕中或屏幕上方（document.documentElement.scrollTop + document.documentElement.clientHeight >= document.documentElement.offsetHeight-2），则立即append三张新图片。
    
    通过windows.onresize事件来监测浏览器窗口大小的变化，然后通过window.location.reload()事件来重新加载当前文档。

    具体可参考 [瀑布流布局](http://www.zhangxinxu.com/wordpress/2012/03/多栏列表原理下实现的瀑布流布局-waterfall-layout/)

    offsetHeight: 获取对象相对于版面或由父坐标 offsetParent 属性指定的父坐标的高度
    
    clientHeight: 网页可见区域的高度
    
    scrollTop:设置或获取位于对象最顶端和窗口中可见内容的最顶端之间的距离，也就是网页被卷去的高度
    
    scrollHeight: 获取对象的滚动高度
    
    具体可参考[scrollHeight，clientHeight，offsetHeight在火狐、IE、谷歌浏览器下的区别](http://www.cnblogs.com/vicky-wangjiao/p/6949972.html)
    数组中取最大值思想，先把数组中第一个数当作最大值取出来放到变量max里面，再遍历去和数组中其他数比较，如果小于其他数，就把其他数赋值给max。

    注：想获得img的宽高，如果没有写样式的话直接去获得是空的

    网页加载的过程：
    1. 首先加载的是document文档。也就是HTML，以及包含的js文件、css文件。
    2. 加载完毕之后，才会继续加载各个图片，每个图片相当于一个单独的请求。
    3. 当document的ready的时候，也就是加载完成的时候，图片可是还没有加载完成，是刚刚准备加载。这时是得不到图片尺寸的。
    4. 当image的load或者onreadystatechange事件，可以处理判断，得到image的尺寸。

    所以把获取的方式加载img.onload函数里面去就能获得宽高了，或者设置一个timeout
    
    参考 [JS快速获取图片宽高的方法](http://www.css88.com/archives/5224/comment-page-1)

## 实现 [效果图](https://lulujianglab.github.io/waterfall-layout/)
