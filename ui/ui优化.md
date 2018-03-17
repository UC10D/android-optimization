# UI性能优化

cpu=>draw call=>gpu    
优化的方式: 减少没有必要的layouts, invalidations, Overdraw.

### Overdraw的检测

手机检测: 设置 -> 开发者选项 -> 调试GPU过度绘制 -> 显示GPU过度绘制   

```

Overdraw

1  <  2  <   3 < 4

蓝  < 绿  <  粉 <  红

```    

```
getWindow().setBackgroundDrawable(null);

# 去除
android:background="@android:color/black"

```

* 移除不必要的background(xml, code)
* 使用clipRect: 自定义view


### 减少不必要的层次：Hierarchy Viewer

工具位置: tools -> Android -> Android Device Monitor

* xml 减少嵌套, 减少cpu不必要的节点计算 
* include, merge 复用


### 参考

* [Android UI性能优化实战 识别绘制中的性能问题](http://blog.csdn.net/lmj623565791/article/details/45556391/)
* [Google 发布 Android 性能优化典范](http://www.oschina.net/news/60157/android-performance-patterns?sid=07vbqo00ovnh233e0ain6ue5a6)
* [Android 系统性能(code)](https://github.com/udacity/ud825-render/tree/1.11_chat_with_overdraws)
* [Profile Your Layout with Hierarchy Viewer](https://developer.android.com/studio/profile/hierarchy-viewer.html)
