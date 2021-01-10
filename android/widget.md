# fading
## 设置颜色
https://blog.csdn.net/u012702547/article/details/52913538
        android:background="@color/colorPrimary"
        android:fadingEdgeLength="200dp"
        android:requiresFadingEdge="horizontal"
        
    <TextView
        android:id="@+id/tv"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:singleLine="true"
        android:ellipsize="none"
        android:background="@color/colorPrimary"
        android:fadingEdgeLength="200dp"
        android:requiresFadingEdge="horizontal"
        android:text="@string/content"/>
        
        
## 屏蔽顶部阴影解决方法        
解决这个一般就是你在哪个view里设置了fadingEdge你就自定义一个View继承并重写其中某个方法并返回0
getTopFadingEdgeStrength() 决定是否有顶部阴影 (return 0 就是否 return 1 为有)
getBottomFadingEdgeStrength() 决定是否有底部阴影
getLeftFadingEdgeStrength() 决定是否有左边阴影
getRightFadingEdgeStrength()决定是否有右边阴影

# 反锯齿
方法一：给Paint加上抗锯齿标志。然后将Paint对象作为参数传给canvas的绘制方法。

paint.setAntiAlias(true);
drawpath

对自定义 view 比较熟悉的同学应该知道，使用 canvas.clipPath(path) 会有锯齿效果，为了实现抗锯齿效果，我们使用 canvas.drawPath(path, paint)，为 paint 添加抗锯齿标记，并设置 XFermodes。
http://www.androidchina.net/9519.html


方法二：给Canvas加上抗锯齿标志。有些地方不能用paint的，就直接给canvas加抗锯齿，更方便。

canvas.setDrawFilter(new PaintFlagsDrawFilter(0, Paint.ANTI_ALIAS_FLAG|Paint.FILTER_BITMAP_FLAG));

三 PorterDuffXfermode
https://github.com/LT5505/SliderLayout

 2     protected void dispatchDraw(Canvas canvas) {
 3         Paint paint = new Paint();
 4         paint.setAntiAlias(true);
 5         paint.setColor(Color.WHITE);
 6         int saveCount = canvas.saveLayer(0, 0, getWidth(), getHeight(), null, Canvas.ALL_SAVE_FLAG);
 7         super.dispatchDraw(canvas);
 8         paint.setXfermode(new PorterDuffXfermode(PorterDuff.Mode.MULTIPLY));
 9         canvas.drawPath(clipPath, paint);
10         canvas.restoreToCount(saveCount);
11         paint.setXfermode(null);
12     }
