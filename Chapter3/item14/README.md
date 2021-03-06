# 条款14：在资源管理类中小心copying行为
-------------------

**1.”资源取得时机便是初始化时机“(RAII)基本守则。**<br>
资源在构造期间获得，在析构期间释放。

**2.当一个RAII对象被复制，会发生什么？**<br>
通常有以下两种可能：<br>
(1)禁止复制。许多时候允许RAII对象被复制并不合理。
(2)对底层资源祭出”引用计数法“(reference-count)。有时候我们希望保有资源，直到它的最后一个使用者（某对象）被销毁。这种情况下复制RAII对象时，应该将资源的”被引用数“递增。tr1::shared_ptr便是如此。<br>
通常，只要内含一个tr1::shared_ptr成员变量，RAII class便可实现出reference-counting copying行为。

**3.”删除器“。**<br>
tr1::shared_ptr允许指定所谓的”删除器“(deleter)，那是一个函数或函数对象，当引用次数为0时便被调用。

## 请记住；
* 复制RAII对象必须一并复制它所管理的资源，所以资源的copying行为决定RAII对象的copying行为。
* 普遍而常见的RAII class copying行为是：抑制copying、施行引用计数法。不过其他行为也都可能被实现。
