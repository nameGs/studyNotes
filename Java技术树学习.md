[TOC]

# 学习

## Java基础

### 数据类型

> #### 基本数据类型
>
> | 基本类型 | 对应包装类 |                  取值范围                  | 二进制位数 | 默认值 | 所占字节 |
> | :------: | :--------: | :----------------------------------------: | :--------: | :----: | :------: |
> |   int    |  Integer   |          -2147483648 ~ 2147483647          |     32     |   0    |    4     |
> |  short   |   Short    |               -32768 ~ 32767               |     16     |   0    |    2     |
> |   long   |    Long    | -9223372036854775808 ~ 9223372036854775807 |     64     |   0    |    8     |
> |  double  |   Double   |     4.9E-324 ~ 1.7976931348623157E308      |     64     |  0.0   |    8     |
> |  float   |   Float    |           1.4E-45 ~ 3.4028235E38           |     32     |  0.0   |    4     |
> |   byte   |    Byte    |                 -128 ~ 127                 |     8      |   0    |    1     |
> | boolean  |  Boolean   |               true \| false                |     1      | false  |          |
> |   char   | Character  |              \u0000 ~ \uFFFF               |     16     |   空   |    2     |
> |   void   |    Void    |                     -                      |     -      |   -    |    -     |
>
> * 注意 : 
>   * 在开发中，整数用int，小数用double。
>   * long类型一般描述日期时间，内存或文件大小(字节)。
>   * 需要进行编码转换或二进制数据传输使用byte。
>   * char一般用于描述中文。
>   * boolean用于描述程序逻辑使用。
> * int整型出现最大值溢出情况时变成最小值，最小值溢出变成最大值。
> * Java使用Unicode编码，这个编码中包括ASCII码的部分内容，包含的编码内容多余ASCII码。该编码使用16进制，可以保存任何字符包括中文。
> * 在方法内部必须先赋值后使用。
>
> #### 引用数据类型 :
>
> 1. 接口
> 2. 数组
> 3. 类
>
> * 注意：
>   * equals()方法的默认行为是比较引用，如果是自己写的类，应该重写equals()方法来比较对象的内容，大多数java类库都实现了比较对象内容的equals()方法。

### 标识符

> 1. 标识符是用户编程时使用的名字。
> 2. 命名规则：
>    1. 可以由**字母、数字、下划线和美元符**组成 ，不能以数字开头
>    2. 严格区分大小写
>    3. 不能是java的关键字和保留字
>    4. 最好能反映出它的作用

### 关键字

> | abstract  | boolean   | break        | byte    | case     | catch   |
> | --------- | --------- | ------------ | ------- | -------- | ------- |
> | char      | class     | continue     | default | do       | double  |
> | else      | extends   | false        | final   | finally  | float   |
> | for       | if        | implements   | import  | native   | int     |
> | interface | long      | instanceof   | new     | null     | package |
> | private   | protected | public       | return  | short    | static  |
> | super     | switch    | synchronized | this    | throw    | throws  |
> | transient | true      | try          | void    | volatile | while   |

### 常量

> 1. final关键字定义常量(final int N=10);
>
> 2. 常量的命名规则是一般以它的作用的英文全称，并且字母全部大写，单词间用下划线隔开，如final Integer MAX_VALUE;
> 3. 常量不可以修改，变量可以。

### 变量

> 1. 变量的三个元素：**变量类型，变量名，和变量值**
> 2. 命名规则
>    1. 满足标识符命名规则
>    2. 符合驼峰命名法
>    3. 见名知意
>    4. 长度没有限制

### 集合

#### Array

> 1. 数组属于引用类型，使用前需要初始化，否则会报空指针异常。
>
> 2. 数组初始化：
>
>    1. 静态初始化：
>
>       * `int [] num = {1,2,3,};`
>
>       * `int [] num  = new int[]{1,2,3};`
>
>    2. 动态初始化：
>
>       * `int [] num = new int[length];`
>
> 3. 二维数组：
>
>    1. 静态初始化：
>
>       * `int [][] num = {{1,2,3,},{1,2,3}};`
>
>       * `int [][] num  = new int[][]{{1,2,3},{1,2,3}};`
>
>    2. 动态初始化：
>
>       * `int [][] num = new int[length][length];`

#### Set

> #### HashSet
>
> #### LinkedHashSet
>
> #### SynchronizedSet

#### List

> #### ArrayList
>
> ArrayList的本质是数组，它的默认容量是10。ArrayList有自动扩容，每次在执行添加等操作时都是检查是否超出容量，每次扩容的大小是：==minCapacity = minCapacity + minCapacity >> 2==。
>
> ArrayList查询速度特别快，但是执行修改操作时效率较低。
>
> #### LinkedList
>
> LinkedList不但实现了List接口，还实现了Queue接口，因此它包含有一部分队列的方法。LinkedList本质上时Node节点，它没有空间扩容的概念。在初始化一个空的LinkedList时，会生成一个空的Node节点，每次插值时都会创建一个新的Node对象并连接上原有的节点。
>
> LinkedList查询相对ArrayList来说慢一点，因为它要获取到节点的item，但是它修改操作速度更快。
>
> #### Vector
>
> Vector是线程安全的ArrayList，但是Vector每次扩容是原来的一倍，因此效率相对来说低一些。
>
> #### SynchronizedList
>
> SynchronizedList是线程安全的ArrayList。

#### Map

> #### HashMap
>
> #### HashTable
>
> #### ConcurrentHashMap

#### Intecptor

> #### ListInterator
>
> ListInterator是List集合的迭代器。它的允许对集合以任意方向进行遍历、修改、获取当前的位置。它本·身是一个指针，通过移动指针来实现对集合的遍历等操作。而指针指向的位置并不是当前元素前一个位置，而是两个元素之间的位置，比如：在遍历集合{1，2，3}时，遍历到2时，指针处于1和2之间的位置，因此它可以通过next()和previous()方法很容易的获取到下一个元素和之前的元素，也可以通过nextIndex()和previousIndex()获取到下一个元素的位置和上一个元素的位置。
>
> | 编号 |        方法名         |                             解释                             |
> | :--: | :-------------------: | :----------------------------------------------------------: |
> |  1   |   boolean hasNext()   |   判断是否有下一个元素，如果有则返回true，否则返回false。    |
> |  2   |    int nextIndex()    |                     返回下一个元素的下标                     |
> |  3   |       E next()        | 返回下一个元素，如果没有下一个，则会报NoSuchElementException。 |
> |  4   | boolean hasPrevious() |   判断是否有上一个元素，如果有则返回true，否则返回false。    |
> |  5   |  int previousIndex()  |                     返回上一个元素的下标                     |
> |  6   |     E previous()      | 返回上一个元素，如果没有上一个，则会报NoSuchElementException。 |
> |  7   |     void remove()     | 删除下一个或者上一个元素，取决于刚刚执行的是next()方法还是previous()方法，如果没执行而调用该方法，则会报IllegalStateException。 |
> |  8   |     void set(E e)     | 修改下一个或者上一个元素，取决于刚刚执行的是next()方法还是previous()方法，如果没执行而调用该方法，则会报IllegalStateException。 |
> |  9   |     void add(E e)     |           在当前指针的previous位置插入指定的元素。           |

### 运算符

#### 算数运算符

> | 名称 | 名称  |   举例    |
> | :--: | :---: | :-------: |
> |  +   | 加法  |   1+1=2   |
> |  -   | 减法  |   2-1=1   |
> |  *   | 乘法  |   1*2=2   |
> |  /   | 除法  |   2*1=2   |
> |  %   | 求余  |   2%1=0   |
> |  ++  | 自增1 | 1++;/++1; |
> |  --  | 自减1 | --1;/1--; |
>
> * ++和--放在左边和右边的结果不同 :
>
>   a++：计算过程是先执行a，之后在增加1。
>
>   ++a：计算过程是先加上1，之后再执行a。

#### 赋值运算符

> | 运算符 |  名称  |          举例           |
> | :----: | :----: | :---------------------: |
> |   =    |  赋值  | c=a+b，把a+b的结果赋给c |
> |   +=   | 加等于 |    a+=b，等同于a=a+b    |
> |   -=   | 减等于 |    a-=b，等同于a=a-b    |
> |   *=   | 乘等于 |   a*=b，等同于a=a\*b    |
> |   /=   | 除等于 |    a/=b，等同于a=a/b    |
> |   %=   | 模等于 |    a%=b，等同于a=a%b    |

#### 逻辑运算符

>| 运算符 |   名称   |      举例       |                             结果                             |
>| :----: | :------: | :-------------: | :----------------------------------------------------------: |
>|  \|\|  | (短路)或 | true \|\| false | true，表达式中有一个条件为true则结果为true，**不再往后判断** |
>|   &&   | (短路)与 |  false && true  | false，表达式中有一个条件为false则结果为false，**不再往后判**断 |
>|   \|   | (逻辑)或 |  true \| false  | true，表达式中有一个条件为true则结果为true，**后边的条件仍然判断** |
>|   &    | (逻辑)与 |  false & true   | false，表达式中有一个条件为false则结果为false，**后边的条件仍然判断** |
>|   ！   |    非    |     ! true      |                            false                             |
>|   ^    |   异或   |  true ^ false   |           两个条件中有且仅有一个为true，则返回true           |

#### 比较运算符

> | 运算符 |   名称   | 举例 |
> | :----: | :------: | :--: |
> |   >    |   大于   | a>b  |
> |  \>=   | 大于等于 | a>=b |
> |   <    |   小于   | a<b  |
> |   <=   | 小于等于 | a<=b |
> |   !=   |  不等于  | a!=b |

#### 三元运算符

> | 运算符 |    名称    |                             举例                             |
> | :----: | :--------: | :----------------------------------------------------------: |
> |   ?:   | 三元运算符 | 1==1?true:false，意思是1=1条件是否为true，如果为true则返回 : 前的结果，否则为 : 后的结果 |

#### 位运算

> | 运算符 |    名称    |                             解释                             |
> | :----: | :--------: | :----------------------------------------------------------: |
> |   &    |  与运算符  |                    两位都为1，那么结果为1                    |
> |   \|   |  或运算符  |                    有一位为1，那么结果为1                    |
> |   ^    | 异或运算符 |                     两位不相同，结果为1                      |
> |   ~    |     非     |                        ~0 = 1,~1 = 0                         |
> |  \>>   |    右移    | 各二进制位全部右移N位，若值为正，则在高位插入 0，若值为负，则在高位插入 1 |
> |   <<   |    左移    |           各二进制位全部左移N位，高位丢弃，低位补0           |
> |  \>>>  | 无符号右移 |        各二进制位全部右移N位，无论正负，都在高位插入0        |

#### 运算符优先级

> 从上到下，由高到低
>
> | 优先级 |              运算符              |
> | :----: | :------------------------------: |
> |   1    |                ()                |
> |   2    | !     +(正)    -(负)    ++    -- |
> |   3    |           *    /    %            |
> |   4    |          +(加)    -(减)          |
> |   5    |        <    <=    >    >=        |
> |   6    |             ==    !=             |
> |   7    |                ^                 |
> |   8    |                &&                |
> |   9    |               \|\|               |
> |   10   |                ?:                |
> |   11   | =    +=    -=    *=    /=    %=  |

### 控制语句

#### 循环

> #### for循环
>
> ```java
> for(int i = 0;i < 10 ;i ++ ){
>    
> }
> ```
>
> #### while循环
>
> ```java
> while(i < 10){
>    
> }
> ```
>
> #### do...while循环
>
> ```java
> do{
>    	i++;
> }while(i < 10);
> ```
>
> #### foreach循环
>
> ```java
> for(int a:array){
>    	System.out.println(a);
> }
> ```

#### 判断

> #### if判断
>
> ```java
> if(1 == 1){
>    	
> }else if(1 == 2){
>    	
> }else{
>    	
> }
> ```
>
> #### switch判断
>
> ```java
> switch(n){
>     case 1:...;
>         break;
>     case 2:...;
>         break;
>     default:...;
>         break;
> }
> ```

### 注释

> 1. 注释不会被编译器编译。
>
> 2. 注释类型 : 
>
>    * 单行注释(==多用==)
>
>      ```java
>      //注释内容
>      ```
>
>    * 多行注释(==少用==)
>
>      ```java
>      /*
>       注释内容
>       注释内容
>      */
>      ```
>
>    * 文档注释(==多用==)   和项目文档存在联系。
>
>      ```java
>      /**
>        * 文档注释内容
>        * 文档注释内容
>        */
>      ```
>

### 方法、类声明和调用

> ```java
> //声明类
> //文件名和类名相同时才可以使用public
> class Demo{
>     
> }
> ```
>
> ```java
> //声明对象
> Demo demo = new Demo();
> ```
>
> ```java
> //声明方法
> public static 返回类型  Method(类型 参数){
>     
> }
> ```
>
> ```java
> //调用方法
> //普通方法通过对象.方法名(参数)进行调用
> //静态方法通过类名.方法名(参数)调用
> Demo.Method();
> ```

### 包管理

> 1. 定义包
>
>    ```java
>    package 企业域名倒写.模块名.组件名;
>    ```
>
> 2. 引用包
>
>    ```java
>    import 包名
>    ```

### 运行环境

> #### Java环境变量配置
>
> 1. ==CLASSPATH== : 类加载路径。
> 2. ==PATH== : jdk中bin路径。
> 3. ==JAVA_HOME== : jdk路径。

### 语言基础功能

#### 代码块

