# <img src="qt_94938.svg" width="64" border="0" style="margin-bottom:-12px"/><font face="微软雅黑" size=6> **学习笔记**</font>

* #### 槽函数中sender()返回为空的可能原因

  >1. 可以检查下槽函数是否被当成C++函数直接调用
  >2. 有可能是在槽函数调用过程中，发送者被析构了

<br>

* #### 设置QComboBox item高度
```
    comboBox->setStyleSheet("QComboBox{border:1px solid gray;}"
        "QComboBox QAbstractItemView::item{height:25px;}"
        "QComboBox::down-arrow{image:url(:/icon/arrowdown);}";
    comboBox->setView(new QListView());     // 非常重要
```