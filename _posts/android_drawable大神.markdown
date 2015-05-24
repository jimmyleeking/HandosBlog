#Android Drawable大神

###Selector

选择器，是一个非常实用的drawable资源，可以轻松地控制视图的点击回馈状态，比如给予Button赋予点击效果，selector下面会包含多个item，item的属性如下，其中每一个属性都可以组合使用。

|item属性|说明|
|--|--|
|android:drawable|drawable资源|
|android:state_focused|是否聚焦状态|
|android:state_selected|是否位选中状态|
|android:state_pressed|是否为按住状态|

###shape

shape资源，可以用来做圆角，渐变等简单的图形处理。shape分别包含四个子项:solid,stroke,conrners,gradient。solid用于指定填充效果，stroke则是边框属性，corner为指定边角弧度，gradient则指定渐变效果,三个配合起来就可以简单做一些图形的特效处理。

shape本身也是有指定属性的，可以预定图形为rectangle,ring等

|shape属性|说明|
|--|--|
|shape|rectangle方形<br/>oval椭圆<br/>line直线<br/>ring环形|

|solid属性|说明|
|--|--|
|android:color|填充颜色|


|stroke属性|说明|
|--|--|
|android:width|边框的宽度|
|android:color|边框颜色|
||

|size

|corners属性|说明|
|--|--|
|radius|弧度|





