### 8.1、SpringBoot的自动装配原理是什么？
答：（1）启动类上开启@EnableAutoConfiguration
	（2）内部通过@import注解引入ImporttSelector
	（3）查找工程jar包中META-INF/spring.factories文件
	（4）装载内部的对象到容器
 
### 8.2、SpringBoot的启动方式有哪些？
答：（1）通过启动类里的main方法运行
	（2）采用jar包的方式启动，java -jar
	（3）通过maven命令运行，mvn spring-boot:run
