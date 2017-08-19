# FactoryBean

```java
public interface BeanFactory{

    String FACTORY_BEAN_PREFIX = "&";
    /*
    @throws NoSuchBeanDefinitionException 如果没有指定名字的bean的bean definition
    @throws BeansException 如果不能获取到此bean
    */
    Object getBean(String name) throws BeansException;

    /*
    @throws NoSuchBeanDefinitionException 如果没有指定名字的bean的bean definition
    @throws BeanNotOfRequiredTypeException 如果bean不是需要的类型
    @throws BeansException 如果不能获取到此bean
    */
    <T> T getBean(String name, Class<T> requiredType) throws BeansException;

    /*
    @throws NoSuchBeanDefinitionException 如果没有指定名字的bean的bean definition
    @throws NoUniqueBeanDefinitionException 如果找到了指定类型的多个bean
    @throws BeansException 如果不能获取到此bean
    */
    <T> T getBean(Class<T> requiredType) throws BeansException;

    /*
    @throws NoSuchBeanDefinitionException 如果没有指定名字的bean的bean definition
    @throws BeanDefinitionStoreException 如果指定了参数，但影响到的bean不是prototype
    @throws BeansException 如果不能获取到此bean
    */
    Object getBean(String name, Object... args) throws BeansException;

    /*
    @throws NoSuchBeanDefinitionException 如果没有指定名字的bean的bean definition
    @throws BeanDefinitionStoreException 如果指定了参数，但影响到的bean不是prototype
    @throws BeansException 如果不能获取到此bean
    */
    <T> T getBean(Class<T> requiredType, Object... args) throws BeansException;

    boolean containsBean(String name);

    /*
    @throws NoSuchBeanDefinitionException 如果没有指定名字的bean的bean definition
    */
    boolean isSingleton(String name) throws NoSuchBeanDefinitionException;
    
    /*
    @throws NoSuchBeanDefinitionException 如果没有指定名字的bean的bean definition
    */
    boolean isPrototype(String name) throws NoSuchBeanDefinitionException;
    
    /*
    @throws NoSuchBeanDefinitionException 如果没有指定名字的bean的bean definition
    */
    boolean isTypeMatch(String name, ResolvableType typeToMatch) throw NoSuchBeanDefinitionException;
    
    /*
    @throws NoSuchBeanDefinitionException 如果没有指定名字的bean的bean definition
    */
    boolean isTypeMatch(String name, Class<?> typeToMatch) throws NoSuchBeanDefinitionException;
    
    /*
    @throws NoSuchBeanDefinitionException 如果没有指定名字的bean的bean definition
    */
    Class<?> getType(String name) throws NoSuchBeanDefinitionException;

    String[] getAlias(String name)
```



