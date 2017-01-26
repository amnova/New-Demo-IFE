# Task03

DEMO地址：

## 这个DEMO磨练我的技能
- 三栏布局练习


## 这个DEMO涉及的我的知识盲区
- 解决子元素浮动后，父元素塌陷的问题
- 解决子元素绝对定位后，父元素高度比绝对定位的子元素小

#### 1、解决浮动后父元素的塌陷问题

- 讨巧的办法
- 张鑫旭大神推荐的办法
- 设置overflow的方法

**①先说讨巧的办法**


```
<div style="clear:both;"></div>
```
直接一个div，当作最后一个子标签放到父标签那儿，此方法屡试不爽，兼容性强，使用方便，是初学时使用的上佳之选。

不过在语义方面做得不够好，而且有时候一不留神中间多了个空格会产生一段空白高度的。

**②张大神推荐的办法：after + zoom方法**

> 先来简单讲讲after，所谓after，就是指标签的最后一个子元素的后面。于是呢，我们可以用CSS代码生成一个具有clear属性的元素，其中的关键样式就是content了。或许您从网上看到的content里面的内容是”.”一个点，我试了很多次，貌似随便写什么东西都没有问题，比如content:'clear both';没问题，或是content:'张鑫旭'也是ok的。

> 于是有：
> 
```
.fix{zoom:1;}
.fix:after{display:block; content:'clear'; clear:both; line-height:0; visibility:hidden;}
```

> 这里的line-height:0写成height:0也是可以的。此方法可以说是综合起来最好的方法了，我都是用这个样式清除浮动的，不会影响任何其他样式，通用性强，覆盖面广，我很推荐哦。

原文地址：
http://www.zhangxinxu.com/wordpress/2010/01/css-float%E6%B5%AE%E5%8A%A8%E7%9A%84%E6%B7%B1%E5%85%A5%E7%A0%94%E7%A9%B6%E3%80%81%E8%AF%A6%E8%A7%A3%E5%8F%8A%E6%8B%93%E5%B1%95%E4%BA%8C/

我不太清楚的一点：  
zoom:1;是如何起作用的？——原来是在IE浏览器中，这句话**可以触发haslayout机制**。一篇辅助理解的文章：
http://www.cnblogs.com/ideaplusl/archive/2011/07/07/2099843.html


③设置overflow触发BFC模式


```
html：
<div class="aa">
  <div class="bb">sffsssssssssssss</div>
  <div class="cc">sffss</div>
</div>
```


```
css：
.aa{ border:1px solid #000; background:#CC4;overflow:hidden;}
.bb { border:1px solid #f00; background:#999; float:left;}
.cc{ border:1px solid #f00; background:#999; float:left;}
```

此方法的重点在于，子元素有float之后，父元素需要设置一个overflow:hidden;，这样就可以自动撑开父元素aa。

**特别注释：**
overflow:hidden要有宽度或者高度才会溢出部分隐藏，如果外部盒子没有宽度或者高度，里面又是浮动元素，就会被撑开

overflow为什么会起作用的真实原因：
https://www.zhihu.com/question/30938856
**是因为触发了BFC模式**  
一篇辅助理解BFC的文章：
http://www.cnblogs.com/dojo-lzz/p/3999013.html


#### 2、解决绝对定位父元素的塌陷问题

##### ①遇到的问题描述
对这个DEMO中的中间和右半部分使用了绝对定位之后，父元素高度不能包含住定位的元素。

##### ②思考
- 造成问题的原因是对元素使用了绝对定位，导致该绝对定位元素被删除出了整个文档流。
- 解决思路一：为父元素设置min-height;
- 解决思路二：js动态为父元素设置高度
- 解决思路三：父元素还可以被其他没有绝对定位过的元素撑开

补充文章观点，**想重构页面布局，少用绝对定位布局。**
http://www.zhangxinxu.com/wordpress/2010/12/css-%E7%9B%B8%E5%AF%B9%E7%BB%9D%E5%AF%B9%E5%AE%9A%E4%BD%8D%E7%B3%BB%E5%88%97%EF%BC%88%E4%B8%80%EF%BC%89/


---
用position实现布局的效果不是很理想，主要没有解决的问题是：  
1、父元素的宽度没有自适应  
2、设置了min-width没有起作用