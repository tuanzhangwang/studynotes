<font color=green face="微软雅黑" size=6>studynotes<br><br></font>

# <img src="qt/qt_94938.svg" width="64">

  ><font color=green face="微软雅黑" size=4><br>&emsp;&emsp;Open qt notes : </font><font color=green face="微软雅黑" size=4>[<u>qt study notes.md</u>](qt/qt%20study%20notes.md "open qt study note markdown fille")<br><br></font>

<br><br>
# <img src="C++/C++title.png" width="64">
 
+ ### *C++ std::string和std::wstring之间的转换*

    ```
    // 需包含locale、string头文件、使用setlocale函数。
    // string转wstring
    std::wstring StringToWstring(const std::string str)
    {
        unsigned len = str.size() * 2;// 预留字节数
        setlocale(LC_CTYPE, "");     //必须调用此函数
        wchar_t *p = new wchar_t[len];// 申请一段内存存放转换后的字符串
        mbstowcs(p,str.c_str(),len);// 转换
        std::wstring str1(p);
        delete[] p;// 释放申请的内存
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

