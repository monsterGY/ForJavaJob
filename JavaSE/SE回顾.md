## 基础语法

### 注释

- 行内注释
- 多行注释
- **文档注释**  /**    */   javadoc生成帮助文档

###  标识符

- 关键字

  | abstract   | assert       | boolean   | break      | byte   |
  | ---------- | ------------ | --------- | ---------- | ------ |
  | case       | catch        | char      | class      | const  |
  | continue   | default      | do        | double     | else   |
  | enum       | extends      | final     | finally    | float  |
  | for        | goto         | if        | implements | import |
  | instanceof | int          | interface | long       | native |
  | new        | package      | private   | pretected  | public |
  | return     | strictfp     | short     | static     | super  |
  | switch     | synchronized | this      | throw      | throws |
  | transient  | try          | void      | volatile   | while  |

  - assert:断言，用来进行程序调试
  - final：定义常量 finally：异常中肯定执行的代码块
  - goto: Java中不用
  - native：用来声明一个方法是由与计算机相关的语言（如C/C++/FORTRAN语言）实现的
  - strictfp：用来声明FP_strict（单精度或双精度浮点数）表达式遵循[IEEE 754](https://baike.baidu.com/item/IEEE 754/0?fromModule=lemma_inlink)算术规范
  - throw：抛出一个异常  throws：声明在当前定义的成员方法中所有需要抛出的异常
  - transient：声明不用序列化的成员域
  - volatile：表明两个或者多个变量必须同步地发生变化

### 数据类型

- 基本数据类型
  - 整数
    - byte  1
    - short 2
    - int 默认  4
    - long  8
  - 浮点数
    - float  4
    - double  默认  8
  - 字符
    - char 2
  - 布尔值
    - boolean  1位（其他的都指的是字节）
- 引用数据类型
  - 类
  - 接口
  - 数组

金融中的数字使用 BigDecimal

### 变量和常量

变量的作用域：在JAVA中，变量的作用域分为四个级别：类级、对象实例级、方法级、块级

- 类级变量又称全局级变量或静态变量，需要使用static关键字修饰。类级变量在类定义后就已经存在，占用内存空间，可以通过类名来访问，不需要实例化。
- 对象实例级变量就是成员变量，实例化后才会分配内存空间，才能访问。成员变量是定义在方法之外，类之内的。成员变量随着对象的创建而存在，随着对象的消失而消失。
- 方法级变量就是在方法内部定义的变量，就是局部变量。局部变量在调用了对应的方法时执行到了创建该变量的语句时存在，局部变量的作用域从它被声明的点开始，一旦出了自己的作用域马上从内存中消失。
- 块级变量就是定义在一个块内部的变量，变量的生存周期就是这个块，出了这个块就消失了，比如 if、for 语句的块。块是指由大括号包围的代码

说明：

- 方法内部除了能访问方法级的变量，还可以访问类级和实例级的变量。

- 块内部能够访问类级、实例级变量，如果块被包含在方法内部，它还可以访问方法级的变量。
- 同一作用域范围的包裹下成员变量名和局部变量名是可以变量名相同的。在方法中使用变量时，如果不指明使用成员变量还是局部变量，那么默认使用局部变量（就近原则），但是如果局部变量超出了它本身的作用域范围则会失效，被JVM垃圾回收，那么则可以重复命名此变量。
- 同一个作用域范围的包裹下局部变量和局部变量不可以变量名相同（作用域内不能重复命名）。

### 运算符

位运算符：

- &  按位与 操作数对应位同为1，该位为1，否则为0
- |  按位或  操作数对应位同为0，该位为0，否则为1
- ^  按位异或  操作数对应位不同为1，否则为0
- ~  按位非  1变0,0变1
- \>>  右位移运算符   高位补0
- <<  左位移运算符   低位补0
- \>>>  按位右移补零操作符  左操作数的值按右操作数指定的位数右移，移动得到的空位以零填充

位运算常见应用：

- m<<n=m*2^n
- 判断一个数n的奇偶性  n&1 == 1?”奇数”:”偶数”;
- 不用临时变量交换两个数  

``` java
 		n = n ^ m;
        m = m ^ n;  //m = m ^ (n ^ m) => m=n
        n = n ^ m;  //n = (n ^ m)^[m ^ (n ^ m)] => n=m
```

​		常见的计算法则：
​		① a ^ a =0 （任何数异或本身结果为0）
​		② a ^ b =b ^ a （交换律）
​		③ a ^ b ^ c = a ^ (b ^ c) = (a ^ b) ^ c （结合律）
​		④ 0 ^ a = a （异或0具有保持的特点）
​		⑤ a ^ b ^ a = b （根据①②④可得）

- 取绝对值

> 公式： |a| = (a^(a>>31))-(a>>31)

### 面向对象

- 多态
  - 父类的引用指向子类的对象  Person person=new Student();

- 修饰符
  - public
  - protected
  - private
  - static
  - final
  - abstract

|           | 类内部 | 本包 | 子类 | 外部包 |
| --------- | ------ | ---- | ---- | ------ |
| public    | √      | √    | √    | √      |
| protected | √      | √    | √    | ×      |
| default   | √      | √    | ×    | ×      |
| private   | √      | ×    | ×    | ×      |

- 内部类
  - 局部内部类
  - 静态内部类
  - **匿名内部类**

### 常用类

- Object类
  - hashcode()
  - toString()
  - clone()
  - getClass()
  - notify()
  - wait()
  - equals()
- Math类
- Random类
- File类
  - 创建文件
  - 查看文件
  - 修改文件
  - 删除文件
- 包装类
  - 自动装箱和拆箱
- Date类
  - Date
  - SimpleDateFormat    yyyy-MM-dd HH:mm:ss
  - Calendar(建议使用)
- String类
  - 不可变性 final
  - 操作量较少
- StringBuffer类
  - 可边长
  - append()
  - 多线程数据量较大
  - 效率低，安全
- StringBuilder类
  - 可边长
  - 单线程数据量较大
  - 效率高，不安全

### 集合框架

- Collection  
  - List  有序可重复  接口
    - ArrayList（常用）  接口实现类  底层数组  方便随机访问  线程不安全
      - add
      - remove
      - contains
      - size
    - LinkedList（常用）  接口实现类 底层链表  方便插入删除 线程不安全
      - getFirst()
      - getLast()
      - removeFirst()
      - addFirst()
    - Vector   接口实现类  底层数组  同步、线程安全
    - Stack  vector类的实现类
  - Set  无序不可重复  存储顺序不一致
    - HashSet（常用）  hash表(数组)存储元素
      - LinkedHashSet  链表维护元素的插入次序
    - TreeSet  底层二叉树  元素排好序
  - Iterator迭代器

- Map  接口  键值对的集合
  - Hashtable 接口实现类 线程安全
  - ***HashMap*** 重点  接口实现类  线程不安全
    - LinkedHashMap  双向链表和哈希表实现
    - WeakHashMap  

  - TreeMap  红黑树对所有的key进行排序

- Collections 工具类
- 泛型 <> 约束，避免类型转换之间的问题

HashSet底层是采用哈希表来实现，可以存储null，元素唯一不可重复，唯一性依靠hashCode()和equals()方法判别(可以重写构建想要的判断重复的方式)

>具体实现唯一性的比较过程：存储元素首先会使用hash()算法函数生成一个int类型hashCode散列值，然后已经的所存储的元素的hashCode值比较，如果hashCode不相等，则所存储的两个对象一定不相等，此时存储当前的新的hashCode值处的元素对象；如果hashCode相等，存储元素的对象还是不一定相等，此时会调用equals()方法判断两个对象的内容是否相等，如果内容相等，那么就是同一个对象，无需存储；如果比较的内容不相等，那么就是不同的对象，就该存储了，此时就要采用哈希的解决地址冲突算法，在当前hashCode值处类似一个新的链表， 在同一个hashCode值的后面存储存储不同的对象，这样就保证了元素的唯一性。

Set实现类底层是数组存储数据，默认16，加载因子0.75(即存储大小达到16*0.75=12时，数组扩容至两倍大小32)，

***

Map保存键值对key-value key不能重复  HashMap至多存在一个空key，无数个空value，Hashtable不可为空,

LinkedHashMap使用双向链表维护键值对次序，迭代顺序与插入顺序一致，因需要维护插入顺序，性能略差  

### IO流

- 字节流
  - 输出 OutputStream
  - 输入 InputStream
- 字符流
  - Reader
  - Writer
- 节点流
  - CharArray
    - CharArrayReader
    - CharArrayWriter
    - CharArrayInputStream
    - CharArrayOutputStream
  - String
    - StringReader
    - StringWriter
  - pipe
    - PipeOutputStream
  - File
- 处理流
  - buffer
    - bufferInputStream
    - bufferOutputStream
    - bufferReader
    - bufferWriter
  - 序列化   反序列化  Serializable    transient(透明的)
  - data
    - DataInputStream
    - DataOutputStream
  - object流
  - 转换流
    - InputStreamReader
    - InputStreamWriter
  - Filter
    - FilterInputStream
    - FilterOutputStream
    - FilterReader
    - FilterWriter
  - print
    - PrintWriter
    - PrintStream
