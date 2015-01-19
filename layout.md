polymer layout
============

layout attributes in polymer

[更多参考](https://www.polymer-project.org/docs/polymer/layout-attrs.html)


当一个容器包含 layout 属性，它会变成一个 flex 容器

## horizontal vs vertical

``` html
<div horizontal layout>
  <div>One</div>
  <div>Two</div>
  <div>Three</div>
</div>

<div vertical layout style="height:250px">
  <div>Alpha</div>
  <div flex>Beta (flex)</div>
  <div>Gamma</div>
</div>
```

> Note: for vertical layouts, the container needs to have a height for the children to flex correctly.


我们来看看源码实现：

``` css
html /deep/ [layout][horizontal], html /deep/ [layout][vertical] {
  display: -ms-flexbox;
  display: -webkit-flex;
  display: flex;
}


html /deep/ [layout][horizontal] {
  -ms-flex-direction: row;
  -webkit-flex-direction: row;
  flex-direction: row;
}


html /deep/ [layout][vertical] {
  -ms-flex-direction: column;
  -webkit-flex-direction: column;
  flex-direction: column;
}
```

#### 区别在于：flex-direction

它可以来设置 [伸缩容器的主轴的方向]，决定了用户代理配置伸缩项目的方向，有如下值：

* row  			  默认值。表示伸缩容器的主轴与当前书写模式的行内轴（文字布局的主要主向）
* row-reverse	  除了主轴起点与主轴终点方向交换以外同 row 属性值的作用。
* column  		  伸缩容器的主轴与当前书写模式的块轴（块布局的主要方向）同向	
* column-reverse  除了主轴起点与主轴终点方向交换以外同“column”的属性值作用。


horizontal（水平） 里面 flex-direction: row;   	 单行里面放多个 item
vertical（垂直）   里面 flex-direction: column;   多行


#### 换种方式：

flex-flow：用来伸缩行换行，同时设定“flex-direction(伸缩流的方向)”和“flex-wrap（伸缩行换行）”属性的缩写，

两个属性决定了伸缩容器的主轴与侧轴。此属性主要适用于伸缩容器。

所以上面的代码可以改成：

html /deep/ [layout][horizontal] {
  flex-flow: row;
}


html /deep/ [layout][vertical] {
  flex-flow: column;
}


## flex 与数字等分


``` html
<div horizontal layout>
  <div>Alpha</div>
  <div flex>Beta (flex)</div>
  <div>Gamma</div>
</div>
```



举例：“Gamma” 2x larger than “Beta” and “Alpha” 3x larger。

``` html
<div horizontal layout class="demo">
  <div flex three>Alpha</div>
  <div flex>Beta</div>
  <div flex two>Gamma</div>
</div>
```


我们来看看源码实现：


``` css
html /deep/ [flex] {
  -ms-flex: 1 1 0.000000001px;
  -webkit-flex: 1;
  flex: 1;
  -webkit-flex-basis: 0.000000001px;
  flex-basis: 0.000000001px;
}
```

one:

``` css
html /deep/ [flex][one] {
  -ms-flex: 1;
  -webkit-flex: 1;
  flex: 1;
}
```

two:

``` css
html /deep/ [flex][two] {
  -ms-flex: 2;
  -webkit-flex: 2;
  flex: 2;
}
```

three:

``` css
html /deep/ [flex][three] {
  -ms-flex: 3;
  -webkit-flex: 3;
  flex: 3;
}
```

一共到 twelve （12）

``` css
html /deep/ [flex][twelve] {
  -ms-flex: 12;
  -webkit-flex: 12;
  flex: 12;
}
```


## 对齐：

* 侧轴对齐

我们看到子元素div的位置，[在线示例地址]()

``` html
.demo {
	background-color: #ccc;
	padding: 4px;
	margin: 12px;
}

.tall {
	height: 124px;
}
```

``` html
<div horizontal layout start class="demo tall">
  <div>start</div>
</div>
<div horizontal layout center class="demo tall">
  <div>center</div>
</div>
<div horizontal layout end class="demo tall">
  <div>end</div>
</div>
```

源码：

``` css
html /deep/ [layout][start] {
  -ms-flex-align: start;
  -webkit-align-items: flex-start;
  align-items: flex-start;
}
html /deep/ [layout][center] {
  -ms-flex-align: center;
  -webkit-align-items: center;
  align-items: center;
}
html /deep/ [layout][end] {
  -ms-flex-align: end;
  -webkit-align-items: flex-end;
  align-items: flex-end;
}
```



* 主轴对齐

我们看到子元素div的位置，[在线示例地址]()

``` html
.demo {
	background-color: #ccc;
	padding: 4px;
	margin: 12px;
}
```

``` html
<div horizontal start-justified layout class="demo">
  <div>start-justified</div>
</div>

<div horizontal center-justified layout class="demo">
  <div>center-justified</div>
</div>

<div horizontal end-justified layout class="demo">
  <div>end-justified</div>
</div>
```

源码：

``` css
html /deep/ [layout][start-justified] {
  -ms-flex-pack: start;
  -webkit-justify-content: flex-start;
  justify-content: flex-start;
}

html /deep/ [layout][center-justified] {
  -ms-flex-pack: center;
  -webkit-justify-content: center;
  justify-content: center;
}

html /deep/ [layout][end-justified] {
  -ms-flex-pack: end;
  -webkit-justify-content: flex-end;
  justify-content: flex-end;
}
```


举例： equal space between each element

<div horizontal justified layout class="demo">
  <div>justified</div>
  <div>justified</div>
  <div>justified</div>
</div>


## body上的fullbleed

源码：

``` css
body[fullbleed] {
  margin: 0;
  height: 100vh;
}
```

## 位置属性：

* block

``` html
<div>Before <span block>A Block Span</span> After</div>
```

源码：

``` css
html /deep/ [block] {
  display: block;
}
```


* hidden

``` html
<div>Hidden: <span hidden>Not displayed</span></div>
```

源码：

``` css
html /deep/ [hidden] {
  display: none !important;
}
```


* relative 和 fit

使用 fit 属性的时候一定要给父容器加上 relative。

``` html
<div relative style="height: 100px;">
  <div fit style="background-color: #000;color: white">Fit</div>
</div>
```

源码：

``` css
html /deep/ [relative] {
  position: relative;
}

html /deep/ [fit] {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
```