> #### 代码块
>
> * 在程序中使用“{}”定义的结构就称为代码块，根据代码块出现的位置和定义可以划分为: 
>
>   1. 普通代码块：定义在一个方法中的代码块；
>
>      ```java
>      if(true){
>          //普通代码块
>      }
>      ```
>
>   2. 构造块：构造块是定义在一个类中的，构造块在每次实例化对象时，构造方法执行之前执行；
>
>      ```java
>      class Person{
>          {
>              //构造块
>          }
>      }
>      ```
>
>   3. 同步代码块：多线程；
>
>   4. 静态代码块 : static定义的代码块，主要用于为类中的静态属性初始化。在构造块执行之前执行，并且只会执行一次。并且静态代码块优先于静态代码块执行，帮助main方法实现一些辅助功能；
>
>      ```java
>      class Person{
>          static{
>              //静态代码块
>         }
>      }
>      ```
>
> * 在同一代码块中不能出现相同名称属性；
>
> * 执行顺序：==**（优先级从高到低）父静态代码块 > 子静态代码块 > main方法 > 父构造代码块 > 父构造方法 > 子构造代码块 > 子构造方法。**==
>
>   ![image-20200901171622362](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200901171622362.png)

#### 内部类

> #### 内部类
>
> * 内部类破坏了类的基本结构，但是可以==轻松访问外部类的私有属性==；
>
>   ```java
>   public class Text01 {
>       public static void main(String[] args) {
>           Test test = new Test();
>           test.say();
>       }
>   }
>   class Test{
>       private String message = "我去！张子怡小可爱！";
>       public void say(){
>           gsSay gs = new gsSay();
>           gs.say();
>       }
>       class gsSay{
>           public void say(){
>               System.out.println(Test.this.message);
>           }
>       }
>   }
>   ```
>
> * 内部类实例化格式为：`外部类.内部类 对象 = new 外部类().new 内部类();`
>
>   ```java
>   public class Text01 {
>       public static void main(String[] args) {
>           //实例化内部类前首先确保外部类被实例化
>           Test.gsSay gs = new Test().new gsSay();
>           gs.say();
>       }
>   }
>   class Test{
>       private String message = "我去！张子怡小可爱！";
>       public void say(){
>           gsSay gs = new gsSay();
>           gs.say();
>       }
>       class gsSay{
>           public void say(){
>               System.out.println(Test.this.message);
>           }
>       }
>   }
>   ```
>
> * 如果内部类只想本类中使用，则可以使用private修饰内部类。
>
>   ```java
>   class Test{
>       private String message = "我去！张子怡小可爱！";
>       public void say(){
>           gsSay gs = new gsSay();
>           gs.say();
>       }
>       private class gsSay{
>           public void say(){
>               System.out.println(Test.this.message);
>           }
>       }
>   }
>   ```
>
> * 除了类之外，接口和抽象类都可以定义内部结构。
>
>   ```java
>   //内部接口
>   interface outInterface{
>       public void say(String s);
>       interface inInterface{
>           public void say(String s);
>       }
>   }
>   class outInterfaceImpl implements outInterface{
>       @Override
>       public void say(String s) {
>           inInterface in = (str)->{
>               System.out.println(str);
>           };
>           in.say(s);
>       }
>   }
>   public class Text01 {
>       public static void main(final String[] args) {
>           outInterfaceImpl in = new outInterfaceImpl();
>           in.say("你好小蝴蝶我是葫芦娃");
>       }
>   }
>   ```
>
>   ```java
>   //内部抽象类
>   abstract class outAbstractClass{
>       public void say(String say){};
>       abstract class inAbstractClass{
>           public void say(String say){};
>       }
>   }
>   class outAbstractClassImpl extends outAbstractClass{
>       class inAbstractClassImpl extends inAbstractClass{
>           @Override
>           public void say(String say) {
>               System.out.println(say);
>           }
>       }
>   }
>   public class Text01 {
>       public static void main(final String[] args) {
>           outAbstractClassImpl.inAbstractClassImpl in = new outAbstractClassImpl().new inAbstractClassImpl();
>           in.say("你好小蝴蝶我是葫芦娃");
>       }
>   }
>   ```
>
> #### static定义内部类
>
> * 实例化static定义的内部类需要采用 ` 外部类.内部类 对象名称 = 外部类.内部类` 即可。
>
> * static定义内部接口最为常用。
>
>   * 使用static定义内部接口因为这是同种类型的操作。
>
>   ```java
>   public class Text01 {
>       public static void main(final String[] args) {
>           Message.send(new DefaultMessage(), new DefaultChannel());//发送消息
>       }
>   }
>   interface Message {//消息包装
>       static interface IMessage{//获得消息
>           public String getContent();
>       }
>       static interface IChannel{//获得连接
>           public boolean connect();
>       }
>       public static void send(IMessage msg,IChannel channel){//发送消息
>           if(channel.connect()){
>               System.out.println(msg.getContent()); 
>           }else{
>               System.out.println("消息发送失败！");
>           }
>       }
>   }
>   class DefaultMessage implements Message.IMessage{//获得消息内容
>   	@Override
>   	public String getContent() {
>   		return "哇！是张子怡小宝宝";
>   	}
>   }
>   class DefaultChannel implements Message.IChannel{//获取连接
>       @Override
>       public boolean connect() {
>           return true;
>       }
>   }
>   ```
>
> * 追加static方法可以不受到实例化对象的控制，可以说变成了外部类。
>
>   ```java
>   public class Text01 {
>       public static void main(final String[] args) {
>           outInterface in = outInterface.getInstance();
>           in.say("你好小蝴蝶我是葫芦娃");
>       }
>   }
>   interface outInterface{
>       public void say(String s);
>       interface inInterface{
>           public void say(String s);
>       }
>       class outInterfaceImpl implements outInterface{
>           @Override
>           public void say(String s) {
>               inInterface in = (str)->{
>                   System.out.println(str);
>               };
>               in.say(s);
>           }
>       }
>       public static outInterfaceImpl getInstance(){
>           return new outInterfaceImpl();
>       }
>   }
>   ```
>
> #### 方法中定义内部类
>
> * 方法中的内部类直接访问方法中的参数是从JDK1.8开始。JDK1.8之前如果想要访问需要在方法中的参数前追加final关键字。JDK1.8取消这种操作是为了编程时函数做准备。
>
>   ```java
>   public class Text01 {
>       public static void main(final String[] args) {
>           String say = "哇！是张子怡小宝宝!";
>           class say{
>               public void sayMessage(){
>                   System.out.println(say);
>               }
>           }
>           say s = new say();
>           s.sayMessage();
>       }
>   }
>   ```
>
> #### 		匿名内部类
>
> * 没有名字只使用一次的内部类叫做匿名内部类。
>
> * 使用次数不多，写实现类比较浪费时，使用匿名内部类。
>
>   ```java
>   public class Text01 {
>       public static void main(final String[] args) {
>           sayMes say = new sayMes(){//匿名内部类
>               @Override
>               public void say() {
>                   System.out.println("哇！是张子怡小宝宝!");
>               }
>           };
>           say.say();
>       }
>   }
>   interface sayMes{
>       public void say();
>   }
>   ```
>

#### 字符串处理

> #### 操作
>
> 1. 根据元素查找下标：
>
>    ```java
>    //找到字符串中第一次出现的指定元素的位置下标
>    int firstIndex = "123".indexof("1");
>    //找到字符串中最后一次出现的指定元素的位置下标
>    int lastIndex = "123".lastIndexOf("1");
>    ```
>
> 2. 根据下标查找元素
>
>    ```java
>    //查找下标为2的字符
>    char str = "123".charAt(2);
>    ```
>
> 3. 获得子字符串
>
>    ```java
>    //从下标为0开始，截取到下标为2的字符串
>    String str = "123".subString(0,2);
>    //从下标为1开始截取到字符串的结束
>    String str = "123".subString(1);
>    ```
>
> 4. 去除字符串的空格，只移除开头和结尾
>
>    ```java
>    //将目标字符串前置的空格和结尾的空格去掉并返回
>    String str = " 123  ".trim();
>    ```
>
> 5. 字符串替换，把字符串中出现的所有A字符替换为B字符
>
>    ```java
>    //所有都替换
>    String str = "123".replace('1','4');
>    ```
>
> 6. 字符串比较
>
>    ```java
>    //如果长度和字符相同则返回true
>    boolean isEquals = "123".equals("321");
>    ```
>
>    ```java
>    //忽略大小写
>    boolean isEquals = "ASD".equals("asd");
>    ```
>
>    ```java
>    //按照字典顺序比较两个字符串
>    boolean isEquals = "ASD".compareTo("asd");
>    ```
>
> 7. 大小写转换
>
>    ```java
>    //把指定字符串中所有不是大写的母变成大写字母
>    String upperCase = "asd".toUpperCase();
>    ```
>
>    ```java
>    //把指定字符串中所有不是小写的字母变成小写字母
>    String lowerCase = "asd".toLowerCase();
>    ```
>
> 8. 字符串分割
>
>    ```java
>    //将指定的字符串按照指定的字符或字符串进行分隔，并把结果保存在字符数组中
>    String[] str = "123123123".split('1');
>    ```
>
>    **ps：大多数的的字符串操作都有正则表达式相关的操作**
>
> #### String
>
> * String的底层是char数组，如果在创建时赋值的话则把赋予的值保存在数组中，如果没有赋值则默认是空。`默认值：''`
>
> * 由于String不可改变，因此它是线程安全的。
>
> * String类被final关键字修饰，因此在创建完赋过值后不能发生改变，每个赋值或修改的语句都是新创建一个String对象，并让当前的变量名指向新的字符串对象。（*修改字符串流程图如下*）
>
>   ![image-20200904165104420](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200904165104420.png)
>
>   ------
>
> * String类并不是线程安全的。
>
> #### StringBuilder
>
> * StringBuilder类继承AbstractStringBuilder，在AbstractStringBuilder中有一个方法是拼接字符串，因此虽然StringBuilder是final类，但是它的值仍然可以通过`append()`方法进行修改。（*修改字符串工作流程图如下*）
>
>   ![image-20200904174110269](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200904174110269.png)
>
> * StringBuilder是线程不安全的。
>
> #### StringBuffer
>
> * StringBuffer大多数方法都有synchronized锁，因此它是线程安全的；由于它大多数方法加有锁，因此它执行起来速度比StringBuilder慢。

#### 日期处理

> #### Date（1.8不推荐）
>
> * Date是在`java.util`包中，而不是`java.sql`包。
>
> * 常用方法：
>
>   ```java
>   public class Main{
>   	public static void main(String[] args) {
>               //无参构建对象，时间为当前电脑显示时间
>               Date date = new Date();
>               //有参构建对象，时间为指定的long类型变量转换而得，变量是毫秒数，从格林尼治标准时间开始算
>               Date date1 = new Date(19990628);
>               //after方法判断当前日期是否在指定日期之后
>               System.out.println(date.after(date1));
>               //before方法判断当前日期是否在指定日期之前
>               System.out.println(date.before(date1));
>               //获得当前时间，毫秒
>               System.out.println(date.getTime());
>               //设置时间
>               date.setTime(19990628);
>               System.out.println(date);
>           }
>   }
>   ```
>
> #### SimpleDateFormat(线程不安全)
>
> * 对date日期进行格式化
>
>   ```java
>   public class Main{
>   	public static void main(String[] args) {
>           	Date date = new Date();
>           	SimpleDateFormat simpleDateFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
>           	String nowDate = simpleDateFormat.format(date);
>           	System.out.println(nowDate);
>   	}
>   }
>   ```
>
> #### Calender(推荐)
>
> * 1.8后支持，可以指定格式，也可以
>
>   ```java
>   
>   ```
>
> #### LocalDateFormat
>
> * 这个类存储时间的精确度非常高，可以精确到纳秒。它是ISO-8601日历系统中不带时区的日期时间。

#### 错误和异常处理

> * 异常是导致程序中断的一种指令流。在程序出错后，整个程序不会按照既定的方式进行执行，而是中断操作。
> * 编译时异常必须显式处理，运行时异常交给虚拟机。
> * 捕获到的异常不仅可以在本方法中处理，还能抛给调用它的上一级方法。
>
> #### 处理异常
>
> * 使用try、catch、finally关键字。
>
>   ```java
>   try{
>       //可能出现异常的代码
>   }catch(异常类型 异常对象){
>       
>   }catch(异常类型 异常对象){
>       
>   }finally{
>       //无论时有出现异常都一定执行
>   }
>   ```
>
>   组合格式有 ：
>
>   * try{...}catch(...){...}
>   * try{...}catch(...){...}catch(...){...}
>   * try{...}catch(...){...}catch(...){...}finally{...}
>
> * 获得完整的异常信息使用异常中的printStackTrace()方法。
>
> * 如果没有正确的捕获异常，程序依然会中断。
>
> #### 异常处理流程
>
> 1. 程序运行过程中产生异常，将自动进行指定类型的异常类对象实例化处理。
>
> 2. 如果程序没有提供异常处理机制，则会默认使用JVM默认处理机制：打印出相关信息然后退出程序。
> 3. 如果有异常处理机制，产生的异常类的实例化对象将会被try语句所捕获。
> 4. try捕获到异常后与其catch中的异常类型依次比对，如果和catch中异常相同用，则使用此catch处理，如果不匹配则继续匹配后续的catch。如果没有任何匹配则意味着这个异常无法进行处理。
> 5. 无论怎样都要执行finally语句，执行完finally后判断是否处理完成，如果没有则交由JVM处理，如果完成则继续执行下边的代码。
>
> 在程序中可以处理的异常的最大类型就是Throwable。Throwable有两个子类
>
> * Exception：程序运行中产生的异常，开发者重点处理的类型。
> * Error：此时程序未执行的错误，开发者无法处理。
>
> 所有的异常都可以用Exception来进行处理，但是描述错误信息不明确。
>
> #### throws关键字
>
> * 告诉使用者可能会产生什么异常。
>
>   ```java
>   public void throwsFunction throws Exception{
>       //可能会产生Exception异常
>   }
>   ```
>
> * 使用throws时如果出现异常可以直接处理对应的异常而不用try{}catch(){}捕获处理异常，默认将异常向上抛出。
>
> #### throw关键字
>
> * 手工产生一个异常类的对象并抛出。
>
>   ```java
>   public void throwFunction(){
>       try{
>           throw new Exception("手工抛出异常");//手工创建异常并抛出
>       }catch(Exception e){
>           e.printStackTrace(); 
>       }
>   }
>   ```
>
> throw和throws的区别:
>
> * throw是在代码块中使用,主要是进行手工对异常对象的抛出。
> * throws是定义在方法上,表示此方法可能产生的异常,明确告诉调用出。
>
> #### 异常处理的标准格式
>
> * 对方法要求如下:
>
>   1. 在进行数学计算开始与结束的时候进行信息提示;
>   2. 如果在进行计算时产生异常，则交给调用处处理。
>
>   ```java
>   public void throwException() throws Exception{
>       try{
>           System.out.println("产生异常");
>       }catch(Exception e){
>           throw e;//将异常交给调用处处理,该catch在这种结构中可以省略
>       }finally{
>           System.out.println("方法结束")
>       }
>   }
>   ```
>
> #### RuntimeException异常
>
> * RuntimeException的子类可以不需要强制性处理。
> * RuntimeException是Exception的子类，并且不需要强制执行。
> * 常见的RuntimeException常见的子类 : ClassCastException , NoPoniterException。
>
> #### 自定义异常
>
> * 自定义异常类有两种实现方法: 继承Exception和继承RuntimeException。 
>
>   ```java
>   class MyException extends Exception{
>       public MyException(String msg){
>           super(msg);
>       }
>   }
>   class Test{
>       public static void main(String []args){
>           throw new MyException("啊啊啊异常啦");
>       }
>   }
>   ```
>
> #### assert断言
>
> * 确定代码执行到某行后一定是自己期待的内容。
>
>   ```java
>   class Test{
>       public void assertTest(){
>           int sad = 10;
>           assert sad == 100;
>       }
>   }
>   ```
>
>   断言默认不开启使用，如果需要开启使用则需要在运行时加入`java -ea`。

