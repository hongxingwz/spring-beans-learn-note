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

**在启动时会抛出异常：**

如果是java config 则会抛出**ConflictingBeanDefinitionException**

```
Caused by: org.springframework.context.annotation.ConflictingBeanDefinitionException:
    Annotation-specified bean name 'repeat' for bean class [com2.jianglei.comp.BeanNameRepeat2] conflicts with existing, non-compatible bean definition of same name and class [com2.jianglei.comp.BeanNameRepeat]
```

如果是xml config 则会抛出：

```
Exception in thread "main" org.springframework.beans.factory.parsing.BeanDefinitionParsingException: 
    Configuration problem: Bean name 'beanNameRepeat' is already used in this <beans> element
```

**在用BeanFactory.getBean\(Class\)时，如果bean不唯一，无论时java config 还是 xml config，则都会抛出异常：**

```
Exception in thread "main" org.springframework.beans.factory.NoUniqueBeanDefinitionException: 
    No qualifying bean of type 'com2.jianglei.comp.interfaces.A' available: expected single matching bean but found 2: AImpl2,AImpl
```



