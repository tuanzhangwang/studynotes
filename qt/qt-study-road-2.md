# <img src="qt_94938.svg" width="64" border="0" style="margin-bottom:-12px"/><font face="微软雅黑" size=6>[***《Qt 学习之路 2》***](https://www.devbean.net/2012/08/qt-study-road-2-catelog/) 学习笔记</font>

<br>  

* #### 事件的接受与忽略

  >&emsp;&emsp;Qt 的事件对象有两个函数：accept()和ignore()。正如它们的名字一样，
  >前者用来告诉 Qt，这个类的事件处理函数想要处理这个事件；后者则告诉 Qt，这个类
  >的事件处理函数不想要处理这个事件。在事件处理函数中，可以使用isAccepted()来查
  >询这个事件是不是已经被接收了。
  >
  >&emsp;&emsp;具体来说：如果一个事件处理函数调用了一个事件对象的accept()函数，
  >这个事件就不会被继续传播给其父组件；如果它调用了事件的ignore()函数，Qt 会从其
  ><font face="微软雅黑" color=red> **父组件** </font>中寻找另外的接受者。
  >
  >&emsp;&emsp;事件对象默认是 accept 的,而作为所有组件的父类QWidget的默认实现则
  >是调用ignore()。这么一来，如果你自己实现事件处理函数，不调用QWidget的默认实现，
  >你就等于是接受了事件；如果你要忽略事件，只需调用QWidget的默认实现。<br>
  
  <font face="微软雅黑" color=red>即，一个qwidget对象上放置一个button，如果在
button的mousePressEvent中调用QMouseEvent
的accept()或者不调用，则这个事件被button接受，不会传递给父组件qwidget。
如果调用了QMouseEvent的ignore()，则qwidget的mousePressEvent函数也会</font>

<br>

* #### 事件过滤器
  事件过滤器: `virtual bool QObject::eventFilter ( QObject * watched,
 QEvent * event );`  
  安装过滤器: `void QObject::installEventFilter ( QObject * filterObj )`  
  移除过滤器: `void QObject::removeEventFilter(QObject *obj)`
<br>

  >事件过滤器和被安装过滤器的组件必须在同一线程，否则，过滤器将不起作用。另外，
  >如果在安装过滤器之后，这两个组件到了不同的线程，那么，只有等到二者重新回到
  >同一线程的时候过滤器才会有效。

<br>

* #### 自定义事件

  [*Qt 学习之路 2（23）：自定义事件*](https://www.devbean.net/2012/10/qt-study-road-2-custom-event/)
<br>

  注册事件：`static int QEvent::registerEventType ( int hint = -1 )`  
  发送事件：`static bool QCoreApplication::sendEvent(QObject *receiver, QEvent *event)`
  或`static void QCoreApplication::postEvent(QObject *receiver, QEvent *event);`  
  处理事件：`void QObject::customEvent(QEvent *event);`

<br>

* #### Qt 绘制系统简介
  
  [*Qt 学习之路 2（24）：Qt 绘制系统简介*](https://www.devbean.net/2012/10/qt-study-road-2-paint-sys/)
<br>

* #### 视图和委托
  [Qt 学习之路 2（46）：视图和委托](https://www.devbean.net/2013/03/qt-study-road-2-view-delegate/)

  委托：　　
  >继承QItemDelegate和QStyledItemDelegate需要实现以下几个函数：
  > * createEditor()：返回一个组件。该组件会被作为用户编辑数据时所使用的编辑器，从模型中接受数据，返回用户修改的数据。
  > * setEditorData()：提供上述组件在显示时所需要的默认值。
  > * updateEditorGeometry()：确保上述组件作为编辑器时能够完整地显示出来。
  > * setModelData()：返回给模型用户修改过的数据。
  
  然后，调用`void QAbstractItemView::setItemDelegate(QAbstractItemDelegate *delegate)`为view设置委托
   
* #### 视图选择
  [Qt 学习之路 2（47）：视图选择](https://www.devbean.net/2013/03/qt-study-road-2-view-selection/)

  >　　Qt 使用QItemSelectionModel类获取视图中项目的选择情况。这个模型保持有项目的索引，并且独立于任何视图。
  >这意味着，我们可以让不同的视图共享同一个选择模型，从来达到一种同步操作的目的。　　
  >
  >　　一个视图的选择模型可以通过`selectionModel()`函数获取，然后使用`setSelectionModel()`提供给其它视图共享
  >
  >　　如果需要创建一个选区，我们需要指定一个模型以及一对索引，使用这些数据创建一个QItemSelection对象。
  >然后使用`QItemSelectionModel::Select`将这个对象设置为选择模型的选择区。
  >
  >获取选区需要使用`selectedIndexes()`函数