#### 数据库连接和查询

> 

#### 文件IO

> 

#### JavaNIO

> 

#### XML

##### DOM

> 

##### SAX

> 

##### DOM4J/JDOM/Castor

> 

#### 算法

> #### 1.异或运算(^)
>
> * 性质 : 
>   1. 任何数和 00 做异或运算，结果仍然是原来的数，即 ==a⊕0=a==。
>   2. 任何数和其自身做异或运算，结果是 00，即==a*⊕*a=0==。
>   3. 异或运算满足交换律和结合律，即==a⊕b⊕a=b⊕a⊕a=b⊕(a⊕a)=b⊕0=b==。
>
> #### 2.递归算法(基础算法之一)
>
> * 递归是指在函数的定义中使用函数自身的方法，所有递归问题都有非递归解法。递归包括两部分 : ==递和归==。
>   1.  ==递== : 递归问题必须可以分解为若干个规模较小，与原问题形式相同的子问题，这些子问题可以用相同的解题思路来解决。
>   2.  ==归== : 有一个明确的终点(临界点)，一旦到达了这个临界点，就不用再往更小、更远的地方走下去。最后，从这个临界点开始，原路返回到原点，原问题解决。
> * 递归三要素 : 
>   * 明确递归终止条件；
>   * 给出递归终止时的处理办法；
>   * 提取重复逻辑，缩小问题规模。
>
> #### 3.贪心算法(基础算法之一)
>
> #### 4.动态规划算法(基础算法之一)
>
> #### 5.穷举法(基础算法之一)
>
> #### 6.中心扩展算法
>
> * 把每个元素都当成中心点，然后像两端进行扩展。

### Servlet

> #### JSP
>
> JSP是动态网站，会随着用户操作、时间、地点的改变而改变。JSP本质是servlet文件，他俩之间可以互相转换。
>
> ##### 1. 配置文件server.xml
>
> 设置文件读取路径，docBase表示文件在本地的路径，path表示访问的路径。path可以是相对路径，也可以是绝对路径。在浏览器中可以根据path的位置实现对项目的访问。
>
> ```xml
> <Context docBase="绝对路径(/)" path="\路径名"></Context>
> ```
>
> * 域名解析流程：输入域名->本地解析(host文件)->域名解析器
>
> * 本地解析首先在本地查找是否有这个网址，如果找到就不再访问互联网，否则则访问。
>
> * 配置本地主机：在server.xml中增加：
>
>   ```xml
>   <Engine name="Catalina" defaultHost="www.test.com"></Engine>
>   <Host appBase="项目的实际位置" name="主机名" >
>   	<Context docBase="路径" path="\路径名"></Context>
>   </Host>
>   ```
>
>   修改本机host文件，增加一个映射。
>
> #####   2. JSP执行流程
>
> 第一次访问将JSP翻译成Java，然后将Java编译成class文件，最终执行。
>
> 第二次访问(服务端代码未修改，否则会重新翻译编译)，直接访问class文件。
>
> ##### 3. JSP编码问题，页面元素和request对象
>
> 9大内置对象，不需要new：
>
> * out：输出对象，向客户端输出内容
> * pageContext：
> * request：请求对象，存储客户端向服务端发送的请求信息，常见方法：
>   * getParameter，返回一个值
>   * getParameterValues，返回数组
>   * setCharacterEncoding，设置编码，tomcat8为utf-8。
>   * getRequestDispatcher().forward()，请求转发。
>   * getServerContext()。
> * response：
> * session：
> * application：
> * config：
> * page：
> * exception

### 泛型

> 类名<T>，在定义时指定类型，则T就是该指定的类型。
>
> 使用泛型解决大部分的对象转换问题。
>
> #### 泛型通配符
>
> * 可以接受所有的泛型类型，不允许修改里边的数据，并且不能修改里边的数据，因此需要用到通配符 ? 。
> * ? 通配符基础上还有两类小的通配符 : 
>   1. ` ? extends Number` 类型设置泛型上限 : 该泛型只允许设置Number或Number的子类。
>   2. `? super Number` 类型设置泛型下限 : 只能使用Number或Number的父类。
>
> #### 泛型接口
>
> * 定义泛型接口
>
>   ```java
>   //定义泛型接口
>   interface IMessage<T>{
>       public T getIMessage();
>   }
>   ```
>
> * 实现泛型接口
>
>   1. 在子类中继续使用泛型定义。
>
>      ```java
>      //H可以替换为其他的字母
>      class IMessageImpl<H> implements IMessage<H>{
>          @Override
>          public H getIMessage() {
>              return null;
>          }
>      }
>      ```
>
>   2. 实现父接口时，直接定义父类接口泛型类型。
>
>      ```java
>      IMessage<String> im = new IMessage<String>() {
>          		//覆写接口方法
>          @Override
>          public String getIMessage() {
>              return null;
>          }
>      };
>      ```
>
> #### 泛型方法
>
> * 将泛型标记写在方法上，叫做泛型方法。泛型方法不一定非出现在泛型类中，非泛型类也可以使用泛型方法。
>
>   ```java
>   //定义泛型方法
>   class Fun {
>       public <T> T[] getMessage(T ... args){
>           return args;
>      }
>   }
>   ```
>

### 反射

> #### 反射
>
> * 所有技术的实现目的都是重用性。
>
>   * 对于反射首先考虑反与正的概念：
>   * 正：使用类得时候首先导入程序所在包，然后根据类实现对象，依靠对象调用方法。
>   * 反：根据实例化对象反推出其类型。
>
> * 实现反射技术首先使用Object提供的一个获取类信息的方法(`Object.getClass();`)，该方法可以让使用者找到对象的根源。
>
> * 反射中的所有核心操作都是通过Class类对象展开的，Class类是反射操作的根源所在。可以采用三种方式完成实例化。
>
>   1. 【Object支持】Object根据实例化对象获取Class对象。
>
>      * 特点：如果想要获得对象，首先得实例化一个对象才可以获取。
>
>      ```java
>      public class Text01 {
>          public static void main(String[] args) {
>              Main m = new Main();
>              Class cls = m.getClass();
>              System.out.println(cls.getName());
>          }
>      }
>      ```
>
>   2. 【JVM唯一支持】==类.class==方式是JVM直接可以支持的方式，也是唯一支持的。
>
>      * 特点：需要导包。
>
>      ```java
>      public class Text01 {
>          public static void main(String[] args) {
>              Class cls = Main.class;
>              System.out.println(cls.getName());
>          }
>      }
>      ```
>
>      
>
>   3. 【Class类支持】Class类中的forName方法，使用字符串形式定义要使用的类型，程序中不需要编写任何的import语句。
>
>      * 特点：使用字符串，极大降低耦合性。如果使用的程序类不存在则会报ClassNotFoundException异常，因此需要对异常进行处理。
>
>      ```java
>      public class Text01 {
>          public static void main(String[] args) throws ClassNotFoundException{
>              Class cls = Class.forName("program01.Main");
>              System.out.println(cls.getName());
>          } 
>      }
>      ```
>
> #### 反射获取对象参数
>
> `getDeclaredFields()`：获取某个类中所有声明的字段，包括public、private、protected，但不包括父类中的。
>
> `getFields()`：获取某个类中所有的public字段，包括父类。（只能是public，protected和default都不行）。
>
> ```java
> public class Text01 {
> 	public static void main (String[] args){
> 		Son son = new Son();
> 		Field[] field = son.getClass().getDeclaredFields();
> 		Field[] field2 = son.getClass().getFields();
> 		try{
> 			for(Field f:field){
> 				f.setAccessible(true);
>                 		//得到值
> 				Object v = f.get(son);
>                 		//getName()得到参数名字
> 				System.out.println("f.name:"+ f.getName() +",f.value:"+v);
> 			}
> 			for(Field f2:field2){
> 				Object v = f2.get(son);
> 				System.out.println("f2.name:"+ f2.getName() +",f.value:"+v);
> 			}
> 		}catch(Exception e){
> 			e.printStackTrace();
> 		}
> 	}
> }
> class Father{
> 	private String username;
> 	public final String GENDER = "男";
> 	public void setUsername(String username){
> 		this.username = username;
> 	}
> 	public String getUsername(){
> 		return this.username;
> 	}
> }
> class Son extends Father{
> 	private String password;
> 	public void setPassword(String password){
> 		this.password = password;
> 	}
> 	public String getPassword(){
> 		return this.password;
> 	}
> }
> ```
>
> 

### 并发

> 

### 多线程

> 

### 网络传输

#### TCP/IP

> 

#### HTTP

> 

#### socket

> 

### Java消息服务(JMS)

### XSLT

> 

### EJB

> 

### javaBean

> 

### Flex

> 

### ESB

> 

### 字符集和编码

#### ASCII字符集&编码

> 

#### GBK字符集&编码

> 

#### GB2312字符集&编码

> 

#### UTF-8字符集&编码

> 

#### UTF-16字符集&编码

> 

### 设计模式

#### 设计模式的目的

> 1. 代码可重用性 （相同功能代码不用重复编写）
> 2. 可读性 （编程规范性，方便阅读和理解）
> 3. 可扩展性 （即增加新功能时，非常方便）
> 4. 可靠性 （当增加新功能后对之前功能没有影响）
> 5. 使程序呈现==高内聚，低耦合==的特性

#### 七大原则

> 1. 单一职责原则
>    * 降低类的复杂度，一个类只负责一个职责。
>    * 提高类的可读性，可维护性。
>    * 降低变更引起的风险。
> 2. 接口隔离原则
>    * 客户端不应该依赖它不需要的接口，一个类对另一个类的依赖应该建立在最小的接口上。
> 3. 依赖倒置原则
> 4. 里氏替换原则
> 5. 开闭原则
> 6. 迪米特法则
> 7. 合成复用原则

#### 23种设计模式

> 

#### J2EE模式

> 

### 表达式

#### Lambda表达式

