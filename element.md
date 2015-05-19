polymer-element
============

custom element


```
<polymer-element name="tag-name">
	<template></template>
	<script>
		Polymer('tag-name', {

		});
	</script>
</polymer-element>
```

> Polymer element 里面的 this 是 custom element 本身： this.localName == 'tag-name'

