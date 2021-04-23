### 4.1、String str = "123" 和 String str = new String("123")有什么区别？
答：String str = "xxx"声明的是一个常量，JVM会将其分配到常量池中
   String str = new String("xxx")声明的是一个对象，JVM会在堆中创建一个对象，并把这个对象的引用地址存放在栈中
### 4.2、String、StringBuilder、StringBuffer的区别？
答：（1）对象是否可变，String类中使用了final关键字来保存字符串，所以 String 对象是不可变的。StringBuider和StringBuffer声明的对象是可变的
	（2）线程安全的区别。String类因为对象不可变，可以理解为常量，线程安全。StringBuilder没有对方法加同步锁，所以是线程不安全的;StringBuffer对方法加了同步锁，所以是线程安全的
	（3）性能。StringBuilder > StringBuffer > String
### 4.3、==和equals有什么区别？
答：==比较的是两个对象的地址是否相等。判断的是两个对象是否是同一个对象（基本数据类型比较的是值，引用数据类型比较的是内存地址）
	equals也是判断两个对象是否相等。但它一般有两种使用情况：一种是没有重写Object类的equals方法，等价于==比较；一种是重写了equals方法，比较的是内容是否相等，若内容相等，则返回true（即，认为两个对象相等）
### 4.4、String的equals方法和StringBuffer的equals方法有什么区别？
答：String类的equals方法重写了，比较的是两个对象的内容是否相等；StringBuffer的equals方法未重写，比较的是两个对象的地址是否相等；
