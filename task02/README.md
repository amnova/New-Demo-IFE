# Task02

demo地址：https://amnova.github.io/New-Demo-IFE/task02/

---
## 这个DEMO我主要磨练掌握的技能

- 导航栏制作的复习（设置line-height实现文字垂直居中对齐的小技巧）
- HTML5 新标签<figure> <figcaption> 的用法掌握
- 怎么做一个好看的表格？
- 怎么根据要求对齐表单控件？
- 页面整体的布局练习
- 小乐趣：给网页标题前加一个可爱的小图标




## 这个DEMO涉及的我的知识盲区
> 简单把曾经遗忘的东西记录一下，下一次打开时我就会轻松忆起往昔的痛苦和迷茫

#### 1.点击链接后，如何在新的窗口打开相应链接？

```
<a href="#" target="_blank">我是一个贱萌贱萌的链接<a>
```

#### 2.box-shadow怎么用来着？
- 忘记了box-shadow怎么玩起来？下面是box-shadow的标志性用法

```
div{
    box-shadow: 5px 5px 5px rgba(0,0,0,.6);
}
```

#### 3.border-radius也忘了？
- 典型用法
```
input[type="submit"] {
    border-radius: 10px;
}
```
(掌握基本的经典用法就好啦，这个就是最常用的，其他复杂的参数了解就好，没必要一蹴而就的全都死记硬背。毕竟人的精力有限啊，况且记忆力也并不可靠)

#### 4.深度学习带标题的图像
https://www.w3.org/Style/Examples/007/figures


```
HTML:
    <figure>
        <figcaption>新年快乐</figcaption>
        <img src="imgs/01_edit.png">
    </figure>
	
CSS:
    article figure {
	border: 1px solid #999;
	width: 100px;
	padding:10px;
	text-align: center;
}

    article figure img {
	width: 100px;
}
```

#### 5.掌握好看的表格
- 跨列和跨行
colspan , rowspan

#### 6.掌握好看的表单
- label有两种用法，我更喜欢下面这种，用label包围文字和相应控件即可
- 运用 fieldset 和 legend 组合表单控件们

```
HTML:
    <fieldset>
        <legend>联系信息</legend>
        <label>
            Email: <br>
            <input type="text" name="email">
        </label>
        <label>
            Tel:<br>
            <input type="text" name="tel">
        </label>
    </fieldset>
```

#### 7.表单控件怎么对齐？
- 用浮动标题的方法对齐表单控件们（详见CSS代码注释部分）
- 用display:inline-block 实现对控件的名称部分（对应HTML 是<label><span>等行内元素）设置宽度，然后text-align:right实现想要的效果（代码详见task02的css文件）
- inline-block 产生神秘间距的小秘密
[点击我](http://www.zhangxinxu.com/wordpress/2012/04/inline-block-space-remove-%E5%8E%BB%E9%99%A4%E9%97%B4%E8%B7%9D/)

上面链接的原文地址：
http://www.zhangxinxu.com/wordpress/2012/04/inline-block-space-remove-%E5%8E%BB%E9%99%A4%E9%97%B4%E8%B7%9D/

相关内容的扩展阅读（有关display：inline-block)
http://www.zhangxinxu.com/wordpress/2010/11/%E6%8B%9C%E6%8B%9C%E4%BA%86%E6%B5%AE%E5%8A%A8%E5%B8%83%E5%B1%80-%E5%9F%BA%E4%BA%8Edisplayinline-block%E7%9A%84%E5%88%97%E8%A1%A8%E5%B8%83%E5%B1%80/

#### 8.设置了宽度，margin:0 atuo 才起作用？

是的，就是因为忽略了这一点，我为表单设置居中效果失败了。

而当为form设置了width:800px;我不仅得到了效果，而且惊喜的解决了之前么有理解的问题，就是收缩视窗之后，内容不会变形，不会流动起来，而是维持原样。原来这才是流式布局和冻结布局的巧妙运用！

之前学习整理的几种经典布局不仅是对整个页面，页面中的某一部分也可以异曲同工之妙的运用起来。**把某个div当做是body一样的运用**！ 这里就是这样的，我对form其实是运用起来了之前学习到的冻结布局，实现了我想要的效果！



#### 9.为网页标签的标题前加一个有趣的icon？

```
<link rel="icon" src="imgs/xx.ico" type="image/x-icon">
```
