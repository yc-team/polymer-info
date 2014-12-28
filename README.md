polymer-info
============

info for polymer

## pager-item

[官方文档](https://www.polymer-project.org/docs/elements/paper-elements.html#paper-item)

目前我们用的0.4.2，所以配置比较老

```html
<paper-item icon="refresh" label="Refresh"></paper-item>
```

```html
<paper-item label="GitHub link">
    <a href="https://github.com/Polymer" target="_blank"></a>
</paper-item>
```

## core-icon

[官方文档](https://www.polymer-project.org/components/core-icon/demo.html)


## core-menu

[官方文档](https://www.polymer-project.org/components/core-menu/demo.html)


## paper-menu-button

[官方文档](https://www.polymer-project.org/components/paper-menu-button/demo.html)


## paper-toast

> 我们目前使用的版本里面不包含autoCloseDisabled，可以升级一下

[官方文档](https://www.polymer-project.org/components/paper-toast/demo.html)

* text       显示的文案
* duration   显示的时间
* opened     一开始是否显示，默认false
* 

注释：

1. class="capsule"  可以出现圆角

```css
:host(.capsule) {
  border-radius: 24px;
}
```


2. class="fit-bottom" 

```css
:host(.fit-bottom) {
  bottom: 0;
  left: 0;
  width: 100%;
  min-width: 0;
  border-radius: 0;
}
```

```html
<paper-toast id="toast1" text="Your draft has been discarded."></paper-toast>
```
