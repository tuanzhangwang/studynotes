# <img src="qt_94938.svg" width="64" border="0" style="margin-bottom:-12px"/><font face="΢���ź�" size=6>[***��Qt ѧϰ֮· 2��***](https://www.devbean.net/2012/08/qt-study-road-2-catelog/) ѧϰ�ʼ�</font>

<br>  

* #### �¼��Ľ��������

  >&emsp;&emsp;Qt ���¼�����������������accept()��ignore()���������ǵ�����һ����
  >ǰ���������� Qt���������¼���������Ҫ��������¼������������ Qt�������
  >���¼�����������Ҫ��������¼������¼��������У�����ʹ��isAccepted()����
  >ѯ����¼��ǲ����Ѿ��������ˡ�
  >
  >&emsp;&emsp;������˵�����һ���¼�������������һ���¼������accept()������
  >����¼��Ͳ��ᱻ�����������丸�����������������¼���ignore()������Qt �����
  ><font face="΢���ź�" color=red> **�����** </font>��Ѱ������Ľ����ߡ�
  >
  >&emsp;&emsp;�¼�����Ĭ���� accept ��,����Ϊ��������ĸ���QWidget��Ĭ��ʵ����
  >�ǵ���ignore()����ôһ����������Լ�ʵ���¼���������������QWidget��Ĭ��ʵ�֣�
  >��͵����ǽ������¼��������Ҫ�����¼���ֻ�����QWidget��Ĭ��ʵ�֡�<br>
  
  <font face="΢���ź�" color=red>����һ��qwidget�����Ϸ���һ��button�������
button��mousePressEvent�е���QMouseEvent
��accept()���߲����ã�������¼���button���ܣ����ᴫ�ݸ������qwidget��
���������QMouseEvent��ignore()����qwidget��mousePressEvent����Ҳ��</font>

<br>

* #### �¼�������
  �¼�������: `virtual bool QObject::eventFilter ( QObject * watched,
 QEvent * event );`  
  ��װ������: `void QObject::installEventFilter ( QObject * filterObj )`  
  �Ƴ�������: `void QObject::removeEventFilter(QObject *obj)`
<br>

  >�¼��������ͱ���װ�����������������ͬһ�̣߳����򣬹��������������á����⣬
  >����ڰ�װ������֮��������������˲�ͬ���̣߳���ô��ֻ�еȵ��������»ص�
  >ͬһ�̵߳�ʱ��������Ż���Ч��

<br>

* #### �Զ����¼�

  [*Qt ѧϰ֮· 2��23�����Զ����¼�*](https://www.devbean.net/2012/10/qt-study-road-2-custom-event/)
<br>

  ע���¼���`static int QEvent::registerEventType ( int hint = -1 )`  
  �����¼���`static bool QCoreApplication::sendEvent(QObject *receiver, QEvent *event)`
  ��`static void QCoreApplication::postEvent(QObject *receiver, QEvent *event);`  
  �����¼���`void QObject::customEvent(QEvent *event);`

<br>

* #### Qt ����ϵͳ���
  
  [*Qt ѧϰ֮· 2��24����Qt ����ϵͳ���*](https://www.devbean.net/2012/10/qt-study-road-2-paint-sys/)
<br>

