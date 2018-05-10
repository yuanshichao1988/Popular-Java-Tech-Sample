## Guava Optional类
***
> Optional用于包含非空对象的不可变对象。  
Optional对象，用于不存在值表示null。这个类有各种实用的方法，以方便代码来处理为可用或不可用，而不是检查null值。

#### 类声明
以下是com.google.common.base.Optional<T>类的声明：

@GwtCompatible(serializable=true)
public abstract class Optional<T>
   extends Object
      implements Serializable
#### 类方法
S.N.	方法及说明
1	static <T> Optional<T> absent()
返回没有包含的参考Optional的实例。
2	abstract Set<T> asSet()
返回一个不可变的单集的唯一元素所包含的实例(如果存在);否则为一个空的不可变的集合。
3	abstract boolean equals(Object object)
返回true如果对象是一个Optional实例，无论是包含引用彼此相等或两者都不存在。
4	static <T> Optional<T> fromNullable(T nullableReference)
如果nullableReference非空，返回一个包含引用Optional实例;否则返回absent()。
5	abstract T get()
返回所包含的实例，它必须存在。
6	abstract int hashCode()
返回此实例的哈希码。
7	abstract boolean isPresent()
返回true，如果这支架包含一个(非空)的实例。
8	static <T> Optional<T> of(T reference)
返回包含给定的非空引用Optional实例。
9	abstract Optional<T> or(Optional<? extends T> secondChoice)
返回此Optional，如果它有一个值存在; 否则返回secondChoice。
10	abstract T or(Supplier<? extends T> supplier)
返回所包含的实例(如果存在); 否则supplier.get()。
11	abstract T or(T defaultValue)
返回所包含的实例(如果存在);否则为默认值。
12	abstract T orNull()
返回所包含的实例(如果存在);否则返回null。
13	static <T> Iterable<T> presentInstances(Iterable<? extends Optional<? extends T>> optionals)
从提供的optionals返回每个实例的存在的值，从而跳过absent()。
14	abstract String toString()
返回此实例的字符串表示。
15	abstract <V> Optional<V> transform(Function<? super T,V> function)
如果实例存在，则它被转换给定的功能;否则absent()被返回。

#### 继承的方法
这个类继承了以下类的方法：

java.lang.Object

### Optional示例：
使用所选择的编辑器，创建下面的java程序

#### GuavaTester.java
```java
 
import com.google.common.base.Optional;

public class GuavaTester {
   public static void main(String args[]){
      GuavaTester guavaTester = new GuavaTester();

      Integer value1 =  null;
      Integer value2 =  new Integer(10);
      //Optional.fromNullable - allows passed parameter to be null.
      Optional<Integer> a = Optional.fromNullable(value1);
      //Optional.of - throws NullPointerException if passed parameter is null
      Optional<Integer> b = Optional.of(value2);		

      System.out.println(guavaTester.sum(a,b));
   }

   public Integer sum(Optional<Integer> a, Optional<Integer> b){
      //Optional.isPresent - checks the value is present or not
      System.out.println("First parameter is present: " + a.isPresent());

      System.out.println("Second parameter is present: " + b.isPresent());

      //Optional.or - returns the value if present otherwise returns
      //the default value passed.
      Integer value1 = a.or(new Integer(0));	

      //Optional.get - gets the value, value should be present
      Integer value2 = b.get();

      return value1 + value2;
   }	
}
```

### 验证结果
使用javac编译器编译如下类

C:\Guava>javac GuavaTester.java
现在运行GuavaTester看到的结果

C:\Guava>java GuavaTester
看到结果。

First parameter is present: false
Second parameter is present: true
10