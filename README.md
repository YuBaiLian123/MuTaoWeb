**慕淘网**	

一、网页预览

![幕淘网](https://github.com/YuBaiLian123/MuTaoWeb/blob/master/mutaoimg.png)

二、网页功能简介

1、搜索框具有提交验证和自动完成（对接淘宝网）以及显示隐藏下拉层的功能；

2、“我的慕淘”、“收藏夹”、“卖家中心”、“联系客服”、“商品分类”、“幻灯片”、“商品楼层的切换选项卡“等均可以切换多种显示效果，例如淡入淡出效果、上下滚动效果、左右滚动等效果；

3、电梯具有跳转相应楼层的功能以及滚动监听功能；

4、侧栏工具条具有回到顶部功能以及一定的动画效果。

5、“卖家中心”、“联系客服”、“商品分类”、“幻灯片”、“商品楼层的切换选项卡”、“商品楼层”均具有按需加载的功能，其中电梯的滚动监听功能配合商品楼层来实现按需加载，使性能得到优化。

三、实现过程简介

1、站点导航的实现：导航中将“我的慕淘”、“收藏夹”、“卖家中心”的下拉菜单封装成为组件，使得下拉菜单功能组件能够在网页其他部分（“收藏夹”、“卖家中心”、）进行很好的复用。其中下拉层的显示隐藏主要采用了两种方式来实现，第一种是无动画的方式，第二种是有动画的方式（淡入淡出、上卷下卷、左右卷、或者上卷下卷耦合淡入淡出等）；有动画的方式按照实现的方式来分类又分为JS方式和CSS3方式，因浏览器兼容性问题导致的无法实现CSS3方式的动画效果时，可由JS方式替代。显示隐藏不仅仅用在下拉菜单中，网页中的幻灯片、Tab选项卡等均需要用到显示隐藏效果，故将显示隐藏相关的代码单独封装成一个模块以便复用。

2、搜索功能组件化：采用面向对象的方式来对搜索框的功能进行封装，搜索框的自动完成的触发是通过给输入框绑定input事件（IE678都不兼容，亦可采用keyup事件来实现）来达到输入内容即发送ajax请求。

3、中心focus区组件化：对幻灯片的淡入淡出组件和滑入滑出组件进行封装并优化代码，”商品分类“和幻灯片的按需加载同”卖家中心“一样，通过向后台获取Json数据，然后加载进来，并且只加载一次。

4、按需加载楼层模块的实现：通过对之前封装好的组件的复用和调整，来实现按需加载的效果。

5、电梯和侧栏工具条的实现：电梯能实现标识楼层和滚动监听，可对相应的楼层进行标识和按需加载，在点击相应的楼层号时可以到达相应的楼层；侧栏工具条可以实现回到顶部并具有一定的动画效果
