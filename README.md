# waterfall-layout

## 多图片瀑布布局法

瀑布流布局的原理是分栏装载图片吗，一开始误以为横排横排的加载，就去想着怎么才能实现参差不齐的效果。用分栏的瀑布去解决就很简单了，根本不需要什么样式。瀑布流思想主要参考文章[瀑布流布局]（http://www.zhangxinxu.com/wordpress/2012/03/多栏列表原理下实现的瀑布流布局-waterfall-layout/）

数组中取最大值，先把数组中第一个数当作最大值取出来放到变量max里面，再遍历去和数组中其他数比较，如果小于其他数，就把其他数赋值给max。

注：想获得img的宽高，如果没有写样式的话直接去获得是空的，
    网页加载的过程是这样的，首先加载的是document文档。也就是HTML，以及包含的js文件、css文件。加载完毕之后，才会继续加载各个图片，每个图片相当于一个单独的请求。所以当document的ready的时候，也就是加载完成的时候，图片可是还没有加载完成，是刚刚准备加载。此时你当然得不到图片的尺寸了。当image的load或者onreadystatechange事件，可以处理判断，得到image的尺寸。

所以把获取的方式加载img.onload函数里面去就能获得宽高了，或者设置一个timeout。[参考](http://www.css88.com/archives/5224/comment-page-1)

 实现[效果图](https://lulujianglab.github.io/waterfall-layout/)
