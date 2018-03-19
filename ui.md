# UI性能优化

* ui渲染流程
  * cpu(计算)=>draw call=>gpu(绘制)
* ui问题的表现    
  * 感觉不到问题, 或者稍微卡顿
* 解决方案
  * 减少Overdraw过渡绘制
  * 优化layout, 减少cpu对节点的计算

### Overdraw的检测

* 数据收集: 手机检测: 设置 -> 开发者选项 -> 调试GPU过度绘制 -> 显示GPU过度绘制   
* 分析问题

```
Overdraw

1  <  2  <   3 < 4

蓝  < 绿  <  粉 <  红
```    

* 解决办法
  * 移除不必要的background(xml, code)
  * 使用clipRect: 自定义view

```
getWindow().setBackgroundDrawable(null);

# 去除
android:background="@android:color/black"
```
![Alt text](https://github.com/UC10D/android-optimization/blob/master/image/4A7C20C5-FCF4-424A-96C8-AC8AF06D6D47.png)



### 减少不必要的层次：Hierarchy Viewer

工具位置: tools => Android => Android Device Monitor| window => reset perspective
 

* 查看每个控件的渲染速度
* 分析原因
* xml 减少嵌套, code优化 
* include, merge 复用

##### ps:

* [java版本号1.8.144以下](https://github.com/UC10D/Bugs/blob/master/README.md)
* 最好使用模拟器
* [不是模拟器加这个](https://github.com/romainguy/ViewServer)


### to do

* 使用clipRect: 自定义view


### 参考

* [Android UI性能优化实战 识别绘制中的性能问题](http://blog.csdn.net/lmj623565791/article/details/45556391/)
* [Android 系统性能(code)](https://github.com/udacity/ud825-render/tree/1.11_chat_with_overdraws)
* [Profile Your Layout with Hierarchy Viewer](https://developer.android.com/studio/profile/hierarchy-viewer.html)