> #### 简介
>
> * 1.8为简化开发引入lambda表达式。
> * 通过指定格式实现只有一个方法的接口。
> * 使用要求   SAM。接口中只有一个抽象方法，该接口称为函数式接口，只有函数式接口才能使用lambda表达式。函数式接口：加入@FunctionalInterface注释。
> * lambda用来替换符合SAM的匿名内部类。
>
> #### 格式
>
> ```java
> public class Text01 {
>     public static void main(String[] args) {
>         Demo demo = ()->{
>             System.out.println("我是无参无返回函数式接口");
>         };
>         Demo1 demo1 = (i)->{
>             i++;
>             System.out.println("我是有参无返回函数式接口:"+i);
>         };
>         Demo2 demo2 = (j)-> ++j;//有返回值可以直接省略return
>         demo.say();
>         demo1.say(1);
>         System.out.println(demo2.say(3)); 
>     }
> }
> @FunctionalInterface
> interface Demo{
>     public void say();
> }
> @FunctionalInterface
> interface Demo1{
>     public void say(int i);
> }
> @FunctionalInterface
> interface Demo2{
>     public int say(int j);
> }
> ```
>
> * 方法没有参数：`()->{}。`
> * 方法有参数：`(参数)->{}。`
> * 只有一行语句返回：`(参数)->{语句}。`
>
> #### 方法引用
>
> * 不同的方法名称可以描述同一方法，只是这里说是引用，从本质来说不是调用方法，而是==给要引用的方法起个别名==，再通过别名调用。==起别名的方法的参数必须和调用方法的一样,接口的抽象方法没有返回值，引用的方法可以有返回值也可以没有;接口的抽象方法有返回值，引用的方法必须有相同类型的返回值！！==
>
> * 引用静态方法
>
>   * 类名称::静态方法名;
>
>     ```java
>     public class Text01 {
>         public static void main(String[] args) {
>             Fun fun = Gs :: say;//给静态方法所起的别名
>             fun.s();//引用静态方法
>         }
>     }
>     class Gs{
>         public static void say(){//要引用的静态方法
>             System.out.println("哇！是张子怡小宝宝！");
>         }
>     }
>     interface Fun{
>         public void s();//对应的别名
>     }
>     ```
>
> * 引用某个对象实例方法
>
>   * 实例化对象::普通方法;
>
>     ```java
>     public class Text01 {
>         public static void main(String[] args) {
>             Gs gs = new Gs();
>             Fun fun = gs :: say;//实例化对象
>             fun.s();
>         }
>     }
>     class Gs{
>         public void say(){
>             System.out.println("哇！是张子怡小宝宝！");
>         }
>     }
>     interface Fun{
>         public void s();
>     }
>     ```
>
> * 引用特定类型方法
>
>   * 特定类::普通方法;
>
>   * 在引用时，实现方法中第一个参数必须是目标方法的对象，作为临时的this使用。
>
>     ```java
>     public class Text01 {
>         public static void main(String[] args) {
>             Fun<Gs> fun = Gs :: say;
>             fun.compare(new Gs(),"123");
>         }
>     }
>     class Gs{
>         public void say(String str){
>             System.out.println(str);
>         }
>     }
>     interface Fun<T>{
>         public void compare(Gs gs,String str);//第一个参数必须得为目标类的对象
>     }
>     ```
>
> * 引用构造方法
>
>   * 类名称::new 类名。
>
>     ```java
>     public class Text01 {
>         public static void main(String[] args) {
>             Fun fun = Gs :: new;
>             fun.compare();
>         }
>     }
>     class Gs{
>         Gs(){
>             System.out.println("构造方法执行...");
>         }
>     }
>     interface Fun{
>         public void compare();
>     }
>     ```
>
> #### 内建函数式接口
>
> ##### 	功能型函数接口Function
>
> * Function<对象类型，返回值类型> function ;
>
> * 有返回值。
>
>   ```java
>   import java.util.function.Function;
>   
>   public class Text01 {
>       public static void main(String[] args) {
>           Function<String ,Integer> function = "GS" :: compareTo;
>           System.out.println(function.apply("ZZY")); 
>       }
>   }
>   ```
>
> ##### 消费型函数接口Consumer 
>
> * Consumer <对象类型> consumer;
>
> * 无返回值。
>
>   ```java
>   import java.util.function.Consumer;
>   
>   public class Text01 {
>       public static void main(String[] args) {
>           Consumer<String> consumer = System.out::println;
>           consumer.accept("哇！是张子怡小宝宝！");
>       }
>   }
>   ```
>
> ##### 供给型函数接口Suppiler
>
> * Suppiler<返回值类型> suppiler;
>
> * 有返回值，无对象类型。
>
>   ```java
>   import java.util.function.Supplier;
>   
>   public class Text01 {
>       public static void main(String[] args) {
>           Supplier<String> supplier = "GS love ZZY" :: toUpperCase;
>           System.out.println(supplier.get());
>       }
>   }
>   ```
>
> ##### 断言型函数接口Predicate
>
> * Predicate<参数类型>  predicate;
>
> * 返回类型为boolean，有对象类型。
>
>   ```java
>   import java.util.function.Predicate;
>   
>   public class Text01 {
>       public static void main(String[] args) {
>           Predicate<String> predicate = "ZZY"::equals;
>           System.out.println(predicate.test("GS"));
>       }
>   }
>   ```
>
>   

#### 正则表达式

> 1. \* 表示任意长度的字符串
>
> 2. ？表示长度为1的任意字符
>
> 3. 元字符
>
>    | 元字符 |             说明             |
>    | :----: | :--------------------------: |
>    |   .    |  匹配除换行符意外的任意字符  |
>    |   \w   | 匹配字母或数字或下划线或汉字 |
>    |   \s   |       匹配任意的空白符       |
>    |   \d   |           匹配数字           |
>    |   \b   |     匹配单词的开始或结束     |
>    |   ^    |       匹配字符串的开始       |
>    |   \$   |       匹配字符串的结束       |
>
> 4. 反义，与元字符意思相反
>
>    |   语法   |                    说明                    |
>    | :------: | :----------------------------------------: |
>    |    \W    | 匹配任意不是字母，数字，下划线，汉字的字符 |
>    |    \S    |          匹配任意不是空白符的字符          |
>    |    \D    |            匹配任意非数字的字符            |
>    |    \B    |        匹配不是单词开头或结束的位置        |
>    |   [^x]   |          匹配除了x以外的任意字符           |
>    | [^aeiou] |   匹配除了aeiou这几个子母以外的任意字符    |
>
> 5. 转义字符: `\`
>
> 6. 重复：
>
>    | 语法  |       说明       |
>    | :---: | :--------------: |
>    |   *   | 重复零次或更多次 |
>    |   +   | 重复一次或更多次 |
>    |   ?   |  重复零次或一次  |
>    |  {n}  |     重复n次      |
>    | {n,}  | 重复n次或更多次  |
>    | {n,m} |   重复n次到m次   |
>
> 7. 分支条件：`|`，表示分割，从左到右测试每个条件，如果满足某个分支，则不用管其他条件。
>
> 8. 

#### Cron表达式

#### EL表达式

#### JSTL表达式

#### OGNL表达式

### MVC框架

#### struts

#### JSF

#### WebWork

### 数据库连接

#### C3P0

#### DBCP

#### DRUID

#### Proxool

#### BoneCP

#### Weblogic连接池

#### Tomcat JDBC 连接池

### log

#### log4j

#### commons-log

#### logback

#### slf4j

### JDK

#### Java8新特性

#### Java7新特性

#### JVM

#### Java运行类库

> #### 五大内存区域
>
> 1. 程序计数器
>
>    1. 程序计数器可看作当前线程所执行的**字节码的行号指示器**，内存空间比较小。
>    2. 程序计数器是**线程私有的**。
>
> 2. Java虚拟机栈
>
>    1. 虚拟机栈描述的是Java方法执行的线程内存模型：每个**方法**执行时，Java虚拟机会同步创建一个栈帧用于存储**局部变量，方法出口等信息**。每一个方法被调用到结束都对应着一个栈帧从入栈到出栈的过程。
>    2. 虚拟机栈存储了编译期可知的**基本数据类型，对象应用和方法返回类型**。
>    3. *局部变量槽*
>    4. Java虚拟机栈是**线程私有的**。
>
> 3. 本地方法栈
>
>    1. 为使用到的Native方法服务。
>
> 4. Java堆
>
>    1. **存放对象实例**。
>
>    2. 分代思想是为了便于垃圾收集：
>
>       1. 老年代
>
>       2. 新生代
>
>       3. Eden
>
>       4. Survivor
>
>          .   .   .
>
>    3. Java堆既可以被是现成固定大小，也可以是可扩展的。如果Java堆中没有完成实例分配，并且堆也无法再扩展，Java虚拟机将会抛出OutOfMemoryError（OOM）。
>
>    4. Java堆是各个线程所共享的。
>
> 5. 方法区
>
>    1. 以前被叫做永久代，JDK1.8之后完全废除永久代，变为元空间。
>    2. 运行时常量池：
>       1. 存放编译期生成的各种字面量和符号引用。
>       2. 常量池也会报OOM 异常。
>    3. 方法区是各个线程所共享的。
>    
>    #### 对象创建
>    
>    	1. ==检查是否已经有相同的对象==。虚拟机遇到new指令，首先在常量池中查找这个参数是否有对应的一个类的符号引用，并检查这个符号引用代表的类是否已被加载、解析和初始化过，否则执行相应的类加载过程。
>     	2. ==为新生对象分配内存==。对象所需内存的大小在类加载结束后便可确定。
>     	3. ==初始化内存空间==。如果使用TLAB（本地线程分配缓冲区），这一项工程可提前到TLAB分配时顺便进行。
>     	4. ==对对象进行必要的设置==。比如这个对象是哪个类的实例，对象的哈希码，对象的GC分代年龄等信息。
>     	5. ==执行构造方法==。
>    
>    

### 数据结构

#### 栈、队列、链表

#### 散列表

#### 二叉树、红黑树、B树

#### 图

## 前端技术

### HTML5

### CSS

> #### 优先级
>
> ##### 优先级分级
>
> 1. ==类选择器==（.h），==伪元素==（::before）
>
> 2. ==类选择器==（.example），==属性选择器==，==伪类==（:hover）
>
> 3. ==ID选择器==
>
> 4. ==内联样式==（`style=""`）
>
> 5. `!import`声明，可以使用的情况：
>
>    1. 覆盖内联样式
>    2. 覆盖优先级高的选择器
>
>    覆盖`!import`
>
>    * ==用魔法打败魔法==
>
> **在否定伪类（`:not()`）内部声明的选择器会影响优先级**
>
> ##### `:not()`和`:is()`例外规则
>
> #####  `:where()`
>
> ##### `基于形式的优先级`
>
> ```html
> <style>
>     #foo{
>         color: green;
>     }
>     [id="foo"]{
>         color: pruple;
>     }
> </style>
> ```
>
> 虽然`[id="foo"]`选择了一个ID，但它还是以一个属性选择器来计算自身优先级。
>
> ##### 计算方法
>
> ![image-20201113163531225](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201113163531225.png)
>
> 设a代表特指度为10的选择器，b代表特指度为100的选择器，c代表特指度为1000的选择器，则选择器表达式优先度的计算公式为：
>
> ​	**a \* 10 + b \* 100 + c \* 1000**

### JavaScript

> #### 特点
>
> 1. 脚本编写语言：采用小程序段的方式实现编程；不用先编译，而是在运行过程中逐行解释翻译。
> 2. 基于对象
> 3. 简单性
> 4. 安全性：针对性语言，不允许访问硬盘，不允许对网络文档进行修改和删除，从而有效防止数据丢失。
> 5. 动态性：对用户或客户的输入做出响应，采用事件驱动。
> 6. 跨平台性：依赖于浏览器本身而和操作系统无关。
>
> #### JavaScript和Java的区别
>
> 1. 基于对象和面向对象：java是面向对象，必须设计对象；javascript是基于对象和事件驱动的编程语言。
> 2. 解释和编译：java必须先编译再执行。javascript则是解释执行。
> 3. 强变量和弱变量
> 4. 代码格式：java代码以字节码形式保存在独立文档；javascript是嵌入在html文档中。
> 5. 嵌入方式：java：\<applet>\</applet>；javascript：\<script>\</script>
> 6. 静态联编和动态联编：Java的对象引用必须在编译时的进行；JavaScript的对象引用在运行时进行检查。
>
> #### JavaScript嵌入
>
> ```html
> <script>
> 	//js代码
> </script>
> <script src="链接" language="javascript"></script>
> ```
>
> * 解释器执行过程：程序源代码--〉词法分析--〉单词流--〉语法分析--〉抽象语法树--〉指令流(可选)--〉解释器--〉解释执行
>
> #### JavaScript注释
>
> ```javascript
> //单行注释
> ```
>
> ```javascript
> /*
> 多行注释
> 多行注释
> 多行注释
> */
> ```
>
> #### 变量命名
>
> 1. 第一个是ASCII字母或下划线，不能是数字
> 2. 后续必须是字母数字或下划线
> 3. 变量名不能是保留字
>
> ##### var定义变量
>
> 1. 使用var定义变量，这个变量属于当前作用域，如果在任何函数外边，那么就是作用域全局作用域。
>
> 2. var定义变量会发生提升。提升是指无论 var 出现在一个作用域的哪个位置，这个声明都属于当前的整个作用域，在其中到处都可以访问到。注意只有变量声明才会提升，对变量赋值并不会提升。
>
>    ```java
>    //定义变量
>    console.log(a);//此处输出undefined而不是报没有这个参数的错误
>    var a = 1;
>    ```
>
> ##### let定义变量
>
> 1. let 声明的变量具有块作用域的特征。
>
> 2. 在同一个块级作用域，不能重复声明变量。
>
> 3. let 声明的变量不存在变量提升
>
>    ``` javascript
>    let a = 123;
>    ```
>
> ##### const定义变量
>
> 1. 定义后不能发生更改
>
> ##### 总结
>
> 1. var 声明的变量属于函数作用域，let 和 const 声明的变量属于块级作用域；
> 2. var 存在变量提升现象，而 let 和 const 没有此类现象；
> 3. var 变量可以重复声明，而在同一个块级作用域，let 变量不能重新声明，const 变量不能修改。
>
> #### 变量类型强制转换
>
> |        运算        |           结果           |
> | :----------------: | :----------------------: |
> |  数值与字符串相加  |  将数值强制转换为字符串  |
> | 布尔值与字符串相加 | 将布尔值强制转换为字符串 |
> |  数值与布尔值相加  |  将布尔值强制转换为数值  |
>
> #### 函数
>
> ```javascript
> function 函数名(参数){
>     //函数体
> }
> ```
>
> * 函数中参数默认是数字类型，如果穿递字符串等需要对它进行相应的处理。
>
>   ```javascript
>   function  Test(参数){
>       
>   }
>   //如果想传字符串，则需要加引号
>   Test('1');
>   ```
>
>   
>
> #### 对象
>
> 1. 用户自定义对象
> 2. 内置对象：比如Date
> 3. 宿主对象：比如window,dom等。
>
> ```javascript
> var my = new 对象();
> ```
>
> #### 数组
>
> ```javascript
> //定义数组
> var nums = new Array();
> nums[0] = 1;
> nums[0] = 2;
> //
> ```
>
> 1. 数组的函数：
>
>    1. join(separator);
>
>       1. separator是可选参数，表示每个元素之间用什么符号分割，如果没写表示使用`,`分割。
>
>       2. 该方法用于将数组中得所有元素放入到一个字符串中，并以指定得格式分隔。
>
>          ```javascript
>          var my = new Array();
>          my[0]=1;
>          my[1]=2;
>          console.log(my.join());
>          console.log(my.join('-'));
>          ```
>
>    2. pop();
>
>       1. 该方法用于删除并返回数组的最后一个元素，并返回。
>
>          ```javascript
>          var my = new Array();
>          my[0]=1;
>          my[1]=2;
>          my.pop();
>          ```
>
>    3. push();
>
>       1. 该方法可向数组的末尾添加一个或多个元素，并返回新的长度。
>
>          ```javascript
>          var my = new Array();
>          my[0]=1;
>          my[1]=2;
>          console.log(my.push(123));
>          ```
>
>    4. reverse();
>
>       1. 该方法用于颠倒数组中元素的顺序。
>
>          ```javascript
>          var my = new Array();
>          my[0]=1;
>          my[1]=2;
>          my.reverse();
>          ```
>
>    5. shift();
>
>       1. 该方法用于把数组的第一个元素从其中删除，并返回第一个元素的值。
>
>          ```javascript
>          var my = new Array();
>          my[0]=1;
>          my[1]=2;
>          console.log(my.shift());
>          ```
>
>    6. concat(Array);
>
>       1. 该方法用于连接两个或多个数组。该方法不会改变现有的数组，而仅仅会返回被连接数组的一个副本。
>
>       2. 参数为另一个数组。
>
>          ```javascript
>          var my = new Array(1,2);
>          var my2 = new Array(3,4);
>          console.log(my.concat(my2));
>          ```
>
>
> #### 事件函数
>
> 1. onclick             鼠标点击某个对象时触发
>
> 2. onfocus           元素获得焦点时触发（鼠标移上并点击使其获得焦点、tab键、使其可以接受键盘输入）
>
> 3. onblur              元素失去焦点
>
> 4. onchange         用户改变域的内容
>
>    1. 点击下拉框触发事件：
>
>       ```javascript
>       <select onchange="func()>
>           <option value="0" >选项一</option>
>           <option value="1" >选项二</option>
>       </select>
>       
>       function func(){
>        //获取被选中的option标签
>        var vs = $('select  option:selected').val();
>       }
>       ```
>
> 5. onkeydown      某个键盘的键被按下
>
> 6. onkeyup           某个键盘的键被松开
>
> 7. onmouseover   鼠标移到某元素上（鼠标移上触发）
>
> 8. onmouseout     鼠标移出某元素
>
> 9. onload              用户进入页面时触发
>
> 10. onunload          用户离开页面触发
>
> ##### `DOM0`事件
>
> * 写法一
>
>   `document.getElementById("test").onclick(this);`
>
>   事件中的`this`指向注册事件的元素，即**注册该事件，this指向谁**。
>
> * 写法二：
>
>   `<input onclick="()">`
>
>   将事件作为属性放入标签内
>
> ##### `DOM2`事件
>
> * `DOM2`事件支持同一dom元素注册多个同种事件
>
> * `DOM2`新增捕获和冒泡的概念
>
> * `DOM2`事件通过`addEventListener`和`removeEventListener`进行管理。
>
>   * `addEventListener`有三个参数，分别是*事件名称*、*事件回调*、*捕获/冒泡*。
>
>     ```javascript
>     <button id="test">测试</button>
>     <script>
>     	window.onload = function(){
>     		document.getElementById("test").addEventListener("click",function(e){
>     			alert("zouqi")
>     		},false)
>     	}
>     </script>
>     ```
>
>     事件名称移除原有的on，比如`onclick`变为`click`；事件回调则是点击后执行的方法；最后一个值false表示冒泡，true表示捕获，默认是false。
>
>   * 冒泡是指内部元素先被触发，再触发外部元素
>
>   * 捕获是指外部元素先被触发，再触发内部元素
>
>     ```html
>     <div id="father" style="width: 150px;height: 150px;background-color: #0000FF;">
>     		<div id="son" style="width: 100px;height: 100px;background-color: #009688;">
>     			<div id="grandson" style="width: 50px;height: 50px;background-color: #00FF00;"></div>
>     		</div>
>     	</div>
>         <script>
>     		document.getElementById("father").addEventListener("mouseover",function(e){
>     			console.log("father")
>     		},true)
>     		document.getElementById("son").addEventListener("mouseover",function(e){
>     			console.log("son")
>     		},false)
>     		document.getElementById("grandson").addEventListener("mouseover",function(e){
>     			console.log("grandson")
>     		},true)
>     	</script>
>     ```
>
>   * `stopPropagation()`：阻止冒泡，阻止触发外部元素的事件。
>
>     ```javascript
>     document.getElementById("grandson").addEventListener("mouseover",function(e){
>     	e.stopPropagation()
>     	console.log("grandson")
>     },false)
>     ```
>
>   * IE8及以下使用`attachEvent(element,type,handle)`和`detachEvent`
>
> #### DOM树
>
> * 整个文档是一个文档节点 
> * 每个 HTML 标签是一个元素节点 
> * 包含在 HTML 元素中的文本是文本节点 
> * 每一个 HTML 属性是一个属性节点 
> * 注释属于注释节点 
>
> #### js改变html样式
>
> * `document.getElementById().style.property="新样式"`一次更改单个
> * `document.getElementById().style.cssTest="width:100px;height="50px"`一个更改多个
> * `document.getElementById().className="class1"`直接更改class
>
> #### 对象
>
> ##### `window.location`对象
>
> |   参数   |    解释    |                   例子                    |
> | :------: | :--------: | :---------------------------------------: |
> |   href   |  当前url   | http://localhost:8848/html/main/home.html |
> | protocol |    协议    |                   http:                   |
> |   host   | 域名+端口  |           http://localhost:8848           |
> | hostname |    域名    |           http://www.baidu.com            |
> |   port   |    端口    |                   8848                    |
> | pathname |  路径部分  |           /html/main/home.html            |
> |  search  | 请求的参数 |             ?username=123&...             |
>
> |            方法名            |                      作用                       |                             参数                             |
> | :--------------------------: | :---------------------------------------------: | :----------------------------------------------------------: |
> | location.reload(*bForceGet*) |                    刷新界面                     | **可选参数**，默认为false，从客户端缓存中取页面。如果为true，则通过GET方式，从服务端获取新的页面，相当于F5。 |
> |   location.replace(*URL*)    | 通过指定URL替换当前缓存在历史里（客户端）的项目 |                          指定的URL                           |
> |    location.assign(*URL*)    |               加载一个新的文档。                |                          指定的URL                           |
>
> ##### `window.localStorage`对象和`sessionStorage`对象
>
> 1. `localStorage`用于长久保存整个网站的数据，保存的数据没有过期时间，除非手动删除。它是==只读==的。
>
>    1. 保存数据
>
>       ```js
>       localStorage.setItem("key","value");
>       ```
>
>    2. 读取数据
>
>       ```js
>       var name = localStorage.getItem("key");
>       ```
>
>    3. 删除数据
>
>       ```js
>       localStorage.removeItem("key");
>       ```
>
> 2. `sessionStorage`只保存在当前会话，关闭标签页后删除
>
>    1. 保存数据
>
>       ```js
>       window.sessionStorage.setItem("key","value");
>       ```
>
>    2. 读取数据
>
>       ```js
>       window.sessionStorage.getItem("key");
>       ```
>
>    3. 删除数据
>
>       ```js
>       window.sessionStorage.removeItem("key");
>       ```
>
>    4. 清空数据
>
>       ```js
>       window.sessionStorage.clear();
>       ```
>
> #### JS查看对象中所有属性
>
> ```javascript
> var p = "";
> for(var i in vdata.content){
> 	p += i+";";
> }
> console.log(p);
> ```

