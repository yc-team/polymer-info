polymer-info
============

other element info for polymer in wandoujia’s fe-team

## polymer-jsonp

it can be used to perform JSONP requests.

## 属性：

* url 
* auto 默认是 false
* bustCache
* response

```html
<polymer-jsonp auto url="https://clients1.google.com/finance/info?q=GOOG&client=ig&callback="></polymer-jsonp>
```

```js
document.addEventListener('polymer-ready', function() {
  var jsonp = document.querySelector("polymer-jsonp");
  jsonp.addEventListener("polymer-response", 
    function(e) {
      document.querySelector('template').model = {
        stockquote: e.detail.response[0]
      };
    }
  );
});
```