#模板类
[参考博客](https://blog.csdn.net/low5252/article/details/94654468)

模板类中类成员函数的声明在类的外部,如果是在同一个文件中的时候,其函数的定义需要使用 :
tempalte<typename T, ..... > 返回类型  类类型::函数名(函数参数){}的形式.

还有一个很重要的问题:模板类中的友元函数如果在类中声明的时候,可以按照成员函数的实现,如果在类外实现定义的时候,需要一个前置声明.[参考博客](https://www.jianshu.com/p/70ca94872418)

模板参数的特化:分为个数的特化和范围的特化.[参考B站]
模板模板参数的介绍 [参考B站]