### jQuery

> #### 概念
>
> * jQuery有比js更为强大的选择器体系，jQuery的选择器和css选择器保持一致。
> * jQuery筛选器是对特定的JQuery对象做进一步的选择。
> * jQuery的选择器比js选择器性能上有不少差距，jQuery的id选择器比class选择器快得多，如果要查询class可以使用`$("#id").find("class");$`
> * jQuery事件
>
> #### 语法
>
> * 基本语法：`$(选择器).操作`
> * 链式写法：`$(选择器).操作1.操作2`

### avalon

> #### 概念
>
> * avalon比较类似vue
>
> #### 总结
>
> 1. 绑定元素，不同于Vue的是它调用了`avaion.define`方法。
>
>    ```javascript
>    var indexVm = avalon.define({
>            //对应前端界面中 :controller中的值
>    	$id:"indexView",
>            //参数可直接放在这里
>    	searchForm:{
>    		name:"123",	
>    	}
>    })
>    ```
>
>    `ms-duplex`：双向绑定，可以简写为`:duplex`
>
>    ```html
>    <div :controller="indexView">
>    	<p>{{data.name}}</p>
>    	<input type="text" id="" :duplex="data.name" />
>    </div>
>    <script type="application/javascript">
>    	var indexVm = avalon.define({
>    		$id:"indexView",
>    		data:{
>    			name:"123"
>    		}
>    	})
>    </script>
>    ```
>
>    * 如果想全部写完，失去焦点后再更新，可以在`ms-duplex`后边加上`| change`
>
>      ```html
>      <input type="text" id="" :duplex="data.name | blur" />
>      ```
>
>    * 如果想计时刷新，可以加上`debounce(时间)`，参数是毫秒(ms)
>
>      ```html
>      <input type="text" id="" :duplex="data.name | debounce(10000)" />
>      ```
>
> 2. 循环：
>
>    ```html
>    <div :controller="indexView">
>    	<select :duplex="getName">
>            	<!--循环-->
>    		<option :for="name in names" :attr="{value:name}">{{name}}</option>
>    	</select>
>    </div>
>    <script type="application/javascript">
>    	var indexVm = avalon.define({
>    		$id:"indexView",
>    		names:["123","321","456","654"]
>    	})
>    </script>
>    ```
>
>    

### Ajax

### 请求方式

> #### 设置默认URL和SUCCESS函数
>
> ```js
> $.ajax({name:value,name:value, ......})
> ```
>
> ```js
> $.ajaxSetup({
> 	type: "POST",
> 	contentType: "application/json;charset=UTF-8",
> 	dataType: "json",
>         headers: {
> 		"token": !!window.sessionStorage["token"] ? window.sessionStorage["token"] : "no_token"
> 	}
> });
> ```

> #### option请求
>
> 1. 用于获取目的资源所支持的通信选项，用于请求服务器对于某些接口等资源的支持情况的，包括各种请求方法、头部的支持情况，仅作查询使用。
> 2. 特性
>    1. 没有请求体
>    2. 成功响应又响应体
>    3. 安全
>    4. 密等性，不变性，同一接口请求多少次都一样
>    5. 不能缓存
>    6. 不能在表单使用

### Json

#### JWT -> JSON WEB TOKEN

> #### 传统的SESSION
>
> * 服务器存储一份用户登录的信息，这份登录信息会在响应时传递给浏览器，告诉其保存为cookie,以便下次请求时发送给我们的应用。
> * ==问题==：通常而言session都是保存在内存中，而随着认证用户的增多，服务端的开销会明显增大。
>
> #### Token
>
> * 流程：
>   * 用户使用用户名密码来请求服务器
>   * 服务器进行验证用户的信息
>   * 服务器通过验证发送给用户一个token
>   * 客户端存储token，并在每次请求时附送上这个token值
>   * 服务端验证token值，并返回数据
> * 这个token必须要在每次请求时传递给服务端，它应该保存在请求头里， 另外，服务端要支持`CORS(跨来源资源共享)`策略，一般我们在服务端这么做就可以了`Access-Control-Allow-Origin: *`。
>
> #### JWT
>
> * JWT是由三段信息构成的，将这三段信息文本用`.`链接一起就构成了Jwt字符串
>
> * 构成
>
>   * 头部（header）
>
>     * 声明类型
>
>     * 声明加密的算法，通常直接使用`HS156`
>
>       ```json
>       {
>         'typ': 'JWT',
>         'alg': 'HS256'
>       }
>       ```
>
>     * 将头部信息进行base64加密，构成第一部分
>
>   * 载荷（payload）  ->  存放有效信息
>
>     * 标准中注册的声明
>       * iss：jwt签发者
>       
>       * sub：jwt所面向的用户
>       
>       * aud：接受jwt的一方
>       
>     * exp：jwt的过期时间
>       
>       * nbf：定义在什么时间之前，该jwt都是不可用的
>       
>       * iat：jwt的签发时间
>       
>       * jti：jwt的唯一身份表示，主要用来作为一次性token，从而回避重放攻击。
>       
>         **重放攻击**：指攻击者发送一个目的主机已接收过的包，来达到欺骗系统的目的，主要用于身份认证过程，破坏认证的正确性。
>     * 公共的声明：一般添加用户的相关信息或其他业务需要的必要信息，不建议添加敏感信息。
>     * 私有的声明：不建议存放敏感信息，因为base64是对称解密。
>   
>   * 签证（signature）
>   
>     * header（加密后）
>     * payload（加密后）
>     * secret
>   
>     该部分需要加密后的header和payload用`.`连接组成的字符串，然后通过header中声明的加密方式进行加盐`secret`组合加密。
>   
>     secret是保存在服务器端的，jwt的签发生成也是在服务器端，它是服务端的私钥。

#### Json-lib

#### Jackson

#### Gson

### bootstrap

### ExtJs

### AngularJS

### Vue

