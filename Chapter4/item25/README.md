# 条款25：考虑写出一个不抛异常的swap函数
----------------

**1.swap是个有趣的函数。**<br>
原本它只是STL的一部分，而后成为异常安全性编程的脊柱，以及用来处理自我赋值可能性的一个常见机制。

**2.在class内对std::swap()进行全特化。**<br>
它使得类型专属之swap实现版本也可被这些”迷途代码“所用。

**3.如果swap缺省实现版的效率不足，试着做以下事情：**<br>
(1)提供一个public swap成员函数，让它高效的置换你的类型的两个对象值。并且这个函数绝不该抛出异常。<br>
(2)在你的class或template所在的命名空间内提供一个non-member swap，并令它调用上述swap成员函数。<br>
(3)如果你正编写一个class，为你的class特化std::swap。并令它调用你的swap成员函数。<br>
最后，如果你调用swap，请确定包含一个using声明式，以便让std::swap在你的函数内曝光课件，然后不加任何namespace修饰符，赤裸裸的调用swap。

**4.成员版swap决不可抛出异常。**<br>
因为swap的一个最好的应用是帮助class提供强烈的异常安全性保障。这一约束只施于成员版，不可施行于费成员版。

## 请记住：
* 当std::swap对你的类型效率不高时，提供一个swap成员函数，并确定这个函数不抛出异常。
* 如果你提供一个member swap，也该提供一个non-member swap用来调用前者。对于class，也请特化std::swap。
* 调用swap时应针对std::swap使用using声明式，然后调用swap并且不带任何”命名空间资格修饰“。
* 为”用户定义类型“进行std template全特化是好的，但千万不要尝试在std内加入某些对std而言全新的东西。