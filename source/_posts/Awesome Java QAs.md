---
title: Awesome Java QAs
date: 2016-05-07 21:17:45
tags: java
categraies: java
---


### Java中是否可以覆盖(override)一个private或者是static的方法?
static表示静态的意义，它可以修饰一个变量，一个方法，被其修饰的变量被称为类变量，被其修饰的方法成为类方法，其随着类的加载而被加载。
无法重写被private修饰的方法，因为被private修饰的父类方法在子类中是不可见的。
static修饰的方法是静态绑定的，而方法覆盖是为了实现多态，是动态绑定，所以static修饰的方法不需要被覆盖。

### Java支持的数据类型有哪些？什么是自动拆装箱？
 byte short int long float double boolean char
 把int转化成Integer是自动装箱。反之就是自动拆箱。
<!--more-->
### Java为什么不支持多继承? 
多继承指一个子类能同时继承于多个父类，从而同时拥有多个父类的特征，但缺点是显著的。
1.若子类继承的父类中拥有相同的成员变量，子类在引用该变量时将无法判别使用哪个父类的成员变量。
2.若一个子类继承的多个父类拥有相同方法，同时子类并未覆盖该方法（若覆盖，则直接使用子类中该方法），那么调用该方法时将无法确定调用哪个父类的方法。
因此，Java仅允许单继承，即一个子类只能继承于一个父类。但为了拓展子类的功能，Java使用接口以克服不使用多继承带来的不足。
接口是一个特殊的抽象类，接口中成员变量均默认为 static final 类型，即常量，且接口中的方法都为抽象的，都没有方法体。
具体方法只能由实现接口的类实现，在调用的时候始终只会调用实现类的方法（不存在歧义），因此不存在多继承的第二个缺点；而又因为接口只有静态的常量，但是由于静态变量是在编译期决定调用关系的，即使存在一定的冲突也会在编译时提示出错；而引用静态变量一般直接使用类名或接口名，从而避免产生歧义，因此也不存在多继承的第一个缺点。对于一个接口继承多个父接口的情况也一样不存在这些缺点。

### java中的值传递和引用传递到底有什么区别?
值传递：(形式参数类型是基本数据类型)：方法调用时，实际参数把它的值传递给对应的形式参数，形式参数只是用实际参数的值初始化自己的存储单元内容，是两个不同的存储单元，所以方法执行中形式参数值的改变不影响实际参数的值。
引用传递：(形式参数类型是引用数据类型参数)：也称为传地址。方法调用时，实际参数是对象(或数组)，这时实际参数与形式参数指向同一个地址，在方法执行中，对形式参数的操作实际上就是对实际参数的操作，这个结果在方法结束后被保留了下来，所以方法执行中形式参数的改变将会影响实际参数。

###  java创建线程的方式和区别？
采用实现Runnable、Callable接口的方式创见多线程时，优势是：线程类只是实现了Runnable接口或Callable接口，还可以继承其他类。在这种方式下，多个线程可以共享同一个target对象，所以非常适合多个相同线程来处理同一份资源的情况，从而可以将CPU、代码和数据分开，形成清晰的模型，较好地体现了面向对象的思想。
劣势是：编程稍微复杂，如果要访问当前线程，则必须使用Thread.currentThread()方法。
使用继承Thread类的方式创建多线程时优势是：编写简单，如果需要访问当前线程，则无需使用Thread.currentThread()方法，直接使用this即可获得当前线程。
劣势是：线程类已经继承了Thread类，所以不能再继承其他父类。
[原文](http://blog.csdn.net/longshengguoji/article/details/41126119)

### HashMap和Hashtable的区别
HashMap是Hashtable的轻量级实现（非线程安全的实现），他们都完成了Map接口，主要区别在于HashMap允许空（null）键值（key）,由于非线程安全，效率上可能高于Hashtable。HashMap允许将null作为一个entry的key或者value，而Hashtable不允许。 
HashMap把Hashtable的contains方法去掉了，改成containsvalue和containsKey。因为contains方法容易让人引起误解。Hashtable继承自Dictionary类，而HashMap是Java1.2引进的Mapinterface的一个实现。
最大的不同是，Hashtable的方法是Synchronize的，而HashMap不是，在多个线程访问Hashtable时，不需要自己为它的方法实现同步，而HashMap 就必须为之提供外同步。 Hashtable和HashMap采用的hash/rehash算法都大概一样，所以性能不会有很大的差别。
[references](http://www.cnblogs.com/langtianya/archive/2013/03/19/2970273.html)

### Java接口与抽象类的区别?

```java
interface Alram {
    void alarm();
}
 
abstract class Door {
    void open();
    void close();
}
 
class AlarmDoor extends Door implements Alarm {
    void oepn() {
      //....
    }
    void close() {
      //....
    }
    void alarm() {
      //....
    }
}
```

[references](http://www.cnblogs.com/dolphin0520/p/3811437.html)

### java中的四大特性?
抽象: 把现实中需要处理的事物通过数据的方法表达出来
封装: 把事物的数据和方法用类的方式集合起来
继承: 封装的数据和方法通过继承来实现重用
多态: 同一个方法通过方法的重载实现不同的逻辑

### java socket编程？
[原文](http://blog.csdn.net/lovesummerforever/article/details/8813343)

### Callable和Runnable的区别？
Runnable只有一个run()函数，用于将耗时操作写在其中，该函数没有返回值。然后使用某个线程去执行该runnable即可实现多线程，Thread类在调用start()函数后就是执行的是Runnable的run()函数。
Callable与Runnable的功能大致相似，Callable中有一个call()函数，但是call()函数有返回值，而Runnable的run()函数不能将结果返回给客户程序。
[原文](http://blog.csdn.net/bboyfeiyu/article/details/24851847?utm_source=tuicool&utm_medium=referral)
