## 排序: `Guava`强大的"流畅风格比较器"


`Ordering`是`Guava`对于`Java`中的`Comparator`比较器的一种流畅风格的实现，它可以用来为构建复杂的比较器，以完成集合排序的功能。

从实现上说，`Ordering`实例就是一个特殊的`Comparator`实例。`Ordering`把很多基于`Comparator`的静态方法（如Collections.max）包装为自己的实例方法（非静态方法），并且提供了链式调用方法，来定制和增强现有的比较器。

**创建排序器**：常见的排序器可以由下面的静态方法创建

|--|--|

参考文章:

http://ifeve.com/google-guava-ordering/