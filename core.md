core element
============

core element in polymer

## core-icon

[官方文档](https://www.polymer-project.org/components/core-icon/demo.html)


## core-icon-button

[官方文档](https://www.polymer-project.org/components/core-icon-button/demo.html)

 core-icon-button is an icon with button behaviors.

可以指定一个你自己的icon URL
```html
<core-icon-button src="star.png"></core-icon-button>
```

也可以用内置的icon name
```html
<core-icon-button icon="menu"></core-icon-button>
```

## 属性：

* src    自定义图片的URL
* icon   指定polymer自带的icon name
* active 默认false。设置true的化会加box-shadow和背景颜色来表示选中。

源码：

```css
:host(:active:not([disabled]), .selected:active:not([disabled])) {
  background-color: rgba(0, 0, 0, 0.05);
  box-shadow: inset 0 1px 0 0 rgba(0, 0, 0, 0.1), 0 0 0 1px rgba(0, 0, 0, 0.12);
}
```

#### 如何设置不可编辑？

增加 disabled 属性就可以了

```html
<core-icon-button icon="menu" disabled></core-icon-button>
```

源码：

```css
:host([disabled]) {
  opacity: 0.6;
  pointer-events: none;
}
```

## core-item

[官方文档](https://www.polymer-project.org/components/core-item/demo.html)

core-item is a simple line-item object: a label and/or an icon that can also act as a link.

```html
<core-item icon="settings" label="Settings"></core-item>
```

可以包裹一个a来作一个链接

```html
<core-item icon="settings" label="Settings">
  <a href="#settings" target="_self"></a>
</core-item>
```

属性：

* src   自定义图片的URL
* icon  指定polymer自带的icon name
* label 显示的文案

#### 可否做一些复杂的item

```html
<core-item icon="account-circle" class="contact-item">
  <div flex>
    <div class="name">John Doe</div>
    <div class="address">123 A Street, San Francisco, CA</div>
  </div>
  <core-icon icon="more-vert"></core-icon>
</core-item>
```

因为core-item 的shadow 里面支持 content。


#### 可否配置来缩小item的大小：

```html
<core-item icon="account-box" label="Account" class="font-scalable small"></core-item>
```

```css
core-item.small {
  font-size: 12px;
}
```

类似反推也可以：

```css
core-item.big {
  font-size: 24px;
}
```

源码里面：

```css
:host(.font-scalable) {
  min-height: 2.5em;
}
```

## core-input

[官方文档](https://www.polymer-project.org/components/core-input/demo.html)

core-input is an unstyled single-line input field. 
It extends the native input element.

源码：

```html
<polymer-element name="core-input" extends="input">
</polymer-element>
```

举例：

```html
<input is="core-input" placeholder="a single-line input" value="{{value1}}" committedValue="{{committedValue1}}">

<p>value: {{value1}}, committedValue: {{committedValue1}}</p>
```

```html
<input is="core-input" type="number" preventInvalidInput placeholder="input type = number, preventInvalidInput" value="{{value2}}" committedValue="{{committedValue2}}">

<p>value: {{value2}}, committedValue: {{committedValue2}}</p>
```

属性：

* committedValue   the input value when the user hits the "enter" key or blurs the input after changing the value. 
* preventInvalidInput  默认是 false，如果设置的true的化可以阻止不合法的输入

方法：

* commit


源码：

```css
:host {
  display: inline-block;
  text-align: inherit;
  position: relative;
  width: 20em;
}

:host:hover {
  cursor: text;
}
```


## core-menu

[官方文档](https://www.polymer-project.org/components/core-menu/demo.html)


## core-ajax

[官方文档](https://www.polymer-project.org/components/core-ajax/demo.html)

```html
<core-ajax method="POST" params='{"alt":"json", "q":"chrome"}' auto url="http://somesite.com" body='{"foo":1, "bar":2}' headers='{"X-Requested-With": "XMLHttpRequest"}'>
</core-ajax>
```

## 属性：

* url		请求的服务地址
* method	请求的方法，一般是：'GET', 'POST', 'PUT', or 'DELETE'。默认是 GET
* handleAs  处理response数据格式，默认是text，还有其他如下：

	`text`: uses `XHR.responseText`.
	`xml`: uses `XHR.responseXML`.
	`json`: uses `XHR.responseText` parsed as JSON.
	`arraybuffer`: uses `XHR.response`.
	`blob`: uses `XHR.response`.
	`document`: uses `XHR.response`.

* auto				默认是false。当url或者params变化的时候，自动发送一次ajax请求
* params			默认是''，是一个json string
* contentType 		默认是application/x-www-form-urlencoded
* withCredentials	默认是false



## core-tooltip

[官方文档](https://www.polymer-project.org/components/core-tooltip/demo.html)

## 属性：

* label    显示的文案，默认是null
* position 显示的位置，默认是bottom
* disabled 可以设置这个属性来不让toottip显示

```html
<core-tooltip label="我永远都不会显示" disabled>
    <core-icon-button icon="drawer"></core-icon-button>
</core-tooltip>
```

* 用 tip 属性来丰富toottip

```html
<core-tooltip>
    <div>Example of a rich information tooltip</div>
    <div tip>
        <img src="profile.jpg">Foo <b>Bar</b> - <a href="#">@baz</a>
    </div>
</core-tooltip>
```

* noarrow 属性来去掉箭头

```html
<core-tooltip label="我没有箭头" noarrow>
    <core-icon-button icon="drawer"></core-icon-button>
</core-tooltip>
```

* tipAttribute 来丰富toottip，默认值就是上面的tip

```html
<core-tooltip tipAttribute="htmltooltip">
  <div>Example of a rich information tooltip</div>
  <div htmltooltip>
    ...
  </div>
</core-tooltip>
```


## core-label

provides a version of the `<label>` element that works with Custom Elements as well as native elements.

有两种使用方式：

```html
<core-label>
  是否已婚
  <input for type="checkbox">
  木有
</core-label>
```

```html
<core-label for=".two">
    Hi!
</core-label>

<button class="one">sup</button>
<button class="two">whazzup</button>
```

不自带组件样式，只有一个：

```css
html /deep/ core-label {
  cursor: default;
}
```





## core-meta
