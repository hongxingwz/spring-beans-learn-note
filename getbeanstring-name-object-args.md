### Object getBean\(String name, Object... args\) throws BeansException

**情境一：**

**&lt;bean/&gt;**元素的lazy-init属性为true

```xml
<bean id="love5" class="com2.jianglei.bean.Love5"
        lazy-init="true"/>
```

如果bean是**singleton, **仅可以设置一次有效属性

```java
public class XmlApp6 {
    public static void main(String[] args) {
        ClassPathXmlApplicationContext context =
                new ClassPathXmlApplicationContext("classpath:com2/jianglei/spring-context5.xml");
        Object love = context.getBean("love5", "dengyi", 1, 1);
        love = context.getBean("love5", "dengyi2", 2, 2);
        System.out.println(love);
    }
}
/*
Love5{name='dengyi', age=1, level=1}
*/
```

**情况2：**

不设置**&lt;bean&gt;**元素的lazy-init属性，其scope属性设置为prototype

```
<bean id="love5" class="com2.jianglei.bean.Love5"
        c:name="dengyi" c:level="1" c:age="1" scope="prototype"/>
```

可以设置多次有效属性

```java
public class XmlApp6 {
    public static void main(String[] args) {
        ClassPathXmlApplicationContext context =
                new ClassPathXmlApplicationContext("classpath:com2/jianglei/spring-context5.xml");
        Object love = context.getBean("love5", "dengyi", 11, 11);
        System.out.println(love);
        love = context.getBean("love5", "dengyi2", 2, 2);
        System.out.println(love);
        love = context.getBean("love5");
        System.out.println(love);
    }
}
/*
Love5{name='dengyi', age=11, level=11}
Love5{name='dengyi2', age=2, level=2}
Love5{name='dengyi', age=1, level=1}
*/
```



