core element
============

core element in polymer

## core-icon

[官方文档](https://www.polymer-project.org/components/core-icon/demo.html)


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


