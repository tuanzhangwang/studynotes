# <img src="qt_94938.svg" width="64">

* #### 槽函数中sender()返回为空的可能原因
    >```  
    >1. 可以检查下槽函数是否被当成C++函数直接调用
    >2. 有可能是在槽函数调用过程中，发送者被析构了
    >``` 

<br>  

* #### 事件的接受与忽略

  >&emsp;&emsp;Qt 的事件对象有两个函数：accept()和ignore()。正如它们的名字一样，
  >前者用来告诉 Qt，这个类的事件处理函数想要处理这个事件；后者则告诉 Qt，这个类
  >的事件处理函数不想要处理这个事件。在事件处理函数中，可以使用isAccepted()来查
  >询这个事件是不是已经被接收了。<br>
  >&emsp;&emsp;具体来说：如果一个事件处理函数调用了一个事件对象的accept()函数，
  >这个事件就不会被继续传播给其父组件；如果它调用了事件的ignore()函数，Qt 会从其
  ><font face="微软雅黑" color=red> **父组件** </font>中寻找另外的接受者。<br>
  >&emsp;&emsp;事件对象默认是 accept 的,而作为所有组件的父类QWidget的默认实现则
  >是调用ignore()。这么一来，如果你自己实现事件处理函数，不调用QWidget的默认实现，
  >你就等于是接受了事件；如果你要忽略事件，只需调用QWidget的默认实现。<br>
  
  <font face="微软雅黑" color=red>即，一个qwidget对象上放置一个button，如果在button的mousePressEvent中调用QMouseEvent
的accept()或者不调用，则这个事件被button接受，不会传递给父组件qwidget。
如果调用了QMouseEvent的ignore()，则qwidget的mousePressEvent函数也会</font>  

<br>  

* ####