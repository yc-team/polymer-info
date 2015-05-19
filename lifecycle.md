polymer element lifecycle
============

## Element lifecycle 方法

* created

> 初始化对象建议在 created 里面完成

```
//正确
Polymer('tag-name', {
	created: function () {
		this.list = [];
	}
});

//不建议
Polymer('tag-name', {
	list: []
});
```


* ready
