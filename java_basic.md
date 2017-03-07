JAVA 表达式计算总是从左往右的，即使右边操作符的优先级高于左边。

例如：

```java

int a = 2;

int b = ++a + ++a * ++a;

```

该表达式中`b=3+4*5=23`。表达式计算总是从左往右的。

但是有特殊情况，如`&& || ?:` 这三个操作符不会计算全部的表达式。


try执行结束后一般都要执行finally模块，除非在try中执行system.exti().

finally中的`return continue break`或者是抛出异常都会导致之前控制流的中止。

例如：finally中抛出异常会取代之前等待抛出的异常。

如果finally中正常return 会取代try中的return值。

JAVA中有try-with-resource的说法，在使用io资源时，带上try JVM会自动处理资源释放。