> #### EL挂载点
>
> ```javascript
> var vue = new Vue({
> 	el:"#hello",
> 	data:{
> 		message : "hello world"
> 	}
> })
> ```
>
> 其中el可以使用哪些方法获取页面元素呢？
>
> 1. id选择器（==建议==）
>
>    ```javascript
>    var vue = new Vue({
>        //使用idxuan'z
>    	el:"#hello",
>    	data:{
>    		message : "hello world"
>    	}
>    })
>    ```
>
> 2. class选择器
>
>    ```javascript
>    var vue = new Vue({
>    	el:".app",
>    	data:{
>    		message : "hello world"
>    	}
>    })
>    ```
>
> 3. 标签选择器，不能以body，html等
>
>    ```javascript
>    var vue = new Vue({
>    	el:"div",
>    	data:{
>    		message : "hello world"
>    	}
>    })
>    ```
>
> #### data属性
>
> ```javascript
> var vue = new Vue({
>  	el:"div",
> 	data:{
> 		message : "hello world",
> 		student: {
> 			name:"高中",
> 			address:"博爱"
> 		},
> 		campus:["北京","上海"]
> 	}
> })
> ```
>
> #### Vue指令
>
> #####  v-text：用于覆盖内容（全部替换，部分替换使用{{}}）
>
> ```html
> <div id="hello" class="app">
> 	<h2 v-text="message+'!'"></h2>
> 	{{message+"!"}}
> </div>
> ```
>
> ##### v-html：设置标签的innerHTML，类似于v-text，但是v-text不会解析html内容，v-html则会解析。
>
> ```html
> <div id="hello" class="app">
> 	<h2 v-text="message"></h2>
> 	<h2 v-html="message"></h2>
> </div>
> <script>
> var vue = new Vue({
>      el:"div",
>      data:{
>          message : "<p>123123</p>",
>      }
>  })
> </script>
> ```
>
> ##### v-on为元素绑定事件，绑定键盘事件时可以使用@keyup.键盘按钮。
>
> ```html
> <div id="div">
> 	<h1 v-text="message"></h1>
> 	<button v-on:click="click">v-变</button>
> 	<button @click="click">@变</button>
> </div>
> <script src="js/jquery_min_341.js"></script>
> <script src="js/vue.js"></script>
> <script src="js/Demo1.js"></script>
> <script>
> 	var vue = new Vue({
> 		el:"#div",
> 		data:{
> 			message:"hello"
> 		},
>      //定义方法
> 		methods:{
> 			click:function(){
> 				this.message="world";
> 			}
> 		}
> 	})
> </script>
> ```
>
> ##### 案例：计数器
>
> ```html
> <div id="div">
> 	<button @click="sub">-</button>
> 	<span v-text="num"></span>
> 	<button @click="add">+</button>
> </div>
> <script src="js/jquery_min_341.js"></script>
> <script src="js/vue.js"></script>
> <script src="js/Demo1.js"></script>
> <script>
> 	var vue = new Vue({
> 		el:"#div",
> 		data:{
> 			num:0
> 		},
> 		methods:{
> 			add:function(){
> 				if(this.num < 10){
> 					this.num++;
> 				}
> 			},
> 			sub:function(){
> 				if(this.num > 0){
> 					this.num --;
> 				}
> 			}
> 		}
> 	})
> </script>
> ```
>
> ##### v-show：设置内容是否可以显示，参数为Boolean参数，可以绑定vue中定义的变量，也可以跟表达式。它改变的是display的值。
>
> ```html
> <div id="div">
>  <!-- v-show改变了元素style中的display的属性 -->
> 	<h1 v-show="isShow">12312312</h1>
> 	<button @click="show">show</button>
> </div>
> <script src="js/jquery_min_341.js"></script>
> <script src="js/vue.js"></script>
> <script src="js/Demo1.js"></script>
> <script>
> 	var vue = new Vue({
> 		el:"#div",
> 		data:{
> 			isShow:false
> 		},
> 		methods:{
> 			show:function(){
> 				this.isShow = !this.isShow;
> 			}
> 		}
> 	})
> </script>
> ```
>
> ##### v-if：设置内容是否可以显示，参数为Boolean参数，可以绑定vue中定义的变量，也可以跟表达式。它改变的是DOM树。
>
> ```html
> <div id="div">
>  <!-- 直接将这个标签删除 -->
> 	<p v-if="isShow">123123123</p>
> 	<button @click="show">123123</button>
> </div>
> <script src="js/jquery_min_341.js"></script>
> <script src="js/vue.js"></script>
> <script src="js/Demo1.js"></script>
> <script>
> 	var vue = new Vue({
> 		el:"#div",
> 		data:{
> 			isShow:false
> 		},
> 		methods:{
> 			show:function(){
> 				this.isShow = !this.isShow;
> 			}
> 		}
> 	})
> </script>
> ```
>
> ##### 案例：实现图片切换（模拟）
>
> ```html
> <div id="title">
> 	<button @click="prev" v-show="index > 0">上一个</button>
> 	<p v-text="messageArr[index]"></p>
> 	<button @click="next" v-show="index < messageArr.length-1">下一个</button>
> </div>
> <script src="js/jquery_min_341.js"></script>
> <script src="js/vue.js"></script>
> <script src="js/Demo1.js"></script>
> <script>
> 		var vue = new Vue({
> 		el:"#title",
> 		data:{
> 		messageArr:[
> 				"111",
> 				"222",
> 				"333"
> 			],
> 			index:0
> 		},
> 		methods:{
> 			next:function(){
> 				this.index ++;
> 			},
> 			prev:function(){
> 				this.index --;
> 			}
> 		}
> 	})
> </script>
> ```
>
> ##### v-for：循环
>
> ```html
> <div id="title">
> 	<ul>
>      <!--循环生成列表，语法为(item,index) in 数组-->
> 		<li v-for="item in messageArr" v-text="item.name"></li>
> 	</ul>
> 	<button @click="add">添加</button>
> 	<button @click="del">删除</button>
> </div>
> <script src="js/jquery_min_341.js"></script>
> <script src="js/vue.js"></script>
> <script src="js/Demo1.js"></script>
> <script>
> 	var vue = new Vue({
> 		el:"#title",
> 		data:{
> 			messageArr:[
> 				{name:"Hello"},
> 				{name:"World"},
> 				{name:"!!!"}
> 			],
> 		},
> 		methods:{
> 			add:function(){
> 				this.messageArr.push({name:"gogogo"});
> 			},
> 			del:function(){
> 				this.messageArr.shift();
> 			}
> 		}
> 	})
> </script>
> ```
>
> ##### v-model：获取和设置表单元素的值（==双向绑定==，一方改变，另一方一起改变）
>
> ```html
> <div id="title">
> 	<h2 v-text="message"></h2>
> 	<input v-model="message" />
> </div>
> <script src="js/jquery_min_341.js"></script>
> <script src="js/vue.js"></script>
> <script src="js/Demo1.js"></script>
> <script>
> 	var vue = new Vue({
> 		el:"#title",
> 		data:{
> 			message:"666"
> 		},
> 	})
> </script>
> ```
>
> #### axios
>
> 本质就是ajax
>
> ```javascript
> document.querySelector(".get").onclick = function(){
>     //通过get或post方法进行发送请求，then方法中的回调函数会在请求成功或失败时触发，通过回调函数进行获取返回参数。
> 	axios.get("https://autumnfish.cn/api/joke/list?num=5")
> 	.then(function(response){
> 		console.log(response);
> 	},function(err){
> 		console.log(err)
> 	})
> }
> ```
>
> #### axios+vue
>
> ```html
> <div id="demo">
> 	<input type="button" value="获取" @click="getJoke" />
> 	<p>{{joke}}</p>
> </div>
> <script src="js/vue.js"></script>
> <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
> <script>
> 	var app = new Vue({
> 		el:"#demo",
> 		data:{
> 			joke: "笑话"
> 		}	,
> 		methods:{
> 			getJoke:function(){
> 				var that = this;
> 				axios.get("https://autumnfish.cn/api/joke")
> 				.then(function(response){
> 					that.joke = response.data;
> 				},function(err){
> 					console.log(err);
> 				})
> 			}
> 		}
> 	})
> </script>
> ```
>
> #### vue生命周期
>
> > ##### 1.
>
> #### 子父组件之间的通讯
>
> ##### 1.通过props向子组件通讯
>
> 1. 在子组件中props属性中放入参数
>
> 2. 在父组件中定义参数
>
> 3. 引用子组件中添加绑定 : `v-bind:props中参数的名字="父组件中的参数"`
>
>    ```javascript
>    <!--父组件-->
>    <add-user v-bind:dialog-form-visible="dialogFormVisible"></add-user>
>    <script>
>    	export default {
>            data() {
>                dialogFormVisible: false
>            }
>        }
>    </script>
>    
>    <!--子组件-->
>    <script>
>    	export default {
>            name: "addUser",
>            props: {
>                dialogFormVisible:{
>                    default:false,
>                    required:true
>                },
>            }
>        }
>    </script>
>    ```
>
> ##### 2.通过自定义事件向父组件发送消息($emit)
>
> 1. 在子组件中绑定方法跳转到vue方法中，在vue方法中使用this.$emit('父组件中绑定的事件名')
>
> 2. 父组件中子组件标签处绑定事件，再绑定的事件中触发父组件的方法
>
>    ```javascript
>    <!--子组件中绑定方法进入vue方法中-->
>    <el-button @click="closeThisWindows(this)" >取 消</el-button>
>    <script>
>    	methods:{
>            closeThisWindows(obj){
>                //使用vue中的this进行回调
>                this.$emit('closeAddUser');
>            }
>        }
>    </script>
>    <!--父组件中绑定方法-->
>    <add-user :dialog-form-visible="dialogFormVisible" @closeAddUser="closeAddUser"></add-user>
>    <script>
>    	methods:{
>            closeAddUser(){
>                //执行父组件中的方法
>            }
>        }
>    </script>
>    ```

### nodeJS

### LayUI

> #### 日期与时间选择
>
> ```javascript
> laydate.render{
>     elem:'id选择器',
>     value:'默认值，如果设置了format，则必须和format格式一样',
>     range:'开启范围选择，可以为true false 或其他连接字符，比如2020-2-1 ~ 2021-2-1',
>     type:'如果开启了range后可以使用type对范围类型进行一个划分，可以为年、月、日等'
> }
> ```
>
> 1. `lay.digit()`对日期进行格式化。

### echart

### Velocity

### Freemarker

### JSP

### 前后端分离

## 开发框架

### Spring

#### BeanFactory/IOC

#### 注解

> #### `@CrossOrigin(origins  ,maxAge)`注解
>
> * 跨域支持，Spring Framework 4.2 GA版本及之上版本支持这个注解。
>
> * 这个注解配合XXXMapping注解使用，比如：
>
>   ```java
>   @CrossOrigin 
>   @RequestMapping(
>   ```
>
> * 参数：
>
>   * `orgins`：允许可访问的域列表，如果全部的话可以使用`*`符号
>   * `maxAge`：准备响应前的缓存持续的最大时间，单位秒
>
> #### `@SuppressWarnings(values...)`注解
>
> * 注解目标为类、字段、函数、函数入参、构造函数和函数的局部变量，建议把注解放在最近进警告发生的位置。
>
> * 取消警告
>
>   ```java
>   Map<String, Object> pp = (Map<String, Object>)dao.queryForObject(sqlId+"getBmd", map, Map.class);//会出警告
>   ```
>
>   ```java
>   @SuppressWarnings("unchecked")
>   Map<String, Object> pp = (Map<String, Object>)dao.queryForObject(sqlId+"getBmd", map, Map.class);//不会出警告
>   ```
>
> * `@SuppressWarnings("unchecked")`抑制单类型的警告。
>
>   `@SuppressWarnings("unchecked","rawtypes")`抑制多类型的警告。
>
>   `@SuppressWarnings("all")`抑制所有类型的警告。

#### Spring上下文

#### Spring AOP

#### Spring DAO

#### Spring ORM

#### Spring Web

### Struts2

### SpringMVC

### SpringBoot

> 

### WebWork

### 安全框架

#### Shiro

#### Spring Security

