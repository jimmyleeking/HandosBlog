---
layout: post
title:  "support-v13新增资源限定注解说明"
date:   2015-04-22 16:46:00
categories: AndroidNewFeature
---


###新增参数注解限定
通过指定不同的注解标签，能够限定传入参数的类型，比如限定位@stringRes，那么必须传入R.string.类型的id。

<pre>
<code>

//定义
public void showToast(@StringRes int resID)
{
}

//正确调用
showToast(R.string.app_name);

//错误，无法被调用,IDE抛出错误
showToast(R.dimen.activity_horizontal_margin);

</code>
</pre>
详细可以参考包android.support.annotation，以及对应列表如下:

|注解|说明|
|--|--|
|AnimatorRes|animator资源|
|AnimRes|anim资源|
|AnyRes|任何资源|
|ArrayRes|数组资源|
|AttrRes|属性资源|
|BoolRes|bool资源|
|ColorRes|颜色资源|
|DimenRes|dimen资源|
|DrawableRes|drawable资源|
|FractionRes|Fraction资源|
|IdRes|id资源|
|IntDef|限定位为特定的int常量|
|IntegerRes|整形资源|
|InterpolatorRes|加速器资源|
|LayoutRes|layout资源|
|MenuRes|menu资源|
|NonNull|不允许为null|
|Nullable|可为null|
|PluralsRes|Plurals资源|
|RawRes|raw资源|
|StringDef|字符串常量|
|StringRes|限定位特定的字符串常量|
|StyleableRes|Styleable资源|
|StyleRes|style资源|
|XmlRes|xml资源|

###关于IntDef和StringDef
具体了解可以参考：http://tools.android.com/tech-docs/support-annotations

官方例子：
<pre>
<code>

@Retention(SOURCE)
  @IntDef({NAVIGATION_MODE_STANDARD, NAVIGATION_MODE_LIST, NAVIGATION_MODE_TABS})
  public @interface NavigationMode {}
  public static final int NAVIGATION_MODE_STANDARD = 0;
  public static final int NAVIGATION_MODE_LIST = 1;
  public static final int NAVIGATION_MODE_TABS = 2;
  ...
  //也就是说传入的类型只限定于上述三种常量
  public abstract void setNavigationMode(@NavigationMode int mode);
  @NavigationMode
  public abstract int getNavigationMode();
 </code>
</pre>







