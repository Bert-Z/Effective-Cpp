# 条款19：设计class犹如设计type
--------------------

**1.新type的对象应该如何被创建和销毁？**<br>
**2.对象的初始化和对象的赋值该有什么样的差别？**<br>
**3.新type的对象如果被passed by value（以值传递），意味着什么？**<br>
**4.什么是新的type的”合法值“？**<br>
**5.你的新type需要配合某个继承图系(inheritance graph)吗？**<br>
**6.你的新type需要什么样的转换？**<br>
**7.什么样的操作符和函数对此新type而言是合理的？**<br>
**8.什么样的标准函数应该驳回？**<br>
**9.谁该取用新type的成员？**<br>
**10.什么是新type的”未声明接口“？**<br>
**11.你的新type有多么一般化？**<br>
**12.你真的需要一个新type吗？**

## 请记住：
* Class的设计就是type的设计。在定义一个新的type之前，请确定你已经考虑过本条款覆盖的所有讨论主题。