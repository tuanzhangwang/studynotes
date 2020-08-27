<font color=green face="微软雅黑" size=6>studynotes<br><br></font>

# <img src="qt/qt_94938.svg" width="64"> #

　　[<font color=green face="微软雅黑" size=4><u>***Qt踩坑笔记***</u></font>](qt/qt%20study%20notes.md "open qt study note markdown fille")  
<br>
　　[<font color=green face="微软雅黑" size=4><u>***《Qt学习之路2》学习笔记***</u></font>](qt/qt-study-road-2.md "open qt-study-road-2 markdown fille")

<br>
<br>

# <img src="c++/C++title.png" width="64">
 
+ ### *C++ `std::string`和`std::wstring`之间的转换*

    ```
    // 需包含locale、string头文件、使用setlocale函数。
    // string转wstring
    std::wstring StringToWstring(const std::string str)
    {
        unsigned len = str.size() * 2;  // 预留字节数
        setlocale(LC_CTYPE, "");        // 必须调用此函数
        wchar_t *p = new wchar_t[len];  // 申请一段内存存放转换后的字符串
        mbstowcs(p,str.c_str(),len);    // 转换
        std::wstring str1(p);           
        delete[] p;                     // 释放申请的内存
        return str1;
    }
    
    // wstring转string
    std::string WstringToString(const std::wstring str)
    {
        unsigned len = str.size() * 4;
        setlocale(LC_CTYPE, "");
        char *p = new char[len];
        wcstombs(p,str.c_str(),len);
        std::string str1(p);
        delete[] p;
        return str1;
    }
    ```
    * 欲将string转换为wstring，或反向转换，可使用`ctype<>facet`的成员函数`widen()`和`narrow()`。
    * 欲将一连串multibyte转换为wstring，或者反向转换，可使用`class template wstring_convert<>`以及相应的`codecvt<>facet`。
    * `class codecvt<>`可被`class basic_filebuf<>`用来在内部和外部表述之间进行转换--当读文件或写文件时。
    * 欲读或写一连串multibyte字符，可使用`class wbuffer_convert<>`以及相应的`codecvt<>fact`。
