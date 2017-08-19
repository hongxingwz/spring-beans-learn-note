# FactoryBean

FactoryBean管理的Bean名字是唯一的，不能重复：  
如果定义了两个具有相同组件名的组件则会报错，例：

```java
@Component("repeat")
public class BeanNameRepeat {
}
```

```java
@Component("repeat")
public class BeanNameRepeat2 {
}
```

则会抛出**ConflictingBeanDefinitionException**

```
Caused by: org.springframework.context.annotation.ConflictingBeanDefinitionException:
 Annotation-specified bean name 'repeat' for bean class [com2.jianglei.comp.BeanNameRepeat2] conflicts with existing, non-compatible bean definition of same name and class [com2.jianglei.comp.BeanNameRepeat]

```



