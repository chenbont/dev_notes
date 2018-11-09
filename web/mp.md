# 微信公众号
微信公众号开发相关问题

1. 监听返回键关闭弹出层
```js
var popupShow = false  //是否存在弹出层
$(function () {
 pushHistory();
      var bool=false;
      setTimeout(function(){
          bool=true;
      },1500);
      window.addEventListener("popstate", function(e) {
          if (popupShow) {
              $.closePopup()
              pushHistory()
              return true
          } else {
              return false
          }
      }, false);

  });

  function pushHistory() {
      var state = {
          title: "标题",
          url: "#"
      };
      window.history.pushState(state, state.title, state.url);
  }
```
