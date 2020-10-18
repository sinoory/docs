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

ok
