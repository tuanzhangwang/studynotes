# <img src="qt_94938.svg" width="64" border="0" style="margin-bottom:-12px"/><font face="΢���ź�" size=6> **ѧϰ�ʼ�**</font>

* #### �ۺ�����sender()����Ϊ�յĿ���ԭ��

  >1. ���Լ���²ۺ����Ƿ񱻵���C++����ֱ�ӵ���
  >2. �п������ڲۺ������ù����У������߱�������

<br>

* #### ����QComboBox item�߶�
```
    comboBox->setStyleSheet("QComboBox{border:1px solid gray;}"
        "QComboBox QAbstractItemView::item{height:25px;}"
        "QComboBox::down-arrow{image:url(:/icon/arrowdown);}";
    comboBox->setView(new QListView());     // �ǳ���Ҫ
```