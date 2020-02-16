原项目地址：https://github.com/glongdev/Reader

###主要是对原项目做一个分析，添加注释：


    #####核心view：ReaderView

         onLayout    onDraw


    #####onLayout: 初始化当前页和下一页（两个bitmap对象以及bitmap对象关联的canvas）

        貌似会绘制当前页

        mCurrPageBitmap当前页       mNextPageBitmap下一页


    #####onDraw:

        调用翻页动画的onDraw


    #####现象：

        进入页面：onLayout   onDraw  onDraw

        翻页时：onDraw  onDraw  onDraw  onDraw  onDraw  ..........


 ###源码分析：


    #####第一阶段：

         分析ReaderView的onLayout、onDraw




    #####第二阶段

        分析ReaderView的onTouchEvent、dispatchDraw

        dispatchDraw:在View的draw方法中有对这个方法的调用：先调用自己的onDraw方法，然后调用dispatchDraw用来绘制子View，
                     ReaderView中的这个方法有实现，但是没有起到什么作用，没明白作者本来的意图。

        onTouchEvent:由翻页动画来接管所有事件


