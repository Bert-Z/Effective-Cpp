## Introduction

- **explicit** 阻值编译器进行隐式类型转换，仍可进行显示转换。

- **拷贝构造** 和 **拷贝赋值** 

  ```c++
  class Widget {
  public:
      Widget();	// default 构造函数
      Widget(const Widget& rhs);	// 拷贝构造函数
      Widget& operator=(const Widget& rhs);	// 拷贝赋值操作符
      ...
  };
  Widget w1;	// default
  Widget w2(w1);	// copy 构造
  Widget w3=w2;	// copy 构造
  w1=w2;	// copy assignment
  ```

- Pass-by-reference-to-const 往往是一个比较好的选择。