> # SpringSecurity实现登录注册
>
> > ##  技术栈：
> >
> > * 后台：
> >   * [ SpringBoot ](https://docs.spring.io/spring-boot/docs/2.2.6.RELEASE/reference/htmlsingle/)
> >   * [SpringScurity](https://docs.spring.io/spring-security/site/docs/5.3.3.BUILD-SNAPSHOT/reference/html5/#authentication)
> >   * [MybatisPlus]([https://mp.baomidou.com/guide/#%E7%89%B9%E6%80%A7](https://mp.baomidou.com/guide/#特性))
> > * 数据库：
> >   * [Oracle11g](https://www.w3cschool.cn/oraclejc/)
> > * 前端：
> >   * [Freemarker](http://freemarker.foofun.cn/)
> >   * [LayUI](https://www.layui.com/doc/)
>
> ## 数据库搭建
>
> ```sql
> CREATE TABLE "SCOTT"."ADMIN"
>   (
>     "ID"       VARCHAR2(20 BYTE) NOT NULL ENABLE,
>     "USERNAME" VARCHAR2(20 BYTE) NOT NULL ENABLE,
>     "PASSWORD" VARCHAR2(255 CHAR) NOT NULL ENABLE,
>     CONSTRAINT "ID" PRIMARY KEY ("ID") USING INDEX PCTFREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645 PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT) TABLESPACE "USERS" ENABLE
>   )
>   SEGMENT CREATION IMMEDIATE PCTFREE 10 PCTUSED 40 INITRANS 1 MAXTRANS 255 NOCOMPRESS LOGGING STORAGE
>   (
>     INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645 PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1 BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT
>   )
>   TABLESPACE "USERS" ;
> COMMENT ON COLUMN "SCOTT"."ADMIN"."ID"
> IS
>   '主键';
>   COMMENT ON COLUMN "SCOTT"."ADMIN"."USERNAME"
> IS
>   '用户名';
>   COMMENT ON COLUMN "SCOTT"."ADMIN"."PASSWORD"
> IS
>   '密码';
> ```
>
> ![image-20200807090520656](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200807090520656.png)
>
> 使用SQL Developer创建表。
>
> ## 配置pom.xml文件
>
> 所有用到的jar包都通过maven导入。在引入ojdbc6中需要先下载ojdbc6，然后加入到本地maven仓库中。
>
> ```xml
> <dependencies>
>       <dependency>
>           <groupId>com.oracle</groupId>
>           <artifactId>ojdbc6</artifactId>
>           <version>11.2.0.3</version>
>       </dependency>
>       <dependency>
> 	    <groupId>org.springframework.boot</groupId>
> 	    <artifactId>spring-boot-starter-web</artifactId>
> 	</dependency>
>     <dependency>
>     	<groupId>org.springframework.boot</groupId>
>     	<artifactId>spring-boot-starter-freemarker</artifactId>
>     </dependency>
>       <dependency>
>           <groupId>org.springframework.boot</groupId>
>           <artifactId>spring-boot-starter-test</artifactId>
>       </dependency>
>       <dependency>
>           <groupId>com.baomidou</groupId>
>           <artifactId>mybatis-plus-boot-starter</artifactId>
>           <version>3.3.2</version>
>       </dependency>
>       <dependency>
>           <groupId>junit</groupId>
>           <artifactId>junit</artifactId>
>           <scope>test</scope>
>       </dependency>
>       <dependency>
>           <groupId>org.springframework.boot</groupId>
>           <artifactId>spring-boot-starter-security</artifactId>
>       </dependency>
>   </dependencies>
> ```
>
> ## 配置文件
>
> 在resources中创建application.properties文件
>
> ```properties
> server.port=8084
> 
> #配置freemarker
> spring.freemarker.prefix=/views/
> spring.freemarker.suffix=.html
> spring.freemarker.content-type=text/html
> spring.freemarker.charset=UTF-8
> spring.freemarker.cache=false
> spring.freemarker.template-loader-path=classpath:/templates
> 
> #配置静态资源
> spring.resources.static-locations=classpath:/static/,classpath:/templates/
> 
> #配置数据库
> spring.datasource.driver-class-name=oracle.jdbc.driver.OracleDriver
> spring.datasource.url=jdbc:oracle:thin:@localhost:1521:orcl
> spring.datasource.username=账号
> spring.datasource.password=密码
> ```
>
> ## 编写后台代码
>
> > ### 编写实体类
>
> 创建bean.Admin类
>
> ```java
> package com.gs.springbootdemo.bean;
> 
> public class Admin {
>     private Integer id;
>     private String username;
>     private String password;
> 
>     public void setId(Integer id) {
>         this.id = id;
>     }
> 
>     public void setUsername(String username) {
>         this.username = username;
>     }
> 
>     public void setPassword(String password) {
>         this.password = password;
>     }
> 
>     public Integer getId() {
>         return id;
>     }
> 
>     public String getUsername() {
>         return username;
>     }
> 
>     public String getPassword() {
>         return password;
>     }
> 
>     @Override
>     public String toString() {
>         return "Admin{" +
>                 "id=" + id +
>                 ", username='" + username + '\'' +
>                 ", password='" + password + '\'' +
>                 '}';
>     }
> }
> ```
>
> > ### 编写mapper
>
> 因为只有一张表，因此只需要一个mapper。由于使用的是MybatisPlus，因此不需要xml文件即可。
>
> **AdminMapper：**
>
> ```java
> package com.gs.springbootdemo.mapper;
> 
> import com.baomidou.mybatisplus.core.mapper.BaseMapper;
> import com.gs.springbootdemo.bean.Admin;
> import org.apache.ibatis.annotations.Mapper;
> 
> @Mapper
> public interface AdminMapper extends BaseMapper<Admin> {
> 	
> }
> ```
>
> > ### 编写service
>
> **AdminService**：
>
> ```java
> package com.gs.springbootdemo.service;
> 
> import com.baomidou.mybatisplus.core.conditions.Wrapper;
> import com.gs.springbootdemo.bean.Admin;
> 
> import java.util.List;
> 
> public interface AdminService {
>     public List<Admin> selectList(Wrapper<Admin> queryWrapper);
>     public boolean insert(Admin admin);
>     public Admin selectAdminByUsername(String username);
> }
> ```
>
> **AdminServiceImpl：**
>
> ```java
> package com.gs.springbootdemo.service;
> 
> import com.baomidou.mybatisplus.core.conditions.Wrapper;
> import com.baomidou.mybatisplus.core.conditions.query.QueryWrapper;
> import com.gs.springbootdemo.bean.Admin;
> import com.gs.springbootdemo.mapper.AdminMapper;
> import org.springframework.beans.factory.annotation.Autowired;
> import org.springframework.security.crypto.password.PasswordEncoder;
> import org.springframework.stereotype.Service;
> 
> import java.util.List;
> 
> /**
>  * @author GS
>  */
> @Service
> public class AdminServiceImpl implements AdminService{
> 
>     @Autowired
>     private AdminMapper adminMapper;
> 
>     @Autowired
>     private PasswordEncoder passwordEncoder;
> 
>     private final Integer INSERT_SUCCESS = 1;
>     @Override
>     public List<Admin> selectList(Wrapper<Admin> queryWrapper) {
>         return adminMapper.selectList(queryWrapper);
>     }
> 
>     @Override
>     public boolean insert(Admin admin) {	
>         admin.setPassword(passwordEncoder.encode(admin.getPassword()));
>         return adminMapper.insert(admin) == INSERT_SUCCESS;
>     }
> 
>     @Override
>     public Admin selectAdminByUsername(String username) {
>         QueryWrapper<Admin> wrapper = new QueryWrapper<>();
>         wrapper.eq("username",username);
>         return adminMapper.selectOne(wrapper);
>     }
> }
> ```
>
> **UserDetailsServiceImpl：**
>
> ```java
> package com.gs.springbootdemo.service;
> 
> import com.gs.springbootdemo.bean.Admin;
> import org.springframework.beans.factory.annotation.Autowired;
> import org.springframework.security.core.authority.SimpleGrantedAuthority;
> import org.springframework.security.core.userdetails.User;
> import org.springframework.security.core.userdetails.UserDetails;
> import org.springframework.security.core.userdetails.UserDetailsService;
> import org.springframework.security.core.userdetails.UsernameNotFoundException;
> import org.springframework.stereotype.Service;
> 
> import javax.servlet.http.HttpServletRequest;
> import java.util.ArrayList;
> import java.util.List;
> 
> @Service
> public class UserDetailsServiceImpl implements UserDetailsService {
>     @Autowired
>     private AdminService adminService;
>     @Autowired
>     private HttpServletRequest request;
> 
>     @Override
>     public UserDetails loadUserByUsername(String s) throws UsernameNotFoundException {
>         Admin admin = adminService.selectAdminByUsername(s);
>         if (admin == null){
>             throw new UsernameNotFoundException("用户名不存在");
>         }
>         //讲用户信息放入session中，以便登录认证
>         request.getSession().setAttribute("user",admin);
> 
>         //给用户授权，ROLE_USER表示是USER权限而不是ROLE_USER权限
>         List<SimpleGrantedAuthority> authorities = new ArrayList<>();
>         authorities.add(new SimpleGrantedAuthority("ROLE_USER"));
>         return new User(admin.getUsername(),admin.getPassword(),authorities);
>     }
> }
> ```
>
> > ### 编写Controller
>
> **AdminController：**
>
> ```java
> package com.gs.springbootdemo.controller;
> 
> import com.gs.springbootdemo.bean.Admin;
> import com.gs.springbootdemo.service.AdminService;
> import org.springframework.beans.factory.annotation.Autowired;
> import org.springframework.stereotype.Controller;
> import org.springframework.web.bind.annotation.PostMapping;
> 
> @Controller
> public class AdminController {
> 
> 	@Autowired
> 	private AdminService adminService;
> 
> 	@PostMapping("/doRegister")
> 	public String register(Admin admin) {
> 		if (adminService.insert(admin)){
> 			return "redirect:/toLogin";
> 		}else{
> 			return "redirect:/toRegister";
> 		}
> 	}
> }
> ```
>
> **JumpPageController：**
>
> ```java
> package com.gs.springbootdemo.controller;
> 
> import com.gs.springbootdemo.service.AdminService;
> import org.springframework.beans.factory.annotation.Autowired;
> import org.springframework.stereotype.Controller;
> import org.springframework.web.bind.annotation.GetMapping;
> 
> import javax.servlet.http.HttpServletRequest;
> 
> @Controller
> public class JumpPageController {
>     @Autowired
>     private AdminService adminService;
>     @GetMapping("/toLogin")
>     public String toLogin(){
>         return "login";
>     }
>     @GetMapping("/toRegister")
>     public String toRegister(HttpServletRequest request) {
>         request.setAttribute("adminSum",adminService.selectList(null).size()+1);
>         return "register";
>     }
>     @GetMapping("/toSuccess")
>     public String toSuccess(){
>         return "success";
>     }
> }
> ```
>
> #### 配置SpringSecurity
>
> ### SpringSecurity工作流程：
>
> ![img](https://upload-images.jianshu.io/upload_images/14483918-184b1c4eab5d2bcd.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)
>
> 创建Config.SecurityConfig
>
> ```java
> package com.gs.springbootdemo.config;
> 
> import com.gs.springbootdemo.service.UserDetailsServiceImpl;
> import org.springframework.context.annotation.Bean;
> import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
> import org.springframework.security.config.annotation.web.builders.HttpSecurity;
> import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
> import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
> import org.springframework.security.core.userdetails.UserDetailsService;
> import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;
> import org.springframework.security.crypto.password.PasswordEncoder;
> /**
>  * @author GS
>  */
> @EnableWebSecurity
> public class SecurityConfig extends WebSecurityConfigurerAdapter {
> 
>     /**
>      * 过滤登录注册界面，设置主页登录权限，配置自定义登录页
>      * **/
>     @Override
>     protected void configure(HttpSecurity http) throws Exception {
>         http.authorizeRequests()
>         .antMatchers("/toLogin","/toRegister","/login","/doRegister","/doLogin").permitAll()
>         .antMatchers("/layui/**").permitAll().and()
>         .formLogin().loginPage("/doLogin")
>         .failureUrl("/toLogin")
>         .defaultSuccessUrl("/toSuccess").permitAll().and()
>         .rememberMe().rememberMeParameter("记住我").and()
>         .logout().logoutSuccessUrl("/toLogin").permitAll().and()
>         .csrf().disable();
> 		//必须登录才能访问
>         http.authorizeRequests().antMatchers("/toSuccess").authenticated();
>     }
>     /**
>      * 设置密码加密方式
>      * **/
>     @Override
>     protected void configure(AuthenticationManagerBuilder auth) throws Exception {
>         auth.userDetailsService(customUserService()).passwordEncoder(new BCryptPasswordEncoder());
>     }
>     /**
>      * 自定义登录认证
>      * **/
>     @Bean
>     UserDetailsService customUserService(){
>         return new UserDetailsServiceImpl();
>     }
>     /**
>     *   密码加密，高版本的SpringSecurity强制加密
>     * */
>     @Bean
>     public PasswordEncoder passwordEncoder(){
>         return new BCryptPasswordEncoder();
>     }
> }
> ```
>
> #### 前端界面
>
> 在templates中创建views界面，在views界面中创建login.html，success.html和register.html。在views下放入LayUI相关文件。
>
> **login.html：**
>
> ```html
> <!DOCTYPE html>
> <html lang="en">
>     <head>
>         <meta charset="UTF-8">
>         <title>登录</title>
>         <link rel="stylesheet" href="views/layui/css/layui.css">
>         <style>
>             body{
>                 background-color: #f4f4f1;
>             }
>             .register{
>                 height: 100%;
>                 width: 190px;
>                 margin: 0 auto;
>                 overflow: hidden;
>                 padding-top: 15px;
>             }
>             .pictureMa{
>                 margin: 30px auto 0;
>                 width: 230px;
>                 height: 150px;
>             }
>             input{
>                 border-radius: 5px;
>             }
>             .title{
>                 text-align: center;
>             }
>             .a{
>                 text-align: center;
>             }
>         </style>
>     </head>
>     <body>
>         <form action="/doLogin" method="post" onsubmit="return checkUserMessage()">
>             <div class="layui-form-item">
>                 <div class="pictureMa">
>                     <img src="timg.jpg" width="230px" height="150px" >
>                 </div>
>                 <div class="title">
>                     <h1>进入饭堂，马上开饭！</h1>
>                 </div>
>                 <div class="register">
>                     <div class="layui-inline">
>                         <div class="layui-input-inline">
>                             <input type="tel" name="username" placeholder="账号" id="username" class="layui-input">
>                         </div>
>                     </div><br>
> 
>                     <div class="layui-inline">
>                         <div class="layui-input-inline">
>                             <input type="password" name="password" placeholder="密码" id="password" class="layui-input">
>                         </div>
>                     </div><br>
> 
>                     <div class="layui-inline">
>                         <label class="layui-form-label" ></label>
>                         <div class="layui-input-inline">
>                             <button type="submit" id="submitBtn" class="layui-btn layui-btn-fluid">芜湖，起飞！</button>
>                         </div>
>                     </div>
>                     <div class="layui-inline">
>                         <label class="layui-form-label" ></label>
>                         <div class="layui-input-inline a">
>                             <a href="/toRegister">我要注册成为食客</a>
>                         </div>
>                     </div>
> 
>                 </div>
>             </div>
>         </form>
>         <script type="text/javascript">
>             function checkUserMessage(){
>                 var username = $("#username").val();
>                 var password = $("#password").val();
>                 if(username == ""){
>                     alert("用户名不能为空");
>                     return false;
>                 }else if(password == ""){
>                     alert("密码不能为空");
>                     return false;
>                 }else if(password.length < 8 || password.length > 32 || password.match(/\d+/g) == null || password.match(/^.*[A-Z]+.*$/) == null || password.match(/^.*[a-z]+.*$/) == null){
>                     alert("密码格式错误");
>                     return false;
>                 }else{
>                     return true;
>                 }
>             }
>         </script>
>         <script type="text/javascript" src="views/layui/layui.all.js"></script>
>         <script type="text/javascript" src="views/layui/jquery_min_341.js"></script>
>     </body>
> </html>
> ```
>
> **register.html：**
>
> ```html
> <!DOCTYPEhtml>
> <html>
> 	<head>
> 		<metacharset="UTF-8">
> 		<title>立刻成为食客！</title>
> 		<link rel="stylesheet" href="views/layui/css/layui.css">
> 		<style>
> 			body{
> 				background-color: #f4f4f1;
> 			}
> 			.register{
> 				height: 100%;
> 				width: 190px;
> 				margin: 0 auto;
> 				overflow: hidden;
> 				padding-top: 15px;
> 			}
> 			.pictureMa{
> 				margin: 30px auto 0;
> 				width: 230px;
> 				height: 150px;
> 			}
> 			input{
> 				border-radius: 5px;
> 			}
> 			.title{
> 				text-align: center;
> 			}
> 			.a{
> 				text-align: center;
> 			}
> 		</style>
> 	</head>
> 	<body>
> 		<form action="doRegister" method="post" onsubmit="return checkUserMessage()">
> 			<div class="layui-form-item">
> 				<div class="pictureMa">
> 					<img src="timg.jpg" width="230px" height="150px" >
> 				</div>
> 				<div class="title">
> 					<h1>注册账号，成为食客！</h1>
> 				</div>
> 				<div class="register">
> 					<input hidden name="id" value="${adminSum }">
> 					<div class="layui-inline">
> 					  <div class="layui-input-inline">
> 						<input type="tel" name="username" placeholder="账号" id="username" class="layui-input">
> 					  </div>
> 					</div><br>
> 
> 					<div class="layui-inline">
> 					  <div class="layui-input-inline">
> 						<input type="password" name="password" placeholder="密码" id="password" class="layui-input">
> 					  </div>
> 					</div><br>
> 
> 					<div class="layui-inline">
> 					  <div class="layui-input-inline">
> 						<input type="password" name="confirmPassword" placeholder="确认密码" id="confirmPassword" class="layui-input">
> 					  </div>
> 					</div><br>
> 
> 					<div class="layui-inline">
> 						<label class="layui-form-label" ></label>
> 						<div class="layui-input-inline">
> 							<button type="submit" id="submitBtn" class="layui-btn layui-btn-fluid">芜湖，起飞！</button>
> 						</div>
> 					</div>
> 					<div class="layui-inline">
> 						<label class="layui-form-label" ></label>
> 						<div class="layui-input-inline a">
> 							<a href="/toLogin">我是食客，我要进饭堂</a>
> 						</div>
> 					</div>
> 
> 				</div>
>   			</div>
> 		</form>
> 		<script type="text/javascript">
> 			$("#submitBtn").bind("onfocus",function (){
> 				$("title").text("开饭");
> 			});
> 			function checkUserMessage(){
> 				var username = $("#username").val();
> 				var password = $("#password").val();
> 				var confirmPassword = $("#confirmPassword").val();
> 				if(username == ""){
> 					alert("用户名不能为空");
> 					return false;
> 				}else if(password == ""){
> 					alert("密码不能为空");
> 					return false;
> 				}else if(password.length < 8 || password.length > 32){
> 					alert("密码不能小于8位，不能大于32位");
> 					return false;
> 				}else if(password.match(/\d+/g) == null || password.match(/^.*[A-Z]+.*$/) == null || password.match(/^.*[a-z]+.*$/) == null){
> 					alert("密码必须包含大小写和数字");
> 					return false;
> 				}else if(confirmPassword == ""){
> 					alert("确认密码不能为空");
> 					return false;
> 				}else if(confirmPassword != password){
> 					alert("两次密码不一样");
> 					return false;
> 				}else{
> 					return true;
> 				}
> 			}
> 		</script>
> 		<script type="text/javascript" src="views/layui/layui.all.js"></script>
> 		<script type="text/javascript" src="views/layui/jquery_min_341.js"></script>
> 	</body>
> </html>
> ```
>
> **success.html：**
>
> ```html
> <!DOCTYPEhtml>
> <html>
> 	<head>
> 		<metacharset="UTF-8">
> 		<title>Insert title here</title>
> 		<link rel="stylesheet" href="views/layui/css/layui.css">
> 		<script type="text/javascript" src="views/layui/layui.all.js"></script>
> 	</head>
> 	<body>
> 		<script type="text/javascript">
> 		layui.use(['layer', 'form'], function(){
> 			  var layer = layui.layer
> 			  ,form = layui.form;
> 			  layer.msg('注册成功');
> 			});
> 		</script>
> 	</body>
> </html>
> ```
>
> 参考：
>
> https://www.jianshu.com/p/f6c4915adc23
>

### 工作流

### ORM框架

#### Spring Data

##### Spring Data JDBC

##### Spring Data JPA

##### Spring Data Mongodb

##### Spring Data Redis

##### Spring Data ElasticSearch

##### Spring Data Apache Solr

##### Spring Data Apache Hadoop

#### Hibernate

#### Mybatis

> #### 引入Mybatis
>
> 1. 使用maven，在pom.xml中加入依赖
>
>    ```xml
>    <!--mybatis依赖-->
>    <dependency>
>      <groupId>org.mybatis</groupId>
>      <artifactId>mybatis</artifactId>
>      <version>3.5.5</version>
>    </dependency>
>    <!--数据库驱动-->
>    <dependency>
>      <groupId>mysql</groupId>
>      <artifactId>mysql-connector-java</artifactId>
>      <version>5.1.46</version>
>    </dependency>
>    ```
>
> 2. 为防止资源导出失败，导致target文件夹中没有相应的mapper文件，需要在pom.xml中配置。
>
>    ```xml
>    <build>
>        <resources>
>          <resource>
>            <directory>src/main/resources</directory>
>            <includes>
>              <include>**/*.xml</include>
>            </includes>
>            <filtering>true</filtering>
>          </resource>
>          <resource>
>            <directory>src/main/java</directory>
>            <includes>
>              <include>**/*.xml</include>
>            </includes>
>            <filtering>true</filtering>
>          </resource>
>        </resources>
>    </build>
>    ```
>
> #### 配置Mybatis
>
> 1. 在resources文件下创建mybatisConfig.xml文件，在该文件中一下代码以连接数据库
>
>    ```xml
>    <?xml version="1.0" encoding="UTF-8" ?>
>    <!DOCTYPE configuration
>            PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
>            "http://mybatis.org/dtd/mybatis-3-config.dtd">
>    <configuration>
>        	<!--配置数据库-->
>            <environments default="development">
>                <environment id="development">
>                    <transactionManager type="JDBC"/>
>                    <dataSource type="POOLED">
>                        <property name="driver" value="com.mysql.jdbc.Driver"/>
>                        <property name="url" value="jdbc:mysql://localhost:3306/demo?useSSL=true&amp;useUnicode=true&amp;characterEncoding=UTF-8"/>
>                        <property name="username" value="root"/>
>                        <property name="password" value="root"/>
>                    </dataSource>
>                </environment>
>            </environments>
>        	<!--注册mapper，如果没有注册则会报BindingException-->
>     	<mappers>
>                <package name="com.gs.mapper"/>
>            </mappers>
>    </configuration>
>    ```
>
> #### 使用Mybatis编写简单Demo
>
> ```
> package com.gs.pojo;
> 
> public class User {
>     private Integer id;
>     private String username;
>     private String password;
> 
>     public Integer getId() {
>         return id;
>     }
> 
>     public void setId(Integer id) {
>         this.id = id;
>     }
> 
>     public String getUsername() {
>         return username;
>     }
> 
>     public void setUsername(String username) {
>         this.username = username;
>     }
> 
>     public String getPassword() {
>         return password;
>     }
> 
>     public void setPassword(String password) {
>         this.password = password;
>     }
> }
> ```
>
> 项目目录：
>
> ![image-20200723161137347](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200723161137347.png)
>
> #####   1.获取SqlSessionFactory对象实例
>
> * 每个Mybatis程序都以一个SqlSessionFactory实例为核心，因此首先需要获取SqlSessionFactory实例。
>
>   ```java
>   public class MybatisUtils {
>       private static SqlSessionFactory sqlSessionFactory;
>       static{
>           //第一步、获取mybatis配置文件
>           String resource = "mybatisConfig.xml";
>           //第二步、读入流内
>           InputStream inputStream = null;
>           try {
>               inputStream = Resources.getResourceAsStream(resource);
>           } catch (IOException e) {
>               e.printStackTrace();
>           }
>           //第三步、获取SqlSessionFactory实例
>            sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
>       }
>   }
>   ```
>
> #####   2.获取SqlSession对象实例
>
> * 通过SqlSessionFactory中的openSession()方法可以获取到SqlSession的实例。
>
>   ```java
>   public static SqlSession getsqlSession(){
>       return sqlSessionFactory.openSession();
>   }
>   ```
>
> #####   3.实体类编写，mapper(dao)层编写
>
> * 根据数据库编写出实体类
>
>   ```java
>   package com.gs.pojo;
>   
>   public class User {
>       private Integer id;
>       private String username;
>       private String password;
>   
>       public Integer getId() {
>           return id;
>       }
>   
>       public void setId(Integer id) {
>           this.id = id;
>       }
>   
>       public String getUsername() {
>           return username;
>       }
>   
>       public void setUsername(String username) {
>           this.username = username;
>       }
>   
>       public String getPassword() {
>           return password;
>       }
>   
>       public void setPassword(String password) {
>           this.password = password;
>       }
>       @Override
>       public String toString() {
>           return "User{" +
>                   "id=" + id +
>                   ", username='" + username + '\'' +
>                   ", password='" + password + '\'' +
>                   '}';
>       }
>   }
>   ```
>
> * mapper层中需要一个接口和一个xml文件，它俩所处的项目结构必须相同，并且mapper中不同的标签对应不同的操作。
>
>   ```xml
>   <!DOCTYPE mapper
>           PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
>           "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
>   <!--namespace映射mapper中的接口-->
>   <mapper namespace="com.gs.mapper.UserMapper">
>       <!--id对应接口中的方法，如果方法有参数，则继续在后边加上parameterType参数，返回集加上resultType参数-->
>       <select id="getAllUser" resultType="com.gs.pojo.User">
>           select * from user ;
>       </select>
>   </mapper>
>   ```
>
> #####   4.使用junit进行测试
>
> * 引入junit依赖
>
>   ```xml
>   <dependency>
>     <groupId>junit</groupId>
>     <artifactId>junit</artifactId>
>     <version>4.11</version>
>     <scope>test</scope>
>   </dependency>
>   ```
>
> * 测试类的编写分为四步：
>
>   1. 获取SqlSession实例；
>   2. 通过反射获取mapper对象；
>   3. 调用方法，执行sql操作；
>   4. 关闭SqlSession。
>
>   ```java
>   package com.gs.mapper;
>   
>   import com.gs.pojo.User;
>   import com.gs.utils.MybatisUtils;
>   import org.apache.ibatis.session.SqlSession;
>   import org.junit.Test;
>   
>   import java.util.List;
>   
>   public class UserMapperTest {
>       @Test
>       public void getAllUser(){
>           //第一步、获取SqlSession实例
>           SqlSession sqlSession = MybatisUtils.getsqlSession();
>           //第二步、通过反射获取mapper对象
>           UserMapper userMapper = sqlSession.getMapper(UserMapper.class);
>           //第三步、执行sql操作
>           List<User> allUser = userMapper.getAllUser();
>           for (User user:allUser) {
>               System.out.println(user.toString());
>           }
>           //第四步、关闭sqlSession
>           sqlSession.close();
>       }
>   }
>   ```
>
>   运行该方法，成功！
>
>   ![image-20200723161108340](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200723161108340.png)
>
> #### CRUD
>
> #### 注意
>
> 1. `#{}`和` ${}`得区别：
>
>    `#{}`中的参数会被自动解析为带引号格式，而`${}`则是不加引号的形式，因此`#{}`可以很好的防止sql注入。
>
> #### 调用存储过程
>
> ```xml
> <!--配置参数-->
> <parameterMap type="参数类型" id="参数id">
>     	<parameter property="属性名" mode="IN | OUT" jdbcType=""></parameter>
> </parameterMap>
> <insert id="sql语句id" parameterMap="参数id" statementType="CALLABLE">
> 	call xxx.xxx(?,?);
> </insert>
> ```
>
> * 其中`statementType`参数
>   * 标记操作SQL的对象
>   * 参数：
>     1. `STATEMENT`：直接操作sql，不进行预编译
>     2. `PREPARED`：预处理，参数，进行预编译
>     3. `CALLABLE`：执行存储过程

### 消息中间件(MQ)

#### RocketMQ

#### RabbitMQ

#### ActiveMQ

#### Redis

#### Kafka

#### ZeroMQ

### 计算框架

#### Storm

#### JStorm

#### Spark Streaming

#### Flink

### 任务调度框架

#### Job

##### Quartz

##### ElasticJob

#### Trigger

#### schedule

### RPC框架

#### Hessian

#### Apache Thrift

## 分布式服务框架

### Spring Cloud

### Dubbo

### Zookeeper

### WebService

#### Xfire

#### Axis2

#### CXF

### SOA

### RESTful

### Eureka

### zuul

## 相关技术

### nginx

>  

### Jenkins

#### 持续集成

> 

## IDE/

## 工具

### 项目管理

#### Maven

#### Gradle

> Gradle基于Groovy语言，在Ant和Maven基础上，弥补了它们的不足。
>
> #### 配置Build.gradle
>
> 1. 引入依赖
>
>    * testCompile：jar包的作用域，表示在测试的时候起作用
>    * group：jar包分组
>    * name：jar包名称
>    * version：jar包的版本
>    * respositories：仓库的位置，该配置表示先从本地仓库查找jar包，如果没有再从maven中央仓库查找下载
>    * mavenCentral()：maven中央仓库
>    * mavenLocal()：本地仓库
>
>    ```groovy
>    plugins {
>        /*java文件*/
>        id 'java'
>        /*打war包，变成web项目*/
>        id 'war'
>    }
>    repositories {
>        mavenLocal()
>        mavenCentral()
>    }
>    
>    dependencies{
>        testCompile group: 'junit', name: 'junit', version: '4.12'
>        /*引入子项目的jar包*/
>        compile project('GrandleDemo01Son01')
>    }
>    ```
>
> #### 配置setting.gradle
>
> * 引入子项目
> * 子项目中的build.gradle如果有和父项目中相同的模块，则可以直接删掉
>
> ```groovy
> /*父项目*/
> rootProject.name = 'GradleDemo01'
> /*子项目*/
> include 'GradleDemo01Son01'
> ```
>
> #### Groovy语法
>
> * 类似javascript
>
> #### Groovy闭包
>
> ```groovy
> /*定义闭包*/
> def b1 = {
>     print("123")
> }
> /*定义方法*/
> def method1(Closure closure){
>     /*执行闭包*/
>     closure()
> }
> /*调用方法*/
> method1 (b1);
> ```
>
> 定义参数的闭包
>
> ```groovy
> def b2 = {
>     /*闭包中的参数*/
>     v ->
>         print(v);
>         print("${v}");
> }
> 
> def method2(Closure closure){
>     /*闭包传参*/
>     closure(123)
> }
> 
> method2 (b2);
> ```
>
> 

#### Ant

#### Buck

#### Bazel

#### OSGL