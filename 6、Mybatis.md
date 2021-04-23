### 1、MyBatis与Hibernate有哪些不同？
答：1).Mybatis和hibernate不同，它不完全是一个ORM框架，因为MyBatis需要程序员自己编写Sql语句。
2).Mybatis直接编写原生态sql，可以严格控制sql执行性能，灵活度高，非常适合对关系数据模型要求不高的软件开发，因为这类软件需求变化频繁，一但需求变化要求迅速输出成果。但是灵活的前提是mybatis无法做到数据库无关性，如果需要实现支持多种数据库的软件，则需要自定义多套sql映射文件，工作量大。
3).Hibernate对象/关系映射能力强，数据库无关性好，对于关系模型要求高的软件，如果用hibernate开发可以节省很多代码，提高效率。
### 2、#{}和${}的区别是什么？
答：#{}是预编译处理，${}是字符串替换。Mybatis在处理#{}时，会将sql中的#{}替换为?号，调PreparedStatement的set方法来赋值；Mybatis在处理${}时,就是把${}替换成变量的值；使用#{}可以有效的防止SQL注入，提高系统安全性。
### 3、MyBatis实现一对多有几种方式,怎么操作的？
答：有联合查询和嵌套查询。联合查询是几个表联合查询,只查询一次,通过在resultMap里面的collection节点配置一对多的类就可以完成；嵌套查询是先查一个表,根据这个表里面的结果的外键id,去再另外一个表里面查询数据,也是通过配置collection,但另外一个表的查询通过select节点配置。
### 4、Mybatis是否支持延迟加载？如果支持，它的实现原理是什么？
答：Mybatis仅支持association关联对象和collection关联集合对象的延迟加载，association指的就是一对一，collection指的就是一对多查询。在Mybatis配置文件中，可以配置是否启用延迟加载lazyLoadingEnabled=true|false。它的原理是，使用CGLIB创建目标对象的代理对象，当调用目标方法时，进入拦截器方法，比如调用a.getB().getName()，拦截器invoke()方法发现a.getB()是null值，那么就会单独发送事先保存好的查询关联B对象的sql，把B查询上来，然后调用a.setB(b)，于是a的对象b属性就有值了，接着完成a.getB().getName()方法的调用。这就是延迟加载的基本原理。当然了，不光是Mybatis，几乎所有的包括Hibernate，支持延迟加载的原理都是一样的。