# JavaSE

## 基本速查

命名规范:

|     类型      |  命名方式   |
| :-----------: | :---------: |
|     包名      |  xxxyyyzzz  |
|  类名,接口名  |  XxxYyyZzz  |
| 变量名,方法名 |  xxxYyyZzz  |
|    常量名     | XXX_YYY_ZZZ |

 

### IDEA常用快捷键

|           说明            |      快捷键      |
| :-----------------------: | :--------------: |
|         删除一行          |      Ctrl+Y      |
|      向下复制当前行       |      Ctrl+D      |
|      上下移动当前行       |   Alt+Shift+↑↓   |
|       代码自动生成        |     Alt+Ins      |
| 代码包裹（surround with） |    Ctrl+Alt+T    |
|      英文大小写转化       |   Ctrl+Shift+U   |
|         查找替换          |      Ctrl+R      |
|         批量修改          |     shift+F6     |
|          查找类           |      Ctrl+N      |
|         查找文件          |   Ctrl+Shift+N   |
|         代码提示          |  Ctrl+Space改<   |
|       方法参数提示        |      Ctrl+P      |
|       文档注释查看        |      Ctrl+Q      |
|     类的层次结构查看      |      Ctrl+H      |
|  查看当前类所有方法属性   | Ctrl+F12或Alt+7  |
|         重写方法          |      Ctrl+O      |
|         继承方法          |      Ctrl+I      |
|     切换窗口（文件）      | Ctrl+Tab或Alt+←→ |

### JDK

- JDK = JRE + 开发工具集（例如Javac编译工具等）
-  JRE = JVM + Java SE标准类库

JDK中包含主要包如下：

1. `java.lang`----包含一些Java语言的核心类，如String、Math、Integer、 System和 Thread，提供常用功能
2. `java.net`----包含执行与网络相关的操作的类和接口
3. `java.io` ----包含能提供多种输入/输出功能的类
4. `java.util`----包含一些实用工具类，如定义系统特性、接口的集合框架类、使用与日 期日历相关的函数
5. `java.text`----包含了一些java格式化相关的类
6. `java.sql`----包含了java进行JDBC数据库编程的相关类/接口
7.  `java.awt`----包含了构成抽象窗口工具集（abstract window toolkits）的多个类，这 些类被用来构建和管理应用程序的图形用户界面(GUI)。

> 只有java.lang包下类引用不需要import



### Scanner类

> 控制台输入不同类型的变量

实现步骤：

1. 导包: import java.until.Scanner;

2. Scanner的实例化: Scanner scan = new Scanner(System.in);

3. 调用Scanner类的相关方法,来获取 指定类型 的变量
4. char类型获取Scanner没有相关方法,只能获取一个字符串
5. 获取字符串某个位置字符char getChar = getString.charAt(0);

```java
import java.util.Scanner;

class ScannerTest {
    public static void main(String[] args) {

        //输入整数
        Scanner scan = new Scanner(System.in);
        int num = scan.nextInt();
        System.out.println(num);
        //输入单个字符
        String getString = scan.next();
        char getChar = getString.charAt(0);
        System.out.println(getChar);
    }
}
```

### 随机数获取

```java
//math.random()获得一个double型的随机数,其范围为 [0.0,1.0)
double value = Math.random();
//需要其他类型就转换
int valueInt = (int) value;
```

### 时间(秒)获取

```java
//获取当前时间距离1970-01-01 00:00:00的毫秒数
long time = System.currentTimeMillis();
```



### 单元测试

选择默认的JUnit4

两个jar包：`junit-4.12.jar` + `hamcrest-core-1.3.jar`

要求：

1. 当前类是public的
2. 当前类提供公共的无参构造器
3. import org.junit.Test



### Object类

1. Object类是所有Java类的根父类

2. 如果在类的声明中未使用extends关键字指明其父类，则默认父类为java.lang.Object类

3. Object类中的功能(属性、方法)就具有通用性。
   属性：无

|    方法     |                             作用                             |
| :---------: | :----------------------------------------------------------: |
| toString()  |                             输出                             |
| getClass()  |                          获取当前类                          |
|  equals()   |                         比较是否相等                         |
| hashCode()  |                          计算哈希值                          |
|   clone()   |                          复制一个类                          |
| finalize()  |                    垃圾回收释放对象前xxx                     |
|   wait()    |      使得调用的线程进入阻塞状态，<br />并释放同步监视器      |
|  notify()   | 唤醒被wait的一个线程<br />如果有多个线程被wait，就唤醒优先级高的那个 |
| notifyAll() |                     唤醒所有被wait的线程                     |

> `wait()`,`notify()`,`notifyAll()`见`线程通信`
>
> `hashCode()`见`集合Set接口`

#### equals()

`==` 和 `equals()` 区别

- == ：运算符
  1. 可以使用在基本数据类型变量和引用数据类型变量中
  2. 如果比较的是`基本数据类型变量`：比较两个变量保存的`数据是否相等`。（不一定类型要相同）
     如果比较的是`引用数据类型变量`：比较两个对象的`地址值是否相同`。即`两个引用是否指向同一个对象实体`
     补充： `== 符号使用时，必须保证符号左右两边的变量类型一致`。

- equals()方法的使用：

1. 是一个方法，而非运算符

2. `只能`适用于`引用数据类型`

3. Object类中equals()的定义：
   
	```java
	public boolean equals(Object obj) {
   	return (this == obj);
   }
   ```
   
   说明：`Object类中定义的equals()和==的作用是相同的`：比较两个对象的地址值是否相同。即两个引用是否指向同一个对象实体
   
4. 像`String、Date、File、包装类等`都`重写`了Object类中的equals()方法。重写以后，比较的不是两个引用的地址是否相同，而是比较两个对象的"`实体内容`"是否相同。
   
5. 通常情况下，我们自定义的类如果使用equals()的话，也通常是比较两个对象的"实体内容"是否相同。那么，我们就需要`对Object类中的equals()进行重写`。
   `重写的原则`：`比较两个对象的实体内容是否相同`。

#### toString()

1. 当我们`输出`一个对象的引用时，实际上就是调用当前对象的`toString()`

2. Object类中toString()的定义：
   
     ```java
    public String toString() {
      	return getClass().getName() + "@" + Integer.toHexString(hashCode());
    }

3. 像String、Date、File、包装类等都`重写`了Object类中的toString()方法。使得在调用对象的toString()时，返回"`实体内容`"信息
   
4. 自定义类也可以重写toString()方法，当调用此方法时，返回对象的"实体内容"

### System类

- System类代表系统，系统级的很多属性和控制方法都放置在该类的内部，该类位于java.lang包
- 由于该类的构造器是private的，所以无法创建该类的对象，也就是无法实例化该类。其内部的成员变量和成员方法都是static的，所以也可以很方便的进行调用。

#### 属性

System类内部包含`in`、`out`和`err`三个成员变量，分别代表`标准输入流 (键盘输入)`，`标准输出流(控制台/显示器输出)`和`标准错误输出流(显示器)`

#### 方法

- `native long currentTimeMillis()`：

  该方法的作用是返回当前的计算机时间，时间的表达格式为当前计算机时间和GMT时间(格林威治时间)1970年1月1号0时0分0秒所差的毫秒数。

- `void exit(int status)`：

  该方法的作用是退出程序。其中status的值为0代表正常退出，非零代表异常退出。使用该方法可以在图形界面编程中实现程序的退出功能等

-  `void gc()`：

  该方法的作用是请求系统进行垃圾回收。至于系统是否立刻回收，则 取决于系统中垃圾回收算法的实现以及系统执行时的情况

- `String getProperty(String key)`：

  该方法的作用是获得系统中属性名为key的属性对应的值。系统中常见 的属性名以及属性的作用如下表所示：

  |    属性名    |      属性说明      |
  | :----------: | :----------------: |
  | java.version | Java运行时环境版本 |
  |  java.home   |    Java安装目录    |
  |   os.name    |   操作系统的名称   |
  |  os.version  |   操作系统的版本   |
  |  user.name   |   用户的账户名称   |
  |  user.home   |   用户的 主目录    |
  |   user.dir   | 用户的当前工作目录 |

  

### 字符集

- `ASCII`：美国标准信息交换码。用`一个字节`的`7位`可以表示。

  被其他编码兼容，意味着其中的字符仍用一个字节表示，节省空间

- `ISO8859-1`：拉丁码表。欧洲码表用`一个字节`的`8位`表示。

- `GB2312`：中国的中文编码表。`最多两个字节`编码所有字符

- `GBK`：中国的中文编码表`升级`，融合了`更多`的中文文字符号。`最多两个字节`编码

- `Unicode`：国际标准码，融合了目前人类使用的所有字符。为每个字符分配唯一的字符码。所有的文字都用`两个字节`来表示。(**不够用，不能区分Unicode和ASCII**)

- UTF-8：变长的编码方式，可用`1-4个字节`来表示一个字符。8代表每次8个位传输数据

> **Unicode**只是定义了一个庞大的、全球通用的字符集，并为每个字符规定了唯 一确定的编号，具体存储成什么样的字节流，取决于字符编码方案。推荐的 Unicode编码是UTF-8和UTF-16
>
> 从 unicode 到 uft-8 并不是直接的对应，而是要过一些算法和规则来转换（即 **Uncidoe 字符集≠UTF-8 编码方式**）
>
> ![](https://cdn.jsdelivr.net/gh/6hqt9/TyporaNotes/img/202210211134911.png)

### 字符串编码改变

> 编码：String --> byte[]:调用String的`getBytes(String charsetName)`
> 解码：byte[] --> String:调用String的构造器`String str = new String(byte bytes[], String charsetName);`

```java
@Test
public void test3() throws UnsupportedEncodingException {
    String str1 = "abc123中国";
    byte[] bytes = str1.getBytes();//使用默认的字符集，进行编码。//abc123是ASCII,中国是utf-8,三位一个字
    System.out.println(Arrays.toString(bytes));
    byte[] gbks = str1.getBytes("gbk");//使用gbk字符集进行编码。
    System.out.println(Arrays.toString(gbks));
    System.out.println("******************");
    String str2 = new String(bytes);//使用默认的字符集，进行解码。
    System.out.println(str2);
    String str3 = new String(gbks);
    System.out.println(str3);//出现乱码。原因：编码集和解码集不一致！
    String str4 = new String(gbks, "gbk");
    System.out.println(str4);//没有出现乱码。原因：编码集和解码集一致！
}
```

> `编码`：字符串 -->字节  (看得懂 --->看不懂的二进制数据)
> `解码`：编码的逆过程，字节 --> 字符串 （看不懂的二进制数据 ---> 看得懂）
> 说明：解码时，要求解码使用的字符集必须与编码时使用的字符集一致，否则会出现乱码。
>
> `getBytes()和String构造器都有重载，有多个，上面仅参考`

### 异常

`Error`:Java虚拟机无法解决的严重问题。如：JVM系统内部错误、资源耗尽等严重情况。比如：StackOverflowError和OOM。

1. 栈溢出：`java.lang.StackOverflowError`
2. 堆溢出：`java.lang.OutOfMemoryError`

> 异常体系结构

`java.lang.Throwable`

- `java.lang.Error`:一般不编写针对性的代码进行处理。
- `java.lang.Exception`:可以进行异常的处理
  - 编译时异常(checked)
    - `IOException`
      - `FileNotFoundException`
    - `ClassNotFoundException`
  - 运行时异常(unchecked,RuntimeException)
    - `NullPointerException`
    - `ArrayIndexOutOfBoundsException`
    - `ClassCastException`
    - `NumberFormatException`
    - `InputMismatchException`
    - `ArithmeticException`

> 异常的处理：`抓抛模型`

- "抛"：程序在正常执行的过程中，一旦出现异常，就会在异常代码处`生成一个对应异常类的对象`。并`此对象抛出`。一旦抛出对象以后，`其后的代码就不再执行`。
  关于异常对象的产生：
  1. 系统`自动生成`的异常对象
  2. `手动的生成`一个异常对象，并`抛出(throw)`
- "抓"：可以理解为异常的`处理方式`：
  1. `try-catch-finally`
  2. `throws`



> `try-catch-finally`

- 编译时异常要处理(try,catch)才能不报错,运行时异常可以不处理也不报错
- throw可以看作:在这个语句的地方,发成了错误(手动调用)
- 发成异常时`运行顺序`: `try{...异常(后面不执行)} --> catch(){} -->finally{}`
  `finally优先于try,catch中的return和throw`执行,`若有return或throw,会在执行完finally后再回头执行`
- `return和throw从语句流转来看是等效的`

```java
try{
	//可能出现异常的代码
}catch(异常类型1 变量名1){
	//处理异常的方式1
}catch(异常类型2 变量名2){
	//处理异常的方式2
}catch(异常类型3 变量名3){
	//处理异常的方式3
}
....
finally{
	//一定会执行的代码
}
```

说明：
1. finally是可选的。
2. 使用try将可能出现异常代码包装起来，在执行过程中，一旦出现异常，就会生成一个对应异常类的对象，根据此对象的类型，去catch中进行匹配
3. 一旦try中的异常对象匹配到某一个catch时，就进入catch中进行异常的处理。一旦处理完成，就跳出当前的try-catch结构（在没有写finally的情况）。`继续执行其后的代码`
4. catch中的异常类型如果没有子父类关系，则谁声明在上，谁声明在下无所谓。
   catch中的异常类型如果满足子父类关系，则要求子类一定声明在父类的上面。否则，报错
5. 常用的异常对象处理的方式： ① `String getMessage()`获取异常信息    ② `printStackTrace()`打印堆栈信息(`较常用`)
6. 在try结构中声明的变量，在出了try结构以后，就不能再被调用
6. try-catch-finally结构可以嵌套

体会1：使用try-catch-finally处理编译时异常，使得程序在编译时就不再报错，但是运行时仍可能报错。
 相当于我们使用try-catch-finally将一个编译时可能出现的异常，延迟到运行时出现。
体会2：开发中，由于运行时异常比较常见，所以我们通常就不针对运行时异常编写try-catch-finally了。
  针对于编译时异常，我们说一定要考虑异常的处理。

> `throws`

1. "`throws + 异常类型`"写在`方法的声明处`。指明此方法执行时，可能会抛出的异常类型。
    一旦当方法体执行时，出现异常，仍会在异常代码处生成一个异常类的对象，此对象`满足throws后异常类型`时，就会`被抛出`。异常代码后续的代码，就`不再执行` ！
2. 体会：`try-catch-finally`:真正的`将异常给处理掉了`。
       `throws`的方式只是`将异常抛给了方法的调用者`。  并没有真正将异常处理掉。
3. 开发中如何选择使用try-catch-finally 还是使用throws？
    - 如果父类中被重写的方法`没有`throws方式处理异常，则子类重写的方法也`不能`使用throws
       意味着`如果子类重写的方法中有异常，必须使用try-catch-finally方式处理`。
  - 执行的方法a中，先后又调用了另外的几个方法，这几个方法是`递进关系执行`的。我们建议这几个方法使用`throws`的方式进行处理。而执行的方法a可以考虑使用`try-catch-finally`方式进行处理。

> 方法重写的异常

- `子类`重写的方法`抛出`的异常类型`不大于父类`被重写的方法`抛出`的异常类型
- `多态性`:因为用`子类对象去应用形参要求为父类`的`方法`时,实际调用的是`子类重写的方法`,若比父类的大,比catch的大,catch不住，如要Object给String，String抛出异常就要比Object小（子类）

> `自定义异常`

1. `继承`于现有的异常结构：RuntimeException 、Exception
2. `提供全局常量`：serialVersionUID
3. `提供重载的构造器`

```java
//自定义异常类
public class MyException extends Exception {

    static final long serialVersionUID = -7034897193246939L;

    public MyException() {

    }

    public MyException(String msg) {
        super(msg);
    }
}
//使用自定义异常类
class Student {

    private int id;

    public void regist(int id) throws Exception {
        if (id > 0) {
            this.id = id;
        } else {
//            System.out.println("您输入的数据非法！");
            //手动抛出异常对象
//            throw new RuntimeException("您输入的数据非法！");
//            throw new Exception("您输入的数据非法！");
            throw new MyException("不能输入负数");
//            错误的
//			throw new String("不能输入负数");
        }

    }
    @Override
    public String toString() {
        return "Student [id=" + id + "]";
    }
}
//测试
class StudentTest {

    public static void main(String[] args) {
        try {
            Student s = new Student();
            s.regist(-1001);
            System.out.println(s);
        } catch (Exception e) {
//			e.printStackTrace();
            System.out.println(e.getMessage());
        }
    }

}
```



## 数据类型

```
一.基本数据类型
    1.数值型:
      ①整数: byte  short  int  long
      ②浮点:float  double
    2.字符型:char
    3.布尔型:boolean
二.引用数据类型
    1.类:class   字符串在这里
    2.接口:interface
    3.数组:array[]
    

            |实例变量(不以static修饰)
    丨成员变量
    丨      |类变量(以static修饰)
变量--
    丨      丨形参(方法,构造器中定义的变量)
    丨局部变量--方法局部变量(在方法内定义)
            丨代码块局部变量(在代码块内定义)
```

### 基本数据类型

> 1字节=8bit位

| 变量名  |  类型  | 大小  |         范围         | 默认初始值  |              备注              |
| ------- | :----: | :---: | :------------------: | :---------: | :----------------------------: |
| byte    |  整型  | 1字节 |      -128 ~ 127      |      0      |                                |
| short   |  整型  | 2字节 |   -2^15 ~ 2^15 - 1   |      0      |                                |
| int     |  整型  | 4字节 |   -2^31 ~ 2^31 - 1   |      0      |         `整型默认类型`         |
| long    |  整型  | 8字节 |   -2^63 ~ 2^63 - 1   |      0      |           以l/L结尾            |
| float   | 浮点型 | 4字节 |  -3.403E38~3.403E38  |     0.0     |         必须以f/F结尾          |
| double  | 浮点型 | 8字节 | -1.798E308~1.798E308 |     0.0     |        `浮点型默认类型`        |
| char    | 字符型 | 2字节 |                      | 0或`\u0000` | 有且仅有一个字符，要用`''`包裹 |
| boolean | 布尔型 | 1字节 |                      |    false    |                                |

> float（余127码）：1符号位+8指数位+23尾数位
>
> double（余1023码）：1符号位+11指数位+52尾数位
>
> `基本数据类型赋值传递的是数值`



### 引用数据类型

实际上就是各种实现类

Java

> 默认初始值`null`，引用数据类型的值只为`null`或`地址值（变量类型@地址）`
>
> `引用数据类型赋值传递的是地址`



#### Array数组

分一维数组和多维数组，多维数组实质为一维数组的元素也为数组

- 数组在存储多个数据方面的特点：
  - 一旦初始化以后，其`长度就确定`了
  - 数组一旦定义好，其`元素的类型`也就`确定`了。我们也就只能操作指定类型的数据了
- 数组在存储多个数据方面的缺点：
  - 一旦初始化以后，其长度就`不可修改`
  - 数组中提供的`方法非常有限`，对于添加、删除、插入数据等操作，非常不便，同时效率不高
  - 获取数组中实际元素的个数的需求，数组没有现成的属性或方法可用
  - 数组存储数据的`特点`：`有序`、`可重复`。对于无序、不可重复的需求，不能满足



##### 定义

`[]` 既可以`int[] array=new int[]{xxxxx}`,也可以`int array[]=new int[x]`

`[][]`可以是`int[][] arr1=new int[][]{xxxxx}`,也可以是`int[x] arr1[y]`,也可以是`int arr1[x][]`

> `[]`代表一维数组，`[][]`代表二维数组，`int`只作示例，可为其他，`xy`代表数组长度
>
> 特别的`int[] x, y[];` 意思是定义一个一维数组x,二维数组y
>
> `array2=array1` 相当于把array1的各个元素地址赋给array2



##### 方法

`java.util.Arrays`:操作数组的工具类  里面定义了很多操作数组的方法



1. `boolean equals(int[]a,int[]b ...)`判断两个数组是否相等

   ```java
   boolean isEquals = Arrays.equals(arr1, arr2);

2. `String toString(int[] a ...)`输出数组信息

   ```java
   System.out.println(Arrays.toString(arr1));


  3. `void sort(int[] a)` 对数组进行排序，从左往右由小到大

     ```java
     Arrays.sort(arr2);

  4. `int binarySearch(int[] a,int key)`二分法找,要先排序,返回的是[]里的角标,如果返回的是负数,就是没找到

     ```java
     Arrays.sort(arr3);
     int index1 = Arrays.binarySearch(arr3, 648);
     ```

5. `void fill(int[] a,int val)` 将指定值填充到数组之中

   ```java
   Arrays.fill(arr1, 10);//arr1里面元素全变10
   System.out.println(Arrays.toString(arr1));
   ```



#### 字符串

> `String`、`StringBuffer`、`StringBuilder`三者的`异同`

- String: `不可变`的字符序列；底层使用char[]存储
- StringBuffer: `可变`的字符序列；线程安全的，`效率低`；底层使用char[]存储
- StringBuilder: `可变`的字符序列；jdk5.0新增的，线程`不安全`的，`效率高`；底层使用char[]存储

三者的效率：从高到低排列：StringBuilder > StringBuffer > String

> 源码分析：

```java
String str = new String();//char[] value = new char[0];
String str1 = new String("abc");//char[] value = new char[]{'a','b','c'};
StringBuffer sb1 = new StringBuffer();//char[] value = new char[16];底层创建了一个长度是16的数组。
System.out.println(sb1.length());//
sb1.append('a');//value[0] = 'a';
sb1.append('b');//value[1] = 'b';
StringBuffer sb2 = new StringBuffer("abc");//char[] value = new char["abc".length() + 16];
```

- 问题1. System.out.println(sb2.length());//3

- 问题2. `扩容问题`:如果要添加的数据底层数组盛不下了，那就需要扩容底层的数组。`默认情况`下，扩容为`原来容量的2倍 + 2`，同时将原有数组中的元素`复制`到新的数组中。如果扩容还不够，就用需要的大小直接作为容量。

- `指导意义`：如果经常变，建议使用`StringBuffer(int capacity)`或`StringBuilder(int capacity)`。capacity为容量，为避免扩容，提高效率，提前设置。

  



##### String

> `String`的`特性`

`String`:字符串，使用一对`""`引起来表示。

1. String声明为`final`的，`不可被继承`
2. String实现了`Serializable`接口：表示字符串是`支持序列化`的。
           实现了`Comparable`接口：表示String`可以比较大小`
3. String内部定义了`final char[] value`用于`存储字符串数据`
4. String:代表`不可变的字符序列`。简称:`不可变性`。
   体现：
   - 当对字符串`重新赋值`时，需要`重写指定内存区域赋值`，不能使用原有的value进行赋值。
   - 当对现有的字符串进行`连接操作`时，也需要`重新指定内存区域赋值`，不能使用原有的value进行赋值。
   - 用String的replace()方法`修改指定字符或字符串`时，也需要`重新指定内存区域赋值`，不能使用原有的value进行赋值。
5. 通过`字面量`的方式（区别于new）给一个字符串赋值，此时的字符串值声明在`字符串常量池`中
6. `字符串常量池`中是`不会存储相同内容的字符串`的

###### 构造器

- 方式一：通过`字面量定义`的方式

  通过字面量定义的方式：String声明在方法区中的字符串常量池中

- 方式二：通过`new + 构造器`的方式

  通过new + 构造器的方式：数据在堆空间中开辟空间以后对应的地址值
  
  1. new String("xxx")
  
  2. new String(char value[])
  
  3. new String(char value[], int offset, int count)
  
  3. new String(byte bytes[], int offset, int length)
  
     > offset：初始偏移，即从第几位开始
     > count：从初始偏移开始读几位字符

```java
@Test
public void test2() {
    //通过字面量定义的方式：此时的s1和s2的数据javaEE声明在方法区中的字符串常量池中。
    String s1 = "javaEE";
    String s2 = "javaEE";
    //通过new + 构造器的方式:此时的s3和s4保存的地址值，是数据在堆空间中开辟空间以后对应的地址值。
    String s3 = new String("javaEE");
    String s4 = new String("javaEE");
    System.out.println(s1 == s2);//true
    System.out.println(s1 == s3);//false
    System.out.println(s1 == s4);//false
    System.out.println(s3 == s4);//false
    System.out.println("***********************");
    Person p1 = new Person("Tom", 12);
    Person p2 = new Person("Tom", 12);
    System.out.println(p1.name.equals(p2.name));
    //true，euqals()比较值
    System.out.println(p1.name == p2.name);
    //true，Tom都是通过字面量方式定义，先在常量池生成，然后地址值赋给堆空间中p1，p2的属性
    p1.name = "Jerry";
    System.out.println(p2.name);//Tom
}
```

面试题：String s = new String("abc");方式创建对象，在内存中创建了几个对象？
            `两个`:一个是`堆空间中new结构`，另一个是char[]对应的`常量池中的数据`："abc"

> `String`的`拼接`

结论：

1. `常量与常量`的拼接结果在`常量池`。且常量池中不会存在相同内容的常量。
2. `只要其中有一个是变量`，结果就在`堆`中。
3. 如果拼接的结果调用`intern()`方法，返回值就在`常量池`中

```java
@Test
public void test4() {
    String s1 = "javaEEhadoop";
    String s2 = "javaEE";
    String s3 = s2 + "hadoop";
    System.out.println(s1 == s3);//false
    final String s4 = "javaEE";//s4:加final后变成常量
    String s5 = s4 + "hadoop";
    System.out.println(s1 == s5);//true
    String s6 = "javaEE" + "hadoop";
    System.out.println(s1 == s6);//true
    String s7 = s3.intern();//返回值得到的s8使用的常量值中已经存在的“javaEEhadoop”
    System.out.println(s1 == s7);//true
}
```

###### 常用方法

|                             方法                             |                             作用                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
|                         int length()                         |                       返回字符串的长度                       |
|                    char charAt(int index)                    |                      返回某索引处的字符                      |
|                      boolean isEmpty()                       |                      判断是否是空字符串                      |
|                     String toLowerCase()                     |                将String中的所有字符转换为小写                |
|                     String toUpperCase()                     |                将String中的所有字符转换为大写                |
|                        String trim()                         |         返回字符串的副本<br />忽略前导空白和尾部空白         |
|                  boolean equals(Object obj)                  |                   比较字符串的内容是否相同                   |
|        boolean equalsIgnoreCase(String anotherString)        |                 与equals方法类似，忽略大小写                 |
|                  String concat(String str)                   |      将指定字符串连接到此字符串的结尾<br />等价于用“+”       |
|             int compareTo(String anotherString)              |               一个个字符的比较两个字符串的大小               |
|               String substring(int beginIndex)               |                  从beginIndex开始截取到最后                  |
|        String substring(int beginIndex, int endIndex)        |         从beginIndex(包含)开始截取到endIndex(不包含)         |
|               boolean endsWith(String suffix)                |               测试此字符串是否以指定的后缀结束               |
|              boolean startsWith(String prefix)               |               测试此字符串是否以指定的前缀开始               |
|        boolean startsWith(String prefix, int toffset)        | 测试此字符串从指定索引开始的<br />子字符串是否以指定前缀开始 |
|              boolean contains(CharSequence s)：              |     当且仅当此字符串包含指定的 char 值序列时，返回 true      |
|                   int indexOf(String str)                    |              返回指定子字符串第一次出现处的索引              |
|            int indexOf(String str, int fromIndex)            |      从指定的索引开始，<br />子字符串第一次出现处的索引      |
|                 int lastIndexOf(String str)                  |                 子字符串在最右边出现处的索引                 |
|          int lastIndexOf(String str, int fromIndex)          | 从指定的索引开始反向搜索，<br />子字符串最后一次出现处的索引 |
|          String replace(char oldChar, char newChar)          |    用newChar替换此字符串中出现的所有oldChar得到新的字符串    |
| String replace(CharSequence target, CharSequence replacement) | 使用指定的字面值替换序列替换此字符串所有匹配字面值目标序列的子字符串 |
|     String replaceAll(String regex, String replacement)      | 使用给定的 replacement 替换此字符串所有匹配给定的正则表达式的子字符串 |
|    String replaceFirst(String regex, String replacement)     | 使用给定的 replacement 替换此字符串匹配给定的正则表达式的第一个子字符串 |
|                boolean matches(String regex)                 |             测试此字符串是否匹配给定的正则表达式             |
|                 String[] split(String regex)                 |             根据给定正则表达式的匹配拆分此字符串             |
|           String[] split(String regex, int limit)            | 根据匹配给定的正则表达式来拆分此字符串，不超过limit个，如果超过了，剩下的都放到最后一个元素中 |



##### StringBuffer&StringBuilder

- StringBuffer: `可变`的字符序列；线程安全的，`效率低`；底层使用char[]存储
- StringBuilder: `可变`的字符序列；jdk5.0新增的，线程`不安全`的，`效率高`；底层使用char[]存储

|                         方法                         |                作用                |
| :--------------------------------------------------: | :--------------------------------: |
|               StringBuffer append(xxx)               |         用于进行字符串拼接         |
|        StringBuffer delete(int start,int end)        |         删除指定位置的内容         |
| StringBuffer replace(int start, int end, String str) |     把[start,end)位置替换为str     |
|         StringBuffer insert(int offset, xxx)         |         在指定位置插入xxx          |
|                StringBuffer reverse()                |         把当前字符序列逆转         |
|            public int indexOf(String str)            |  返回指定子字符串第一次出现的索引  |
|      public String substring(int start,int end)      | 从start(包含)开始截取到end(不包含) |
|                 public int length()                  |          返回字符串的长度          |
|              public char charAt(int n)               |         返回某索引处的字符         |
|        public void setCharAt(int n ,char ch)         |         把n处的字符换为ch          |



#### 时间

时间相关类除system类获取毫秒数外，JDK8以前与JDK8以后分别各有三个常用类，互相对应

|         功能         |    JDK8以前类    |             JDK8以后类              |
| :------------------: | :--------------: | :---------------------------------: |
|      获取毫秒数      |       Date       |               Instant               |
|     获取各种时间     |     Calendar     | LocalDateTime、LocalDate、LocalTime |
| 时间格式及字符串转化 | SimpleDateFormat |          DateTimeFormatter          |



##### System类

```java
//获取当前时间距离1970-01-01 00:00:00的毫秒数
long time = System.currentTimeMillis();
```



##### JDK8之前

###### Date

分两个Date类，为子父类关系

- `java.util.Date`类
  - `java.sql.Date`类

> `java.util.Date`类

Date定义

- 构造器一：Date()：创建一个对应当前时间的Date对象
- 构造器二：Date(long date): 创建指定毫秒数的Date对象

Date方法

- `toString()`:显示当前的`年、月、日、时、分、秒`,如`Tue Aug 30 19:16:10 GMT+08:00 2022`
- `getTime()`:获取当前Date对象对应的毫秒数。（时间戳）

> `java.sql.Date`类

java.sql.Date定义

要注意导包是否正确，如果已经使用过java.util.Date，则需要按下面方式定义，即上面的构造器二（`只剩这一个没过时`）

`java.sql.Date date3 = new java.sql.Date(35235325345L);`

java.sql.Date方法

- toString():显示`年、月、日`,如`1971-02-13`
- getTime():获取当前Date对象对应的毫秒数（意义不大）

> java.util.Date对象转换为java.sql.Date对象

- 方式一

  ```Java
  Date date = new java.sql.Date(2343243242323L);
  java.sql.Date sqlDate = (java.sql.Date) date;
  ```

- `方式二`

  ```Java
  Date date = new Date();
  java.sql.Date sqlDate = new java.sql.Date(date.getTime());
  ```

  

```java
@Test
public void test2() {
    //构造器一：Date()：创建一个对应当前时间的Date对象
    Date date1 = new Date();
    System.out.println(date1.toString());//Sat Feb 16 16:35:31 GMT+08:00 2019
    System.out.println(date1.getTime());//1645804166928
    //构造器二：创建指定毫秒数的Date对象
    Date date2 = new Date(155030620410L);
    System.out.println(date2.toString());
    //创建java.sql.Date对象
    java.sql.Date date3 = new java.sql.Date(35235325345L);
    System.out.println(date3);//1971-02-13
    //如何将java.util.Date对象转换为java.sql.Date对象
    //情况一：
    //Date date4 = new java.sql.Date(2343243242323L);
    //java.sql.Date date5 = (java.sql.Date) date4;
    //情况二：
    Date date6 = new Date();
    java.sql.Date date7 = new java.sql.Date(date6.getTime());
}
```



###### SimpleDateFormat

SimpleDateFormat的使用：`SimpleDateFormat`对日期`Date类`的`格式化`和`解析`

**构造器**

|      构造器      |                             示例                             |
| :--------------: | :----------------------------------------------------------: |
|   默认的构造器   |        SimpleDateFormat sdf = new SimpleDateFormat();        |
| 调用带参的构造器 | SimpleDateFormat sdf1 = new SimpleDateFormat("yyyy-MM-dd hh:mm:ss"); |

- 默认日期格式：`19-12-18 上午11:43`
- 常用日期格式：`yyyy-MM-dd hh:mm:ss`、`yyyy-MM-dd`

> 字符串`必须`是`符合`SimpleDateFormat识别的`格式`(通过构造器参数体现)

**方法**

- `格式化`：`日期` --->`字符串`  `SimpleDateFormat.format(date)`
- `解析`：格式化的`逆过程`，`字符串` ---> `日期`  `SimpleDateFormat.parse(日期格式字符串)`

> 例：字符串"2020-09-08"转换为java.sql.Date

```java
@Test
public void testExer() throws ParseException {
    String birth = "2020-09-08";
    SimpleDateFormat sdf1 = new SimpleDateFormat("yyyy-MM-dd");
    Date date = sdf1.parse(birth);
    java.sql.Date birthDate = new java.sql.Date(date.getTime());
    System.out.println(birthDate);
}
```



###### Calendar(抽象类)

实例化

- 方式一：创建其`子类`（`GregorianCalendar`）的对象
- 方式二：调用其`静态方法getInstance()`

常用方法

|          方法           |         作用          |
| :---------------------: | :-------------------: |
|        int get()        |       获取时间        |
|       void set()        |    设置(修改)时间     |
|       void add()        | 增加是正数,减少是负数 |
|     Date getTime()      |    日历类---> Date    |
| void setTime(Date date) |   Date ---> 日历类    |

时间获取

| 时间 |                     参数                     |
| :--: | :------------------------------------------: |
|  年  |         calendar.get(Calendar.YEAR)          |
|  月  |    calendar.get(Calendar.MONTH)实际月份-1    |
|  日  |     calendar.get(Calendar.DAY_OF_MONTH)      |
| 星期 | calendar.get(Calendar.DAY_OF_WEEK)周日1周六7 |



##### java.time JDK8之后

###### LocalDateTime

时间相关三个重要类：`LocalDate`、`LocalTime`、`LocalDateTime`

- `LocalDateTime`相较于LocalDate、LocalTime，使用频率要高
- 类似于Calendar

|                             方法                             |                     作用                     |
| :----------------------------------------------------------: | :------------------------------------------: |
|               static XXX `now()`/(ZoneId zone)               | 获取当前的日期、时间、日期+时间（`实例化`）  |
| static XXX `of`(int year, int month, int dayOfMonth, int hour, int minute, int second) | 设置指定的年、月、日、时、分、秒。没有偏移量 |
|                        int getYear()                         |                    获取年                    |
|                       Month getMonth()                       |                获取月（单词）                |
|                     int getMonthValue()                      |                获取月（数字）                |
|                      int getDayOfYear()                      |                获取一年第几天                |
|                     int getDayOfMonth()                      |                获取一月第几天                |
|                   DayOfWeek getDayOfWeek()                   |               获取星期（单词）               |
|                          getHour()                           |                    获取时                    |
|                       int getMinute()                        |                    获取分                    |
|                       int getSecond()                        |                    获取秒                    |
|                       XXX withxxx(xxx)                       |           修改时间，用对应对象接收           |
|                       XXX plusxxx(xxx)                       |                 添加xxx时间                  |
|                      XXX minusxxx(xxx)                       |                 减去xxx时间                  |

> `XXX`对应`LocalDate`、`LocalTime`、`LocalDateTime`

```java
@Test
public void test1() {
    //now():获取当前的日期、时间、日期+时间
    LocalDate localDate = LocalDate.now();//2022-09-03
    LocalTime localTime = LocalTime.now();//15:40:33.967
    LocalDateTime localDateTime = LocalDateTime.now();//2022-09-03T15:40:33.967
    System.out.println(localDate);
    System.out.println(localTime);
    System.out.println(localDateTime);
    //of():设置指定的年、月、日、时、分、秒。没有偏移量
    LocalDateTime localDateTime1 = LocalDateTime.of(2020, 10, 6, 13, 23, 43);
    System.out.println(localDateTime1);
    //getXxx()：获取相关的属性
    System.out.println(localDateTime.getDayOfMonth());
    System.out.println(localDateTime.getDayOfWeek());
    System.out.println(localDateTime.getMonth());
    System.out.println(localDateTime.getMonthValue());
    System.out.println(localDateTime.getMinute());
    //体现不可变性
    //withXxx():设置相关的属性
    LocalDate localDate1 = localDate.withDayOfMonth(22);
    System.out.println(localDate);
    System.out.println(localDate1);
    LocalDateTime localDateTime2 = localDateTime.withHour(4);
    System.out.println(localDateTime);
    System.out.println(localDateTime2);
    //不可变性
    LocalDateTime localDateTime3 = localDateTime.plusMonths(3);//加:plus
    System.out.println(localDateTime);
    System.out.println(localDateTime3);
    LocalDateTime localDateTime4 = localDateTime.minusDays(6);//减:minus
    System.out.println(localDateTime);
    System.out.println(localDateTime4);
}
```



###### Instant

类似于 java.util.Date类

|                       方法                       |                             作用                             |
| :----------------------------------------------: | :----------------------------------------------------------: |
|               static Instant now()               |                 获取本初子午线对应的标准时间                 |
|               long toEpochMilli()                | 获取自1970年1月1日0时0分0秒(UTC)开始毫秒数<br />相当于Date类的getTime() |
|          static Instant ofEpochMilli()           | 通过给定的毫秒数，获取Instant实例<br />相当于Date(long millis) |
| OffsetDateTime atOffset<br />(ZoneOffset offset) |                       添加时间的偏移量                       |

```java
@Test
public void test2() {
    //now():获取本初子午线对应的标准时间
    Instant instant = Instant.now();
    System.out.println(instant);//2019-02-18T07:29:41.719Z
    //添加时间的偏移量
    OffsetDateTime offsetDateTime = instant.atOffset(ZoneOffset.ofHours(8));
    System.out.println(offsetDateTime);//2019-02-18T15:32:50.611+08:00
    //toEpochMilli():获取自1970年1月1日0时0分0秒（UTC）开始的毫秒数  ---> Date类的getTime()
    long milli = instant.toEpochMilli();
    System.out.println(milli);
      long milli1 = System.currentTimeMillis();
      System.out.println(milli1);
    //ofEpochMilli():通过给定的毫秒数，获取Instant实例  -->Date(long millis)
    Instant instant1 = Instant.ofEpochMilli(1550475314878L);
    System.out.println(instant1);
}
```



###### DateTimeFormatter

类似于SimpleDateFormat

- 方式一：预定义的标准格式。如：ISO_LOCAL_DATE_TIME；ISO_LOCAL_DATE；ISO_LOCAL_TIME

  ```Java
   DateTimeFormatter formatter = DateTimeFormatter.ISO_LOCAL_DATE_TIME;
   //格式化:日期-->字符串
   LocalDateTime localDateTime = LocalDateTime.now();
   String str1 = formatter.format(localDateTime);
   System.out.println(localDateTime);
   System.out.println(str1);//2019-02-18T15:42:18.797
   //解析：字符串 -->日期
   TemporalAccessor parse = formatter.parse("2019-02-18T15:42:18.797");
   System.out.println(parse);
  ```

- 方式二：本地化相关的格式

  - 如：`ofLocalizedDateTime()`

    FormatStyle.LONG / FormatStyle.MEDIUM / FormatStyle.SHORT：适用于`LocalDateTime`

  - 如：`ofLocalizedDate()`
    FormatStyle.FULL / FormatStyle.LONG / FormatStyle.MEDIUM / FormatStyle.SHORT : 适用于`LocalDate`

  ```Java
  DateTimeFormatter formatter1 = DateTimeFormatter.ofLocalizedDateTime(FormatStyle.LONG);
  //格式化
  String str2 = formatter1.format(localDateTime);
  System.out.println(str2);//2019年2月18日 下午03时47分16秒
  DateTimeFormatter formatter2 = DateTimeFormatter.ofLocalizedDate(FormatStyle.MEDIUM);
  //格式化
  String str3 = formatter2.format(LocalDate.now());
  System.out.println(str3);//2019-2-18
  ```

- 方式三：自定义的格式。如：ofPattern(“yyyy-MM-dd hh:mm:ss”)

  ```java
  DateTimeFormatter formatter3 = DateTimeFormatter.ofPattern("yyyy-MM-dd hh:mm:ss");
  //格式化
  String str4 = formatter3.format(LocalDateTime.now());
  System.out.println(str4);//2019-02-18 03:52:09
  //解析
  TemporalAccessor accessor = formatter3.parse("2019-02-18 03:52:09");
  System.out.println(accessor);
  ```



#### Math类

java.lang.Math提供了一系列`静态方法`用于科学计算。其方法的`参数`和`返回值`类型一般为`double`型

|             方法/属性             |               作用/意义               |
| :-------------------------------: | :-----------------------------------: |
|                 E                 |                自然数                 |
|                PI                 |                圆周率                 |
| sin()cos()tan()asin()acos()atan() |               三角函数                |
|               abs()               |                绝对值                 |
|              sqrt()               |                平方根                 |
|      pow(double a,double b)       |               a的b次幂                |
|           log(),log10()           |          自然对数，10底对数           |
|      max(double a,double b)       |               a,b取其大               |
|      min(double a,double b)       |               a,b取其小               |
|             random()              |    double型随机数,范围为 [0.0,1.0)    |
|       long round(double a)        | double型数据a转换为long型（四舍五入） |
|     toDegrees(double angrad)      |              弧度转角度               |
|     toRadians(double angdeg)      |              角度转弧度               |

##### BigInteger

BigInteger可以表示不可变的任意精度的整数。BigInteger 提供所有Java 的基本整数操作符的对应物，并提供 java.lang.Math 的所有相关方法。另外，BigInteger还提供以下运算：模算术、GCD 计算、质数测试、素数生成、位操作以及一些其他操作。

###### 构造器

`BigInteger(String val)`：根据字符串构建BigInteger对象

###### 常用方法

|                      方法                       |           作用           |
| :---------------------------------------------: | :----------------------: |
|             public BigInteger abs()             |    BigInteger的绝对值    |
|         BigInteger add(BigInteger val)          |     BigInteger + val     |
|       BigInteger subtract(BigInteger val)       |     BigInteger - val     |
|       BigInteger multiply(BigInteger val)       |     BigInteger × val     |
|        BigInteger divide(BigInteger val)        |  BigInteger ÷ val，取整  |
|      BigInteger remainder(BigInteger val)       |  BigInteger ÷ val，取余  |
| BigInteger[] divideAndRemainder(BigInteger val) |    上面两个结果数组存    |
|          BigInteger pow(int exponent)           | BigInteger的exponent次方 |



##### BigDecimal

- 一般的Float类和Double类可以用来做科学计算或工程计算，但在商业计算中，要求`数字精度比较高`，故用到java.math.BigDecimal类。 
- BigDecimal类支持不可变的、任意精度的有符号十进制定点数。

###### 构造器

- `public BigDecimal(double val)`
- ``public BigDecimal(String val)`

###### 常用方法

|                             方法                             | 作用 |
| :----------------------------------------------------------: | :--: |
|           public BigDecimal add(BigDecimal augend)           |  加  |
|      public BigDecimal subtract(BigDecimal subtrahend)       |  减  |
|     public BigDecimal multiply(BigDecimal multiplicand)      |  乘  |
| public BigDecimal divide(BigDecimal divisor, int scale, int roundingMode) |  除  |

> `scale`是保留小数位数，`roundingMode`是四舍五入
>
> 如：`System.out.println(bd1.divide(bd2, 15, BigDecimal.ROUND_HALF_UP))`意思是四舍五入保留15位小数



### 包装类(Wrapper)

5.0 后有`自动装箱`与`自动拆箱`功能,`包装类`就是`基本数据`，`基本数据`就是`包装类`,会`自动转换`,可以`任意用`

| 基本数据类型 |  包装类   |  父类  |
| :----------: | :-------: | :----: |
|     byte     |   Byte    | Number |
|    short     |   Short   | Number |
|     int      |  Integer  | Number |
|     long     |   Long    | Number |
|    float     |   Float   | Number |
|    double    |  Double   | Number |
|   boolean    |  Boolean  |        |
|     char     | Character |        |

> Integer内部定义了IntegerCache结构（内部类），IntegerCache中定义了`Integer[]`,保存了从`-128~127`范围的整数。如果我们使用自动装箱的方式，给Integer赋值的范围在`-128~127`范围内时，可以`直接使用数组中的元素`，`不用再去new`了。目的：`提高效率`

包装类的使用:

1. java提供了8种基本数据类型对应的包装类，使得基本数据类型的变量具有类的特征
2. 掌握的：`基本数据类型、包装类、String三者之间的相互转换`

- `基本数据类型`-->`包装类`

  ```java
  //调用包装类的构造器
  int num1 = 10;
  Integer in1 = new Integer(num1);
  Integer in2 = new Integer("123");
  //报异常
  //Integer in3 = new Integer("123abc");
  //System.out.println(in3.toString());//必须是纯粹的数才行
  Float f1 = new Float(12.3);
  Float f2 = new Float("12.3");
  System.out.println(f1);
  System.out.println(f2);
  Boolean b1 = new Boolean(true);
  Boolean b2 = new Boolean("TrUe");//忽略大小写和true一样就行
  System.out.println(b2);
  Boolean b3 = new Boolean("true123");
  System.out.println(b3);//false	和true不一样(忽略大小写)就是false
  ```

- `包装类`-->`基本数据类型`

  ```java
  //调用包装类Xxx的xxxValue()
  Integer in1 = new Integer(12);
  int i1 = in1.intValue();
  System.out.println(i1 + 1);
  Float f1 = new Float(12.3);
  float f2 = f1.floatValue();
  ```

  

### 数据类型转换

1. 自动类型提升

当容量小的数据类型变量与容量大的数据类型变量做运算时,结果自动提升为容量大的数据类型(容量指表示数的范围大小)
(比较运算符也会自动提升)
byte/char/short --> int --> long --> float --> double
`byte,char,short 做运算时,结果为int型`

> 例如 int+long=long

2. 强制类型转换

自动类型提升的逆运算

- 需要使用强转符:()
- 可能导致精度损失

> 例如 int i1=（int)double型



> 基本数据类型、包装类--->String类型：调用String重载的`valueOf(Xxx xxx)`
>
> String类型 --->基本数据类型、包装类：调用包装类的`parseXxx(String s)`

```java
@Test
public void test() {
    int num1 = 10;
    //方式1：连接运算
    String str1 = num1 + "";
    //方式2：调用String的valueOf(Xxx xxx)
    float f1 = 12.3f;
    String str2 = String.valueOf(f1);//"12.3"
    Double d1 = new Double(12.4);
    String str3 = String.valueOf(d1);
    System.out.println(str2);
    System.out.println(str3);//"12.4"
}

@Test
public void test() {
    String str1 = "123";
    //错误的情况：
	 //int num1 = (int)str1;
	 //Integer in1 = (Integer)str1;
    //可能会报NumberFormatException
    int num2 = Integer.parseInt(str1);
    System.out.println(num2 + 1);
    String str2 = "true1";
    boolean b1 = Boolean.parseBoolean(str2);//非true即false
    System.out.println(b1);
}
```



> String --> char[]:调用String的`toCharArray()`
>
> char[] --> String:调用String的构造器`String str = new String(char value[]);`

```java
@Test
public void test2() {
    String str1 = "abc123";  //题目： a21cb3
    char[] charArray = str1.toCharArray();
    for (int i = 0; i < charArray.length; i++) {
        System.out.println(charArray[i]);
    }
    char[] arr = new char[]{'h', 'e', 'l', 'l', 'o'};
    String str2 = new String(arr);
    System.out.println(str2);
}
```



> 编码：String --> byte[]:调用String的`getBytes(String charsetName)`
> 解码：byte[] --> String:调用String的构造器`String str = new String(byte bytes[], String charsetName);`

```java
@Test
public void test3() throws UnsupportedEncodingException {
    String str1 = "abc123中国";
    byte[] bytes = str1.getBytes();//使用默认的字符集，进行编码。//abc123是ASCII,中国是utf-8,三位一个字
    System.out.println(Arrays.toString(bytes));
    byte[] gbks = str1.getBytes("gbk");//使用gbk字符集进行编码。
    System.out.println(Arrays.toString(gbks));
    System.out.println("******************");
    String str2 = new String(bytes);//使用默认的字符集，进行解码。
    System.out.println(str2);
    String str3 = new String(gbks);
    System.out.println(str3);//出现乱码。原因：编码集和解码集不一致！
    String str4 = new String(gbks, "gbk");
    System.out.println(str4);//没有出现乱码。原因：编码集和解码集一致！
}
```

> `编码`：字符串 -->字节  (看得懂 --->看不懂的二进制数据)
> `解码`：编码的逆过程，字节 --> 字符串 （看不懂的二进制数据 ---> 看得懂）
> 说明：解码时，要求解码使用的字符集必须与编码时使用的字符集一致，否则会出现乱码。
>
> `getBytes()和String构造器都有重载，有多个，上面仅参考`

## 运算符号

- 算数运算符

  `+-*/`: 加减乘除
  `%` : 取余运算  余数的符号与被除数(分子)一样
  `a++` : 先用后自增1   `自增不会改变变量数据类型`
  `++a` : 先自增1后用   `自增不会改变变量数据类型`
  `a--` : 同++
  `--a` : 同++

  > 自增不会改变数据类型意味着short,byte等不能自增，因为自增的1默认为整型

- 赋值运算符

  `=   +=  -=  *=  /= `    
  `a?=x  <==>  a=a?x `   
  和++一样不会改变变量数据类型,哪怕是整形与浮点型

- 比较运算符

  `==  !=  <   >   <=  >=  instanceof`(检查是否为类的对象) 

  > 如"hello" instanceof String

  比较运算符结果都是boolean型,即true或false

- 逻辑运算符

  `&`与(且)  `&&`短路与(且)  `|`或   `||`短路或  `!`非(反的)`^`亦或(a^b是否不一样)

  1. &与&&运算结果相同
  2. 符号左边是true时,都会执行右边的运算
  3. 符号左边是false时,&继续执行右边,&&不再执行

  |与||同理类似
  &&与||相比&和|更"聪明",更会"偷懒"

- 位运算符

  操作的都是整形的数据

  `<<` 左移  每左移一位,相当于原来的数 × 2   二进制的数(1011101...001)-左移2->(1011101...001 00)
  `>>` 右移  向右移,空出的高位用100..或000...补
  `>>>`                               都用0000..补

  - `&`   与     二进制的两个数每一位一一比较,若都为1,则为1,否则为0
  - `|`   或                                              ,若都为0,则为0,否则为1
  - `^`   亦或                                           ,若一0一1,则为1,否则为0
  - `~`   取反   就是反过来,0变1,1变0

- 三元运算符

  ` (条件表达式)?true时表达式1:false时表达式2`
  
  > `三元运算符的优先级高于赋值运算符`,且`表达式1与表达式2`会进行`自动类型提升`
  
   表达式1和表达式要求一致
   可以嵌套使用

> 如double num = (m > n) ? 2 : 1.0;
> 或String maxStr = (m > n) ? "m大" : "n大";
> 或String maxStr = (m > n) ? "m大" : ((m == n) ? "mn相等" : "n大");

表达式1和表达式2会进行自动类型提升

## 程序结构

### 顺序结构

即由上往下按顺序执行

### 分支结构

- if-else结构

  ```java
  if(xxxxx){
      xxxxx
  }else{
      xxxxx
  }
  ```

- switch-case 结构

  ```java
  switch(表达式){
  case 常量1;
      执行语句1;
      //break;
  case 常量2;
  	执行语句2;
      //break;
   .......
  default:         //default相当与else
  	执行语句n;
      //break;
  }
  ```

  > ①根据switch表达式中的值,依此匹配各个case中的常量.一旦匹配成功,则进入相应case结构中,调用对应执行语句.
  > 当调用完执行语句以后,继续向下执行其他case结构中的执行语句,直到遇到break或结束
  > ②switch结构中的表达式,只能是如下6种数据类型之一:
  > `byte / short / char / int / 枚举类型(java5.0) / String类型(java7.0)`
  > ③case只能为具体的数/字符(串),不能为范围,不能为bool
  > ④default相当与else,为其他情况,可有可无. 且可以在switch中的任何地方

### 循环结构

- for循环结构

  ```java
  for (int i = 1; i <= 5; i++) {
      System.out.println("hello");
  }
  ```

  > `for(;;){} = while(true){}死循环`
  > `初始化条件可以写在for循环外面`: `for(;xxx;xxx){}`   除非是上面情况,不然必须有,否则报错
  > `叠代条件可以写在for循环里面`: `for(;xxx;){i++}`     如果没有会无限循环
  > 循环条件没有也会是无限循环

- 增强for循环

  jdk 5.0 新增了`foreach`循环，用于遍历`集合`、`数组`

  `for(集合元素的类型 局部变量 : 集合对象)`

  把`集合`、`数组`对象中的元素一个个的取出来赋给`局部变量`

  ```
  //遍历集合
  for (Object obj : coll) {
      System.out.println(obj);
  }
  //遍历数组
  for (int i : arr) {
      System.out.println(i);
  }
  ```

  

- while循环结构

  ```java
  while(xxx){
       xxx;
       xxx;
  }
  ```

- do-while循环结构

  ```Java
  do{
     xxx;
     xxx;
  }while(xxx);
  ```

### break&continue

|          | 使用范围             | 作用         |
| -------- | -------------------- | ------------ |
| break    | switch-case&循环结构 | 结束当前循环 |
| continue | 循环结构             | 结束当此循环 |

> - 两个关键字后面都不能声明执行语句，否则报错
> - break默认跳出包裹此关键字最近的一层`循环`(for)

```java
class BreakContinue {
    public static void main(String[] args) {
        for (int i = 1; i <= 10; i++) {
            if (i % 4 == 0) {
                //break;//123
                continue;//123 5679 10
            }
            System.out.print(i);
        }
        System.out.println();

        for (int i = 1; i <= 4; i++) {
            for (int j = 1; j <= 10; j++) {
                if (j % 4 == 0) {
                    break;//默认跳出包裹此关键字最近的一层<循环>
                    //continue;
                }
                System.out.print(j);
            }
            System.out.println();
        }
        System.out.println();

        l:
		  //l任意定义
        for (int i = 1; i <= 4; i++) {
            for (int j = 1; j <= 10; j++) {
                if (j % 4 == 0) {
                    break l;//结束指定标识的一层循环结构
                    //continue l;//结束指定标识的一层循环结构档次循环
                }
                System.out.print(j);
            }
            System.out.println();
        }
    }
}
```



> 要结束全部(某个)循环的话可以在前面使用一个`label`(label可以任意定义),写个`label`:,然后写成 break/continue `label`;

## 面向对象

### 类及类的成员

类即class,可包含内容如下：

- `属性`
- `方法`
- `构造器`
- 代码块（不常见）
- 内部类（不常见）

一般声明一个类时，称其为类的`实例化`，如`Phone p = new Phone();`

有时只需单独使用类中的某些东西时可以使用`匿名对象`，即直接`new 对象()`,无需像上面一样声明，直接当作上面的p使用

> 一般情况下定义一个类的过程

1. 声明属性
2. 生成对应的get()方法与set()方法
3. 生成无参构造器与带参构造器
4. 生成toString()方法

#### 属性

即类的属性参数，也称`成员变量`,一般声明为`private`

> 声明：一般在类中最上面`数据类型 变量名 = 变量值;`进行定义

外部调用方法：`对象.属性`

内部调用方法：`this.属性`或`属性`(与参数不同名)

> 类中`不能`对属性进行修改赋值

可以对属性进行赋值的位置:

1. 默认初始化
2. 显式初始化
3. 构造器中初始化
4. 通过对象.赋值
5. 代码块中赋值

|              | 属性（成员变量）  |                    局部变量                    |
| :----------: | :---------------: | :--------------------------------------------: |
|   声明位置   |     类的{}中      | 方法内,方法形参,代码块内,构造器形参,构造器内部 |
|  权限修饰符  |     可以修饰      |                   不可以修饰                   |
|  默认初始值  |    同数据类型     |                无，必须显示赋值                |
| 内存加载位置 | 堆空间（非static) |                     栈空间                     |

> 属性赋值的先后顺序`由先往后`如下

1. 默认初始化
2. 显示初始化/代码块中赋值
3. 构造器中初始化
4. 通过"对象.方法" 或 "对象.属性"的方式或set方法，赋值

#### 方法

> 声明：权限修饰符	返回值类型	方法名(形参列表){
>
> ​        			方法体
>
> ​    	  }

- `权限修饰符`一般情况下都使用`public`，类内部使用的用private

- `返回值类型`分有返回值与无返回值，有返回值必须`return指定类型变量或常量`，无返回值使用`void`，且return如使用只能单独使用，表示结束

- `方法名`属于标识符,遵循标识符的规则和规范(`xxxYyyZzz`),要"见名知意"

- `形参列表`可以有0个，1个或多个形参，格式为`数据类型1 形参1,数据类型2,形参2,...`

  jdk5.0新增`可变个数形参`，具体使用如下：

  1. 可变个数形参的`格式`：`数据类型 ... 变量名`
  2. 当调用可变个数形参的方法时，传入的参数个数可以是：0个，1个,2个，。。。
  3. 可变个数形参的方法与本类中方法名相同，形参不同的方法之间构成重载
  4. 可变个数形参的方法与本类中`方法名相同，形参类型也相同的数组`之间不构成重载。换句话说，`二者不能共存`。如String... strs=String[] strs。二者算等价，可变形参方法可以为数组
  5. 可变个数形参在方法的形参中，`必须声明在末尾`
  6. 可变个数形参在方法的形参中,最多只能声明`一个`可变形参。

> 方法的`重载`(`overload`)

1. `定义`: 在同一个类中,允许存在一个以上的同名方法, 只要他们的参数个数或者参数类型不同即可
     "两同一不同": 同一个类,相同方法名
                 参数列表不同:参数个数不同, 参数类型不同
2. `举例`:
     Arrays类中重载的sort() / binarySearch()
3. `判断是否是重载`:
     跟方法的权限修饰符, 返回值类型, 形参变量名, 方法体都没有关系
     `只看括号内形参`
4. 在`通过对象调用方法`是, 如何确定某一个指定的方法
     `方法名 -->参数列表`

> 方法的`重写`(`override` / `overwrite`)

1. `定义`：子类继承父类以后，可以对`父类`中`同名同参数`的`方法`，进行`覆盖`操作

2. `应用`：重写以后，当创建子类对象以后，通过子类对象调用子父类中的同名同参数的方法时，`实际执行的是子类重写父类的方法`。

3. `规定`：
   方法的声明： 权限修饰符  返回值类型  方法名(形参列表) throws 异常的类型{
   					  //方法体
   				     }
   		约定俗称：`子类`中的叫`重写的方法`，`父类`中的叫`被重写的方法`

   1. 子类重写的方法的方法名和形参列表与父类被重写的方法的方法名和`形参列表相同`
   2. `子类`重写的方法的`权限修饰符不小于父类`被重写的方法的权限修饰符
      - 特殊情况：`子类不能重写父类中声明为private权限的方法`
   3. `返回值类型`：
      - `父类`被重写的方法的返回值类型是`void`，则`子类`重写的方法的返回值类型`只能是void`
      - `父类`被重写的方法的返回值类型是`A类型`，则`子类`重写的方法的返回值类型可以是`A类或A类的子类`(如父类:object,子类:String/int)
      - `父类`被重写的方法的返回值类型是`基本数据类型`(比如：double)，则`子类`重写的方法的返回值类型必须是`相同的基本数据类型`(必须也是double)
   4. `子类`重写的方法抛出的`异常类型不大于父类`被重写的方法抛出的`异常类型`

   

   - 通常把父类定义那排直接复制到子类
   - 子类和父类中的同名同参数的方法要么都声明为非static的（考虑重写），要么都声明为static的（不是重写）。

#### 构造器

构造器（或构造方法、constructor），就是生成类的工具

> 一、构造器的作用：

1. 创建对象
2. 初始化对象的信息

> 二、说明：

1. 如果没有显式的定义类的构造器的话，则系统默认提供一个空参的构造器
2. 定义构造器的格式：`权限修饰符  类名(形参列表){}`
3. 一个类中定义的多个构造器，彼此构成重载
4. `一旦我们显式的定义了类的构造器之后，系统就不再提供默认的空参构造器`
5. 一个类中，`至少会有一个构造器`(可能显示定义，可能默认）。

> 当我们进行类的`实例化`（创建对象）时，实际上就是`new 构造器`

> `JavaBean`

所谓JavaBean，是指符合如下标准的Java类：

- 类是公共的
- 有一个无参的公共的构造器(单纯的public class XXX{}就是一个无参的公共的构造器,此外默认的构造器权限和类的权限相同)
- 有属性，且有对应的get、set方法

#### 代码块

1. 代码块的`作用`：用来`初始化类、对象`
2. 代码块如果有`修饰`的话，`只能使用static`
3. `分类`：`静态代码块` vs `非静态代码块`

> 静态代码块

- 内部可以有输出语句
- `随着类的加载而执行`,而且`只执行一次`
- `作用`：`初始化类的信息`
- 如果一个类中定义了多个静态代码块，则按照`声明的先后顺序`执行
- `静态代码块`的执行要`优先`于`非静态代码块`的执行
- 静态代码块内`只能调用静态的属性、静态的方法`，不能调用非静态的结构

> 非静态代码块

- 内部可以有输出语句
- 随着对象的创建而执行
- 每`创建一个对象`，就`执行一次`非静态代码块
- `作用`：可以在`创建对象`时，对对象的属性等进行初始化
- 如果一个类中定义了多个非静态代码块，则按照`声明的先后顺序`执行
- 非静态代码块内可以调用`静态的属性`、`静态的方法`，或`非静态的属性`、`非静态的方法`

> 当父类子类都有代码块时，执行顺序为`由父及子，静态先行`

#### 内部类

1. Java中允许`将一个类`A`声明在另一个类`B中，则类A就是`内部类`，类B称为`外部类`

2. 内部类的`分类`：`成员内部类`（静态、非静态）vs `局部内部类`(方法内、代码块内、构造器内)

3. `成员内部类`：
   一方面，作为外部类的成员：

   - `调用外部类的结构`
   - 可以被`static`修饰
   - 可以被4种不同的`权限修饰`

   另一方面，作为一个类：

   - 类内可以`定义属性、方法、构造器`等
   - 可以被`final`修饰，表示此类不能被继承。言外之意，不使用final，就可以被继承
   - 可以被`abstract`修饰

4. 关注如下的3个问题

   - 如何`实例化成员内部类`的对象
     	静态:`外部类.内部类 xxx = new 外部类.内部类();`
     	动态:`外部类 xxx = new 外部类();`

     ​          `外部类.内部类 xxx = xxx.new 内部类()`

     `内部类非静态,必须要先有一个外部类实例才能实例化内部类`

   - 如何在成员内部类中区分调用外部类的结构
     	`形参`:`name`
     	`外部类属性`:`this.name`
     	`内部类属性`:`外部类.this.name`

   - 开发中局部内部类的使用

     ```Java
     public Comparable getComparable() {
         //创建一个实现了Comparable接口的类:局部内部类
         //方式一：
     //	class MyComparable implements Comparable{
     //		@Override
     //		public int compareTo(Object o) {
     //			return 0;
     //		}
     //	}
     //	return new MyComparable();
         //方式二：
         return new Comparable() {
             @Override
             public int compareTo(Object o) {
                 return 0;
             }
         };
     ```

     > 在局部内部类的方法中如果调用`声明局部内部类的方法`中的`局部变量`的话,
     > 要求此`局部变量`声明为`final`的。
     > jdk 7及之前版本：要求此局部变量`显式`的声明为final的
     > jdk 8及之后的版本：可以`省略`final的声明

### 面向对象三大特征



#### 封装性

> 为什么要封装

当我们创建一个类的对象以后，我们可以通过 "对象.属性" 的方式，对对象的属性进行赋值。

这里，赋值操作要受到属性的数据类型和存储范围的制约。除此之外，没有其他制约条件。

但是，在实际问题中，我们往往需要给属性赋值加入额外的限制条件。这个条件就不能在属性声明时体现，我们只能通过方法进行`限制条件`的添加。（比如：set()方法）

同时，我们需要避免用户再使用"对象.属性"的方式对属性进行赋值。则需要将属性声明为私有的(`private`).

此时，针对于属性就体现了`封装性`。

> 如何封装

Java规定了4种权限（从小到大排列）：`private`、`缺省`、`protected` 、`public`

|  修饰符   | 类内部 | 同一个包 | 不同包的子类 | 同一个工程 |
| :-------: | :----: | :------: | :----------: | :--------: |
|  private  |   √    |          |              |            |
| （缺省）  |   √    |    √     |              |            |
| protected |   √    |    √     |      √       |            |
|  public   |   √    |    √     |      √       |     √      |

4种权限都可以用来修饰`类的内部结构`：`属性`、`方法`、`构造器`、`内部类`

修饰`类`的话，只能使用：`缺省`、`public`

> 如果在`其他包`调用,那么除了`内部方法`,对应的`类`也必须声明`public`才行

---



#### 继承性

> 为什么要有继承性（`好处`）

1. 减少了代码的冗余，提高了代码的复用性
2. 便于功能的扩展
3. 为之后多态性的使用，提供了前提

> 继承性`格式`

`class A extends B{}`
A：`子类`、`派生类`、`subclass`
B：`父类`、`超类`、`基类`、`superclass`

> 继承性`效果`

1. 一旦子类A继承父类B以后，子类A中就获取了父类B中声明的`所有`的`属性`和`方法`。

   特别的，父类中声明为private的属性或方法，子类继承父类以后，仍然认为获取了父类中私有的结构。只有因为封装性的影响，使得子类不能直接调用父类的结构而已。

2. 子类继承父类以后，还可以声明自己特有的属性或方法：实现功能的拓展。
   子类和父类的关系，不同于子集和集合的关系。
   extends：延展、扩展

> 继承性`规定`

1. 一个类可以被`多个子类`继承。
2. Java中类的单继承性：一个类只能有`一个父类`
3. 子父类是相对的概念。
4. 子类直接继承的父类，称为：`直接父类`。间接继承的父类称为：`间接父类`
5. 子类继承父类以后，就获取了`直接父类以及所有间接父类中声明的属性和方法`

> 其他说明

1. 如果我们没有显式的声明一个类的父类的话，则此类继承于`java.lang.Object`类
2. `所有`的java类（除java.lang.Object类之外）都直接或间接的继承于`java.lang.Object`类
3. 意味着，所有的java类具有java.lang.Object类声明的功能。

---



#### 多态性

> 什么是多态性

多态性可以理解为一个事物的多种形态

即父类的引用指向子类的对象（或子类的对象赋给父类的引用）

`父类 xxx = new 子类()`

`说人话就是`：

- 等号左边看作创建一个模具，等号右边看作生成一个东西，等号看作把东西放到模具里面，放进去的是等号右边的符合模具的，不符合模具的放不进左边的模具
- 创建的本身是子类对象,但是看作父类类型，因此只能访问父类的属性,不能访问子类的特有属性(对于相同属性如果父类和子类都定义了,访问父类)，能够访问方法和子类重写的方法。
- 总的来说就是子类可以当父类用,同时保留自己的特点。

> 多态性的使用

`虚拟方法调用`：有了对象的多态性以后，我们在编译期，只能调用父类中声明的方法，但在运行期，我们实际执行的是子类重写父类的方法。
总结：`编译，看左边；运行，看右边`

> 使用前提

1. 类的继承关系
2. 方法的重写

> 对象的多态性，`只适用于方法，不适用于属性`（编译和运行都看左边）`

即调用属性时是父类属性

> `向下转型`

使用强制类型转换符。(向下==>向子类转型==转为子类)

```java
if (person1 instanceof Man) {
    Man man1 = (Man) person1;
    man1.earnMoney();
    System.out.println("******Man******");
}
```

> `instanceof`关键字

`a instanceof A`:判断对象a是否是类A的实例。如果是，返回true；如果不是，返回false。

使用情境：为了避免在向下转型时出现ClassCastException的异常，我们在向下转型之前，先进行instanceof的判断，一旦返回true，就进行向下转型。如果返回false，不进行向下转型。

如果 a instanceof A返回true,则 a instanceof B也返回true.其中，类B是类A的父类。





### 其他关键字

this,super,static,final,abstract,interface,package,import等

#### package

package : 包

1. 为了更好的实现项目中类的管理，提供包的概念
2. 使用package声明类或接口所属的包，声明在源文件的首行
3. 包，属于标识符，遵循标识符的命名规则、规范(`xxxyyyzzz`)、“见名知意”
4. 每"."一次，就代表一层文件目录。

> `同一个包`下，`不能`命名同名的接口、类。
> `不同的包`下，`可以`命名同名的接口、类。

***



#### import

import : 导入
1. 在源文件中显式的使用import结构导入指定包下的 <类、接口>
2. 声明在包的声明和类的声明之间
3. 如果需要导入多个结构，则并列写出即可
4. 可以使用"`xxx.*`"的方式，表示可以导入xxx包下的所有结构
5. 如果使用的类或接口是`java.lang`包下定义的，则可以`省略import`结构
6. 如果使用的类或接口是`本包`下定义的，则可以`省略import`结构
7. 如果在源文件中，使用了不同包下的同名的类，则必须至少有一个类需要以 全类名 的方式显示。(即直接用com.xxx.xxx.类名.方法()在程序中)
8. 使用"xxx.*"方式表明可以调用xxx包下的所有结构。但是如果使用的是xxx子包下的结构，则仍需要显式导入
9. import static:导入指定类或接口中的静态结构:<属性或方法>

---



#### this

1. this可以用来修饰、调用：`属性`、`方法`、`构造器`

2. this修饰属性和方法：

   `this.`理解为：当前(这个)对象的  或 当前正在创建的对象的

   1. 在类的`方法`中，我们可以使用"`this.属性`"或"`this.方法`"的方式，调用当前对象属性或方法。

      但是，通常情况下，我们都选择省略"this."。

      `特殊情况`下，如果方法的`形参和类的属性同名`时，我们必须显式的使用"this.变量"的方式，表明此变量是属性，而非形参。

   2. 在类的`构造器`中，我们可以使用"this.属性"或"this.方法"的方式，调用当前正在创建的对象属性或方法。
      但是，通常情况下，我们都选择省略"this."
      特殊情况下，如果构造器的形参和类的属性同名时，我们必须显式的使用"this.变量"的方式，表明此变量是属性，而非形参。

3. this调用构造器

   1. 我们在类的构造器中，可以显式的使用"`this(形参列表)`"方式，调用本类中指定的其他构造器
   2. 构造器中不能通过"this(形参列表)"方式调用自己
   3. 如果一个类中有n个构造器，则最多有 n - 1个构造器中使用了"this(形参列表)"
   4. 规定："`this(形参列表)"必须声明在当前构造器的首行`"
   5. 构造器内部，`最多`只能声明`一个`"`this(形参列表)`"，用来调用其他的构造器

   > 构造器使用this示例如下

   ```java
   public Persons(int age) {
       this();
       this.age = age;
   }
   public Persons(String name, int age) {
       this(age);
       this.name = name;
       //this.age = age;
       //Person初始化时，需要考虑如下的1,2,3,4...(共40行代码)
   }
   ```


---



#### super

super : 父类的

super可以用来调用：`属性`、`方法`、`构造器`

> super调用`属性`和`方法`

1. 我们可以在子类的`方法或构造器`中。通过使用"`super.属性`"或"`super.方法`"的方式，显式的调用父类中声明的属性或方法
   - 但是，通常情况下，我们习惯省略"super."
2. 特殊情况：当子类和父类中定义了`同名的属性`时，我们要想在子类中调用父类中声明的属性，则必须显式的使用"`super.属性`"的方式，表明调用的是`父类中声明的属性`。
3. 特殊情况：当`子类重写了父类中的方法`以后，我们想在子类的方法中调用父类中被重写的方法时，则必须显式的使用"`super.方法`"的方式，表明调用的是`父类中被重写的方法`。

> super调用`构造器`

1. 我们可以在子类的构造器中显式的使用"`super(形参列表)`"的方式，调用父类中声明的指定的构造器
2. "`super(形参列表)`"的使用，必须声明在子类构造器的`首行`
3. 我们在类的构造器中，针对于"`this(形参列表)`"或"`super(形参列表)`"`只能二选一，不能同时出现`
4. 在构造器的首行，`没有`显式的声明"this(形参列表)"或"super(形参列表)"，则`默认调用的是父类中空参的构造器`：`super()`
5. 在类的多个构造器中，`至少有一个类`的构造器中使用了"super(形参列表)"，调用父类中的构造器

---



#### static

static:静态的

static可以用来修饰：`属性`、`方法`、`代码块`、`内部类`

> static修饰`属性`：`静态变量（或类变量）`

1. 属性，按是否使用static修饰，又分为：`静态属性` vs `非静态属性`(`实例变量`)

   - `实例变量`：我们创建了类的多个对象，每个对象都独立的拥有一套类中的非静态属性。当修改其中一个对象中的`非静态属性`时，`不会`导致其他对象中同样的属性值的修改。
   - `静态变量`：我们创建了类的多个对象，`多个对象共享同一个静态变量`。当通过某一个对象修改静态变量时，会导致其他对象调用此静态变量时，是修改过了的。

2. static修饰属性的其他说明：

   - 静态变量`随着类的加载而加载`。可以通过"`类.静态变量`"的方式进行调用

   - 静态变量的`加载要早于对象的创建`。

   - 由于类只会加载一次，则静态变量在内存中也`只会存在一份`：存在`方法区的静态域`中。

   - |                    | 静态属性 | 非静态属性 |
     | :----------------: | :------: | :--------: |
     |  类(是否可以调用)  |    √     |     ×      |
     | 对象(是否可以调用) |    √     |     √      |

     > 这里的类和对象调用意思例如`People.属性`与`people.属性`,下面方法意思相同

3. 静态属性`举例`：`System.out`; `Math.PI`;

> 使用static修饰`方法`：`静态方法`

1. 随着类的加载而加载，可以通过"`类.静态方法`"的方式进行调用；直接调用本类中的静态方法可以直接`方法名"(参数)"`

2. |                    | 静态方法 | 非静态方法 |
   | :----------------: | :------: | :--------: |
   |  类(是否可以调用)  |    √     |     ×      |
   | 对象(是否可以调用) |    √     |     √      |

3. 静态方法中，只能调用静态的方法或属性

   非静态方法中，既可以调用非静态的方法或属性，也可以调用静态的方法或属性

   依据：生命周期

> static`注意点`

- 在静态的方法内，`不能使用this关键字、super关键字`
- 关于静态属性和静态方法的使用，都从生命周期的角度去理解(`看哪个活得久`)

> 如何确定一个`属性`是否要声明为static的

- 属性是可以被多个对象所共享的，不会随着对象的不同而不同的。
- 类中的常量也常常声明为static

> 如何确定一个`方法`是否要声明为static的

- 操作静态属性的方法，通常设置为static的
- 工具类中的方法，习惯上声明为static的。 比如：Math、Arrays、Collections

---



#### final

final : 最终的
1. final可以用来`修饰的结构`：`类`、`方法`、`变量`
2. final 用来`修饰一个类`:此类`不能被其他类所继承`
     比如：String类、System类、StringBuffer类
3. final 用来`修饰方法`：表明此方法`不可以被重写`(可以重载）
    	比如：Object类中getClass();
4. final 用来`修饰变量`：此时的"`变量`"就称为是一个`常量`(不可修改）
   - final修饰`属性`：
     - 可以考虑`赋值的位置`有：`显式初始化`、`代码块中初始化`、`构造器中初始化`
     - `final定义的属性必须被赋值`
     - 遵循常量命名规则`XXX_YYY_ZZZ`
   - final修饰`局部变量`：
     - 尤其是使用final修饰形参时，表明此形参是一个常量
     - 当我们调用此方法时，给常量形参赋一个实参。一旦赋值以后，就只能在方法体内使用此形参，但不能进行重新赋值。

> `static final` 用来修饰属性：`全局常量`

---



#### abstract

1. abstract : 抽象的		抽象的东西就不能实例化了

2. abstract可以用来`修饰的结构`：`类`、`方法`

3. abstract修饰类：`抽象类`
	- 此类`不能实例化`
   - 抽象类中`一定有构造器`，便于`子类实例化时调用`（涉及：子类对象实例化的全过程）
   - 开发中，都会提供抽象类的子类，让子类对象实例化，完成相关的操作
4. abstract修饰方法：`抽象方法`
	- 抽象方法`只有方法的声明`，`没有方法体`,`没有{}`。抽象方法没有方法体,要保证不被调用(也要保证子类必须重写,不然抽象方法抽象就没意义)
	- 包含抽象方法的类，一定是一个抽象类。反之，抽象类中可以没有抽象方法的。    方法要用对象调,要保证抽象方法不被调用,就要类不能实例化
   - 若子类`重写了父类中的所有的抽象方法`后，此子类方可实例化
   - 若子类`没有`重写父类中的所有的抽象方法，则此子类`也是一个抽象类`，需要`使用abstract修饰`

> abstract使用上的注意点：

1. abstract`不能`用来修饰：`属性`、`构造器等结构`
2. abstract`不能`用来修饰`私有方法`、`静态方法`、`final的方法`、`final的类`

> `抽象类的匿名子类`

抽象类 xxx=new 抽象类(){

​	重写的抽象方法	

​     ...
  }

```java
//例如
PersonAbs p = new PersonAbs() {
    @Override
    public void eat() {
        System.out.println("吃东西");
    }
    @Override
    public void breath() {
        System.out.println("好好呼吸");
    }
};
```

---



#### interface

想象成: 凡是实现(继承)了接口(比如为USB接口)的类或其他接口自己身上都会有(或安上了)一个USB接口，那么凡是需求USB接口的地方,都可以使用这些类

> `接口`的使用

1. `接口`使用`interface`来定义

2. Java中，`接口和类`是`并列`的两个结构

3. 如何`定义`接口：定义接口中的成员

   - JDK7及以前：只能定义`全局常量`和`抽象方法`

     - `全局常量`：`public static final`的，但是书写时，可以省略不写
     - `抽象方法`：`public abstract`的，但是书写时，可以省略不写

   - JDK8：除了定义全局常量和抽象方法之外，还可以定义`静态方法`、`默认方法`

     ```java
     interface CompareA {
         //静态方法
         public static void method1() {
             System.out.println("CompareA:北京");
         }
         //默认方法(可以有方法体了)
         public default void method2() {
             System.out.println("CompareA：上海");
         }
         default void method3() {
             System.out.println("CompareA：上海");
         }
     }
     ```

     1. 接口中定义的`静态方法`，`只能通过接口来调用`。
     2. 通过`实现类的对象`，可以`调用接口中的默认方法`。如果实现类重写了接口中的默认方法，调用时，仍然调用的是重写以后的方法
     3. 如果子类(或实现类)`继承的父类`和`实现的接口`中声明了`同名同参数的默认方法`，那么子类在`没有重写此方法`的情况下，`默认调用`的是`父类`中的同名同参数的方法。-->类优先原则
     4. 如果实现类`实现了多个接口`，而这多个接口中定义了`同名同参数的默认方法`，那么在实现类`没有重写此方法`的情况下，`报错`。-->接口冲突。
        这就需要我们`必须在实现类中重写此方法`

      

4. 接口中`不能定义构造器`！意味着接口`不可以实例化`

5. Java开发中，接口通过让类去`实现`(`implements`)的方式来使用.
   如果实现类`覆盖`了接口中的`所有的抽象方法`，则此实现类就`可以实例化`
   如果实现类`没有覆盖`接口中`所有的抽象方法`，则此实现类`仍为一个抽象类`
   
6. Java类可以实现`多个`接口   --->弥补了`Java单继承性`的局限性

7. `格式`：`class AA extends BB implements CC,DD,EE`

8. `接口与接口`之间`可以继承`，而且可以`多继承`

9. 接口的具体使用，体现`多态性`

9. 接口，实际上可以`看做是一种规范`







## 线程

### 创建方式

> 多线程的`创建`

两种方式`都要创建Thread类`来调用start()以启用新线程，区别是线程执行任务的`run()方法声明方式不同`以及`调用Thread的构造器不同`

#### 方式一：继承于`Thread`类

1. 创建一个继承于Thread类的子类
2. 重写Thread类的run() --> 将`此线程执行的操作`声明在run()中
3. 创建Thread类的子类的对象
4. 通过此对象调用start()`只有start()才会创建一个新的线程，可以看作调用start()=新线程`

```java
//1. 创建一个继承于Thread类的子类
class MyThread extends Thread {
    //2. 重写Thread类的run()
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            if (i % 2 == 0) {
                System.out.println(Thread.currentThread().getName() + ":" + i);
            }
        }
    }
}
public class ThreadTest {
    public static void main(String[] args) {
        //3. 创建Thread类的子类的对象
        MyThread t1 = new MyThread();
        //4.通过此对象调用start():①启动当前线程 ② 调用当前线程的run()
        t1.start();
        //问题一：我们不能通过直接调用run()的方式启动线程。
//        t1.run();
        //问题二：再启动一个线程，遍历100以内的偶数。
        //不可以还让已经start()的线程去执行。会报IllegalThreadStateException
//        t1.start();
        //我们需要重新创建一个线程的对象
        MyThread t2 = new MyThread();
        t2.start();
        //如下操作仍然是在main线程中执行的。
        for (int i = 0; i < 100; i++) {
            if (i % 2 == 0) {
                System.out.println(Thread.currentThread().getName() + ":" + i + "***********main()************");
            }
        }
    }
}
```



#### 方式二：实现`Runnable`接口

1. 创建一个实现了Runnable接口的类
2. 实现类去实现Runnable中的抽象方法：run()
3. 创建实现类的对象
4. 将此对象作为参数传递到Thread类的构造器中，创建Thread类的对象
5. 通过Thread类的对象调用start()

```java
//1. 创建一个实现了Runnable接口的类
class MThread implements Runnable{
    //2. 实现类去实现Runnable中的抽象方法：run()
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            if(i % 2 == 0){
                System.out.println(Thread.currentThread().getName() + ":" + i);
            }
        }
    }
}
public class ThreadTest1 {
    public static void main(String[] args) {
        //3. 创建实现类的对象
        MThread mThread = new MThread();
        //4. 将此对象作为参数传递到Thread类的构造器中，创建Thread类的对象
        Thread t1 = new Thread(mThread);
        t1.setName("线程1");
        //5. 通过Thread类的对象调用start():① 启动线程 ②调用当前线程的run()-->调用了Runnable类型的target的run()
        t1.start();
        //再启动一个线程，遍历100以内的偶数
        Thread t2 = new Thread(mThread);
        t2.setName("线程2");
        t2.start();
    }

}
```

Thread源码中run方法

```Java
@Override
public void run() {
    if (target != null) {
        target.run();
    }
}
```

其中target是Runnable类型的属性



#### 方式三：实现`Callable`接口 --- JDK 5.0新增

1. 创建一个实现Callable的实现类
2. 实现call方法，将此线程需要执行的操作声明在call()中
3. 创建Callable接口实现类的对象
4. 将此Callable接口实现类的对象作为传递到FutureTask构造器中，创建FutureTask的对象
5. 将FutureTask的对象作为参数传递到Thread类的构造器中，创建Thread对象，并调用start()
6. 获取Callable中call方法的返回值

```java
//1.创建一个实现Callable的实现类
class NumThread implements Callable{
    //2.实现call方法，将此线程需要执行的操作声明在call()中
    @Override
    public Object call() throws Exception {
        int sum = 0;
        for (int i = 1; i <= 100; i++) {
            if(i % 2 == 0){
                System.out.println(i);
                sum += i;
            }
        }
        return sum;//遍历100以内偶数返回总和
    }
}

public class ThreadNew {
    public static void main(String[] args) {
        //3.创建Callable接口实现类的对象
        NumThread numThread = new NumThread();
        //4.将此Callable接口实现类的对象作为传递到FutureTask构造器中，创建FutureTask的对象
        FutureTask futureTask = new FutureTask(numThread);
        //5.将FutureTask的对象作为参数传递到Thread类的构造器中，创建Thread对象，并调用start()
        new Thread(futureTask).start();

        try {
            //6.获取Callable中call方法的返回值
            //get()返回值即为FutureTask构造器参数Callable实现类重写的call()的返回值。
            Object sum = futureTask.get();
            System.out.println("总和为：" + sum);
        } catch (InterruptedException e) {
            e.printStackTrace();
        } catch (ExecutionException e) {
            e.printStackTrace();
        }
    }
}
```

> 为什么Callable接口的方式创建多线程比实现Runnable接口创建多线程方式强大？

1. call()可以`有返回值`的。
2. call()可以`抛出异常`，被外面的操作捕获，获取异常的信息
3. Callable是`支持泛型`的



#### 方式四：使用`线程池` --- JDK 5.0新增

- JDK 5.0起提供了线程池相关API：`ExecutorService`（继承Executors的接口） 和 `Executors`
- `ExecutorService`：真正的线程池接口。常见子类`ThreadPoolExecutor`
  - `void execute(Runnable command)` ：执行任务/命令，没有返回值，一般用来执行
    Runnable
  - `<T> Future<T> submit(Callable<T> task)`：执行任务，有返回值，一般又来执行
    Callable
  - `void shutdown()` ：关闭连接池
- `Executors`：工具类、线程池的工厂类，用于创建并返回不同类型的线程池
  - Executors.`newCachedThreadPool()`：创建一个`可根据需要创建新线程`的线程池
  - Executors.`newFixedThreadPool(n)`; 创建一个`可重用固定线程数`的线程池
  - Executors.`newSingleThreadExecutor()` ：创建一个`只有一个线程`的线程池
  - Executors.`newScheduledThreadPool(n)`：创建一个线程池，它`可安排在给定延迟后运行命令或者定期地执行`



- `好处`：
  1. 提高响应速度（减少了创建新线程的时间）
  2. 降低资源消耗（重复利用线程池中线程，不需要每次都创建）
  3. 便于线程管理

- `创建方式`：

  1. 提供指定线程数量的线程池，

     如`ExecutorService service = Executors.newFixedThreadPool(10);`

  2. 执行指定的线程的操作。需要提供实现Runnable接口或Callable接口实现类的对象
     `service.execute(Runnable runnable);`或`service.submit(Callable callable);`

  1. 关闭连接池,`service.shutdown();`

```java
class NumberThread implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i <= 100; i++) {
            if (i % 2 == 0) {
                System.out.println(Thread.currentThread().getName() + ": " + i);
            }
        }
    }
}

class NumberThread1 implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i <= 100; i++) {
            if (i % 2 != 0) {
                System.out.println(Thread.currentThread().getName() + ": " + i);
            }
        }
    }
}

public class ThreadPool {
    public static void main(String[] args) {
        //1. 提供指定线程数量的线程池
        ExecutorService service = Executors.newFixedThreadPool(10);
        ThreadPoolExecutor service1 = (ThreadPoolExecutor) service;
        //设置线程池的属性
//        System.out.println(service.getClass());
//        service1.setCorePoolSize(15);
//        service1.setKeepAliveTime();

        //2.执行指定的线程的操作。需要提供实现Runnable接口或Callable接口实现类的对象
        service.execute(new NumberThread());//适合适用于Runnable
        service.execute(new NumberThread1());//适合适用于Runnable

//        service.submit(Callable callable);//适合使用于Callable
        //3.关闭连接池
        service.shutdown();
    }
}
```

> 设置线程池的属性

`ThreadPoolExecutor service1 = (ThreadPoolExecutor) service;`

`service1.setXXXXX();`

---

`corePoolSize`：核心池的大小
`maximumPoolSize`：最大线程数
`keepAliveTime`：线程没有任务时最多保持多长时间后会终止





> 创建线程前两种的两种方式的比较

开发中：`优先选择`：实现`Runnable接口`的方式。原因：

1. 实现的方式`没有`类的`单继承性的局限性`

2. 实现的方式`更适合`来处理`多个线程有共享数据`的情况。

联系：public class Thread implements Runnable
相同点：两种方式都需要重写run(),将线程要执行的逻辑声明在run()中。

> 匿名Thread类匿名子类

按如下方式

```java
new Thread() {
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            if (i % 2 == 0) {
                System.out.println(Thread.currentThread().getName() + ":" + i);
            }
        }
    }
}.start();

new Thread(new Runnable() {
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            if (i % 2 == 0) {
                System.out.println(Thread.currentThread().getName() + ":" + i);
            }
        }
    }
}).start();
```



### 常用方法

> Thread类中的`常用方法`

|         方法          |                             作用                             |
| :-------------------: | :----------------------------------------------------------: |
|        start()        |              启动当前线程；调用当前线程的run()               |
|         run()         | 通常需要重写Thread类中的此方法<br />将创建的线程要执行的操作声明在此方法中 |
|    currentThread()    |          `静态方法`，返回执行当前代码的线程（对象）          |
|       getName()       |                      获取当前线程的名字                      |
|       setName()       |                      设置当前线程的名字                      |
|        yield()        |             释放当前cpu的执行权（但不一定切换）              |
|        join()         | 在线程a中调用线程 b的join(),此时线程 a就进入阻塞状态<br />直到线程 b完全执行完以后，线程 a才结束阻塞状态 |
|        stop()         |           已过时,当执行此方法时，强制结束当前线程            |
| sleep(long millitime) | `静态方法`，让当前线程"睡眠"指定的millitime毫秒<br />在指定的millitime毫秒时间内，当前线程是阻塞状态 |
|       isAlive()       |                     判断当前线程是否存活                     |
|     getPriority()     |                       获取线程的优先级                       |
|  setPriority(int p)   |                       设置线程的优先级                       |

线程的优先级：

1. MAX_PRIORITY：10
   MIN _PRIORITY：1
   NORM_PRIORITY：5  -->默认优先级
2. 如何获取和设置当前线程的优先级：
   getPriority():获取线程的优先级
   setPriority(int p):设置线程的优先级

高优先级的线程要抢占低优先级线程cpu的执行权。`但是`只是从概率上讲，高优先级的线程`高概率`的情况下被执行。并`不意味着`只有当高优先级的线程执行完以后，低优先级的线程才执行。

> 设置线程名也可以通过子类重写构造器后实现

### 安全问题

1. 问题：卖票过程中，出现了`重票、错票` -->出现了线程的安全问题
2. 问题出现的原因：当某个线程操作车票的过程中，`尚未完成操作`时，`其他线程参与进来`，也操作车票。
3. 如何解决：当一个线程a在操作ticket的时候，其他线程不能参与进来。直到线程a操作完ticket时，其他线程才可以开始操作ticket。这种情况即使线程a出现了阻塞，也不能被改变。

#### 方式一：`同步代码块`

- 格式：

  `synchronized(同步监视器){`

  `//需要被同步的代码`

  `}`

- 说明：

  1. `需要被同步的代码` ：`操作共享数据的代码` -->不能包含代码多了，也不能包含代码少了
  2. `共享数据`：`多个线程共同操作的变量`。比如：车票就是共享数据。
  3. `同步监视器`：俗称：`锁`。`任何一个类的对象`，都可以充当锁。`多个线程必须要共用同一把锁`。看作所有线程都去抢这个锁，抢到的可以运行

- 示例：

  ```Java
  class Window1 implements Runnable {
      private int ticket = 100;
      Object obj = new Object();
      
      @Override
      public void run() {
  //        Object obj = new Object();
          while (true) {
              //synchronized (this) {//this代表当前对象
              synchronized (obj) {
                  if (ticket > 0) {
                      try {
                          Thread.sleep(100);
                      } catch (InterruptedException e) {
                          e.printStackTrace();
                      }
                      System.out.println(Thread.currentThread().getName() + ":卖票，票号为：" + ticket);
  
                      ticket--;
                  } else {
                      break;
                  }
              }
          }
      }
  }
  public class WindowTest1 {
      public static void main(String[] args) {
          Window1 w = new Window1();
  
          Thread t1 = new Thread(w);
          Thread t2 = new Thread(w);
          Thread t3 = new Thread(w);
  
          t1.setName("窗口1");
          t2.setName("窗口2");
          t3.setName("窗口3");
  
          t1.start();
          t2.start();
          t3.start();
      }
  }
  ```

  > 在实现Runnable接口创建多线程的方式中，我们可以考虑使用`this`充当同步监视器

  ```java
  class Window2 extends Thread {
      private static int ticket = 100;
      private static Object obj = new Object();
  
      @Override
      public void run() {
          while (true) {
              //正确的
              //synchronized (obj){
              synchronized (Window2.class) {
              //Class clazz = Window2.class   Window2.class只会加载一次
              //错误的方式：this代表着t1,t2,t3三个对象
  			   //synchronized (this){
                  if (ticket > 0) {
                      try {
                          Thread.sleep(100);
                      } catch (InterruptedException e) {
                          e.printStackTrace();
                      }
                      System.out.println(getName() + "：卖票，票号为：" + ticket);
                      ticket--;
                  } else {
                      break;
                  }
              }
          }
      }
  }
  public class WindowTest2 {
      public static void main(String[] args) {
          Window2 t1 = new Window2();
          Window2 t2 = new Window2();
          Window2 t3 = new Window2();
  
          t1.setName("窗口1");
          t2.setName("窗口2");
          t3.setName("窗口3");
  
          t1.start();
          t2.start();
          t3.start();
      }
  }
  ```

  > 在继承Thread类创建多线程的方式中，慎用this充当同步监视器，考虑使用`当前类`充当同步监视器

#### 方式二：`同步方法`

如果操作共享数据的代码完整的声明在一个方法中，我们不妨将此方法声明同步的

关于同步方法的总结：
1. 同步方法`仍然涉及`到`同步监视器`，只是`不需要`我们`显式的声明`
2. `非静态`的同步方法，同步监视器是：`this`
`静态`的同步方法，同步监视器是：`当前类本身`

```java
class Window3 implements Runnable {
    private int ticket = 100;

    @Override
    public void run() {
        while (true) {
            show();
        }
    }

    private synchronized void show() {
        //同步方法的同步监视器：this
        //synchronized (this){

        if (ticket > 0) {

            try {
                Thread.sleep(100);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }

            System.out.println(Thread.currentThread().getName() + ":卖票，票号为：" + ticket);

            ticket--;
        }
        //}
    }
}
public class WindowTest3 {
    public static void main(String[] args) {
        Window3 w = new Window3();

        Thread t1 = new Thread(w);
        Thread t2 = new Thread(w);
        Thread t3 = new Thread(w);

        t1.setName("窗口1");
        t2.setName("窗口2");
        t3.setName("窗口3");

        t1.start();
        t2.start();
        t3.start();
    }
}
```

```java
class Window4 extends Thread {
    private static int ticket = 100;

    @Override
    public void run() {
        while (true) {
            show();
        }
    }
    private static synchronized void show(){
        //同步监视器：Window4.class
        
        //private synchronized void show(){
        //同步监视器：t1,t2,t3。此种解决方式是错误的
        
        if (ticket > 0) {

            try {
                Thread.sleep(100);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }

            System.out.println(Thread.currentThread().getName() + "：卖票，票号为：" + ticket);
            ticket--;
        }
    }
}


public class WindowTest4 {
    public static void main(String[] args) {
        Window4 t1 = new Window4();
        Window4 t2 = new Window4();
        Window4 t3 = new Window4();

        t1.setName("窗口1");
        t2.setName("窗口2");
        t3.setName("窗口3");

        t1.start();
        t2.start();
        t3.start();

    }
}
```

#### 方式三：`Lock锁` --- JDK5.0新增

> `使用方式`

1. 实例化ReentrantLock
2. 调用锁定方法lock()
3. 调用解锁方法：unlock()

> `注意事项`

`Lock可以看作同步监视器，意味着对于不同对象Lock要是唯一的`

`即实例化ReentrantLock过程中如果是继承Thread类，要加static`

1. 面试题：synchronized 与 Lock的异同？
  - `相同`：二者都可以解决线程安全问题
  - `不同`：synchronized机制在执行完相应的同步代码以后，`自动`的释放同步监视器
    Lock需要`手动`的启动同步（`lock()`），同时结束同步也需要`手动`的实现（`unlock()`）
2. 优先`使用顺序`：`Lock`-->`同步代码块`（已经进入了方法体，分配了相应资源）-->`同步方法`（在方法体之外）

```java
class Window implements Runnable {

    private int ticket = 100;
    //1.实例化ReentrantLock
    private ReentrantLock lock = new ReentrantLock();

    @Override
    public void run() {
        while (true) {
            try {
                //2.调用锁定方法lock()
                lock.lock();
                if (ticket > 0) {
                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    System.out.println(Thread.currentThread().getName() + "：售票，票号为：" + ticket);
                    ticket--;
                } else {
                    break;
                }
            } finally {
                //3.调用解锁方法：unlock()
                lock.unlock();
            }
        }
    }
}

public class LockTest {
    public static void main(String[] args) {
        Window w = new Window();

        Thread t1 = new Thread(w);
        Thread t2 = new Thread(w);
        Thread t3 = new Thread(w);

        t1.setName("窗口1");
        t2.setName("窗口2");
        t3.setName("窗口3");

        t1.start();
        t2.start();
        t3.start();
    }
}
```



> - 同步的方式，`解决了线程的安全问题`。---`好处`
> - 操作同步代码时，`只能有一个线程参与`，其他线程等待。相当于是一个`单线程`的过程，`效率低`。 ---`局限性`

### 死锁问题

1. 死锁的理解：不同的线程分别占用对方需要的同步资源不放弃，都在等待对方放弃自己需要的同步资源，就形成了线程的死锁
2. 说明：
   - 出现死锁后，不会出现异常，不会出现提示，只是所有的线程都处于阻塞状态，无法继续
   - 我们使用同步时，要避免出现死锁。

```java
public class ThreadTest {
    public static void main(String[] args) {
        StringBuffer s1 = new StringBuffer();
        StringBuffer s2 = new StringBuffer();

        new Thread(){
            @Override
            public void run() {
                synchronized (s1){
                    s1.append("a");
                    s2.append("1");

                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }

                    synchronized (s2){
                        s1.append("b");
                        s2.append("2");

                        System.out.println(s1);
                        System.out.println(s2);
                    }
                }
            }
        }.start();

        
        new Thread(new Runnable() {
            @Override
            public void run() {
                synchronized (s2){
                    s1.append("c");
                    s2.append("3");

                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }

                    synchronized (s1){
                        s1.append("d");
                        s2.append("4");

                        System.out.println(s1);
                        System.out.println(s2);
                    }
                }
            }
        }).start();
    }
}
```

### 线程通信

> 涉及到的三个方法：

- `wait()`:一旦执行此方法，当前线程就`进入阻塞`状态，并`释放同步监视器`
- `notify()`:一旦执行此方法，就会`唤醒被wait的一个线程`。如果有多个线程被wait，就唤醒优先级高的那个
- `notifyAll()`:一旦执行此方法，就会`唤醒所有被wait的线程`

> 注意事项与说明

1. `wait()`，`notify()`，`notifyAll()`三个方法`必须使用在同步代码块或同步方法中`
2. `wait()`，`notify()`，`notifyAll()`三个方法的`调用者必须是`同步代码块或同步方法中的`同步监视器`。否则，会出现`IllegalMonitorStateException`异常
3. `wait()`，`notify()`，`notifyAll()`三个方法是`定义`在`java.lang.Object`类中

```java
class Number implements Runnable {
    private int number = 1;
    private Object obj = new Object();

    @Override
    public void run() {
        while (true) {
            synchronized (obj) {
                obj.notify();
                if (number <= 100) {
                    try {
                        Thread.sleep(10);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    System.out.println(Thread.currentThread().getName() + ":" + number);
                    number++;

                    try {
                        //使得调用如下wait()方法的线程进入阻塞状态
                        obj.wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }

                } else {
                    break;
                }
            }
        }

    }
}

public class CommunicationTest {
    public static void main(String[] args) {
        Number number = new Number();
        Thread t1 = new Thread(number);
        Thread t2 = new Thread(number);

        t1.setName("线程1");
        t2.setName("线程2");

        t1.start();
        t2.start();
    }
}
```

> 面试题：sleep() 和 wait()的异同？

1. `相同点`：一旦执行方法，都可以使得当前的线程进入阻塞状态。
2. `不同点`：
   - 两个方法`声明的位置`不同：Thread类中声明sleep() , Object类中声明wait()
   - 调用的`要求`不同：`sleep()`可以在`任何`需要的场景下调用。 `wait()必须`使用在同步代码块或同步方法中
   - 关于`是否释放同步监视器`：如果两个方法都使用在同步代码块或同步方法中，`sleep()不会`释放锁，`wait()会`释放锁。



## 比较器

Java中的对象，正常情况下，只能进行比较：`==` 或 `!=` ，不能使用`>`或`<`

但是在开发场景中，我们需要对多个对象进行排序，言外之意，就需要比较对象的大小

如何实现？使用两个接口中的任何一个：`Comparable` 或 `Comparator`

> `Comparable`接口的方式一旦一定，保证Comparable接口实现类的对象在`任何位置都可以比较大小`
>
> `Comparator`接口属于`临时性的比较`

### Comparable

Comparable接口的使用举例：自然排序(指实现Comparable接口进行的排序)

1. 像String、包装类等`实现`了`Comparable`接口，`重写`了`compareTo(obj)`方法，给出了比较两个对象大小的方式。
2. 像`String、包装类`重写compareTo()方法以后，进行了`从小到大`的排列

3. 重写compareTo(obj)的规则：
    - 如果当前对象this`大于`形参对象obj，则返回`正整数`，
    - 如果当前对象this`小于`形参对象obj，则返回`负整数`，
    - 如果当前对象this`等于`形参对象obj，则返回`零`。
4. 对于`自定义类`来说，如果需要排序，我们可以让自定义类`实现Comparable接口`，`重写compareTo(obj)方法`，`在compareTo(obj)方法中指明如何排序`

> 例：商品价格排序，源于sort()

```java
public class Goods implements Comparable {
    private String name;
    private double price;
    public Goods() {
    }
    public Goods(String name, double price) {
        this.name = name;
        this.price = price;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public double getPrice() {
        return price;
    }
    public void setPrice(double price) {
        this.price = price;
    }
    @Override
    public String toString() {
        return "Goods{" +
                "name='" + name + '\'' +
                ", price=" + price +
                '}';
    }
    //指明商品比较大小的方式:按照价格从低到高排序,再按照产品名称从高到低排序
    @Override
    public int compareTo(Object o) {
//        System.out.println("**************");
        if (o instanceof Goods) {
            Goods goods = (Goods) o;
            //方式一：
            if (this.price > goods.price) {
                return 1;
            } else if (this.price < goods.price) {
                return -1;
            } else {
//                return 0;
                return this.name.compareTo(goods.name);
            }
            //方式二：
//           return Double.compare(this.price,goods.price);
        }
//        return 0;
        throw new RuntimeException("传入的数据类型不一致！");
    }
}
```



### Comparator

Comparator接口的使用：定制排序

1. 背景：当元素的类型没有实现java.lang.Comparable接口而又不方便修改代码，或者实现了java.lang.Comparable接口的排序规则不适合当前的操作，那么可以考虑使用 Comparator的对象来排序
2. `重写compare(Object o1,Object o2)`方法，比较`o1和o2`的大小：
   - 如果方法返回`正整数`，则表示`o1大于o2`
   - 如果返回`0`，表示`相等`
   - 返回`负整数`，表示`o1小于o2`

> 例：和上面的类一样

```java
@Test
public void test() {
    Goods[] arr = new Goods[6];
    arr[0] = new Goods("lenovoMouse", 34);
    arr[1] = new Goods("dellMouse", 43);
    arr[2] = new Goods("xiaomiMouse", 12);
    arr[3] = new Goods("huaweiMouse", 65);
    arr[4] = new Goods("huaweiMouse", 224);
    arr[5] = new Goods("microsoftMouse", 43);
    Arrays.sort(arr, new Comparator() {
        //指明商品比较大小的方式:按照产品名称从低到高排序,再按照价格从高到低排序
        @Override
        public int compare(Object o1, Object o2) {
            if (o1 instanceof Goods && o2 instanceof Goods) {
                Goods g1 = (Goods) o1;
                Goods g2 = (Goods) o2;
                if (g1.getName().equals(g2.getName())) {
                    return -Double.compare(g1.getPrice(), g2.getPrice());
                } else {
                    return g1.getName().compareTo(g2.getName());
                }
            }
            throw new RuntimeException("输入的数据类型不一致");
        }
    });
    System.out.println(Arrays.toString(arr));
}
```



## 枚举类

> 枚举类的使用

1.枚举类的理解：`类的对象`只有`有限个，确定的`。我们称此类为枚举类
2.当需要定义一组常量时，强烈建议使用枚举类
3.如果枚举类中只有一个对象，则可以作为单例模式的实现方式。

> 枚举类的定义

方式一：jdk5.0之前，`自定义枚举类`
方式二：jdk5.0，可以使用`enum关键字`定义枚举类

> 三、Enum类中的常用方法：

values()方法：返回枚举类型的对象数组。该方法可以很方便地遍历所有的枚举值。
valueOf(String str)：可以把一个字符串转为对应的枚举类对象。要求字符串必须是枚举类对象的“名字”。如不是，会有运行时异常：IllegalArgumentException。
toString()：返回当前枚举类对象常量的名称

> 四、使用enum关键字定义的枚举类实现接口的情况

  情况一：实现接口，在enum类中实现抽象方法
  情况二：让枚举类的对象分别实现接口中的抽象方法

### 自定义枚举类

1. 声明Season对象的`属性`:`private final`修饰
2. `私有化`类的`构造器`,并`给对象属性赋值`
3. `提供当前枚举类的多个对象`：`public static final`的

```java
//自定义枚举类
class Season {
    //1.声明Season对象的属性:private final修饰
    private final String seasonName;
    private final String seasonDesc;
    //2.私有化类的构造器,并给对象属性赋值
    private Season(String seasonName, String seasonDesc) {
        this.seasonName = seasonName;
        this.seasonDesc = seasonDesc;
    }
    //3.提供当前枚举类的多个对象：public static final的
    public static final Season SPRING = new Season("春天", "春暖花开");
    public static final Season SUMMER = new Season("夏天", "夏日炎炎");
    public static final Season AUTUMN = new Season("秋天", "秋高气爽");
    public static final Season WINTER = new Season("冬天", "冰天雪地");
    //4.其他诉求1：获取枚举类对象的属性
    public String getSeasonName() {
        return seasonName;
    }
    public String getSeasonDesc() {
        return seasonDesc;
    }
    //4.其他诉求1：提供toString()
    @Override
    public String toString() {
        return "Season{" +
                "seasonName='" + seasonName + '\'' +
                ", seasonDesc='" + seasonDesc + '\'' +
                '}';
    }
}
```



### enum类

- 相比自定义枚举类，enum类的枚举类的`对象提到最前面`，`属性`与`构造器`的`修饰词`可以`省略`
- 定义的枚举类默认继承于`java.lang.Enum`类

> 定义

1. 提供当前枚举类的对象，多个对象之间用"`,`"隔开，末尾对象"`;`"结束
2. 声明枚举类对象的`属性`:`private final`修饰
3. 私有化类的构造器,并给对象属性赋值

> 方法

- `values()`方法：返回`枚举类型`的`对象数组`。该方法可以很方便地`遍历`所有的枚举值。
- `valueOf(String objName)`：返回枚举类中对象名是objName的对象。可以把一个字符串转为对应的枚举类对象。要求字符串必须是枚举类对象的“名字”。如不是，会有运行时异常：IllegalArgumentException。
- `toString()`：返回当前`枚举类对象常量`的`名称`

> 实现接口

情况一：实现接口，在enum类中实现抽象方法
情况二：让枚举类的对象`分别实现接口中的抽象方法`

```java
enum Season1 implements Info {
    //1.提供当前枚举类的对象，多个对象之间用","隔开，末尾对象";"结束
    SPRING("春天", "春暖花开") {
        @Override
        public void show() {
            System.out.println("春天在哪里？");
        }
    },
    SUMMER("夏天", "夏日炎炎") {
        @Override
        public void show() {
            System.out.println("宁夏");
        }
    },
    AUTUMN("秋天", "秋高气爽") {
        @Override
        public void show() {
            System.out.println("秋天不回来");
        }
    },
    WINTER("冬天", "冰天雪地") {
        @Override
        public void show() {
            System.out.println("大约在冬季");
        }
    };
    //2.声明Season对象的属性:private final修饰
    private final String seasonName;
    private final String seasonDesc;
    //3.私有化类的构造器,并给对象属性赋值
    private Season1(String seasonName, String seasonDesc) {
        this.seasonName = seasonName;
        this.seasonDesc = seasonDesc;
    }
//    @Override
//    public void show() {
//        System.out.println("这是一个季节");
//    }
}
```



## 注解

`Annotation`：jdk 5.0 新增的功能，实就是代码里的特殊标记, 这些标记可以在编译, 类加载, 运行时被读取, 并执行相应的处理。通过使用 Annotation,程序员可以在不改变原有逻辑的情况下, 在源文件中嵌入一些补充信息。

> Annocation的使用示例

1. 生成文档相关的注解
2. 在编译时进行格式检查(JDK内置的三个基本注解)
3. 跟踪代码依赖性，实现替代配置文件功能

### JDK内置的3个基本注解

- `@Override`: 限定重写父类方法, 该注解只能用于方法
- `@Deprecated`: 用于表示所修饰的元素(类, 方法等)已`过时`。通常是因为所修饰的结构危险或存在更好的选择
- `@SuppressWarnings`: `抑制`编译器`警告`

### JDK 提供的4种元注解

`元注解`(`meta-annotation`)：对现有的注解进行解释说明的注解

元数据：对现有的数据进行解释说明的数据



- `Retention`：`指定`所修饰的Annotation的`生命周期`：
  - `SOURCE`(不存在.class里面)：在源文件中有效（即源文件保留），编译器直接丢弃这种策略的 注释
  - `CLASS`(保存在.class文件里但不加载到内存（`默认行为`）)：在class文件中有效（即class保留），当运行Java 程序时,JVM不会保留注解。 这是默认值
  - `RUNTIME`(保存在.class文件里面且加载到内存)：在运行时有效（即运行时保留），当运行Java 程序时, JVM会保留注释。程序可以通过反射获取该注释
    `只有声明为RUNTIME生命周期的注解，才能通过反射获取`
- `Target`:用于指定被修饰的Annotation`能用于修饰哪些程序元素`
  - `PACKAGE`：描述包
  - `FIELD`：描述域
  - `TYPE`：描述类、接口、enum
  - `PARAMETER`：描述参数
  - `CONSTRUCTOR`：描述构造器
  - `METHOD`：描述方法
  - `LOCAL_VARIABLE`：描述局部变量

[--------------------下面两个出现的频率较低--------------------]()

- `Documented`:表示所修饰的注解在被javadoc解析时，保留下来。
- `Inherited`:被它修饰的 Annotation 将具有`继承性`。



### 自定义注解

1. 注解声明为：`@interface`
2. 内部定义成员，通常使用`value`表示
3. 可以指定成员的默认值，使用`default`定义
4. 如果自定义注解没有成员，表明是一个`标识`作用

```java
@Inherited
@Repeatable(MyAnnotations.class)
@Retention(RetentionPolicy.RUNTIME)
@Target({TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE,TYPE_PARAMETER,TYPE_USE})
public @interface MyAnnotation {
    String value() default "hello";
}
```

```java
@Inherited
@Retention(RetentionPolicy.RUNTIME)
@Target({TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE})
public @interface MyAnnotations {
    MyAnnotation[] value();
}
```

> 如果注解有成员，在使用注解时，`需要指明成员的值`
> 自定义注解必须配上注解的信息处理流程(`使用反射`)`才有意义`
> 自定义注解`通常都会指明`两个元注解：`Retention`、`Target`



### 可重复注解

JDK8 中注解的新特性

1. 在MyAnnotation`上`声明`@Repeatable`，`成员值`为`MyAnnotations.class`
2. MyAnnotation的Target和Retention等元注解与MyAnnotations相同。

### 类型注解

JDK8 中注解的新特性

- ElementType.`TYPE_PARAMETER`表示该注解能写在类型变量的声明语句中（如：泛型声明）。
- ElementType.`TYPE_USE`表示该注解能写在使用类型的任何语句中。



## 集合

`集合`、`数组`都是`对多个数据进行存储`操作的结构，简称Java容器

### Collection接口

|             方法             |                       作用                        |
| :--------------------------: | :-----------------------------------------------: |
|            size()            |               获取添加的元素的个数                |
|        add(Object e)         |             将元素e添加到collection中             |
|   addAll(Collection coll)    |       将coll1集合中的元素添加到当前的集合中       |
|           clear()            |                   清空集合元素                    |
|          isEmpty()           |               判断当前集合是否为空                |
|     contains(Object obj)     |      判断当前集合中是否包含obj(`调用equals`)      |
| containsAll(Collection coll) |     判断coll中的所有元素是否都存在于当前集合      |
|      remove(Object obj)      | 从当前集合中移除obj元素(`调用equals`，先看有没有) |
|  removeAll(Collection coll)  |        从当前集合中移除coll中所有 有的元素        |
|  retainAll(Collection coll)  |  获取当前集合和coll集合的交集，并返回给当前集合   |
|      equals(Object obj)      |      判断当前集合和形参集合的元素是否都相同       |
|          hashCode()          |               返回当前对象的哈希值                |
|          toArray()           |                  集合 ---> 数组                   |
|      Arrays.asList(arr)      |                  数组 ---> 集合                   |
|          iterator()          |     返回Iterator接口的实例，用于遍历集合元素      |

> `Arrays.asList`的参数数组不能为为基本数据类型，如int[]，`必须为引用数据类型`，如`Integer[]`，否则会将数组本身作为集合元素而不是数组元素。且通过该方式生成的集合·`没有Collection的方法，长度不能改变，只能用来遍历`。
>
> 变成可变的可以按如下方式：
>
> ```java
> List<String> list = new ArrayList<>();
> list.addAll(Arrays.asList("haha","xixi"));
> ```

> 集合元素的`遍历`操作：使用迭代器`Iterator接口`

`Collection`接口继承了`Iterator`接口

1. 内部的方法：
   - `hasNext()` 判断是否还有下一个元素
   -  `next()`①指针下移 ②将下移以后集合位置上的元素返回(`初始指针不在集合元素上，调用next()后才在第一个元素上`)
2. 集合对象每次调用iterator()方法都得到一个全新的迭代器对象，默认游标都在集合的第一个元素之前
3. 内部定义了`remove()`,可以在遍历的时候，删除集合中的元素。此方法`不同于`集合直接调用remove()

```java
Collection coll = new ArrayList();
Iterator iterator = coll.iterator();
while (iterator.hasNext()) {//hasNext():判断是否还有下一个元素
    //next():①指针下移 ②将下移以后集合位置上的元素返回
    System.out.println(iterator.next());
}
```

> 如果还`未`调用`next`或在上一次调用next方法之后`已经调用`了remove方法，
> 再调用remove都会报`IllegalStateException`



#### List接口

存储`有序的`、`可重复的`数据 ("动态"数组)

> 常用方法

|                    方法                    |                 作用                 |
| :----------------------------------------: | :----------------------------------: |
|      void add(int index, Object ele)       |        在index位置插入ele元素        |
| boolean addAll(int index, Collection eles) | 从index位置开始将eles中所有元素添加  |
|          Object remove(int index)          |  移除index位置的元素，并返回此元素   |
|     Object set(int index, Object ele)      |     设置指定index位置的元素为ele     |
|           Object get(int index)            |       获取指定index位置的元素        |
|          int indexOf(Object obj)           |    返回obj在集合中首次出现的位置     |
|        int lastIndexOf(Object obj)         |  返回obj在当前集合中末次出现的位置   |
|  List subList(int fromIndex, int toIndex)  | 返回从fromIndex到toIndex位置的子集合 |



##### ArrayList

作为List接口的`主要实现类`；线程`不安全`的，`效率高`；底层使用Object[] elementData存储

- JDK7

  ```java
  ArrayList list = new ArrayList();//底层创建了长度是10的Object[]数组elementData
  list.add(123);//elementData[0] = new Integer(123);
  ...
  list.add(11);//如果此次的添加导致底层elementData数组容量不够，则扩容。
  默认情况下，扩容为原来的容量的1.5倍，同时需要将原有数组中的数据复制到新的数组中。
  ```

  建议开发中使用`带参的构造器`：ArrayList list = new ArrayList(int capacity)

- JDK8

  ```java
  ArrayList list = new ArrayList();//底层Object[] elementData初始化为{}.并没有创建长度为10的数组
  list.add(123);//第一次调用add()时，底层才创建了长度10的数组，并将数据123添加到elementData[0]
  ...
  后续的添加和扩容操作与jdk 7 无异。
  ```

  JDK7中的ArrayList的对象的创建类似于`单例的饿汉式`

  JDK8中的ArrayList的对象的创建类似于`单例的懒汉式`，`延迟了数组的创建`，`节省内存`

##### LinkedList

对于`频繁的插入、删除`操作，使用此类效率比ArrayList高；底层使用`双向链表`存储

```java
LinkedList list = new LinkedList(); 内部声明了Node类型的first和last属性，默认值为null
list.add(123);//将123封装到Node中，创建了Node对象。
```

Node定义：

```java
private static class Node<E> {
    E item;
    Node<E> next;
    Node<E> prev;

    Node(Node<E> prev, E element, Node<E> next) {
    this.item = element;
    this.next = next;
    this.prev = prev;
	}
}
```

##### Vector

作为List接口的`古老实现类`；线程`安全`的，`效率低`；底层使用Object[] elementData存储

jdk7和jdk8中通过Vector()构造器创建对象时，底层都创建了长度为10的数组。在扩容方面，默认扩容为原来的数组长度的`2倍`



#### Set接口

存储`无序的`、`不可重复`的数据

Set接口中`没有`额外定义新的方法，使用的都是`Collection中声明过的方法`

- 无序性

  `不等于随机性`。存储的数据在底层数组中并非按照数组索引的顺序添加，而是`根据数据的哈希值决定`的。分配内存可能东一个元素，西一个元素

- 不可重复性

  保证添加的元素`按照equals()判断`时，不能返回true.即：`相同的元素只能添加一个`

> 向Set(主要指：HashSet、LinkedHashSet)中添加的数据，其所在的类一定要`重写hashCode()和equals()`
>
> 重写的hashCode()和equals()尽可能保持`一致性`：`相等的对象必须具有相等的散列码`
>
> 重写两个方法的小技巧：对象中用作 equals() 方法比较的 Field，都应该用来计算 hashCode 值。

##### HashSet

作为Set接口的`主要`实现类；线程`不安全`的；`可以存储null值`

HashSet`底层`：`数组+链表`的结构

> 数组`初始`长度`16`，使用率超过`0.75`，扩容为原来`2倍`

> 实际上是创建HashMap，key作为set值，value都指向同一个new object()

底层添加元素的过程：

1. 我们向HashSet中添加元素a,首先`调用`元素a所在类的`hashCode()`方法，计算元素a的`哈希值`
2. 此哈希值接着通过某种算法`计算`出在HashSet`底层数组中的存放位置`（即为：`索引位置`），判断数组此位置上`是否已经有元素`：
   - 如果此位置上`没有`其他元素，则元素a`添加成功` --- `情况1`
   - 如果此位置上`有`其他元素b(`或以链表形式存在的多个元素`），则`比较`元素a与元素b的`hash值`：
     - 如果hash值`不相同`，则元素a`添加成功` --- `情况2`
     - 如果hash值`相同`，进而需要`调用`元素a所在类的`equals()`方法：
       - equals()返回`true`，元素a`添加失败`
       - equals()返回`false`，则元素a`添加成功` --- `情况3`

对于添加成功的`情况2和情况3`而言：元素a与已经存在指定索引位置上数据以`链表`的方式存储。

- JDK7：元素`a放到数组中`，指向原来的元素。

- JDK8：`原来的元素在数组中`，指向元素a

  总结：`七上八下`

###### LinkedHashSet

作为HashSet的`子类`；遍历其内部数据时，可以`按照添加的顺序遍历`

在添加数据的同时，`每个数据还维护了两个引用`，`记录`此数据`前一个数据`和`后一个数据`。

`优点`：对于`频繁的遍历操作`，LinkedHashSet`效率高`于HashSet



##### TreeSet

可以按照添加对象的指定属性，进行排序

1. 向TreeSet中添加的数据，`要求是相同类的对象`
2. 两种排序方式：`自然排序`（实现`Comparable`接口）和`定制排序`（`Comparator`）
3. `自然排序`中，比较两个对象是否相同的`标准`为：`compareTo()返回0`，不再是equals()
4. `定制排序`中，比较两个对象是否相同的`标准`为：`compare()返回0`，不再是equals()
   `定制排序`生成TreeSet对象时调用`参数为比较器的构造器`：`TreeSet set = new TreeSet(com)`



### Map接口

双列集合，用来存储`key-value对`的数据

- Map结构
  - Map中的`key`：`无序的`、`不可重复的`，使用`Set存储`所有的key  ---> `key所在的类要重写equals()和hashCode()` （以HashMap为例）
  - Map中的`value`：`无序的`、`可重复的`，使用Collection存储所有的value --->`value所在的类要重写equals()`
  - 一个`键值对`：`key-value`构成了一个`Entry对象`。
  - Map中的`entry`：`无序的`、`不可重复的`，使用`Set存储`所有的entry
  
- 常用方法

  |                方法                 |                 作用                  |
  | :---------------------------------: | :-----------------------------------: |
  | Object put(Object key,Object value) |  将key-value添加到(或修改)当前map中   |
  |         void putAll(Map m)          |   将m中的所有key-value对存放到map中   |
  |      Object remove(Object key)      | 移除指定key的key-value对，并返回value |
  |            void clear()             |        清空当前map中的所有数据        |
  |       Object get(Object key)        |        获取指定key对应的value         |
  |   boolean containsKey(Object key)   |           是否包含指定的key           |
  | boolean containsValue(Object value) |          是否包含指定的value          |
  |             int size()              |      返回map中key-value对的个数       |
  |          boolean isEmpty()          |          判断当前map是否为空          |
  |     boolean equals(Object obj)      |   判断当前map和参数对象obj是否相等    |
  |            Set keySet()             |       返回所有key构成的Set集合        |
  |         Collection values()         |   返回所有value构成的Collection集合   |
  |           Set entrySet()            |   返回所有key-value对构成的Set集合    |

- 遍历

  ```Java
  @Test
  public void test5() {
      Map map = new HashMap();
      map.put("AA", 123);
      map.put(45, 1234);
      map.put("BB", 56);
      //遍历所有的key集：keySet()
      Set set = map.keySet();
      Iterator iterator = set.iterator();
      while (iterator.hasNext()) {
          System.out.println(iterator.next());
      }
      System.out.println();
      //遍历所有的value集：values()
      Collection values = map.values();
      for (Object obj : values) {
          System.out.println(obj);
      }
      System.out.println();
      //遍历所有的key-value
      //方式一：entrySet()
      Set entrySet = map.entrySet();
      Iterator iterator1 = entrySet.iterator();
      while (iterator1.hasNext()) {
          Object obj = iterator1.next();
          //entrySet集合中的元素都是entry
          Map.Entry entry = (Map.Entry) obj;
          System.out.println(entry.getKey() + "---->" + entry.getValue());
      }
      System.out.println();
      //方式二：
      Set keySet = map.keySet();
      Iterator iterator2 = keySet.iterator();
      while (iterator2.hasNext()) {
          Object key = iterator2.next();
          Object value = map.get(key);
          System.out.println(key + "=====" + value);
      }
  }
  ```

  

#### HashMap

作为Map的`主要实现类`；线程`不安全`的，`效率高`；`存储null的key和value`

HashMap的`底层`：

- `JDK7`：`数组+链表`

  ```java
  HashMap map = new HashMap():
  在实例化以后，底层创建了长度是16的一维数组Entry[] table。
  ...可能已经执行过多次put...
  map.put(key1,value1):
  ```

  - 调用`key1`所在类的`hashCode()`计算key1哈希值，此哈希值经过某种算法计算以后，`得到`在`Entry数组`中的`存放位置`

    - 如果此位置上的`数据为空`，此时的key1-value1`添加成功`   --- `情况1`

    - 如果此位置上的`数据不为空`，(意味着此位置上存在一个或多个数据(以链表形式存在))，`比较`key1和已经存在的一个或多个数据的`哈希值`：
      - 如果key1的哈希值与已经存在的数据的`哈希值都不相同`，此时key1-value1`添加成功`   --- `情况2`
      - 如果key1的哈希值和已经存在的某一个数据(key2-value2)的`哈希值相同`，继续`比较`：调用key1所在类的`equals(key2)`方法，比较：
        - 如果equals()返回`false`：此时key1-value1`添加成功`   --- `情况3`
        - 如果equals()返回`true`：使用`value1替换value2`

  > 关于`情况2`和`情况3`：此时key1-value1和原来的数据`以链表的方式存储`
  >
  > 在不断的添加过程中，会涉及到扩容问题，当`超出临界值`(且要存放的位置非空)时，扩容。默认的扩容方式：扩容为原来容量的`2倍`，并将原有的数据`复制过来`

- `JDK8`：`数组+链表+红黑树`

  1. `new HashMap()`：底层`没有创建一个长度为16的数组`
  2. JDK8 `底层的数组`是：`Node[]`，而非Entry[]
  3. `首次调用put()方法`时，底层`创建长度为16的数组`
  4. JDK7 底层结构只有：数组+链表。jdk8中底层结构：数组+链表+红黑树。
  - 形成`链表`时，`七上八下`（jdk7:新的元素指向旧的元素。jdk8：旧的元素指向新的元素）
  - 当数组的某一个索引位置上的元素以`链表`形式存在的`数据个数 > 8` 且当前`数组的长度>64`时，此时此索引位置上的所数据改为使用红黑树存储
    - `DEFAULT_INITIAL_CAPACITY` : HashMap的`默认容量`，16
    - `DEFAULT_LOAD_FACTOR`：HashMap的`默认加载因子`：0.75
    - `threshold`：扩容的`临界值`，=容量*填充因子：16 * 0.75 => 12
    - `TREEIFY_THRESHOLD`：Bucket中`链表长度大于该默认值，转化为红黑树`:8
    - `MIN_TREEIFY_CAPACITY`：桶中的Node被树化时`最小的hash表容量`:64
  
  

##### LinkedHashMap

HashMap的`子类`，保证在遍历map元素时，可以`按照添加的顺序实现遍历`。

在原有的HashMap底层结构基础上，添加了一对指针，指向前一个和后一个元素。

对于`频繁的遍历`操作，此类执行`效率高`于HashMap。

源码中：

```java
//内部类
static class Entry<K,V> extends HashMap.Node<K,V> {
    Entry<K,V> before, after;//能够记录添加的元素的先后顺序
    Entry(int hash, K key, V value, Node<K,V> next) {
    super(hash, key, value, next);
	}
}
```



#### TreeMap

保证`按照添加的key-value对进行排序`，实现排序遍历。此时考虑`key`的`自然排序`或`定制排序`，底层使用红黑树

向TreeMap中`添加key-value`，要求`key`必须`是由同一个类创建的对象`。因为要按照key进行排序：自然排序 、定制排序

- 自然排序：TreeMap 的所有的 Key 必须实现 Comparable 接口，而且所有
  的 Key 应该是同一个类的对象，否则将会抛出 ClasssCastException
- 定制排序：创建 TreeMap 时，传入一个 Comparator 对象，该对象负责对
  TreeMap 中的所有 key 进行排序。此时不需要 Map 的 Key 实现
  Comparable 接口

TreeMap判断`两个key相等的标准`：两个key通过`compareTo()`方法或
者`compare()`方法`返回0`

#### Hashtable

作为`古老`的实现类；线程`安全`的，`效率低`；`不能存储null的key和value`

##### Properties

常用来`处理配置文件`。key和value都是`String类型`

1. <a id="load">pros.load(InputStream inStream)</a>
2. <a id="getProperty">pros.getProperty("键名")</a>

```java
public class PropertiesTest {
    //Properties:常用来处理配置文件。key和value都是String类型
    public static void main(String[] args) {
        FileInputStream fis = null;
        try {
            Properties pros = new Properties();

            fis = new FileInputStream("jdbc.properties");
            pros.load(fis);//加载流对应的文件

            String name = pros.getProperty("name");
            String password = pros.getProperty("password");

            System.out.println("name = " + name + ", password = " + password);
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (fis != null) {
                try {
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }

            }
        }

    }
}
```



### Collections工具类

`Collections`：`操作Collection、Map的工具类`

|                            方法                             |                        作用                        |
| :---------------------------------------------------------: | :------------------------------------------------: |
|                        reverse(List)                        |                反转List中元素的顺序                |
|                        shuffle(List)                        |            对 List 集合元素进行随机排序            |
|                         sort(List)                          |   根据元素的自然顺序对指定List集合元素按升序排序   |
|                   sort(List，Comparator)                    |    根据指定的Comparator产生的顺序对List元素排序    |
|                    swap(List，int， int)                    |     将指定list集合中的i处元素和j处元素进行交换     |
|                                                             |                                                    |
|                   Object max(Collection)                    |    根据元素的自然顺序，返回给定集合中的最大元素    |
|             Object max(Collection，Comparator)              | 根据Comparator指定的顺序，返回给定集合中的最大元素 |
|                   Object min(Collection)                    |    根据元素的自然顺序，返回给定集合中的最小元素    |
|             Object min(Collection，Comparator)              | 根据Comparator指定的顺序，返回给定集合中的最小元素 |
|              int frequency(Collection，Object)              |          返回指定集合中指定元素的出现次数          |
|                void copy(List dest,List src)                |             将src中的内容复制到dest中              |
| boolean replaceAll(List list，Object oldVal，Object newVal) |           使用新值替换List对象的所有旧值           |
|                 static synchronizedXxx(xxx)                 |           将指定集合包装成线程同步的集合           |



## 泛型

[只能是类只能是类只能是类只能是类只能是类只能是类只能是类只能是类只能是类]()

JDK1.5后，把元素的类型设计成一个参数，这个类型参数叫做泛型。所谓泛型，就是允许在定义类、接口时通过一个标识表示类中某个属性的类型或者是某个方法的返回值及参数类型。这个类型参数将在使用时（例如，继承或实现这个接口，用这个类型声明变量、创建对象时）确定（即传入实际的类型参数，也称为类型实参）

> 好处：

- 类型安全
- 便捷

### 泛型定义

#### 泛型类&接口

`interface List<T>`和`class GenTest<K,V>`
其中，T,K,V不代表值，而是`表示类型`。这里使用`任意字母`都可以
常用T表示，是Type的缩写

> 简单来说就是在`类名/接口名后面加个<T>`，用`T`来`指代`后面使用时的`数据类型`(随实例化时定义不同而不同)，在当前类中后面凡是需要使用这个数据类型时都使用T来替换
>
> `T只能是类`，`不能用基本数据类型`填充。但`可以使用包装类`填充

```Java
public class Order<T> {
    String orderName;
    int orderId;
    //类的内部结构就可以使用类的泛型
    T orderT;
    
    public Order(){
        //编译不通过
//        T[] arr = new T[10];
        //编译通过
        T[] arr = (T[]) new Object[10];
    }

    public Order(String orderName,int orderId,T orderT){
        this.orderName = orderName;
        this.orderId = orderId;
        this.orderT = orderT;
    }
    //静态方法中不能使用类的泛型。
//    public static void show(T orderT){
//        System.out.println(orderT);
//    }
    }
}
```

> 静态方法中不能使用泛型，以为静态方法随类的加载而加载，但泛型在实例化后才确定

#### 泛型方法

`泛型方法`：在方法中出现了泛型的结构，泛型参数与类的泛型参数没有任何关系

`[访问权限] <泛型> 返回类型 方法名([泛型标识 参数名称]) 抛出的异常`

> 简单来说就是在`使用一个额外字母替代数据类型`的同时，`额外在前面加个<E>`来表明这是泛型方法。因为编译器可能认为这个E代表的是一个具体的数据类型E

```java
public static <E>  List<E> copyFromArrayToList(E[] arr){
    ArrayList<E> list = new ArrayList<>();
    for(E e : arr){
        list.add(e);
    }
    return list;
}
```

> 泛型方法`可以声明为静态`的
> 原因：泛型参数是在调用方法时确定的。并非在实例化类时确定

### 泛型使用

两种方式：

- `ArrayList<Integer> list = new ArrayList<Integer>();`
- `ArrayList<Integer> list = new ArrayList<>();`

> JDK1.7后，等号右边<>中可以省略类型

```java
//在集合中使用泛型的情况：以HashMap为例
@Test
public void test3() {
    //Map<String,Integer> map = new HashMap<String,Integer>();
    //jdk7新特性：类型推断
    Map<String, Integer> map = new HashMap<>();
    map.put("Tom", 87);
    map.put("Jerry", 87);
    map.put("Jack", 67);
    //map.put(123,"ABC");
    //泛型的嵌套
    Set<Map.Entry<String, Integer>> entry = map.entrySet();
    Iterator<Map.Entry<String, Integer>> iterator = entry.iterator();
    System.out.println(entry);
    while (iterator.hasNext()) {
        Map.Entry<String, Integer> e = iterator.next();
        String key = e.getKey();
        Integer value = e.getValue();
        System.out.println(key + "----" + value);
    }
}
```



### 注意事项

0. - 如果`B是A的一个子类型`（子类或者子接口），而G是具有泛型声明的类或接口，`G<B>并不是G<A>的子类型`，二者并列，不能用`=`赋地址值
   - 类`A是类B的父类`，`A<G>是 B<G>的父类`

1. 泛型类可能有`多个参数`，此时应将多个参数一起放在尖括号内。比如：
    `<E1,E2,E3>`

2. 泛型类的`构造器`如下：`public GenericClass(){}`
    而下面是错误的：public GenericClass<E>(){}

3. 实例化后，操作原来泛型位置的结构必须与指定的泛型类型一致。

4. 泛型`不同的引用不能相互赋值`

   尽管在编译时ArrayList<String>和ArrayList<Integer>是两种类型，但是，在运行时只有一个ArrayList被加载到JVM中。

5. 泛型如果不指定，将被擦除，泛型对应的类型均按照Object处理，但不等价
    于Object。经验：泛型要使用一路都用。要不用，一路都不要用。

6. 如果泛型结构是一个接口或抽象类，则不可创建泛型类的对象。

7. jdk1.7，泛型的简化操作：`ArrayList<Fruit> flist = new ArrayList<>();`

8. 泛型的指定中`不能使用基本数据类型`，可以使用`包装类`替换

9. 在类/接口上声明的泛型，在本类或本接口中即代表某种类型，可以作为非静态
   属性的类型、非静态方法的参数类型、非静态方法的返回值类型。但在`静态方法
   中不能使用类的泛型`

10. `异常类不能是泛型的`

11. 不能使用`new E[]`。但是可以：`E[] elements = (E[])new Object[capacity];`
    参考：ArrayList源码中声明：Object[] elementData，而非泛型参数类型数组。

12. 父类有泛型，子类可以选择保留泛型也可以选择指定泛型类型：

    - 子类不保留父类的泛型：按需实现
      - 没有类型 擦除
      - 具体类型
    - 子类保留父类的泛型：泛型子类
      - 全部保留
      - 部分保留

    结论：子类必须是“富二代”，子类除了指定或保留父类的泛型，`还可以增加自
    己的泛型`

### 通配符

由于`泛型继承性的特点`(注意事项0），为了找到泛型如`List<String>`和`List<Object>`的`共同父类`，以便利用多态性来写方法，可以使用`通配符`。

`通配符`：`?`，比如：`List<?>` ，`Map<?,?>`

类`A是类B的父类`，`G<A>`和`G<B>`是没有关系的，二者`共同的父类`是：`G<?>`

- `读取`List的对象list中的元素时，`永远是安全`的，因为不管list的真实类型是什么，它包含的都是Object

- `写入`list中的元素时，`不行`。因为我们`不知道?的元素类型`，我们不能向其中添加对象

  > `唯一的例外的是null`，它是所有类型的成员

> 注意事项

- 注意点1：编译错误：不能用在泛型方法声明上，返回值类型前面<>不能使用?

  ```java
  public static <?> void test(ArrayList<?> list){
  }
  ```

- 注意点2：编译错误：不能用在泛型类的声明上

  ```java
  class GenericTypeClass<?>{
  }
  ```

- 注意点3：编译错误：不能用在创建对象上，右边属于创建集合对象

  ```java
  ArrayList<?> list2 = new ArrayList<?>();
  ```

#### 限制条件通配符

- `? extends A`

  `G<? extends A> `可以作为`G<A>`和`G<B>`的父类，其中B是A的子类

  即继承性来看`小于等于`A

- `? super A`

  `G<? super A>` 可以作为`G<A>`和`G<B>`的父类，其中B是A的父类

  即继承性来看`大于等于`A

```java
@Test
public void test4() {
    List<? extends Person> list1 = null;
    List<? super Person> list2 = null;
    List<Student> list3 = new ArrayList<Student>();
    List<Person> list4 = new ArrayList<Person>();
    List<Object> list5 = new ArrayList<Object>();
    list1 = list3;
    list1 = list4;
    //list1 = list5;
    //list2 = list3;
    list2 = list4;
    list2 = list5;
    //读取数据：
    list1 = list3;
    Person p = list1.get(0);
    //编译不通过
    //因为list1的范围是小于等于person,对于list1来说,接收list1的对象就必须能覆盖person和person的子类,故最小是person
    //Student s = list1.get(0);
    list2 = list4;
    Object obj = list2.get(0);
    //编译不通过
    //因为list2的范围是大于等于person,对于list2来说,接收list2的对象就必须能覆盖person和person的父类,故只能是object
    //Person obj = list2.get(0);
    //写入数据：
    //编译不通过
    //因为list1中person的子类不一定和student有关系,可能?实际代表的比student还小
    //list1.add(new Student());
    //编译通过
    //子类能通过传给父类来写入
    list2.add(new Person());
    list2.add(new Student());
}
```

> `为什么单独通配符不能添加数据，但限制条件的通配符可以？`
>
> - 不要把`继承特点和多态`弄混了，继承特点是指List本身没有关系，而不是List泛型中存的元素没有关系
> - `单独通配符`由于完全没有指定数据类型，只能存null，因为只有null可以保证是所存元素的类型或其子类
> - `限制条件的通配符`
>   - extends时，由于是向下的，情况与单独通配符类似，只能加null，因为只有null可以保证是所存元素的类型或其子类
>   - super时，由于是向上的，那么此时下面的都一定是通配符所限定类型的子类，所以可以添加



## IO流

![](https://cdn.jsdelivr.net/gh/6hqt9/TyporaNotes/img/202210211133656.png)

> 抽象基类就是抽象类，下面的是具体实现类

I/O是Input/Output的缩写， I/O技术是非常实用的技术，用于处理设备之间的数据传输。如读/写文件，网络通讯等。Java程序中，对于数据的输入/输出操作以“流(stream)” 的方式进行。

- `输入input` --- 进入内存

  读取外部数据（磁盘、光盘等存储设备的数据）到程序（内存）中。

- `输出output` --- 写入磁盘

  将程序（内存）数据输出到磁盘、光盘等存储设备中。

> 分类

- 按数据单位
  - `字节流`（8 bit）：处理文本文件(.txt,.java,.c,.cpp)
  - `字符流`（16 bit）：处理非文本文件(.jpg,.mp3,.mp4,.avi,.doc,.ppt,...)
- 按数据流的流向
  - `输入流`：进入内存
  - `输出流`：写入磁盘
- 按流的角色
  - `节点流`：直接作用于文件(输入输出流)
  - `处理流`：节点流或处理流外面包的流(如缓冲流，能加快传输速度)



### 路径

- 相对路径

  相较于某个路径下，指明的路径

  浏览器中参照当前浏览器`地址栏`中的地址

  > 在IDEA中，`@Test`中，单独的文件名代表的是`当前Module下`，`main方法`中，单独的文件名代表的是`当前工程下`

- 绝对路径

  包含盘符在内的文件或文件目录的路径

- 路径分隔符

  - windows和DOS系统默认使用“\”来表示

  - UNIX和URL使用“/”来表示

  - Java程序支持跨平台运行，因此路径分隔符要慎用。为了解决这个隐患，File类提供了一个常量：public static final String `separator`。根据操作系统，动态的提供分隔符。

    ```java
    File file1 = new File("d:\\atguigu\\info.txt");
    File file2 = new File("d:" + File.separator + "atguigu" + File.separator + "info.txt");
    File file3 = new File("d:/atguigu");
    ```

### File

1. File类的一个对象，代表一个文件或一个文件目录(文件夹)
2. File类声明在`java.io`包下
3. File类中涉及到关于文件或文件目录的创建、删除、重命名、修改时间、文件大小等方法，并未涉及到写入或读取文件内容的操作。如果需要`读取或写入`文件内容，必须`使用IO流`来完成。
4. 后续`File类的对象`常会`作为参数传递到流的构造器`中，指明读取或写入的"终点".

#### 构造器

- `public File(String pathname)`

  以pathname为路径创建File对象，可以是绝对路径或者相对路径，如果pathname是相对路径，则默认的当前路径在系统属性user.dir中存储

- `public File(String parent,String child)`

  以parent为父路径，child为子路径创建File对象

- `public File(File parent,String child)`

  根据一个父File对象和子文件路径创建File对象

```java
public void test1() {
    //构造器1
    File file1 = new File("G:\\Java_doc\\JavaLearning\\day08\\he.txt");
    System.out.println(file1);
    //构造器2：
    File file2 = new File("G:\\Java_doc", "JavaLearning");
    System.out.println(file2);//JavaLearning在Java_doc下
    //构造器3：
    File file3 = new File(file2, "hi.txt");
    System.out.println(file3);//在JavaLearning文件下
}
```

#### 常用方法

- 获取

  |              方法               |                   作用                   |
  | :-----------------------------: | :--------------------------------------: |
  | public String getAbsolutePath() |               获取绝对路径               |
  |     public String getPath()     |            获取路径(根据定义)            |
  |     public String getName()     |                 获取名称                 |
  |    public String getParent()    |   获取上层文件目录路径。若无，返回null   |
  |      public long length()       |        获取文件长度（即：字节数）        |
  |   public long lastModified()    |      获取最后一次的修改时间，毫秒值      |
  |     public String[] list()      | 获取指定目录下的所有文件或文件目录的名称 |
  |    public File[] listFiles()    | 获取指定目录下的所有文件或文件目录的File |

  > 最后两个方法只获取目录下面一级的目录

- 重命名

  |                方法                |             作用             |
  | :--------------------------------: | :--------------------------: |
  | public boolean renameTo(File dest) | 把文件重命名为指定的文件路径 |

  file1.renameTo(file2)为例：
  要想保证返回`true`,需要`file1`在硬盘中是`存在`的，且`file2不`能在硬盘中`存在`
  效果是`移动后改名`

- 判断

  |             方法             |        作用        |
  | :--------------------------: | :----------------: |
  | public boolean isDirectory() | 判断是否是文件目录 |
  |   public boolean isFile()    |   判断是否是文件   |
  |   public boolean exists()    |    判断是否存在    |
  |   public boolean canRead()   |    判断是否可读    |
  |  public boolean canWrite()   |    判断是否可写    |
  |  public boolean isHidden()   |    判断是否隐藏    |

- 创建

  |              方法              |                             作用                             |
  | :----------------------------: | :----------------------------------------------------------: |
  | public boolean createNewFile() |          创建文件。若文件存在，则不创建，返回false           |
  |     public boolean mkdir()     | 创建文件目录返回true<br />如果此文件目录存在，就不创建返回false<br />如果此文件目录的上层目录不存在，也不创建返回false |
  |    public boolean mkdirs()     | 创建文件目录返回true<br />如果此文件目录存在，就不创建返回false<br />如果上层文件目录不存在，一并创建 |

- 删除

  |          方法           |        作用        |
  | :---------------------: | :----------------: |
  | public boolean delete() | 删除文件或者文件夹 |

  > Java中的删除`不走回收站`
  > 要删除一个文件目录，请注意该文件目录内`不能包含`文件或者文件目录



### 字符流

处理文本文件(.txt,.java,.c,.cpp)

#### 输入流

##### 字符输入流

`FileReader`

1. File类的实例化
2. FileReader流的实例化
   - File类作为参数传入构造器
   - String类型路径作为参数传入构造器，底层实例化File调用File作参数的构造器。此时无需额外实例化File
3. 数据的读入(使用`read`方法)
4. 资源的关闭(使用close()方法)

> `read方法`

读入的文件一定要存在，否则就会报FileNotFoundException

- `int read()`

  返回读入的一个字符。如果达到文件末尾，返回-1

- `int read(char[] cbuf)`

  返回每次`读入`cbuf数组中`的字符的个数`。如果达到文件末尾，返回-1
  cbuf数组中元素是从左往右一个个一次更新，`不会重置`。意味着如果`文件读取结束但数组未满`，则`数组中最后几个元素还是上一次读满时的元素`

- `int read(char[] cbuf, int offset, int length)`

  使用较少，从角标offset(偏移量)开始，读取length个元素

> readLine()

一次读一行，`不包括换行符`

```java
@Test
public void testFileReader1() {
    FileReader fr = null;
    try {
        //1.File类的实例化
        File file = new File("hello.txt");
        //2.FileReader流的实例化
        fr = new FileReader(file);
        //3.数据的读入(单个读取)
            //read():返回读入的一个字符。如果达到文件末尾，返回-1
            //方式一：
//        int data = fr.read();
//        while(data != -1){
//            System.out.print((char)data);
//            data = fr.read();
//        }

            //方式二：语法上针对于方式一的修改
//            int data;
//            while ((data = fr.read()) != -1) {
//                System.out.print((char) data);
//            }
        //3.数据的读入(批量读取)
        //read(char[] cbuf):返回每次读入cbuf数组中的字符的个数。如果达到文件末尾，返回-1
        char[] cbuf = new char[5];
        int len;
        while ((len = fr.read(cbuf)) != -1) {
            //方式一：
            //错误的写法
            //for(int i = 0;i < cbuf.length;i++){
                 //System.out.print(cbuf[i]);
            //}
            //正确的写法
            //for(int i = 0;i < len;i++){
                //System.out.print(cbuf[i]);
            //}
            //方式二：
            //错误的写法,对应着方式一的错误的写法
            //String str = new String(cbuf);
            //System.out.print(str);
            //正确的写法
            String str = new String(cbuf, 0, len);
            System.out.print(str);
        }
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        if (fr != null) {//防止FileReader实例化失败
            //4.资源的关闭，必须关闭，因为gc不会自动回收流
            try {
                fr.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```

##### 字符输入缓冲流

`BufferedReader`，属于`处理流`

1. 造文件

2. 造流

   1. 造节点流

      ```java
      FileReader fr = new FileReader((srcFile));
      FileWriter fw = new FileWriter(destFile);
      ```

   2. 造缓冲流

      ```
      BufferedReader br = new BufferedReader(fr);
      BufferedWriter bw = new BufferedWriter(fw);
      ```

      > 节点流作为参数传入构造器

   > 也可以写一起：
   > `BufferedReader br = new BufferedReader(new FileReader(new File("dbcp.txt")));`

3. 复制的细节：读取、写入，`缓冲流当前面的流使用`，其余细节`一致`

4. 资源关闭：`先关闭外层的流，再关闭内层的流`

   > `关闭外层流`的同时，`内层流`也会`自动`的进行`关闭`。关于`内层流的关闭`，我们`可以省略`





#### 输出流

##### 字符输出流

`FileWriter`

1. 提供File类的对象，指明写出到的文件
2. 提供FileWriter的对象，用于数据的写出（File类作为参数传入构造器）
   - 如果流使用的构造器是：`FileWriter(file,false)` / `FileWriter(file)`:对原有文件的`覆盖`
   - 如果流使用的构造器是：`FileWriter(file,true)`:不会对原有文件覆盖，而是在原有文件基础上`追加内容`
   - 上面构造器中参数File可以替换为String类型路径作为参数传入构造器，底层实例化File调用File作参数的构造器。此时无需额外实例化File
3. 写出的操作`wirte`
4. 资源的关闭(使用close()方法)

> `wirte方法`

输出操作，对应的File可以不存在的。并不会报异常

- write(String str)

- write(char[] cbuf)

- write(String str, int off, int len)

  off是脚标偏移值，len是长度

- write(char[] cbuf, int off, int len)

  off是脚标偏移值，len是长度

- write(int c)

  这个c代表的是单个字符的代表的整型

```Java
@Test
public void testFileWriter() {
    FileWriter fw = null;
    try {
        //1.提供File类的对象，指明写出到的文件
        File file = new File("hello1.txt");
        //2.提供FileWriter的对象，用于数据的写出
        fw = new FileWriter(file, false);
        char c1 = '5';
        //3.写出的操作
        char[] chars = new char[]{'f', 'd', 'g', '8', '\n'};
        fw.write(chars);
        fw.write(70);
        fw.write("\n就垃圾分类建安费骄傲放假啊");
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        //4.流资源的关闭
        if (fw != null) {
            try {
                fw.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```

##### 字符输出缓冲流

`FileReader`，属于`处理流`

1. 造文件

2. 造流

   1. 造节点流

      ```java
      FileReader fr = new FileReader((srcFile));
      FileWriter fw = new FileWriter(destFile);
      ```

   2. 造缓冲流

      ```
      BufferedReader br = new BufferedReader(fr);
      BufferedWriter bw = new BufferedWriter(fw);
      ```

      > 节点流作为参数传入构造器

   > 也可以写一起：
   > `BufferedWriter bw = new BufferedWriter(new FileWriter(new File("dbcp1.txt")));`

3. 复制的细节：读取、写入，`缓冲流当前面的流使用`，其余细节`一致`

4. 资源关闭：`先关闭外层的流，再关闭内层的流`

   > `关闭外层流`的同时，`内层流`也会`自动`的进行`关闭`。关于`内层流的关闭`，我们`可以省略`

> newLine()方法

提供换行的操作，等价于输出'\n'

### 字节流

处理非文本文件(.jpg,.mp3,.mp4,.avi,.doc,.ppt,...)

#### 输入流

##### 字节输入流

`FileInputStream`

1. File类的实例化
2. FileInputStream流的实例化
   - File类作为参数传入构造器
   - String类型路径作为参数传入构造器，底层实例化File调用File作参数的构造器。此时无需额外实例化File
3. 数据的读入(使用`read`方法)
4. 资源的关闭(使用close()方法)

```Java
@Test
public void testFileInputOutputStream() {
    FileInputStream fis = null;
    FileOutputStream fos = null;
    try {
        //FileInputStream流的实例化
        //FileOutStream流的实例化
        File srcFile = new File("爱情与友情.jpg");
        File destFile = new File("爱情与友情2.jpg");
        //
        fis = new FileInputStream(srcFile);
        fos = new FileOutputStream(destFile);
        //复制的过程
        byte[] buffer = new byte[1024];
        int len;
        while ((len = fis.read(buffer)) != -1) {//输入
            fos.write(buffer, 0, len);//输出
        }
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        if (fos != null) {
            //关闭资源
            try {
                fos.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        if (fis != null) {
            try {
                fis.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```

##### 字节输入缓冲流

`FileInputStream`，属于`处理流`

1. 造文件

2. 造流

   1. 造节点流

      ```java
      FileInputStream fis = new FileInputStream((srcFile));
      FileOutputStream fos = new FileOutputStream(destFile);
      ```

   2. 造缓冲流

      ```
      BufferedInputStream bis = new BufferedInputStream(fis);
      BufferedOutputStream bos = new BufferedOutputStream(fos);
      ```

      > 节点流作为参数传入构造器

   > 也可以写一起：
   > `BufferedInputStream bis = new BufferedInputStream(new FileInputStream(new File("xxx.jpg")));`

3. 复制的细节：读取、写入，`缓冲流当前面的流使用`，其余细节`一致`

4. 资源关闭：`先关闭外层的流，再关闭内层的流`

   > `关闭外层流`的同时，`内层流`也会`自动`的进行`关闭`。关于`内层流的关闭`，我们`可以省略`



#### 输出流

##### 字节输出流

`FileOutputStream`

1. File类的实例化
2. FileOutputStream流的实例化
   - File类作为参数传入构造器
   - String类型路径作为参数传入构造器，底层实例化File调用File作参数的构造器。此时无需额外实例化File
3. 数据的读入(使用`wirte`方法)
4. 资源的关闭(使用close()方法)

```java
@Test
public void testFileInputOutputStream() {
    FileInputStream fis = null;
    FileOutputStream fos = null;
    try {
        //FileInputStream流的实例化
        //FileOutStream流的实例化
        File srcFile = new File("爱情与友情.jpg");
        File destFile = new File("爱情与友情2.jpg");
        //
        fis = new FileInputStream(srcFile);
        fos = new FileOutputStream(destFile);
        //复制的过程
        byte[] buffer = new byte[1024];
        int len;
        while ((len = fis.read(buffer)) != -1) {//输入
            fos.write(buffer, 0, len);//输出
        }
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        if (fos != null) {
            //关闭资源
            try {
                fos.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        if (fis != null) {
            try {
                fis.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```

##### 字节输出缓冲流

`FileOutputStream`，属于`处理流`

1. 造文件

2. 造流

   1. 造节点流

      ```java
      FileInputStream fis = new FileInputStream((srcFile));
      FileOutputStream fos = new FileOutputStream(destFile);
      ```

   2. 造缓冲流

      ```
      BufferedInputStream bis = new BufferedInputStream(fis);
      BufferedOutputStream bos = new BufferedOutputStream(fos);
      ```

      > 节点流作为参数传入构造器

   > 也可以写一起：
   > `BufferedOutputStream bis = new BufferedOutputStream(new FileOutputStream(new File("xxx.jpg")));`

3. 复制的细节：读取、写入，`缓冲流当前面的流使用`，其余细节`一致`

4. 资源关闭：`先关闭外层的流，再关闭内层的流`

   > `关闭外层流`的同时，`内层流`也会`自动`的进行`关闭`。关于`内层流的关闭`，我们`可以省略`

> `flush()`方法

`FileOutputStream`有一个`flush()`方法，功能为`刷新缓冲区`，调用时会直接`清空并写出`缓冲区数据



### 转化流

1. 转换流：属于`字符流`，属于`处理流`
   - `InputStreamReader`：将一个`字节的输入流`转换为`字符的输入流`(读取xx格式的流)
   - `OutputStreamWriter`：将一个`字符的输出流`转换为`字节的输出流`(输出xx格式的流)
2. 作用：提供字节流与字符流之间的`转换`

3. `解码`：字节、字节数组  --->字符数组、字符串
`编码`：字符数组、字符串 ---> 字节、字节数组

#### InputStreamReader

1. File/FileInputStream的实例化

2. InputStreamReader的实例化

   - InputStreamReader(`InputStream in`)

     以`默认字符集`将`字节流`转化为`字符流`

   - InputStreamReader(`InputStream in, String charsetName`)

     以`指定字符集`将`字节流`转化为`字符流`

3. 数据的读入(read方法)

4. 资源流的关闭

```java
//仅作骨架参考
@Test
public void test1() throws IOException {
    FileInputStream fis = new FileInputStream("dbcp.txt");
      InputStreamReader isr = new InputStreamReader(fis);//使用系统默认的字符集
    //参数2指明了字符集，具体使用哪个字符集，取决于文件dbcp.txt保存时使用的字符集
    InputStreamReader isr = new InputStreamReader(fis, "UTF-8");//使用系统默认的字符集
    char[] cbuf = new char[20];
    int len;
    while ((len = isr.read(cbuf)) != -1) {
        String str = new String(cbuf, 0, len);
        System.out.print(str);
    }
    isr.close();
}
```

#### OutputStreamWriter

1. File/FileOutputStream的实例化

2. OutputStreamWriter的实例化

   - OutputStreamWriter(`OutputStream out`)

     以`默认字符集`将`字符流`转化为`字节流`

   - OutputStreamWriter(`OutputStream out, String charsetName`)

     以`指定字符集`将`字符流`转化为`字节流`

3. 数据的写出(write方法)

4. 资源流的关闭

```java
//仅作骨架参考
@Test
public void test2() throws Exception {
    //1.造文件、造流
    File file1 = new File("dbcp.txt");
    File file2 = new File("dbcp_gbk.txt");
    FileInputStream fis = new FileInputStream(file1);
    FileOutputStream fos = new FileOutputStream(file2);
    InputStreamReader isr = new InputStreamReader(fis, "utf-8");
    OutputStreamWriter osw = new OutputStreamWriter(fos, "gbk");
    //2.读写过程
    char[] cbuf = new char[20];
    int len;
    while ((len = isr.read(cbuf)) != -1) {
        osw.write(cbuf, 0, len);
    }
    //3.关闭资源
    isr.close();
    osw.close();
}
```



### 对象流(序列化)

包括`ObjectInputStream`和`OjbectOutputSteam`

用于`存储`和`读取基本数据类型数据或对象`的处理流。它的强大之处就是可以把Java中的对象写入到数据源中，也能把对象从数据源中还原回来

- 序列化：用ObjectOutputStream类保存基本类型数据或对象的机制
- 反序列化：用ObjectInputStream类读取基本类型数据或对象的机制

#### 对象的序列化

`对象序列化机制`允许把内存中的`Java对象转换`成平台无关的`二进制流`，从而允许把这种二进制流持久地`保存`在磁盘上，或通过网络将这种二进制流`传输`到另一个网络节点。当其它程序获取了这种二进制流，就可以`恢复`成原来的Java对象



类需要满足如下的要求，方可序列化：

1. 需要`实现接口`：`Serializable`

2. 当前类提供一个`全局常量`：`serialVersionUID`

   eg:`public static final long serialVersionUID = 475463534532L;`

3. 除了当前类需要实现Serializable接口之外，还必须保证其内部`所有属性`
   也必须是`可序列化`的。（默认情况下，基本数据类型可序列化）

> 如果类固定,不声明UID也可以运行,因为会`默认有一个UID`
> 但`修改类的结构`后,默认的`UID会改变`.此时如果序列化时和反序列化时的`UID不一样`,就会`报错`
> 反序列化需要字节流中的UID与本地相应实体类的UID相同



#### ObjectInputStream

1. ObjectInputStream的实例化ois

   ObjectInputStream(InputStream out)

2. ois.writeXXX

3. ois.flush

4. 关闭流

#### ObjectOutputStream

1. ObjectOutputStream的实例化oos

   ObjectOutputStream(OutputStream out)

2. oos.writeXXX

3. oos.flush

4. 关闭流

> 如果写出到文件，进行文件内容的替换

### RandomAccessFile

随机存取文件流，可以用来实现多线程断点下载。下载前都会建立两个临时文件：一个是与被下载文件大小相同的空文件，另一个是记录文件指针的位置文件，每次暂停的时候，都会保存上一次的指针，然后断点下载的时候，会继续从上一次的地方下载，从而实现断点下载或上传的功能

1. RandomAccessFile直接继承于java.lang.Object类，实现了DataInput和DataOutput接口

2. RandomAccessFile`既可以作为一个输入流，又可以作为一个输出流`

3. 如果RandomAccessFile作为输出流时，写出到的文件如果不存在，则在执行过程中自动创建。
   如果写出到的文件存在，则会`对原有文件内容进行覆盖`。（`默认`情况下，`从头覆盖`）

   > 比如本来abcdefg，写入xyz，变成xyzcdefg

4. 可以通过相关的操作，实现RandomAccessFile“插入”数据的效果

#### 构造器

- RandomAccessFile(File file, String mode)
- RandomAccessFile(String name, String mode)

```
RandomAccessFile raf1 = new RandomAccessFile(new File("爱情与友情.jpg"), "r");
RandomAccessFile raf2 = new RandomAccessFile(new File("爱情与友情1.jpg"), "rw");
```

`mode`：

- `r`: 以`只读`方式打开
- `rw`：打开以便`读取`和`写入`
- `rwd`:打开以便`读取`和`写入`；同步`文件内容`的`更新`
- `rws`:打开以便`读取`和`写入`；同步`文件内容`和`元数据`的`更新`

#### 方法

- void seek(long pos)

  将文件记录指针定位到 pos 位置

- long getFilePointer()

  获取文件记录指针的当前位置

插入数据

```Java
/*
使用RandomAccessFile实现数据的插入效果
 */
@Test
public void test3() throws IOException {
    RandomAccessFile raf1 = new RandomAccessFile("hello.txt", "rw");
    raf1.seek(3);//将指针调到角标为3的位置
    //保存指针3后面的所有数据到StringBuilder中
    StringBuilder builder = new StringBuilder((int) new File("hello.txt").length());
    byte[] buffer = new byte[20];
    int len;
    while ((len = raf1.read(buffer)) != -1) {
        builder.append(new String(buffer, 0, len));
    }
    //调回指针，写入“xyz”
    raf1.seek(3);
    raf1.write("xyz".getBytes());
    //将StringBuilder中的数据写入到文件中
    raf1.write(builder.toString().getBytes());
    raf1.close();
    //思考：将StringBuilder替换为ByteArrayOutputStream
}
```



### 常用功能

#### 删除所有

```Java
public void deleteDirectory(File file) {
	// 如果file是文件，直接到函数最后delete注解
	// 如果file是目录，先把它的下一级干掉，然后删除自己
	if (file.isDirectory()) {
		File[] all = file.listFiles();
		// 循环删除的是file的下一级
		for (File f : all) {// f代表file的每一个下级
			deleteDirectory(f);
		}
	}
	// 删除自己
	file.delete();
}
```



#### 文件加密

```java
//文件的加密
@Test
public void test1() {
    FileInputStream fis = null;
    FileOutputStream fos = null;
    try {
        fis = new FileInputStream("爱情与友情.jpg");
        fos = new FileOutputStream("爱情与友情secret.jpg");
        byte[] buffer = new byte[20];
        int len;
        while ((len = fis.read(buffer)) != -1) {
            //字节数组进行修改
            //错误的
            //            for(byte b : buffer){
            //                b = (byte) (b ^ 5);
            //            }
            //正确的
            for (int i = 0; i < len; i++) {
                buffer[i] = (byte) (buffer[i] ^ 5);
            }
            fos.write(buffer, 0, len);
        }
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        if (fos != null) {
            try {
                fos.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        if (fis != null) {
            try {
                fis.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}

//文件的解密
@Test
public void test2() {
    FileInputStream fis = null;
    FileOutputStream fos = null;
    try {
        fis = new FileInputStream("爱情与友情secret.jpg");
        fos = new FileOutputStream("爱情与友情4.jpg");
        byte[] buffer = new byte[20];
        int len;
        while ((len = fis.read(buffer)) != -1) {
            //字节数组进行修改
            //错误的
            //            for(byte b : buffer){
            //                b = (byte) (b ^ 5);
            //            }
            //正确的
            for (int i = 0; i < len; i++) {
                buffer[i] = (byte) (buffer[i] ^ 5);
            }
            fos.write(buffer, 0, len);
        }
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        if (fos != null) {
            try {
                fos.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        if (fis != null) {
            try {
                fis.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```

#### 字符统计

```java
@Test
public void testWordCount() {
    FileReader fr = null;
    BufferedWriter bw = null;
    try {
        //1.创建Map集合
        Map<Character, Integer> map = new HashMap<Character, Integer>();
        //2.遍历每一个字符,每一个字符出现的次数放到map中
        fr = new FileReader("dbcp.txt");
        int c = 0;
        while ((c = fr.read()) != -1) {
            //int 还原 char
            char ch = (char) c;
            // 判断char是否在map中第一次出现
            if (map.get(ch) == null) {
                map.put(ch, 1);
            } else {
                map.put(ch, map.get(ch) + 1);
            }
        }
        //3.把map中数据存在文件count.txt
        //3.1 创建Writer
        bw = new BufferedWriter(new FileWriter("wordcount.txt"));
        //3.2 遍历map,再写入数据
        Set<Map.Entry<Character, Integer>> entrySet = map.entrySet();
        for (Map.Entry<Character, Integer> entry : entrySet) {
            switch (entry.getKey()) {
                case ' ':
                    bw.write("空格=" + entry.getValue());
                    break;
                case '\t'://\t表示tab 键字符
                    bw.write("tab键=" + entry.getValue());
                    break;
                case '\r'://
                    bw.write("回车=" + entry.getValue());
                    break;
                case '\n'://
                    bw.write("换行=" + entry.getValue());
                    break;
                default:
                    bw.write(entry.getKey() + "=" + entry.getValue());
                    break;
            }
            bw.newLine();
        }
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        //4.关流
        if (fr != null) {
            try {
                fr.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        if (bw != null) {
            try {
                bw.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```





## 网络

`IP 地址`：唯一的标识 Internet 上的计算机（通信实体）

- IPV4：4个字节组成，4个0-255。大概42亿，30亿都在北美，亚洲4亿。2011年初已 经用尽。以点分十进制表示，如192.168.0.1
- IPV6：128位（16个字节），写成8个无符号整数，每个整数用四个十六进制位表示， 数之间用冒号（：）分开，如：3ffe:3201:1401:1280:c8ff:fe4d:db39:1984

`端口号`：标识正在计算机上运行的进程，不同的进程有不同的端口号，被规定为一个 16 位的整数 0~65535

- 公认端口：0~1023。被预先定义的服务通信占用（如：HTTP占用端口 80，FTP占用端口21，Telnet占用端口23）
- 注册端口：1024~49151。分配给用户进程或应用程序。（如：Tomcat占用端口8080，MySQL占用端口3306，Oracle占用端口1521等）
- 动态/私有端口：49152~65535

`Socket`：端口号与IP地址的组合得出一个网络套接字

### InetAddress

InetAddress类对象含有一个Internet主机地址的域名和IP地址 

两个子类：Inet4Address、Inet6Address

#### 实例化

InetAddress类`没有提供公共的构造器`，而是提供了如下几个`静态方法`来获取 InetAddress实例

- public static InetAddress `getLocalHost()`：获取本机地址
- public static InetAddress `getByName(String host)`：根据域名或ip获取地址

#### 常用方法

- public String `getHostAddress()`：返回 IP 地址字符串（以文本表现形式）
- public String `getHostName()`：获取此 IP 地址的主机名
- public boolean `isReachable(int timeout)`：测试是否可以达到该地址

```java
public class InetAddressTest {
    public static void main(String[] args) {
        try {
            //File file = new File("hello.txt");
            InetAddress inet1 = InetAddress.getByName("192.168.10.14");
            System.out.println(inet1);
            InetAddress inet2 = InetAddress.getByName("www.atguigu.com");
            System.out.println(inet2);
            InetAddress inet3 = InetAddress.getByName("127.0.0.1");
            System.out.println(inet3);
            //获取本地ip
            InetAddress inet4 = InetAddress.getLocalHost();
            System.out.println(inet4);
            //getHostName()
            System.out.println(inet2.getHostName());
            //getHostAddress()
            System.out.println(inet2.getHostAddress());
        } catch (UnknownHostException e) {
            e.printStackTrace();
        }
    }
}
```

### Socket

#### 构造器

- `public Socket(InetAddress address,int port)`

  创建一个流套接字并将其连接到指定 IP 地址的指定端口号

- `public Socket(String host,int port)`

  创建一个流套接字并将其连接到指定主机上的指定端口号

#### 常用方法

- `public InputStream getInputStream()`

  返回此套接字的输入流。可以用于`接收`网络消息

-  `public OutputStream getOutputStream()`

  返回此套接字的输出流。可以用于`发送`网络消息

- `public InetAddress getInetAddress()`

  此套接字连接到的远程IP地址；如果套接字是未连接的，则返回 null

- `public InetAddress getLocalAddress()`

  获取套接字绑定的本地地址。即本端的IP地址

- `public int getPort()`

  此套接字连接到的远程端口号；如果尚未连接套接字，则返回0。

- `public int getLocalPort()`

  返回此套接字绑定到的本地端口。如果尚未绑定套接字，则返回 -1。即本端的端口号

- `public void close()`

  关闭此套接字。套接字被关闭后，便不可在以后的网络连接中使用（即无法重新连接或重新绑定）。需要创建新的套接字对象。关闭此套接字也将会关闭该套接字的InputStream 和OutputStream

- `public void shutdownInput()`

  如果在套接字上调用shutdownInput() 后从套接字输入流读取内容，则流将返回EOF（文件结束符）。即不能在从此套接字的输入流中接收任何数据

- `public void shutdownOutput()`

  禁用此套接字的输出流。对于TCP套接字，任何以前写入的数据都将被发送，并且后跟TCP 的正常连接终止序列。如果在套接字上调用shutdownOutput()后写入套接字输出流，则该流将抛出IOException。即不能通过此套接字的输出流发送任何数据

### URL

`URL`(Uniform Resource Locator)：`统一资源定位符`，它表示Internet上某一资源的地址

`<传输协议>://<主机名>:<端口号>/<文件名>#片段名?参数列表`

例如: 
http://192.168.1.100:8080/helloworld/index.jsp#a?username=shkstart&password=123

- `#`片段名：即锚点，例如看小说，直接定位到章节
- `参数列表`格式：参数名=参数值&参数名=参数值....

#### 构造器

- `public URL (String spec)`

  通过一个表示URL地址的字符串可以构造一个URL对象。例
  如：URL url = new URL ("http://www.atguigu.com/");

- `public URL(URL context, String spec)`

  通过基 URL 和相对 URL 构造一个 URL 对象。例如：URL downloadUrl = new URL(url, “download.html")

- `public URL(String protocol, String host, String file)`

  例如：new URL("http", "www.atguigu.com", "download. html");

- `public URL(String protocol, String host, int port, String file)`

  例如：URL gamelan = new URL("http", "www.atguigu.com", 80, "download.html");

#### 常用方法

- 获取

  |            方法             |        作用         |
  | :-------------------------: | :-----------------: |
  |   public String getPath()   | 获取该URL的文件路径 |
  |  public String getQuery()   |  获取该URL的查询名  |
  |   public String getHost()   |  获取该URL的主机名  |
  |   public String getPort()   |  获取该URL的端口号  |
  |   public String getFile()   |  获取该URL的文件名  |
  | public String getProtocol() |  获取该URL的协议名  |



```Java
public class URLTest1 {
    public static void main(String[] args) {
        HttpURLConnection urlConnection = null;
        InputStream is = null;
        FileOutputStream fos = null;
        try {
            URL url = new URL("http://localhost:8080/examples/beauty.jpg");
            urlConnection = (HttpURLConnection) url.openConnection();
            urlConnection.connect();
            is = urlConnection.getInputStream();
            fos = new FileOutputStream("day10\\beauty3.jpg");
            byte[] buffer = new byte[1024];
            int len;
            while((len = is.read(buffer)) != -1){
                fos.write(buffer,0,len);
            }
            System.out.println("下载完成");
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            //关闭资源
            if(is != null){
                try {
                    is.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if(fos != null){
                try {
                    fos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if(urlConnection != null){
                urlConnection.disconnect();
            }
        }
    }
}
```



### Socket的TCP编程

#### 客户端

1. `创建 Socket`

   根据指定服务端的 IP 地址或端口号构造 Socket 类对象。若服务器端响应，则建立客户端到服务器的通信线路。若连接失败，会出现异常

2. `打开连接到 Socket 的输入/出流`

   使用`getInputStream()`方法获得输入流，使用`getOutputStream()`方法获得输出流，进行数据传输

3. `按照一定的协议对 Socket 进行读/写操作`

   通过输入流读取服务器放入线路的信息（但不能读取自己放入线路的信息），通过输出流将信息写入线程

4. `关闭 Socket`

   断开客户端到服务器的连接，释放线路

#### 服务端

1. `调用 ServerSocket(int port)`

   创建一个服务器端套接字，并绑定到指定端口上。用于监听客户端的请求

2. `调用 accept()`

   监听连接请求，如果客户端请求连接，则接受连接，`返回通信套接字对象`

3. `调用该Socket类对象的getOutputStream()和getInputStream()`

   获取输出流和输入流，开始网络数据的发送和接收

4. `关闭ServerSocket和Socket对象`

   客户端访问结束，关闭通信套接字

```java
//从客户端发送文件给服务端，服务端保存到本地。并返回“发送成功”给客户端
public class TCPTest3 {
    /*
        这里涉及到的异常，应该使用try-catch-finally处理
         */
    @Test
    public void client() throws IOException {
        //1.
        Socket socket = new Socket(InetAddress.getByName("127.0.0.1"), 9090);
        //2.
        OutputStream os = socket.getOutputStream();
        //3.
        FileInputStream fis = new FileInputStream(new File("beauty.jpg"));
        //4.
        byte[] buffer = new byte[1024];
        int len;
        while ((len = fis.read(buffer)) != -1) {
            os.write(buffer, 0, len);
        }
        //关闭数据的输出
        socket.shutdownOutput();

        //5.接收来自于服务器端的数据，并显示到控制台上
        InputStream is = socket.getInputStream();
        ByteArrayOutputStream baos = new ByteArrayOutputStream();
        byte[] bufferr = new byte[20];
        int len1;
        while ((len1 = is.read(bufferr)) != -1) {
            baos.write(bufferr, 0, len1);
        }

        System.out.println(baos.toString());

        //6.
        fis.close();
        os.close();
        socket.close();
        baos.close();
    }

    /*
    这里涉及到的异常，应该使用try-catch-finally处理
     */
    @Test
    public void server() throws IOException {
        //1.
        ServerSocket ss = new ServerSocket(9090);
        //2.
        Socket socket = ss.accept();
        //3.
        InputStream is = socket.getInputStream();
        //4.
        FileOutputStream fos = new FileOutputStream(new File("beauty2.jpg"));
        //5.
        byte[] buffer = new byte[1024];
        int len;
        while ((len = is.read(buffer)) != -1) {
            fos.write(buffer, 0, len);
        }

        System.out.println("图片传输完成");

        //6.服务器端给予客户端反馈
        OutputStream os = socket.getOutputStream();
        os.write("你好，美女，照片我已收到，非常漂亮！".getBytes());

        //7.
        fos.close();
        is.close();
        socket.close();
        ss.close();
        os.close();
    }
}
```

### UDP网络通信

1. DatagramSocket与DatagramPacket
2. 建立发送端，接收端
3. 建立数据包
4. 调用Socket的发送、接收方法
5. 关闭Socket

```java
public class UDPTest {
    //发送端
    @Test
    public void sender() throws IOException {
        DatagramSocket socket = new DatagramSocket();
        String str = "我是UDP方式发送的导弹";
        byte[] data = str.getBytes();
        InetAddress inet = InetAddress.getLocalHost();
        DatagramPacket packet = new DatagramPacket(data, 0, data.length, inet, 9090);
        socket.send(packet);
        socket.close();
    }
    //接收端
    @Test
    public void receiver() throws IOException {
        DatagramSocket socket = new DatagramSocket(9090);
        byte[] buffer = new byte[100];
        DatagramPacket packet = new DatagramPacket(buffer, 0, buffer.length);
        socket.receive(packet);
        System.out.println(new String(packet.getData(), 0, packet.getLength()));
        socket.close();
    }
}
```



## 反射

> Java反射机制提供的功能

- 在运行时判断任意一个对象所属的类
- 在运行时构造任意一个类的对象
- 在运行时判断任意一个类所具有的成员变量和方法
- 在运行时获取泛型信息
- 在运行时调用任意一个对象的成员变量和方法
- 在运行时处理注解
- 生成动态代理

> 反射相关的主要API

- java.lang.`Class`:代表一个`类`
- java.lang.`reflect.Method`:代表`类的方法`
- java.lang.`reflect.Field`:代表类的`成员变量`
- java.lang.`reflect.Constructor`:代表`类的构造器`

### Class

java.lang.Class

1. 类的加载过程：
   程序经过javac.exe命令以后，会生成一个或多个字节码文件(.class结尾)。
   接着我们使用java.exe命令对某个字节码文件进行解释运行。相当于将某个字节码文件
   加载到内存中。此过程就称为`类的加载`
   加载到内存中的类，我们就称为`运行时类`，此`运行时类`，就作为`Class的一个实例`。
2. 换句话说，Class的实例就对应着一个运行时类的对象
3. 加载到内存中的运行时类，会`缓存一定的时间`。在此时间之内，我们可以通过不同的方式来获取此运行时类。(获取的实例都是同一个)

#### Class实例的获取

`前三种`方式需要掌握

- 方式一：调用运行时类的属性：`.class`

  ```java
  Class clazz1 = Person.class;
  System.out.println(clazz1);
  ```

- 方式二：通过运行时类的对象,调用`getClass()`

  ```java
  Person p1 = new Person();
  Class clazz2 = p1.getClass();
  System.out.println(clazz2);
  ```

- `方式三`：调用Class的`静态方法`：`forName(String classPath)`使用最多

  1. 需要写完整包名
  2. 会报ClassNotFoundException异常

  ```java
  Class clazz3 = Class.forName("com.atguigu.java.Person");
  System.out.println(clazz3);
  ```

- 方式四：使用类的加载器：`ClassLoader`(了解)

  ```java
  ClassLoader classLoader = ReflectionTest.class.getClassLoader();
  Class clazz4 = classLoader.loadClass("com.atguigu.java.Person");
  System.out.println(clazz4);
  ```
  
  > 这四个class指向同一个

> 哪些类型可以有Class对象？

- `class`：外部类，成员(成员内部类，静态内部类)，局部内部类，匿名内部类
- `interface`：接口
- `[]`：数组
- `enum`：枚举
- `annotation`：注解@interface
- `primitive type`：基本数据类型
- `void`

```java
@Test
public void test4() {
    Class c1 = Object.class;
    Class c2 = Comparable.class;
    Class c3 = String[].class;
    Class c4 = int[][].class;
    Class c5 = ElementType.class;
    Class c6 = Override.class;
    Class c7 = int.class;
    Class c8 = void.class;
    Class c9 = Class.class;
    int[] a = new int[10];
    int[] b = new int[100];
    Class c10 = a.getClass();
    Class c11 = b.getClass();
    // 只要数组的元素类型与维度一样，就是同一个Class
    System.out.println(c10 == c11);
}
```

#### 常用方法

|                       方法                        |                             作用                             |
| :-----------------------------------------------: | :----------------------------------------------------------: |
|         static Class forName(String name)         |               返回指定类名 name 的 Class 对象                |
|               Object newInstance()                |         调用缺省构造函数，返回该Class对象的一个实例          |
|                     getName()                     | 返回此Class对象所表示的实体（类、接口、数组类、基本类型 或void）名称 |
|               Class getSuperClass()               |              返回当前Class对象的父类的Class对象              |
|             Class [] getInterfaces()              |                   获取当前Class对象的接口                    |
|           ClassLoader getClassLoader()            |                      返回该类的类加载器                      |
|               Class getSuperclass()               |           返回表示此Class所表示的实体的超类的Class           |
|          Constructor[] getConstructors()          |            返回一个包含某些Constructor对象的数组             |
| Method getMethod(String  name,Class … paramTypes) |       返回一个Method对象，此对象的形参类型为paramType        |

### ClassLoader

- `Bootstrap ClassLoader`	`引导类加载器`

  用C++编写的，是JVM自带的类加载器，负责Java平台核心库，用来装载核心类库。该加载器`无法直接获取`(输出是null)

- `Extension ClassLoader`	`扩展类加载器`

  负责jre/lib/ext目录下的jar包或–D java.ext.dirs 指定目录下的jar包装入工作库

- `System ClassLoader`	`系统类加载器`

  负责java –classpath 或 –D  java.class.path所指的目录下的类与jar包装入工作，是最常用的加载器，是自定义类的加载器

1. `获取`一个系统类加载器

   ```Java
   ClassLoader classloader = ClassLoader.getSystemClassLoader();
   System.out.println(classloader);
   ```

2. `获取`系统类加载器的`父类`加载器，即扩展类加载器

   ```Java
   classloader = classloader.getParent();
   System.out.println(classloader);
   ```

3. 获取扩展类加载器的父类加载器，即引导类加载器

   ```Java
   classloader = classloader.getParent();
   System.out.println(classloader);
   ```

4. `测试`当前类由`哪个类加载器`进行加载

   ```Java
   classloader = Class.forName("exer2.ClassloaderDemo").getClassLoader();
   System.out.println(classloader);
   ```

5. 测试JDK提供的Object类由哪个类加载器加载

   ```Java
   classloader = Class.forName("java.lang.Object").getClassLoader();
   System.out.println(classloader);
   ```

6. 关于类加载器的一个主要方法：<a id="getResourceAsStream">InputStream getResourceAsStream(String str)</a>:获取`类路径`下的`指定文件`的`输入流`

   这个方法是ClassLoader中的方法，通过系统类加载器调用，可写作：`ClassLoader.getSystemClassLoader().getResourceAsStream("jdbc.properties");`
   
   ```Java
   InputStream in = null;
   in =this.getClass().getClassLoader().getResourceAsStream("exer2\\test.properties"); 
   System.out.println(in);
   ```

### 创建运行时类的对象

[通过Class对象创建运行时类对象]()

#### newInstance()

调用Class对象的newInstance()方法

- 要求：

  1. 类必须有一个无参数的构造器
  2. 类的构造器的访问权限需要足够

- 示例：

  ```Java
  @Test
  public void test1() throws IllegalAccessException, InstantiationException {
      Class<Person> clazz = Person.class;
      /*
      newInstance():调用此方法，创建对应的运行时类的对象。内部调用了运行时类的空参的构造器。
      要想此方法正常的创建运行时类的对象，要求：
      1.运行时类必须提供空参的构造器
      2.空参的构造器的访问权限得够。通常，设置为public。
      在javabean中要求提供一个public的空参构造器。原因：
      1.便于通过反射，创建运行时类的对象
      2.便于子类继承此运行时类时，默认调用super()时，保证父类有此构造器
       */
      Person obj = clazz.newInstance();
      System.out.println(obj);
  }
  ```

- 动态性：

  ```Java
  @Test
  public void test2() {
      for (int i = 0; i < 100; i++) {
          int num = new Random().nextInt(3);//0,1,2
          String classPath = "";
          switch (num) {
              case 0:
                  classPath = "java.util.Date";
                  break;
              case 1:
                  classPath = "java.lang.Object";
                  break;
              case 2:
                  classPath = "com.atguigu.java.Person";
                  break;
          }
          try {
              Object obj = getInstance(classPath);
              System.out.println(obj);
          } catch (Exception e) {
              e.printStackTrace();
          }
      }
  }
  public Object getInstance(String classPath) throws Exception {
      Class clazz = Class.forName(classPath);
      return clazz.newInstance();
  }
  ```

#### getDeclaredConstructor

1. 通过Class类的`getDeclaredConstructor(Class … parameterTypes)`取得本类的指定形参类型的构造器
2. 向构造器的形参中`传递`一个对象数组进去，里面包含了构造器中所需的各个`参数`
3. 通过`Constructor实例化对象`

```java
String name = “atguigu.java.Person";
Class clazz = null;
clazz = Class.forName(name);
Constructor con = clazz.getConstructor(String.class,Integer.class);
Person p2 = (Person) con.newInstance("Peter",20);
System.out.println(p2);
```



### 获取运行时类的结构

[通过Class对象获取运行时类的结构]()

#### 获取属性及修饰词

- `class.getField(String name)`：根据`指定名字`获取`当前运行时类`及其`父类`中声明为`public`访问权限的属性
- `class.getDeclaredField(String name)`：根据`指定名字`获取`当前运行时类`中声明的`属性`（`不包含父类`中声明的属性）

- `class.getFields()`：获取`当前运行时类`及其`父类`中声明为`public`访问权限的属性
- `class.getDeclaredFields()`：获取`当前运行时类`中声明的`所有`属性（`不包含父类`中声明的属性）



- `field.getModifiers()`：获取`权限修饰符`，输出默认为0，1，2...等数字，代表权限修饰符，获取public，private等可以调用`Modifier.toString(modifier)`来得到
- `field.getType()`：获取`数据类型`，获取的完整的数据类型，如private class java.lang.String，如果不想要class，可以调用type.getName()
- `field.getName()`：获取`变量名`，即属性的

```Java
@Test
public void test1(){
    Class clazz = Person.class;
    //获取属性结构
    //getFields():获取当前运行时类及其父类中声明为public访问权限的属性
    Field[] fields = clazz.getFields();
    for(Field f : fields){
        System.out.println(f);
    }
    System.out.println();
    //getDeclaredFields():获取当前运行时类中声明的所有属性。（不包含父类中声明的属性）
    Field[] declaredFields = clazz.getDeclaredFields();
    for(Field f : declaredFields){
        System.out.println(f);
        //1.权限修饰符
		  int modifier = f.getModifiers();
		  System.out.print(Modifier.toString(modifier) + "\t");
		  //2.数据类型
		  Class type = f.getType();
		  System.out.print(type.getName() + "\t");
		  //3.变量名
		  String fName = f.getName();
		  System.out.print(fName);
		  System.out.println();
    }
}
```

#### 获取方法及修饰词

- `getMethods()`：获取`当前运行时类`及其所有`父类`中声明为`public`权限的方法
- `getDeclaredMethods()`：获取`当前运行时类`中声明的`所有方法`（`不包含`父类中声明的方法）



- `method.getAnnotations()`：获取方法声明的`注解`
- `method.getModifiers()`：获取`权限修饰符`
- `method.getReturnType().getName()`：获取`返回值类型`,有没有getName输出结果都一样
- `method.getName()`：获取`方法名`
- `method.getParameterTypes()`：获取`形参列表`，下面输出时的getName有没有输出结果都一样
- `method.getExceptionTypes()`：获取抛出的`异常`，下面输出时的getName有没有输出结果都一样

```java
@Test
public void test1() {
    Class clazz = Person.class;
    //getMethods():获取当前运行时类及其所有父类中声明为public权限的方法
    Method[] methods = clazz.getMethods();
    for (Method m : methods) {
        System.out.println(m);
    }
    System.out.println();
    //getDeclaredMethods():获取当前运行时类中声明的所有方法。（不包含父类中声明的方法）
    Method[] declaredMethods = clazz.getDeclaredMethods();
    for (Method m : declaredMethods) {
        System.out.println(m);
        //1.获取方法声明的注解
        Annotation[] annos = m.getAnnotations();
        for (Annotation a : annos) {
            System.out.println(a);
        }
        //2.权限修饰符
        System.out.print(Modifier.toString(m.getModifiers()) + "\t");
        //3.返回值类型
        System.out.print(m.getReturnType().getName() + "\t");
        //4.方法名
        System.out.print(m.getName());
        System.out.print("(");
        //5.形参列表
        Class[] parameterTypes = m.getParameterTypes();
        if (!(parameterTypes == null && parameterTypes.length == 0)) {
            for (int i = 0; i < parameterTypes.length; i++) {
                if (i == parameterTypes.length - 1) {
                    System.out.print(parameterTypes[i].getName() + " args_" + i);
                    break;
                }
                System.out.print(parameterTypes[i].getName() + " args_" + i + ",");
            }
        }
        System.out.print(")");
        //6.抛出的异常
        Class[] exceptionTypes = m.getExceptionTypes();
        if (exceptionTypes.length > 0) {
            System.out.print("throws ");
            for (int i = 0; i < exceptionTypes.length; i++) {
                if (i == exceptionTypes.length - 1) {
                    System.out.print(exceptionTypes[i].getName());
                    break;
                }
                System.out.print(exceptionTypes[i].getName() + ",");
            }
        }
    }
}
```

#### 获取构造器

- `getConstructors()`：获取`当前运行时类`中声明为`public`的`构造器`
- `getDeclaredConstructors()`：获取`当前运行时类`中声明的`所有`的`构造器`

#### 获取父类

- `getSuperclass()`：获取`运行时类`的`父类`

- `getGenericSuperclass()`：获取`运行时类`的`带泛型`的`父类`

  `获取运行时类的带泛型的父类的泛型`

  1. 获取带泛型的父类
  2. 转成ParameterizedType
  3. getActualTypeArguments()
  4. 读取数组
  
  ```java
  @Test
  public void test4() {
      Class clazz = Person.class;
      Type genericSuperclass = clazz.getGenericSuperclass();
      ParameterizedType paramType = (ParameterizedType) genericSuperclass;
      //获取泛型类型，可能有多个，所以是数组
      Type[] actualTypeArguments = paramType.getActualTypeArguments();
      //System.out.println(actualTypeArguments[0].getTypeName());
      System.out.println(((Class) actualTypeArguments[0]).getName());
  }
  ```

#### 获取接口

- `getInterfaces()`：获取`运行时类`实现的`接口`
- `getSuperclass().getInterfaces()`：获取`运行时类`的`父类`实现的`接口`

#### 获取包名

- `getPackage()`：获取`运行时类`所在的`包`

#### 获取注解

- `getAnnotations()`：获取`运行时类`声明的`注解`

### 调用运行时类的结构

[先获取运行时类的结构，再通过获取的结构进行调用]()

#### 调用属性

1. 创建`Class`实例

2. 创建`运行时类`的对象

3. `getDeclaredField(String fieldName)`：获取运行时类中指定变量名的属性

   > getField(String fieldName)用的少，一般用上面的

4. `field.setAccessible(true)`：设置保证当前属性是可访问的

5. `获取`、`设置`指定对象的此`属性值`

   - `field.get()`：`参数1`：获取哪个对象(运行时类)的当前属性值

   - `set()`：`参数1`：指明设置哪个对象(运行时类)的属性
                        `参数2`：将此属性值设置为多少

     > 如果调用的是`静态属性`，`参数1`用`类.class`或`null`替换

```Java
@Test
public void testField1() throws Exception {
    Class clazz = Person.class;
    //创建运行时类的对象
    Person p = (Person) clazz.newInstance();
    //1. getDeclaredField(String fieldName):获取运行时类中指定变量名的属性
    Field name = clazz.getDeclaredField("name");
    //2.保证当前属性是可访问的
    name.setAccessible(true);
    //3.获取、设置指定对象的此属性值
    String name1 = (String) name.get(p);
    name.set(p, "Tom");
    System.out.println(name.get(p));
}
```

#### 调用方法

1. 创建`Class`实例

2. 创建`运行时类`的对象

3. `getDeclaredMethod()`：获取指定的某个方法
   `参数1` ：指明获取的方法的名称  `参数2`：指明获取的方法的形参列表

4. `method.setAccessible(true)`：设置保证当前方法是可访问的

5. 调用方法的`invoke()`：`参数1`：方法的调用者  `可变形参2`：给方法形参赋值的实参

   `invoke()的返回值`即为`对应类`中`调用的方法的返回值`

   > 如果调用的是`静态方法`，`参数1`用`类.class`或`null`替换

```Java
@Test
public void testMethod() throws Exception {
    Class clazz = Person.class;
    //创建运行时类的对象
    Person p = (Person) clazz.newInstance();
    /*
    1.获取指定的某个方法
    getDeclaredMethod():参数1 ：指明获取的方法的名称  参数2：指明获取的方法的形参列表
     */
    Method show = clazz.getDeclaredMethod("show", String.class);
    //2.保证当前方法是可访问的
    show.setAccessible(true);
    /*
    3. 调用方法的invoke():参数1：方法的调用者  参数2：给方法形参赋值的实参
    invoke()的返回值即为对应类中调用的方法的返回值。
     */
    Object returnValue = show.invoke(p, "CHN"); //String nation = p.show("CHN");
    System.out.println(returnValue);
    System.out.println("*************如何调用静态方法*****************");//调用时参数用类.class或null
    // private static void showDesc()
    Method showDesc = clazz.getDeclaredMethod("showDesc");
    showDesc.setAccessible(true);
    //如果调用的运行时类中的方法没有返回值，则此invoke()返回null
      Object returnVal = showDesc.invoke(null);
    Object returnVal = showDesc.invoke(Person.class);
    System.out.println(returnVal);//null
}
```

#### 调用构造器

1. 创建`Class`实例
2. `getDeclaredConstructor()`：获取指定的构造器    `参数`：指明`构造器`的`参数列表`
3. `constructor.setAccessible(true)`：设置保证此构造器是可访问的
4. `constructor.newInstance(args...)`：调用此构造器创建运行时类的对象

```java
@Test
public void testConstructor() throws Exception {
    Class clazz = Person.class;
    //private Person(String name)
    /*
    1.获取指定的构造器
    getDeclaredConstructor():参数：指明构造器的参数列表
     */
    Constructor constructor = clazz.getDeclaredConstructor(String.class);
    //2.保证此构造器是可访问的
    constructor.setAccessible(true);
    //3.调用此构造器创建运行时类的对象
    Person per = (Person) constructor.newInstance("Tom");
    System.out.println(per);
}
```





# JDBC

JDBC总共做三件事：

1. 获取连接
2. 操作数据库
3. 关闭连接

基础操作中分别将这三件事以最基础的方式实现

数据库连接池优化替代1与3

DBUtils优化替代2，也可以简化3





- JDBC接口（API）包括两个层次：
  - 面向应用的API：Java API，抽象接口，供应用程序开发人员使用（连接数据库，执行SQL语句，获得结果）
  - 面向数据库的API：Java Driver API，供开发商开发数据库驱动程序用

> ORM思想(object relational mapping)

- 一个`数据表`对应一个`java类`
- 表中的`一条记录`对应java类的`一个对象`
- 表中的一个`字段`对应java类的一个`属性`

## 数据类型

> 数据对应转换表

|      Java类型      |         SQL类型          |
| :----------------: | :----------------------: |
|      boolean       |           BIT            |
|        byte        |         TINYINT          |
|       short        |         SMALLINT         |
|        int         |         INTEGER          |
|        long        |          BIGINT          |
|       String       | CHAR,VARCHAR,LONGVARCHAR |
|     byte array     |    BINARY,VAR BINARY     |
|   java.sql.Date    |           DATE           |
|   java.sql.Time    |           TIME           |
| java.sql.Timestamp |        TIMESTAMP         |

### BLOB类型

|    类型    |   大小（字节）    |
| :--------: | :---------------: |
|  TinyBlob  |  最大 255 (2^8)   |
|    Blob    |  最大 65k (2^16)  |
| MediumBlob | 最大 16M() (2^24) |
|  LongBlob  |  最大 4G (2^32)   |

- MySQL中，BLOB是一个二进制大型对象，是一个可以存储大量数据的容器，它能容纳不同大小的数据。
- 插入BLOB类型的数据`必须使用PreparedStatement`，因为BLOB类型的数据`无法使用字符串拼接写`

- MySQL的四种BLOB类型(除了在存储的最大信息量上不同外，他们是等同的)

- 实际使用中根据需要存入的数据大小定义不同的BLOB类型。
- 需要注意的是：如果存储的文件过大，数据库的性能会下降。
- 如果在指定了相关的Blob类型以后，还报错：xxx too large，那么在mysql的安装目录下，找my.ini文件加上如下的配置参数： **max_allowed_packet=16M**。同时注意：修改了my.ini文件之后，需要重新启动mysql服务

- 向数据表customers中插入Blob类型的字段

  ```java
  //向数据表customers中插入Blob类型的字段
  @Test
  public void testInsert() throws Exception {
      Connection conn = JDBCUtils.getConnection();
      String sql = "insert into customers(name,email,birth,photo)values(?,?,?,?)";
      PreparedStatement ps = conn.prepareStatement(sql);
      ps.setObject(1, "袁浩");
      ps.setObject(2, "yuan@qq.com");
      ps.setObject(3, "1992-09-08");
      FileInputStream is = new FileInputStream(new File("girl.jpg"));
      ps.setBlob(4, is);
      ps.execute();
      JDBCUtils.closeResource(conn, ps);
  }
  ```

- 查询数据表customers中Blob类型的字段

  ```Java
  //查询数据表customers中Blob类型的字段
  @Test
  public void testQuery() {
      Connection conn = null;
      PreparedStatement ps = null;
      InputStream is = null;
      FileOutputStream fos = null;
      ResultSet rs = null;
      try {
          conn = JDBCUtils.getConnection();
          String sql = "select id,name,email,birth,photo from customers where id = ?";
          ps = conn.prepareStatement(sql);
          ps.setInt(1, 21);
          rs = ps.executeQuery();
          if (rs.next()) {
              //			方式一：
              //			int id = rs.getInt(1);
              //			String name = rs.getString(2);
              //			String email = rs.getString(3);
              //			Date birth = rs.getDate(4);
              //方式二：
              int id = rs.getInt("id");
              String name = rs.getString("name");
              String email = rs.getString("email");
              Date birth = rs.getDate("birth");
              Customer cust = new Customer(id, name, email, birth);
              System.out.println(cust);
              //将Blob类型的字段下载下来，以文件的方式保存在本地
              Blob photo = rs.getBlob("photo");
              is = photo.getBinaryStream();
              fos = new FileOutputStream("zhangyuhao.jpg");
              byte[] buffer = new byte[1024];
              int len;
              while ((len = is.read(buffer)) != -1) {
                  fos.write(buffer, 0, len);
              }
          }
      } catch (Exception e) {
          e.printStackTrace();
      } finally {
          try {
              if (is != null)
                  is.close();
          } catch (IOException e) {
              e.printStackTrace();
          }
          try {
              if (fos != null)
                  fos.close();
          } catch (IOException e) {
              e.printStackTrace();
          }
          JDBCUtils.closeResource(conn, ps, rs);
      }
  }
  ```

  

## 基础操作

### 获取连接

> `Driver接口`

- `java.sql.Driver` 接口是所有`JDBC驱动程序需要实现的接口`。这个接口是`提供给数据库厂商`使用的，不同数据库厂商提供不同的实现
- 在程序中不需要直接去访问实现了 Driver 接口的类，而是由驱动程序管理器类(java.sql.DriverManager)去调用这些Driver实现
  - `Oracle`的驱动：oracle.jdbc.driver.OracleDriver
  - `MySQL`的驱动：com.mysql.cj.jdbc.Driver

> url：jdbc:mysql://localhost:3306/test

jdbc:mysql：协议与子协议
localhost：ip地址
3306：默认mysql的端口号
test：test数据库

#### 基础连接

使用`mysql-connector-java`包实现

1. 获取`Driver`实现类对象

2. 创建`String url`：提供要连接的数据库

3. 创建`java.util.Properties info`：提供连接需要的`用户名`和`密码`

4. 实例化`Connection`：`driver.connect(url, info)`，获取连接

   ```Java
   @Test
   public void testConnection1() throws SQLException {
       // 获取Driver实现类对象
       Driver driver = new com.mysql.cj.jdbc.Driver();
   
       String url = "jdbc:mysql://localhost:3306/test";
       // 将用户名和密码封装在Properties中
       Properties info = new Properties();
       info.setProperty("user", "root");
       info.setProperty("password", "root");
       Connection conn = driver.connect(url, info);
       System.out.println(conn);
   }
   ```

#### 使用反射

程序中`不出现`第三方的api，使得程序具有更好的`可移植性`

1. 获取`Driver`实现类对象：通过反射

2. 创建`String url`：提供要连接的数据库

3. 创建`java.util.Properties info`：提供连接需要的`用户名`和`密码`

4. 实例化`Connection`：`driver.connect(url, info)`，获取连接

   ```Java
   @Test
   public void testConnection2() throws Exception {
       // 1.获取Driver实现类对象：使用反射
       Class clazz = Class.forName("com.mysql.cj.jdbc.Driver");
       Driver driver = (Driver) clazz.newInstance();
       // 2.提供要连接的数据库
       String url = "jdbc:mysql://localhost:3306/test";
       // 3.提供连接需要的用户名和密码
       Properties info = new Properties();
       info.setProperty("user", "root");
       info.setProperty("password", "root");
       // 4.获取连接
       Connection conn = driver.connect(url, info);
       System.out.println(conn);
   }
   ```

#### 使用DriverManager

使用DriverManager替换Driver

1. 获取`Driver`实现类对象：通过反射

2. 提供另外三个连接的基本信息：`url`，`user`，`password`

3. 注册驱动：`DriverManager.registerDriver(driver)`(此步骤目前`可以省略`)

4. 获取连接：`DriverManager.getConnection(url, user, password)`

   ```java
   @Test
   public void testConnection3() throws Exception {
       // 1.获取Driver实现类的对象
       Class clazz = Class.forName("com.mysql.cj.jdbc.Driver");
       Driver driver = (Driver) clazz.newInstance();
       // 2.提供另外三个连接的基本信息：
       String url = "jdbc:mysql://localhost:3306/test";
       String user = "root";
       String password = "root";
       // 注册驱动
       DriverManager.registerDriver(driver);
       // 获取连接
       Connection conn = DriverManager.getConnection(url, user, password);
       System.out.println(conn);
   }
   ```

#### DriverManager++

在mysql的Driver实现类中，声明了如下的操作：

```java
static {
		try {
			java.sql.DriverManager.registerDriver(new Driver());
		} catch (SQLException E) {
			throw new RuntimeException("Can't register driver!");
		}
}
```

> 此静态代码块使得mysql的Driver`类加载`后就会`直接注册驱动`
> 因此操作可以简化如下

1. 提供三个连接的基本信息：`url`，`user`，`password`

2. 加载Driver：`Class.forName("com.mysql.cj.jdbc.Driver")`

3. 获取连接：`DriverManager.getConnection(url, user, password)`

   ```java
   @Test
   public void testConnection4() throws Exception {
       // 1.提供三个连接的基本信息：
       String url = "jdbc:mysql://localhost:3306/test";
       String user = "root";
       String password = "root";
       // 2.加载Driver
       Class.forName("com.mysql.cj.jdbc.Driver");
       // 相较于方式三，可以省略如下的操作：
   	 // Driver driver = (Driver) clazz.newInstance();
   	 // 注册驱动
   	 // DriverManager.registerDriver(driver);
       // 3.获取连接
       Connection conn = DriverManager.getConnection(url, user, password);
       System.out.println(conn);
   }
   ```

#### 最终版：配置文件

- 实现了`数据与代码的分离`，实现了解耦
- 如果需要`修改配置文件`信息，可以`避免程序重新打包`

```properties
user=root
password=root
url=jdbc:mysql://localhost:3306/test?characterEncoding=utf8&useSSL=false&serverTimezone=UTC&rewriteBatchedStatements=true
driverClass=com.mysql.cj.jdbc.Driver
```

1. 创建配置文件并写入数据

2. 读取配置文件中的4个基本信息

   - InputStream is = ClassLoader.getSystemClassLoader().[getResourceAsStream](#getResourceAsStream)("jdbc.properties");
   - pros.[load](#load)(is);
   - String user = pros.[getProperty](#getProperty)("user");
   - . . . . . . 

3. 加载Driver：`Class.forName("com.mysql.cj.jdbc.Driver")`

4. 获取连接：`DriverManager.getConnection(url, user, password)`

   ```Java
   @Test
   public void getConnection5() throws Exception {
       //1.读取配置文件中的4个基本信息
       InputStream is = ConnectionTest.class.getClassLoader().getResourceAsStream("jdbc.properties");
       Properties pros = new Properties();
       pros.load(is);
       String user = pros.getProperty("user");
       String password = pros.getProperty("password");
       String url = pros.getProperty("url");
       String driverClass = pros.getProperty("driverClass");
       //2.加载驱动
       Class.forName(driverClass);
       //3.获取连接
       Connection conn = DriverManager.getConnection(url, user, password);
       System.out.println(conn);
   }
   ```

### 操作与访问数据库

- 数据库连接被用于向数据库服务器发送命令和 SQL 语句，并接受数据库服务器返回的结果。其实一个数据库连接就是一个Socket连接
- 在 java.sql 包中有 3 个接口分别定义了对数据库的调用的不同方式：
  - `Statement`：用于执行静态 SQL 语句并返回它所生成结果的对象
  - `PrepatedStatement`：SQL 语句被预编译并存储在此对象中，可以使用此对象多次高效地执行该语句
  - CallableStatement：用于执行 SQL 存储过程

#### Statement

[不建议使用]()

- 通过调用 `Connection` 对象的 `createStatement()` 方法创建该对象。该对象用于执行静态的 SQL 语句，并且返回执行结果
- Statement 接口中定义了下列方法用于执行 SQL 语句：
  - `int excuteUpdate(String sql)`：执行`更新`操作INSERT、UPDATE、DELETE
  - `ResultSet executeQuery(String sql)`：执行`查询`操作SELECT

> `存在问题`

- **问题一**：存在拼串操作，繁琐
- **问题二**：存在SQL注入问题

要防范 SQL 注入，只要`用PreparedStatement`(从Statement扩展而来) `取代 Statement`就可以了

```java
public class StatementTest {
	// 使用Statement的弊端：需要拼写sql语句，并且存在SQL注入的问题
	//如何避免出现sql注入：只要用 PreparedStatement(从Statement扩展而来) 取代 Statement
	@Test
	public void testLogin() {
		Scanner scanner = new Scanner(System.in);
		
		System.out.print("请输入用户名：");
		String user = scanner.nextLine();
		System.out.print("请输入密码：");
		String password = scanner.nextLine();
		//SELECT user,password FROM user_table WHERE user = '1' or ' AND password = '=1 or '1' = '1'
		String sql = "SELECT user,password FROM user_table WHERE user = '"+ user +"' AND password = '"+ password +"'";
		User returnUser = get(sql,User.class);
		if(returnUser != null){
			System.out.println("登录成功");
		}else{
			System.out.println("用户名不存在或密码错误");
		}
	}
	// 使用Statement实现对数据表的查询操作
	public <T> T get(String sql, Class<T> clazz) {
		T t = null;
		Connection conn = null;
		Statement st = null;
		ResultSet rs = null;
		try {
			// 1.加载配置文件
			InputStream is = StatementTest.class.getClassLoader().getResourceAsStream("jdbc.properties");
			Properties pros = new Properties();
			pros.load(is);
			// 2.读取配置信息
			String user = pros.getProperty("user");
			String password = pros.getProperty("password");
			String url = pros.getProperty("url");
			String driverClass = pros.getProperty("driverClass");
			// 3.加载驱动
			Class.forName(driverClass);
			// 4.获取连接
			conn = DriverManager.getConnection(url, user, password);
			st = conn.createStatement();
			rs = st.executeQuery(sql);
			// 获取结果集的元数据
			ResultSetMetaData rsmd = rs.getMetaData();
			// 获取结果集的列数
			int columnCount = rsmd.getColumnCount();
			if (rs.next()) {
				t = clazz.newInstance();
				for (int i = 0; i < columnCount; i++) {
					// //1. 获取列的名称
					// String columnName = rsmd.getColumnName(i+1);
					// 1. 获取列的别名
					String columnName = rsmd.getColumnLabel(i + 1);
					// 2. 根据列名获取对应数据表中的数据
					Object columnVal = rs.getObject(columnName);
					// 3. 将数据表中得到的数据，封装进对象
					Field field = clazz.getDeclaredField(columnName);
					field.setAccessible(true);
					field.set(t, columnVal);
				}
				return t;
			}
		} catch (Exception e) {
			e.printStackTrace();
		} finally {
			// 关闭资源
			if (rs != null) {
				try {
					rs.close();
				} catch (SQLException e) {
					e.printStackTrace();
				}
			}
			if (st != null) {
				try {
					st.close();
				} catch (SQLException e) {
					e.printStackTrace();
				}
			}
			if (conn != null) {
				try {
					conn.close();
				} catch (SQLException e) {
					e.printStackTrace();
				}
			}
		}
		return null;
	}
}
```

#### PreparedStatement

PreparedStatement接口是Statement 的`子接口`，它表示一条**预编译**过的SQL语句

- 可以通过调用`Connection`对象的`preparedStatement(String sql)`方法获取 PreparedStatement对象

- PreparedStatement对象所代表的SQL语句中的`参数`用问号(`?`)来表示，叫`占位符`
  调用 PreparedStatement对象的`setXxx()`方法来设置这些参数(Xxx代表数据类型)。`setXxx()`方法有`两个参数`：
  `第一个`参数是要设置的SQL语句中的`参数的索引`(`从1开始`)
  `第二个`是设置的SQL语句中的`参数的值`
  
  > `setObject()`方法可以看作复合函数，能够设置各种数据类型

##### 增删改操作

prepareStatement.execute()进行操作

> 使用步骤

1. 读取`配置文件`中的4个基本信息：pros.getProperty("driverClass")

2. 加载`驱动`：Class.forName(driverClass);

3. 获取`连接`：DriverManager.getConnection(url, user, password);

4. 预编译`sql语句`，返回`PreparedStatement的实例`：conn.prepareStatement(sql);

5. `填充占位符`：ps.setString(1, "哪吒");

6. `执行`操作：ps.execute();

7. `资源的关闭`：.close

   ```Java
   @Test
   public void testInsert() {
       Connection conn = null;
       PreparedStatement ps = null;
       try {
           // 1.读取配置文件中的4个基本信息的4个基本信息
           InputStream is = ClassLoader.getSystemClassLoader().getResourceAsStream("jdbc.properties");
           Properties pros = new Properties();
           pros.load(is);
           String user = pros.getProperty("user");
           String password = pros.getProperty("password");
           String url = pros.getProperty("url");
           String driverClass = pros.getProperty("driverClass");
           // 2.加载驱动
           Class.forName(driverClass);
           // 3.获取连接
           conn = DriverManager.getConnection(url, user, password);
   	System.out.println(conn);
           //4.预编译sql语句，返回PreparedStatement的实例
           String sql = "insert into customers(name,email,birth)values(?,?,?)";//?:占位符
           ps = conn.prepareStatement(sql);
           //5.填充占位符
           ps.setString(1, "哪吒");
           ps.setString(2, "nezha@gmail.com");
           SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
           java.util.Date date = sdf.parse("1000-01-01");
           ps.setDate(3, new Date(date.getTime()));
           //6.执行操作
           ps.execute();
       } catch (Exception e) {
           e.printStackTrace();
       } finally {
           //7.资源的关闭
           try {
               if (ps != null)
                   ps.close();
           } catch (SQLException e) {
               e.printStackTrace();
           }
           try {
               if (conn != null)
                   conn.close();
           } catch (SQLException e) {
               e.printStackTrace();
           }
       }
   }
   ```

##### 查询操作

prepareStatement.executeQuery()进行操作

###### ResultSet

- 查询需要调用PreparedStatement 的`executeQuery()`方法，`查询结果`是一个`ResultSet 对象`

- ResultSet 对象以逻辑表格的形式封装了执行数据库操作的结果集，ResultSet 接口由数据库厂商提供实现

- ResultSet 返回的实际上就是一张数据表。有一个指针指向数据表的第一条记录的前面。

- ResultSet 对象维护了一个指向当前数据行的**游标**，初始的时候，游标在第一行之前，可以通过 ResultSet 对象的`next()`方法移动到下一行。调用 next()方法检测下一行是否有效。若有效，该方法返回 true，且指针下移。相当于Iterator对象的 `hasNext() 和 next() 方法的结合体`

- 当指针指向一行时, 可以通过调用 `getXxx(int index)` 或 `getXxx(String columnLabel)` 获取每一列的值。

  - 例如: getInt(1), getString("name")
  - **注意：Java与数据库交互涉及到的相关Java API中的索引都从1开始。**

- ResultSet 接口的常用方法：

  - boolean next()

  - getString()

  - ###### …

###### ResultSetMetaData

调用 ResultSet 的 `getMetaData()` 方法即可获取`ResultSetMetaData`

- 可用于获取关于 ResultSet 对象中列的类型和属性信息的对象

- ResultSetMetaData meta = rs.getMetaData();
  - `getColumnName(int column)`：获取指定`列的名称`
  - `getColumnLabel(int column)`：获取指定`列的别名`
  - `getColumnCount()`：返回当前 ResultSet 对象中的`列数`。 

  - getColumnTypeName(int column)：检索指定列的数据库特定的类型名称。 
  - getColumnDisplaySize(int column)：指示指定列的最大标准宽度，以字符为单位。 
  - `isNullable(int column)`：指示指定列中的值是否可以为 null。 

  - isAutoIncrement(int column)：指示是否自动为指定列进行编号，这样这些列仍然是只读的。 

###### 参考步骤

> 不太完整，具体可以参考本节`最终方法封装`的`查询操作`

1. 读取`配置文件`中的4个基本信息：pros.getProperty("driverClass")

2. 加载`驱动`：Class.forName(driverClass);

3. 获取`连接`：DriverManager.getConnection(url, user, password);

4. 预编译`sql语句`，返回`PreparedStatement的实例`：conn.prepareStatement(sql);

5. `填充占位符`：ps.setObject(1, 1);

6. `执行`操作：ResultSet resultSet = ps.executeQuery();

7. 处理结果集：
   if(resultSet.next())
   `next()`:`判断`结果集的下一条是否有数据，如果`有数据返回true`,并`指针下移`；如果返回`false`,`指针不会下移`
   resultSet.getXxx(int columnIndex)：参数代表查询结果中第几列的数据，调用对应数据类型的方法，最后封装到类中

8. `资源的关闭`：.close

   ```Java
   @Test
   public void testQuery1() {
   	Connection conn = null;
   	PreparedStatement ps = null;
   	ResultSet resultSet = null;
   	try {
   		conn = JDBCUtils.getConnection();
   		String sql = "select id,name,email,birth from customers where id = ?";
   		ps = conn.prepareStatement(sql);
   		ps.setObject(1, 1);
   		
   		//执行,并返回结果集
   		resultSet = ps.executeQuery();
   		//处理结果集
   		if(resultSet.next()){//next():判断结果集的下一条是否有数据，如果有数据返回true,并指针下移；如果返回false,指针不会下移。
   			
   			//获取当前这条数据的各个字段值
   			int id = resultSet.getInt(1);
   			String name = resultSet.getString(2);
   			String email = resultSet.getString(3);
   			Date birth = resultSet.getDate(4);
   			
   		//方式一：
   		//System.out.println("id = " + id + ",name = " + name + ",email = " + email + ",birth = " + birth);
   			
   		//方式二：
   		//Object[] data = new Object[]{id,name,email,birth};
   			//方式三：将数据封装为一个对象（推荐）
   			Customer customer = new Customer(id, name, email, birth);
   			System.out.println(customer);
   		}
   	} catch (Exception e) {
   		e.printStackTrace();
   	}finally{
   		//关闭资源
   		JDBCUtils.closeResource(conn, ps, resultSet);
   	}
   	
   }
   ```

### 批量操作数据

1. `PreparedStatement`因为是`预编译`的，全程只有一个sql语句,本身比Statement`效率高`

2. 通过`preparedStatement`的`addBatch()`(添加)、`executeBatch()`(执行)、`clearBatch()`(清空)

   > mysql服务器默认是关闭批处理的，我们需要通过一个参数，让mysql开启批处理的支持：`?rewriteBatchedStatements=true`写在配置文件的`url后面`
   >
   > 使用更新的mysql 驱动：mysql-connector-java-5.1.37-bin.jar(`改用8.0`)

3. 设置连接`不允许自动提交数据`：`conn.setAutoCommit(false);`

```Java
@Test
public void testInsert3() {
    Connection conn = null;
    PreparedStatement ps = null;
    try {
        long start = System.currentTimeMillis();
        conn = JDBCUtils.getConnection();
        //设置不允许自动提交数据
        conn.setAutoCommit(false);
        String sql = "insert into goods(name)values(?)";
        ps = conn.prepareStatement(sql);
        for (int i = 1; i <= 1000000; i++) {
            ps.setObject(1, "name_" + i);
            //1."攒"sql
            ps.addBatch();
            if (i % 500 == 0) {
                //2.执行batch
                ps.executeBatch();
                //3.清空batch
                ps.clearBatch();
            }
        }
        //提交数据
        conn.commit();
        long end = System.currentTimeMillis();
        System.out.println("花费的时间为：" + (end - start));
    } catch (Exception e) {
        e.printStackTrace();
    } finally {
        JDBCUtils.closeResource(conn, ps);
    }
}
```



### 最终方法封装

<a id="不考虑事务">考虑事务方法封装</a>[见数据库事务BaseDAO](#考虑事务)

#### 获取连接

```java
/**
 * 
 * @Description 获取数据库的连接
 * @author 
 * @date 上午9:11:23
 * @return
 * @throws Exception
 */
public static Connection getConnection() throws Exception {
	// 1.读取配置文件中的4个基本信息
	InputStream is = ClassLoader.getSystemClassLoader().getResourceAsStream("jdbc.properties");
	Properties pros = new Properties();
	pros.load(is);
	String user = pros.getProperty("user");
	String password = pros.getProperty("password");
	String url = pros.getProperty("url");
	String driverClass = pros.getProperty("driverClass");
	// 2.加载驱动
	Class.forName(driverClass);
	// 3.获取连接
	Connection conn = DriverManager.getConnection(url, user, password);
	return conn;
}
/**
```

#### 增删改操作

```java
/** 
 * @Description: 通用的增删改操作
 * @param sql sql语句
 * @param args sql语句中的占位符，代表查询的属性
 * @return: void 
 * @Author: Transformer HE
 * @Date: 2022/9/26 20:58
 */
public void update(String sql, Object... args) {
//sql中占位符的个数与可变形参的长度相同！
    Connection conn = null;
    PreparedStatement ps = null;
    try {
        //1.获取数据库的连接
        conn = JDBCUtils.getConnection();
        //2.预编译sql语句，返回PreparedStatement的实例
        ps = conn.prepareStatement(sql);
        //3.填充占位符
        for (int i = 0; i < args.length; i++) {
            ps.setObject(i + 1, args[i]);//小心参数声明错误！！
        }
        //4.执行
        ps.execute();
    } catch (Exception e) {
        e.printStackTrace();
    } finally {
        //5.资源的关闭
        JDBCUtils.closeResource(conn, ps);
    }
}
```

#### 查询操作

##### 单个查询

```Java
/**
 * @param clazz 查询结果对象的Class对象
 * @param sql   查询语句
 * @param args  查询语句中的占位符
 * @Description: 查询一条数据
 * @return: T
 * @Author: Transformer HE
 * @Date: 2022/9/26 21:03
 */
public <T> T getForOne(Class<T> clazz,String sql, Object... args) {
	Connection conn = null;
	PreparedStatement ps = null;
	ResultSet rs = null;
	try {
		conn = JDBCUtils.getConnection();
		ps = conn.prepareStatement(sql);
		for (int i = 0; i < args.length; i++) {
			ps.setObject(i + 1, args[i]);
		}
		rs = ps.executeQuery();
		// 获取结果集的元数据 :ResultSetMetaData
		ResultSetMetaData rsmd = rs.getMetaData();
		// 通过ResultSetMetaData获取结果集中的列数
		int columnCount = rsmd.getColumnCount();
		if (rs.next()) {
			T t = clazz.newInstance();
			// 处理结果集一行数据中的每一个列
			for (int i = 0; i < columnCount; i++) {
				// 获取列值
				Object columValue = rs.getObject(i + 1);
				// 获取每个列的列名
				// String columnName = rsmd.getColumnName(i + 1);
                  // 获取每个列的别名
				String columnLabel = rsmd.getColumnLabel(i + 1);
				// 给t对象指定的columnName属性，赋值为columValue：通过反射
				Field field = clazz.getDeclaredField(columnLabel);
				field.setAccessible(true);
				field.set(t, columValue);
			}
			return t;
		}
	} catch (Exception e) {
		e.printStackTrace();
	} finally {
		JDBCUtils.closeResource(conn, ps, rs);
	}
	return null;
}
```



##### 批量查询

```Java
/**
 * @param clazz 查询结果对象的Class对象
 * @param sql 查询语句
 * @param args 查询语句中的占位符
 * @Description: 查询多条数据
 * @return: java.util.List<T> 
 * @Author: Transformer HE
 * @Date: 2022/9/26 21:08
 */
public <T> List<T> getForList(Class<T> clazz, String sql, Object... args) {
    Connection conn = null;
    PreparedStatement ps = null;
    ResultSet rs = null;
    try {
        conn = JDBCUtils.getConnection();
        ps = conn.prepareStatement(sql);
        for (int i = 0; i < args.length; i++) {
            ps.setObject(i + 1, args[i]);
        }
        rs = ps.executeQuery();
        // 获取结果集的元数据 :ResultSetMetaData
        ResultSetMetaData rsmd = rs.getMetaData();
        // 通过ResultSetMetaData获取结果集中的列数
        int columnCount = rsmd.getColumnCount();
        //创建集合对象
        ArrayList<T> list = new ArrayList<T>();
        while (rs.next()) {
            T t = clazz.newInstance();
            // 处理结果集一行数据中的每一个列:给t对象指定的属性赋值
            for (int i = 0; i < columnCount; i++) {
                // 获取列值
                Object columValue = rs.getObject(i + 1);
                // 获取每个列的列名
                // String columnName = rsmd.getColumnName(i + 1);
                // 获取每个列的别名
                String columnLabel = rsmd.getColumnLabel(i + 1);
                // 给t对象指定的columnName属性，赋值为columValue：通过反射
                Field field = clazz.getDeclaredField(columnLabel);
                field.setAccessible(true);
                field.set(t, columValue);
            }
            list.add(t);
        }
        return list;
    } catch (Exception e) {
        e.printStackTrace();
    } finally {
        JDBCUtils.closeResource(conn, ps, rs);
    }
    return null;
}
```



#### 关闭资源

##### 增删改关闭

```Java
/**
 * 
 * @Description 关闭连接和Statement的操作
 * @author shkstart
 * @date 上午9:12:40
 * @param conn
 * @param ps
 */
public static void closeResource(Connection conn,Statement ps){
	try {
		if(ps != null)
			ps.close();
	} catch (SQLException e) {
		e.printStackTrace();
	}
	try {
		if(conn != null)
			conn.close();
	} catch (SQLException e) {
		e.printStackTrace();
	}
}
```

##### 查询关闭

```Java
/**
 * 
 * @Description 关闭资源操作
 * @author shkstart
 * @date 上午10:21:15
 * @param conn Connection
 * @param ps PreparedStatement
 * @param rs ResultSet
 */
public static void closeResource(Connection conn,Statement ps,ResultSet rs){
	try {
		if(ps != null)
			ps.close();
	} catch (SQLException e) {
		e.printStackTrace();
	}
	try {
		if(conn != null)
			conn.close();
	} catch (SQLException e) {
		e.printStackTrace();
	}
	try {
		if(rs != null)
			rs.close();
	} catch (SQLException e) {
		e.printStackTrace();
	}
}
```



## 数据库事务

- **数据库事务：**

  - **一组逻辑操作单元**,使数据从`一种状态变换到另一种状态`

    **一组逻辑操作单元**：一个或多个DML操作(增删改查)


- **事务处理的原则：**

  - 保证所有事务都作为一个工作单元来执行，`即使出现了故障，都不能改变这种执行方式`

  - 当在一个事务中执行多个操作时
    要么所有的事务`都被提交`(`commit`)，那么这些修改就永久地保存下来
    要么数据库管理系统将`放弃所作的所有修改`，整个`事务回滚`(`rollback`)到`最初状态`。


  - `数据一旦提交，就不可回滚`




- **哪些操作会导致数据的自动提交：**

  - `DDL操作`一旦执行，都会自动提交。

    - set autocommit = false 对DDL操作`失效`

    - `DML操作`默认情况下，一旦执行，就会自动提交。

      - 我们`可以`通过`set autocommit = false`的方式取消DML操作的自动提交。


  - 默认在`关闭连接`时，会自动的提交数据

    > `DDL`(Data Definition Language)：`对数据库，表的操作`
    >
    > `DML`(Data Manipulation Language)：`增删改查`




- **综上所述，保证数据库事务一致性需要达成以下条件：**
  1. 将这一组逻辑操作单元（多条SQL语句）串联在一起：`使用同一个连接Connection`
  1. 调用 Connection 对象的 `setAutoCommit(false)`; 以`取消自动提交事务`
  1. 在所有的 SQL 语句都`成功执行`后，调用 `commit()`; 方法提交事务
  1. 在`出现异常`时，调用 `rollback()`; 方法回滚事务


> 若此时 Connection 没有被关闭，还可能被重复使用，则需要恢复其自动提交状态setAutoCommit(true)。尤其是在`使用数据库连接池技术`时，`执行close()方法前`，建议`恢复自动提交状态`

### 事务的ACID属性

1. **原子性（Atomicity）**
   原子性是指事务是一个不可分割的工作单位，事务中的操作`要么都发生`，`要么都不发生`

2. **一致性（Consistency）**
   事务必须使数据库从一个一致性状态变换到另外一个一致性状态

3. **隔离性（Isolation）**
   事务的隔离性是指`一个事务的执行不能被其他事务干扰`，即一个事务内部的操作及使用的数据对并发的其他事务是隔离的，`并发执行的各个事务之间不能互相干扰`

4. **持久性（Durability）**
   持久性是指一个事务一旦被提交，它对数据库中`数据的改变就是永久性的`，接下来的其他操作和数据库故障不应该对其有任何影响

#### 数据库的并发问题

- 对于同时运行的多个事务, 当这些事务访问数据库中相同的数据时, 如果没有采取必要的隔离机制, 就会导致各种并发问题:
  - **脏读**: 对于两个事务 T1, T2, T1 读取了已经被 T2 更新但还**没有被提交**的字段。之后, 若 T2 回滚, T1读取的内容就是临时且无效的。
  - **不可重复读**: 对于两个事务T1, T2, T1 读取了一个字段, 然后 T2 **更新**了该字段。之后, T1再次读取同一个字段, 值就不同了。
  - **幻读**: 对于两个事务T1, T2, T1 从一个表中读取了一个字段, 然后 T2 在该表中**插入**了一些新的行。之后, 如果 T1 再次读取同一个表, 就会多出几行。
- **数据库事务的隔离性**: 数据库系统必须具有隔离并发运行各个事务的能力, 使它们不会相互影响, 避免各种并发问题。
- 一个事务与其他事务隔离的程度称为隔离级别。数据库规定了多种事务隔离级别, 不同隔离级别对应不同的干扰程度, **隔离级别越高, 数据一致性就越好, 但并发性越弱。**

#### 四种隔离级别

从**上往下隔离级别递增**，**性能递减**

- `READ UNCOMMITRED`(**读未提交数据**)

  允许事务读取未被其他事务提交的变更。**脏读、不可重复读和幻读的问题都会出现**

- `READ COMMITED`(**读已提交数据**)

  只允许事务读取已经被其他事务提交的变更。可以**避免脏读**，但**不可重复读和幻读问题仍然可能出现**

- `REPEATABLE READ`(**可重复读**)

  确保事务可以多次从一个字段中读取相同的值。在这个事务持续期间，禁止其他事务对这个字段进行更新。可以**避免脏读和不可重复读**，但**幻读的仍然存在**

- `SERIALIZABLE`(**串行化**)

  确保事务可以从一个表中读取相同的行，在这个事务持续期间，禁止其他事务对该表执行插入、更新和删除操作。**所有的并发问题都可以避免**，但性能十分低下

> - `Oracle` 支持的 `2` 种事务隔离级别：**READ COMMITED**, SERIALIZABLE。 Oracle `默认`的事务隔离级别为: **READ COMMITED** 。
>
>
> - `Mysql` 支持 `4` 种事务隔离级别。Mysql 默认的事务隔离级别为: **REPEATABLE READ**

### BaseDAO

<a id="考虑事务">此处为考虑事务方法封装，</a> [不考虑事务见基础操作最终方法封装](#不考虑事务)

#### 通用增删改

```java
/** 
 * @Description: 通用的增删改操作---version 2.0 （考虑上事务）
 * @param conn 多个事务共用的连接
 * @param sql sql语句
 * @param args sql语句中的占位符
 * @return: int 影响的行数
 * @Author: Transformer HE
 * @Date: 2022/9/28 20:27
 */
public int update(Connection conn, String sql, Object... args) {
    // sql中占位符的个数与可变形参的长度相同！
	PreparedStatement ps = null;
	try {
		// 1.预编译sql语句，返回PreparedStatement的实例
		ps = conn.prepareStatement(sql);
		// 2.填充占位符
		for (int i = 0; i < args.length; i++) {
			ps.setObject(i + 1, args[i]);// 小心参数声明错误！！
		}
		// 3.执行
		return ps.executeUpdate();
	} catch (Exception e) {
		e.printStackTrace();
	} finally {
		// 4.资源的关闭
		JDBCUtils.closeResource(null, ps);
	}
	return 0;
}
```



#### 通用单个查询

```java
/** 
 * @Description: 通用的查询操作，用于返回数据表中的一条记录（version 2.0：考虑上事务）
 * @param conn 多个事务共用的连接
 * @param clazz 查询JavaBean对象的Class对象
 * @param sql sql语句
 * @param args sql语句中的占位符
 * @return: T 返回的一个JavaBean
 * @Author: Transformer HE
 * @Date: 2022/9/28 20:29
 */
public <T> T getForOne(Connection conn, Class<T> clazz, String sql, Object... args) {
    PreparedStatement ps = null;
    ResultSet rs = null;
    try {
        ps = conn.prepareStatement(sql);
        for (int i = 0; i < args.length; i++) {
            ps.setObject(i + 1, args[i]);
        }
        rs = ps.executeQuery();
        // 获取结果集的元数据 :ResultSetMetaData
        ResultSetMetaData rsmd = rs.getMetaData();
        // 通过ResultSetMetaData获取结果集中的列数
        int columnCount = rsmd.getColumnCount();
        if (rs.next()) {
            T t = clazz.newInstance();
            // 处理结果集一行数据中的每一个列
            for (int i = 0; i < columnCount; i++) {
                // 获取列值
                Object columValue = rs.getObject(i + 1);
                // 获取每个列的列名
                // String columnName = rsmd.getColumnName(i + 1);
                String columnLabel = rsmd.getColumnLabel(i + 1);
                // 给t对象指定的columnName属性，赋值为columValue：通过反射
                Field field = clazz.getDeclaredField(columnLabel);
                field.setAccessible(true);
                field.set(t, columValue);
            }
            return t;
        }
    } catch (Exception e) {
        e.printStackTrace();
    } finally {
        JDBCUtils.closeResource(null, ps, rs);
    }
    return null;
}
```



#### 通用批量查询

```java
/**
 * @Description: 通用的查询操作，用于返回数据表中的多条记录构成的集合（version 2.0：考虑上事务）
 * @param conn  多个事务共用的连接
 * @param clazz 查询JavaBean对象的Class对象
 * @param sql sql语句
 * @param args sql语句中的占位符
 * @return: java.util.List<T>
 * @Author: Transformer HE
 * @Date: 2022/9/28 20:34
 */
public <T> List<T> getForList(Connection conn, Class<T> clazz, String sql, Object... args) {
    PreparedStatement ps = null;
    ResultSet rs = null;
    try {
        ps = conn.prepareStatement(sql);
        for (int i = 0; i < args.length; i++) {
            ps.setObject(i + 1, args[i]);
        }
        rs = ps.executeQuery();
        // 获取结果集的元数据 :ResultSetMetaData
        ResultSetMetaData rsmd = rs.getMetaData();
        // 通过ResultSetMetaData获取结果集中的列数
        int columnCount = rsmd.getColumnCount();
        // 创建集合对象
        ArrayList<T> list = new ArrayList<T>();
        while (rs.next()) {
            T t = clazz.newInstance();
            // 处理结果集一行数据中的每一个列:给t对象指定的属性赋值
            for (int i = 0; i < columnCount; i++) {
                // 获取列值
                Object columValue = rs.getObject(i + 1);
                // 获取每个列的列名
                // String columnName = rsmd.getColumnName(i + 1);
                String columnLabel = rsmd.getColumnLabel(i + 1);
                // 给t对象指定的columnName属性，赋值为columValue：通过反射
                Field field = clazz.getDeclaredField(columnLabel);
                field.setAccessible(true);
                field.set(t, columValue);
            }
            list.add(t);
        }
        return list;
    } catch (Exception e) {
        e.printStackTrace();
    } finally {
        JDBCUtils.closeResource(null, ps, rs);
    }
    return null;
}
```



#### 通用特殊查询

如查询数量，查询某条数据的某个字段

```java
/** 
 * @Description: 用于查询特殊值的通用的方法
 * @param conn 查询JavaBean对象的Class对象
 * @param sql sql语句
 * @param args sql语句中的占位符
 * @return: E 
 * @Author: Transformer HE
 * @Date: 2022/9/28 20:35
 */
public <E> E getValue(Connection conn, String sql, Object... args) {
    PreparedStatement ps = null;
    ResultSet rs = null;
    try {
        ps = conn.prepareStatement(sql);
        for (int i = 0; i < args.length; i++) {
            ps.setObject(i + 1, args[i]);
        }
        rs = ps.executeQuery();
        if (rs.next()) {
            return (E) rs.getObject(1);
        }
    } catch (SQLException e) {
        e.printStackTrace();
    } finally {
        JDBCUtils.closeResource(null, ps, rs);
    }
    return null;
}
```



### BaseDAO升级

```Java
import java.lang.reflect.Field;
import java.lang.reflect.ParameterizedType;
import java.lang.reflect.Type;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.ResultSetMetaData;
import java.sql.SQLException;
import java.util.ArrayList;
import java.util.List;
import com.atguigu1.util.JDBCUtils;
/*
 * DAO: data(base) access object
 * 封装了针对于数据表的通用的操作
 */
public abstract class BaseDAO<T> {
	
	private Class<T> clazz = null;
	
	{	
		//获取当前BaseDAO的子类继承的父类中的泛型
         //Class类实现了Type
		Type genericSuperclass = this.getClass().getGenericSuperclass();
         //强转以便调用方法
		ParameterizedType paramType = (ParameterizedType) genericSuperclass;
		Type[] typeArguments = paramType.getActualTypeArguments();//获取了父类的泛型参数
		clazz = (Class<T>) typeArguments[0];//泛型的第一个参数
		
	}
	
	
	// 通用的增删改操作---version 2.0 （考虑上事务）
	public int update(Connection conn, String sql, Object... args) {// sql中占位符的个数与可变形参的长度相同！
		PreparedStatement ps = null;
		try {
			// 1.预编译sql语句，返回PreparedStatement的实例
			ps = conn.prepareStatement(sql);
			// 2.填充占位符
			for (int i = 0; i < args.length; i++) {
				ps.setObject(i + 1, args[i]);// 小心参数声明错误！！
			}
			// 3.执行
			return ps.executeUpdate();
		} catch (Exception e) {
			e.printStackTrace();
		} finally {
			// 4.资源的关闭
			JDBCUtils.closeResource(null, ps);
		}
		return 0;
	}
	// 通用的查询操作，用于返回数据表中的一条记录（version 2.0：考虑上事务）
	public T getForOne(Connection conn, String sql, Object... args) {
		PreparedStatement ps = null;
		ResultSet rs = null;
		try {
			ps = conn.prepareStatement(sql);
			for (int i = 0; i < args.length; i++) {
				ps.setObject(i + 1, args[i]);
			}
			rs = ps.executeQuery();
			// 获取结果集的元数据 :ResultSetMetaData
			ResultSetMetaData rsmd = rs.getMetaData();
			// 通过ResultSetMetaData获取结果集中的列数
			int columnCount = rsmd.getColumnCount();
			if (rs.next()) {
				T t = clazz.newInstance();
				// 处理结果集一行数据中的每一个列
				for (int i = 0; i < columnCount; i++) {
					// 获取列值
					Object columValue = rs.getObject(i + 1);
					// 获取每个列的列名
					// String columnName = rsmd.getColumnName(i + 1);
					String columnLabel = rsmd.getColumnLabel(i + 1);
					// 给t对象指定的columnName属性，赋值为columValue：通过反射
					Field field = clazz.getDeclaredField(columnLabel);
					field.setAccessible(true);
					field.set(t, columValue);
				}
				return t;
			}
		} catch (Exception e) {
			e.printStackTrace();
		} finally {
			JDBCUtils.closeResource(null, ps, rs);
		}
		return null;
	}
	// 通用的查询操作，用于返回数据表中的多条记录构成的集合（version 2.0：考虑上事务）
	public List<T> getForList(Connection conn, String sql, Object... args) {
		PreparedStatement ps = null;
		ResultSet rs = null;
		try {
			ps = conn.prepareStatement(sql);
			for (int i = 0; i < args.length; i++) {
				ps.setObject(i + 1, args[i]);
			}
			rs = ps.executeQuery();
			// 获取结果集的元数据 :ResultSetMetaData
			ResultSetMetaData rsmd = rs.getMetaData();
			// 通过ResultSetMetaData获取结果集中的列数
			int columnCount = rsmd.getColumnCount();
			// 创建集合对象
			ArrayList<T> list = new ArrayList<T>();
			while (rs.next()) {
				T t = clazz.newInstance();
				// 处理结果集一行数据中的每一个列:给t对象指定的属性赋值
				for (int i = 0; i < columnCount; i++) {
					// 获取列值
					Object columValue = rs.getObject(i + 1);
					// 获取每个列的列名
					// String columnName = rsmd.getColumnName(i + 1);
					String columnLabel = rsmd.getColumnLabel(i + 1);
					// 给t对象指定的columnName属性，赋值为columValue：通过反射
					Field field = clazz.getDeclaredField(columnLabel);
					field.setAccessible(true);
					field.set(t, columValue);
				}
				list.add(t);
			}
			return list;
		} catch (Exception e) {
			e.printStackTrace();
		} finally {
			JDBCUtils.closeResource(null, ps, rs);
		}
		return null;
	}
	//用于查询特殊值的通用的方法
	public <E> E getValue(Connection conn,String sql,Object...args){
		PreparedStatement ps = null;
		ResultSet rs = null;
		try {
			ps = conn.prepareStatement(sql);
			for(int i = 0;i < args.length;i++){
				ps.setObject(i + 1, args[i]);
				
			}
			
			rs = ps.executeQuery();
			if(rs.next()){
				return (E) rs.getObject(1);
			}
		} catch (SQLException e) {
			e.printStackTrace();
		}finally{
			JDBCUtils.closeResource(null, ps, rs);
			
		}
		return null;
		
	}	
}
```



## 数据库连接池

**数据库连接池技术的优点**

**1. 资源重用**

由于数据库连接得以重用，避免了频繁创建，释放连接引起的大量性能开销。在减少系统消耗的基础上，另一方面也增加了系统运行环境的平稳性。

**2. 更快的系统反应速度**

数据库连接池在初始化过程中，往往已经创建了若干数据库连接置于连接池中备用。此时连接的初始化工作均已完成。对于业务请求处理而言，直接利用现有可用连接，避免了数据库连接初始化和释放过程的时间开销，从而减少了系统的响应时间

**3. 新的资源分配手段**

对于多应用共享同一数据库的系统而言，可在应用层通过数据库连接池的配置，实现某一应用最大可用数据库连接数的限制，避免某一应用独占所有的数据库资源

**4. 统一的连接管理，避免数据库连接泄漏**

在较为完善的数据库连接池实现中，可根据预先的占用超时设定，强制回收被占用连接，从而避免了常规数据库连接操作中可能出现的资源泄露



- JDBC 的数据库连接池使用 `javax.sql.DataSource` 来表示，`DataSource` 只是`一个接口`，该接口通常由服务器(Weblogic, WebSphere, Tomcat)提供实现，也有一些开源组织提供实现：
  - **DBCP** 是Apache提供的数据库连接池。tomcat 服务器自带dbcp数据库连接池。**速度相对c3p0较快**，但因自身存在BUG，Hibernate3已不再提供支持。
  - **C3P0** 是一个开源组织提供的一个数据库连接池，**速度相对较慢，稳定性还可以。**hibernate官方推荐使用
  - **Proxool** 是sourceforge下的一个开源项目数据库连接池，有监控连接池状态的功能，**稳定性较c3p0差一点**
  - **BoneCP** 是一个开源组织提供的数据库连接池，速度快
  - **Druid** 是阿里提供的数据库连接池，据说是集DBCP 、C3P0 、Proxool 优点于一身的数据库连接池，但是速度不确定是否有BoneCP快
- DataSource 通常被称为数据源，它包含连接池和连接池管理两个部分，习惯上也经常把 DataSource 称为连接池
- **DataSource用来取代DriverManager来获取Connection，获取速度快，同时可以大幅度提高数据库访问速度。**
- 特别注意：
  - 数据源和数据库连接不同，数据源无需创建多个，它是产生数据库连接的工厂，因此**整个应用只需要一个数据源即可。**
  - `当数据库访问结束后，程序还是像以前一样关闭数据库连接：conn.close(); 但conn.close()并没有关闭数据库的物理连接，它仅仅把数据库连接释放，归还给了数据库连接池`



### C3P0

`c3p0-0.9.1.2.jar`

- DBCP 是 Apache 软件基金组织下的开源连接池实现，该连接池依赖该组织下的另一个开源系统：Common-pool。如需使用该连接池实现，应在系统中增加如下两个 jar 文件：
  - Commons-dbcp.jar：连接池的实现
  - Commons-pool.jar：连接池实现的依赖库
- **Tomcat 的连接池正是采用该连接池来实现的。**该数据库连接池既可以与应用服务器整合使用，也可由应用程序独立使用。
- 数据源和数据库连接不同，数据源无需创建多个，它是产生数据库连接的工厂，因此整个应用只需要一个数据源即可。
- 当数据库访问结束后，程序还是像以前一样关闭数据库连接：conn.close(); 但上面的代码并没有关闭数据库的物理连接，它仅仅把数据库连接释放，归还给了数据库连接池。
- 配置属性说明

| 属性                       | 默认值 | 说明                                                         |
| -------------------------- | ------ | ------------------------------------------------------------ |
| initialSize                | 0      | 连接池启动时创建的初始化连接数量                             |
| maxActive                  | 8      | 连接池中可同时连接的最大的连接数                             |
| maxIdle                    | 8      | 连接池中最大的空闲的连接数，超过的空闲连接将被释放，如果设置为负数表示不限制 |
| minIdle                    | 0      | 连接池中最小的空闲的连接数，低于这个数量会被创建新的连接。该参数越接近maxIdle，性能越好，因为连接的创建和销毁，都是需要消耗资源的；但是不能太大。 |
| maxWait                    | 无限制 | 最大等待时间，当没有可用连接时，连接池等待连接释放的最大时间，超过该时间限制会抛出异常，如果设置-1表示无限等待 |
| poolPreparedStatements     | false  | 开启池的Statement是否prepared                                |
| maxOpenPreparedStatements  | 无限制 | 开启池的prepared 后的同时最大连接数                          |
| minEvictableIdleTimeMillis |        | 连接池中连接，在时间段内一直空闲， 被逐出连接池的时间        |
| removeAbandonedTimeout     | 300    | 超过时间限制，回收没有用(废弃)的连接                         |
| removeAbandoned            | false  | 超过removeAbandonedTimeout时间后，是否进 行没用连接（废弃）的回收 |



#### 直接获取连接

```java
//使用C3P0数据库连接池的方式，获取数据库的连接：不推荐
public static Connection getConnection1() throws Exception{
	ComboPooledDataSource cpds = new ComboPooledDataSource();
	cpds.setDriverClass("com.mysql.jdbc.Driver"); 
	cpds.setJdbcUrl("jdbc:mysql://localhost:3306/test");
	cpds.setUser("root");
	cpds.setPassword("abc123");
		
//	cpds.setMaxPoolSize(100);
	
	Connection conn = cpds.getConnection();
	return conn;
}
```



#### 配置文件获取连接

```java
//使用C3P0数据库连接池的配置文件方式，获取数据库的连接：推荐
private static DataSource cpds = new ComboPooledDataSource("helloc3p0");
public static Connection getConnection2() throws SQLException{
	Connection conn = cpds.getConnection();
	return conn;
}
```

#### 配置文件

`src下`的配置文件为：【c3p0-config.xml】

```xml
<?xml version="1.0" encoding="UTF-8"?>
<c3p0-config>
	<named-config name="helloc3p0">
		<!-- 获取连接的4个基本信息 -->
		<property name="user">root</property>
		<property name="password">abc123</property>
		<property name="jdbcUrl">jdbc:mysql:///test</property>
		<property name="driverClass">com.mysql.jdbc.Driver</property>
		
		<!-- 涉及到数据库连接池的管理的相关属性的设置 -->
		<!-- 若数据库中连接数不足时, 一次向数据库服务器申请多少个连接 -->
		<property name="acquireIncrement">5</property>
		<!-- 初始化数据库连接池时连接的数量 -->
		<property name="initialPoolSize">5</property>
		<!-- 数据库连接池中的最小的数据库连接数 -->
		<property name="minPoolSize">5</property>
		<!-- 数据库连接池中的最大的数据库连接数 -->
		<property name="maxPoolSize">10</property>
		<!-- C3P0 数据库连接池可以维护的 Statement 的个数 -->
		<property name="maxStatements">20</property>
		<!-- 每个连接同时可以使用的 Statement 对象的个数 -->
		<property name="maxStatementsPerConnection">5</property>

	</named-config>
</c3p0-config>
```

#### 连接方法封装

```Java
//数据库连接池只需提供一个即可。
private static ComboPooledDataSource cpds = new ComboPooledDataSource("hellc3p0");

public static Connection getConnection1() throws SQLException {
    Connection conn = cpds.getConnection();
    return conn;
}
```



### DBCP

`commons-dbcp-1.4.jar` + `commons-pool-1.5.5.jar`

#### 直接获取连接

```java
@Test
public void testGetConnection() throws SQLException {
    //创建了DBCP的数据库连接池
    BasicDataSource source = new BasicDataSource();
    //设置基本信息
    source.setDriverClassName("com.mysql.cj.jdbc.Driver");
    source.setUrl("jdbc:mysql:///test");
    source.setUsername("root");
    source.setPassword("root");
    //还可以设置其他涉及数据库连接池管理的相关属性：
    source.setInitialSize(10);
    source.setMaxActive(10);
    //。。。
    Connection conn = source.getConnection();
    System.out.println(conn);
}
```



#### 配置文件获取连接

```java
@Test
public void testGetConnection1() throws Exception {
    Properties pros = new Properties();
    //方式1：
	//InputStream is = ClassLoader.getSystemClassLoader().getResourceAsStream("dbcp.properties");
    //方式2：
    FileInputStream is = new FileInputStream(new File("src/dbcp.properties"));
    pros.load(is);
    DataSource source = BasicDataSourceFactory.createDataSource(pros);
    Connection conn = source.getConnection();
    System.out.println(conn);
}
```



#### 配置文件

```properties
driverClassName=com.mysql.cj.jdbc.Driver
url=jdbc:mysql:///test
username=root
password=root
initialSize=10
```



#### 连接方法封装

```java
//创建一个DBCP数据库连接池
private static DataSource source;

static {
    try {
        Properties pros = new Properties();
        FileInputStream is = new FileInputStream(new File("src/dbcp.properties"));
        pros.load(is);
        source = BasicDataSourceFactory.createDataSource(pros);
    } catch (Exception e) {
        e.printStackTrace();
    }
}

public static Connection getConnection() throws Exception {
    Connection conn = source.getConnection();
    return conn;
}
```



### Druid

`druid-1.1.10.jar`

| **配置**                      | **缺省** | **说明**                                                     |
| ----------------------------- | -------- | ------------------------------------------------------------ |
| name                          |          | 配置这个属性的意义在于，如果存在多个数据源，监控的时候可以通过名字来区分开来。   如果没有配置，将会生成一个名字，格式是：”DataSource-” +   System.identityHashCode(this) |
| url                           |          | 连接数据库的url，不同数据库不一样。例如：mysql :   jdbc:mysql://10.20.153.104:3306/druid2      oracle :   jdbc:oracle:thin:@10.20.149.85:1521:ocnauto |
| username                      |          | 连接数据库的用户名                                           |
| password                      |          | 连接数据库的密码。如果你不希望密码直接写在配置文件中，可以使用ConfigFilter。详细看这里：<https://github.com/alibaba/druid/wiki/%E4%BD%BF%E7%94%A8ConfigFilter> |
| driverClassName               |          | 根据url自动识别   这一项可配可不配，如果不配置druid会根据url自动识别dbType，然后选择相应的driverClassName(建议配置下) |
| initialSize                   | 0        | 初始化时建立物理连接的个数。初始化发生在显示调用init方法，或者第一次getConnection时 |
| maxActive                     | 8        | 最大连接池数量                                               |
| maxIdle                       | 8        | 已经不再使用，配置了也没效果                                 |
| minIdle                       |          | 最小连接池数量                                               |
| maxWait                       |          | 获取连接时最大等待时间，单位毫秒。配置了maxWait之后，缺省启用公平锁，并发效率会有所下降，如果需要可以通过配置useUnfairLock属性为true使用非公平锁。 |
| poolPreparedStatements        | false    | 是否缓存preparedStatement，也就是PSCache。PSCache对支持游标的数据库性能提升巨大，比如说oracle。在mysql下建议关闭。 |
| maxOpenPreparedStatements     | -1       | 要启用PSCache，必须配置大于0，当大于0时，poolPreparedStatements自动触发修改为true。在Druid中，不会存在Oracle下PSCache占用内存过多的问题，可以把这个数值配置大一些，比如说100 |
| validationQuery               |          | 用来检测连接是否有效的sql，要求是一个查询语句。如果validationQuery为null，testOnBorrow、testOnReturn、testWhileIdle都不会其作用。 |
| testOnBorrow                  | true     | 申请连接时执行validationQuery检测连接是否有效，做了这个配置会降低性能。 |
| testOnReturn                  | false    | 归还连接时执行validationQuery检测连接是否有效，做了这个配置会降低性能 |
| testWhileIdle                 | false    | 建议配置为true，不影响性能，并且保证安全性。申请连接的时候检测，如果空闲时间大于timeBetweenEvictionRunsMillis，执行validationQuery检测连接是否有效。 |
| timeBetweenEvictionRunsMillis |          | 有两个含义： 1)Destroy线程会检测连接的间隔时间2)testWhileIdle的判断依据，详细看testWhileIdle属性的说明 |
| numTestsPerEvictionRun        |          | 不再使用，一个DruidDataSource只支持一个EvictionRun           |
| minEvictableIdleTimeMillis    |          |                                                              |
| connectionInitSqls            |          | 物理连接初始化的时候执行的sql                                |
| exceptionSorter               |          | 根据dbType自动识别   当数据库抛出一些不可恢复的异常时，抛弃连接 |
| filters                       |          | 属性类型是字符串，通过别名的方式配置扩展插件，常用的插件有：   监控统计用的filter:stat日志用的filter:log4j防御sql注入的filter:wall |
| proxyFilters                  |          | 类型是List，如果同时配置了filters和proxyFilters，是组合关系，并非替换关系 |



#### 获取连接

```java
public void getConnection() throws Exception {
    Properties pros = new Properties();
    InputStream is = ClassLoader.getSystemClassLoader().getResourceAsStream("druid.properties");
    pros.load(is);
    DataSource source = DruidDataSourceFactory.createDataSource(pros);
    Connection conn = source.getConnection();
    System.out.println(conn);
}
```



#### 配置文件

```properties
url=jdbc:mysql:///test
username=root
password=root
driverClassName=com.mysql.cj.jdbc.Driver
initialSize=10
maxActive=10
```



#### 连接方法封装

```java
private static DataSource source;

static {
    try {
        Properties pros = new Properties();
        InputStream is = ClassLoader.getSystemClassLoader().getResourceAsStream("druid.properties");
        pros.load(is);
        source = DruidDataSourceFactory.createDataSource(pros);
    } catch (Exception e) {
        e.printStackTrace();
    }
}

public static Connection getConnection() throws SQLException {
    Connection conn = source.getConnection();
    return conn;
}
```



## commons-dbutils

**QueryRunner用于数据查询与增删改查**

**ResultSetHandler用于选择查询结果形式，选择的结果形式作为参数传入QueryRunner方法**

**DbUtils提供方法如关闭连接**

- commons-dbutils 是 Apache 组织提供的一个开源 JDBC工具类库，它是对JDBC的简单封装，学习成本极低，并且使用dbutils能极大简化jdbc编码的工作量，同时也不会影响程序的性能。

- API介绍：
  - org.apache.commons.dbutils.`QueryRunner`
  - org.apache.commons.dbutils.`ResultSetHandler`
  - 工具类：org.apache.commons.dbutils.`DbUtils`

### QueryRunner接口

该类简单化了SQL查询，它与`ResultSetHandler`组合在一起使用可以完成大部分的数据库操作，能够大大减少编码量

- QueryRunner类提供了两个构造器：

  - 默认的构造器
  - 需要一个 javax.sql.DataSource 来作参数的构造器

- QueryRunner类的主要方法：

  - **查询**

    - `public Object query(Connection conn, String sql, ResultSetHandler rsh,Object... params) throws SQLException`：

      执行一个查询操作，在这个查询中，对象数组中的每个元素值被用来作为查询语句的置换参数。该方法会自行处理 PreparedStatement 和 ResultSet 的创建和关闭。

    - ...... 

  - **更新**

    - `public int update(Connection conn, String sql, Object... params) throws SQLException`：

      用来执行一个更新（插入、更新或删除）操作。

    - ......

  - **插入**

    - `public <T> T insert(Connection conn,String sql,ResultSetHandler<T> rsh, Object... params) throws SQLException`：

      只支持INSERT语句，其中 rsh - The handler used to create the result object from the ResultSet of auto-generated keys.  返回值: An object generated by the handler.即自动生成的键值

    - ....

  - **批处理**

    - `public int[] batch(Connection conn,String sql,Object[][] params)throws SQLException`：

      INSERT, UPDATE, or DELETE语句

    - `public <T> T insertBatch(Connection conn,String sql,ResultSetHandler<T> rsh,Object[][] params)throws SQLException`：

      只支持INSERT语句

    - .....

#### 增删改

```Java
private QueryRunner queryRunner = new QueryRunner();
/**
 * @param sql  sql语句
 * @param args sql语句中的占位符
 * @Description: 对数据库进行增删改操作
 * @return: int 如果返回-1,说明执行失败;返回其他表示语句影响的行数
 * @Author: HeQingTian
 * @Date: 2022/03/18 23:11
 */
public int update(String sql, Object... args) {
    Connection connection = JDBCUtils.getConnection();
    try {
        return queryRunner.update(connection, sql, args);
    } catch (SQLException e) {
        e.printStackTrace();
    } finally {
        JDBCUtils.close(connection);
    }
    return -1;
}
```



### ResultSetHandler接口

该接口用于处理 java.sql.ResultSet，将数据按要求转换为另一种形式

提供了一个单独的方法：`Object handle (java.sql.ResultSet rs)`，在`自定义`ResultSetHandler的实现类时需要`重写`此方法，自定义返回类型

接口的主要实现类（`加粗的是重点`）：

- ArrayHandler：把结果集中的第一行数据转成对象数组。
- ArrayListHandler：把结果集中的每一行数据都转成一个数组，再存放到List中。
- **BeanHandler：**将结果集中的第一行数据封装到一个对应的JavaBean实例中。
- **BeanListHandler：**将结果集中的每一行数据都封装到一个对应的JavaBean实例中，存放到List里。
- ColumnListHandler：将结果集中某一列的数据存放到List中。
- KeyedHandler(name)：将结果集中的每一行数据都封装到一个Map里，再把这些map再存到一个map里，其key为指定的key。
- **MapHandler：**将结果集中的第一行数据封装到一个Map里，key是列名，value就是对应的值。
- **MapListHandler：**将结果集中的每一行数据都封装到一个Map里，然后再存放到List
- **ScalarHandler：**查询单个值对象

#### BeanHandler(查)

结果集中的第一行数据封装到一个对应的JavaBean实例中

```Java
private QueryRunner queryRunner = new QueryRunner();
/**
 @param type 返回对象类型
 @param sql  sql语句
 @param args sql语句中的占位符
 @Description: 查询数据库返回一个JavaBean
 @return: T null:无结果,否则返回一个JavaBean的泛型
 @Author: HeQingTian
 @Date: 2022/03/18 23:14
 */
public <T> T getForOne(Class<T> type, String sql, Object... args) {
    Connection con = JDBCUtils.getConnection();
    try {
        return queryRunner.query(con, sql, new BeanHandler<T>(type), args);
    } catch (SQLException e) {
        e.printStackTrace();
    } finally {
        //prepareStatement在query方法中关了
        JDBCUtils.close(con);
    }
    return null;
}
```



#### BeanListHandler(查)

```Java
private QueryRunner queryRunner = new QueryRunner();
/**
 @param type 返回的对象类型
 @param sql  sql语句
 @param args sql语句中的占位符
 @Description: 查询数据库, 返回一个javaBean型的List
 @return: java.util.List<T> null:无结果,否则返回一个JavaBean类型的List
 @Author: HeQingTian
 @Date: 2022/03/18 23:18
 */
public <T> List<T> getForList(Class<T> type, String sql, Object... args) {
    Connection con = JDBCUtils.getConnection();
    try {
        return queryRunner.query(con, sql, new BeanListHandler<T>(type), args);
    } catch (SQLException e) {
        e.printStackTrace();
    } finally {
        JDBCUtils.close(con);
    }
    return null;
}
```



#### ScalarHandler(查)

如数量、某条记录的某个字段

```Java
private QueryRunner queryRunner = new QueryRunner();
/**
 @param sql sql语句
 @Description: 查询单个值对象
 @return: java.lang.Integer null:获取失败,否则为记录个数
 @Author: HeQingTian
 @Date: 2022/03/18 23:51
 */
public Object queryForSingleValue(String sql, Object... args){
    Connection conn = JdbcUtils.getConnection();
    try {
        return queryRunner.query(conn, sql, new ScalarHandler(), args);
    } catch (SQLException e) {
        e.printStackTrace();
    } finally {
        JDBCUtils.close(con);
    }
    return null;
}
```



#### MapHandler(查)

```Java
private QueryRunner queryRunner = new QueryRunner();
/**
 @param sql  sql语句
 @param args sql语句中的占位符
 @Description: 将结果集中的第一行数据封装到一个Map里，key是列名，value就是对应的值
 @return: java.util.Map<java.lang.String,java.lang.Object>
 @Author: HeQingTian
 @Date: 2022/03/18 23:14
 */
public Map<String, Object> getForMap(String sql, Object... args) {
    Connection con=null;
    try {
        con = JDBCUtils.getConnection3();
        return queryRunner.query(con, sql, new MapHandler(), args);
    } catch (SQLException e) {
        e.printStackTrace();
    } finally {
        //prepareStatement在query方法中关了
        JDBCUtils.closeResource(con, null);
    }
    return null;
}
```



#### MapListHandler(查)

```Java
private QueryRunner queryRunner = new QueryRunner();
/**
 @param sql  sql语句
 @param args sql语句中的占位符
 @Description: 将结果集中的每一行数据都封装到一个Map里，然后再存放到List
 @return: java.util.List<java.util.Map<java.lang.String,java.lang.Object>>
 @Author: HeQingTian
 @Date: 2022/03/18 23:14
 */
public List<Map<String, Object>> getForMap(String sql, Object... args) {
    Connection con = null;
    try {
        con = JDBCUtils.getConnection3();
        return queryRunner.query(con, sql, new MapListHandler(), args);
    } catch (SQLException e) {
        e.printStackTrace();
    } finally {
        //prepareStatement在query方法中关了
        JDBCUtils.closeResource(con, null);
    }
    return null;
}
```



#### 自定义

```Java
@Test
public void testQuery() {
    Connection conn = null;
    try {
        QueryRunner runner = new QueryRunner();
        conn = JDBCUtils.getConnection3();
        String sql = "select id,name,email,birth from customers where id = ?";
        ResultSetHandler<Customer> handler = new ResultSetHandler<Customer>() {
            @Override
            public Customer handle(ResultSet rs) throws SQLException {
				System.out.println("handle");
				return null;
				return new Customer(12, "成龙", "Jacky@126.com", new Date(234324234324L));
                if (rs.next()) {
                    int id = rs.getInt("id");
                    String name = rs.getString("name");
                    String email = rs.getString("email");
                    Date birth = rs.getDate("birth");
                    Customer customer = new Customer(id, name, email, birth);
                    return customer;
                }
                return null;
            }
        };
        Customer customer = runner.query(conn, sql, handler, 22);
        System.out.println(customer);
    } catch (SQLException e) {
        e.printStackTrace();
    } finally {
        JDBCUtils.closeResource(conn, null);
    }
}
```



### DbUtils

提供如`关闭连接`、`装载JDBC驱动程序`等常规工作的工具类，里面的所有方法都是静态的。主要方法如下：

- `public static void close(…) throws java.sql.SQLException`：

  DbUtils类提供了三个重载的关闭方法。这些方法检查所提供的参数是不是NULL，如果不是的话，它们就关闭Connection、Statement和ResultSet。

- `public static void closeQuietly(…)`：

  这一类方法不仅能在Connection、Statement和ResultSet为NULL情况下避免关闭，还能隐藏一些在程序中抛出的SQLEeception。

- `public static void commitAndClose(Connection conn)throws SQLException`：

  用来提交连接的事务，然后关闭连接

- `public static void commitAndCloseQuietly(Connection conn)`：

  用来提交连接，然后关闭连接，并且在关闭连接时不抛出SQL异常。 

- `public static void rollback(Connection conn)throws SQLException`：

  允许conn为null，因为方法内部做了判断

- `public static void rollbackAndClose(Connection conn)throws SQLException`

- `rollbackAndCloseQuietly(Connection)`

- `public static boolean loadDriver(java.lang.String driverClassName)`：

  这一方装载并注册JDBC驱动程序，如果成功就返回true。使用该方法，你不需要捕捉这个异常ClassNotFoundException。







# JavaWeb 

![](https://cdn.jsdelivr.net/gh/6hqt9/TyporaNotes/img/202210211134440.png)

`分层`的目的是为了`解耦`。解耦就是为了**降低代码的耦合度**。**方便**项目后期的**维护和升级**

| 层             | 包                                  | 说明             |
| -------------- | ----------------------------------- | ---------------- |
| web 层         | com.atguigu.web/servlet/controller  |                  |
| service 层     | com.atguigu.service                 | Service 接口包   |
|                | com.atguigu.service.impl            | Service 接口实现 |
| dao 持久层     | com.atguigu.dao                     | Dao 接口包       |
|                | com.atguigu.dao.impl                | Dao 接口实现     |
| 实体 bean 对象 | com.atguigu.pojo/entity/domain/bean | JavaBean 类      |
| 测试包         | com.atguigu.test/junit              |                  |
| 工具类         | com.atguigu.utils                   |                  |



## 基本知识

### 路径问题

#### 相对路径

当点击`<a>`标签进行跳转时，所有相对路径在工作时都会参照`浏览器地址栏中的地址`来进行跳转

实际开发中，路径`都使用绝对路径`，而不简单使用相对路径

#### 绝对路径

[http://ip:port/工程路径/资源路径](http://ip:port//工程路径//资源路径)

在实际开发中，路径`都使用绝对路径`，而不简单的使用相对路径

1. 绝对路径
2. base+相对路径

#### base标签

`<base href="">`标签可以设置当前页面中所有相对路径工作时参照哪个路径进行跳转

即：不再像相对路径那样以浏览器地址栏为准，而是`以base标签中设置的路径为准`

####  `/` 斜杠

在web中`/`斜杠 是一种绝对路径，且在`不同环境中路径不同`

- 被**浏览器**解析

  得到的地址是：http://ip:port/，如：

  ```html
  <a href="/"></a>
  ```

- 被**服务器**解析

  得到的地址是：[http://ip:port/工程路径/](http://ip:port/工程路径)，如：

  - `<url-pattern>/servlet1</url-pattern>`
  - `servletContext.getRealPath("/");`
  - `request.getRequestDispatcher("/");`

  > **特殊情况**
  > 请求重定向：`response.sendRediect("/");`
  >
  > 把斜杠发送给浏览器解析。得到 http://ip:port

#### 动态路径

```Java
String basePath = request.getScheme()//http
        + "://"
        + request.getServerName()//localhost
        + ":"
        + request.getServerPort()//8080
        + request.getContextPath()//工程名
        + "/";
```

### HTTP协议

- 所谓HTTP协议，就是指，客户端和服务器之间通信时，`发送的数据`，需要`遵守的规则`，叫 HTTP协议

- HTTP 协议中的`数据`又叫`报文`

- `客户端给服务器发送数据`叫`请求`，`服务器给客户端回传数据`叫`响应`
  
  - 请求又分为 GET 请求，和 POST 请求两种
  
  > Edge中查看请求、响应等在`F12`中选择`网络`，点击下方一条数据查看

#### GET请求

1. **请求行**
   1. 请求的`方式`：GET
   2. 请求的`资源路径`：`xxxx+?+请求参数`
   3. 请求的协议的`版本号`：HTTP/1.1
2. **请求头**
   - 由`key:value`组成，不同键值对，表示不同含义

![](https://cdn.jsdelivr.net/gh/6hqt9/TyporaNotes/img/202210211136147.png)

##### 常见类型

1. form标签method=get
2. a 标签
3. link 标签引入css
4. Script 标签引入 js 文件
5. img 标签引入图片
6. iframe 引入 html 页面
7. 在浏览器地址栏中输入地址后敲回车

#### POST请求

1. **请求行**
   1. 请求的`方式`：POST
   2. 请求的`资源路径`：`xxxx+?+请求参数`
   3. 请求的协议的`版本号`：HTTP/1.1
2. **请求头**
   - 由`key:value`组成，不同键值对，表示不同含义
3. **一行空行**
4. **请求体**
   - `发送给服务器的内容`

![](https://cdn.jsdelivr.net/gh/6hqt9/TyporaNotes/img/202210211135498.png)

#####  常见类型

1. form 标签 method=pos

#### 常用请求头

- Accept：表示客户端可以接收的数据类型
- Accpet-Languege：表示客户端可以接收的语言类型
- User-Agent：表示客户端浏览器的信息
- Host：表示请求时的服务器ip和端口号

#### 响应

1. **响应行**
   1. 响应的协议和版本号
   2. 响应状态码
   3. 响应状态描述符
2. **响应头**
   - key : value 不同的响应头，有其不同含义
3. **一行空行**
4. **响应体**
   - 就是回传给客户端的数据

![](https://cdn.jsdelivr.net/gh/6hqt9/TyporaNotes/img/202210211135954.png)

##### 常用响应码

- `200` 表示请求`成功`
- `302` 表示请求`重定向`
- `400`表示[SpringMVC特定环境]请求参数问题
- `403`表示没有权限
- `404` 表示请求服务器已经收到了，但是你要的`数据不存在`（请求地址错误）
- `405`表示请求方式和服务器端对应的处理方式不一致
- `50X` 表示服务器已经收到请求，但是`服务器内部错误`（代码错误）

#### MIME类型

**Multipurpose Internet Mail Extensions**：多功能 Internet 邮件扩充服务

- MIME 是 HTTP 协议中数据类型

- **格式**：`大类型/小类型`并`与某一种文件的扩展名相对应`

| 文件               | 后缀        | MIME类型                 |
| ------------------ | ----------- | ------------------------ |
| 超文本标记语言文本 | .html，.htm | text/html                |
| 普通文本           | .txt        | text/plain               |
| RTF 文本           | .rtf        | application/rtf          |
| GIF 图形           | .gif        | image/gif                |
| JPEG 图形          | .jpeg，.jpg | image/jpeg               |
| au 声音文件        | .au         | audio/basic              |
| MIDI 音乐文件      | mid，.midi  | audio/midi，audio/x-midi |
| RealAudio 音乐文件 | .ra, .ram   | audio/x-pn-realaudio     |
| MPEG 文件          | .mpg，.mpeg | video/mpeg               |
| AVI 文件           | .avi        | video/x-msvideo          |
| GZIP 文件          | .gz         | application/x-gzip       |
| TAR 文件           | .tar        | application/x-tar        |

### 表单重复提交

表单重复提交有三种常见的情况：

1. 提交完表单。服务器使用`请求转发`来进行页面跳转。这个时候，用户按下功能键`F5`，就会发起最后一次的请求。造成表单重复提交问题
   解决方法：**使用`重定向`来进行跳转** 

   > 因为请求转发浏览器地址栏不变，重定向地址栏改变

2. 用户正常提交服务器，但是由于网络延迟等原因，迟迟未收到服务器的响应，这个时候，用户以为提交失败，就会着急，然后`多点了几次提交操作`，也会造成表单重复提交

3. 用户正常提交服务器。服务器也没有延迟，但是提交完成后，用户`回退浏览器`，`重新提交`，也会造成表单重复提交

   [情况2与情况2可以使用验证码解决](#kaptcha)

## Jar包

### 文件上传下载

#### 上传

`commons-fileupload-1.2.1.jar`与`commons-io-1.4.jar`

commons-fileupload.jar 需要依赖 commons-io.jar 这个包，所以两个包我们都要引入

1. form标签，method=post请求

2. form标签的encType属性值必须为multipart/form-data值

   > encType=multipart/form-data表示提交的数据，以多段（每一个表单项一个数据段）的形式进行拼接，然后以二进制流的形式发送给服务器

3. form 标签中使用 input type=file 添加上传的文件

4. 编写服务器代码（Servlet 程序）接收，处理上传的数据

![](https://cdn.jsdelivr.net/gh/6hqt9/TyporaNotes/img/202210211135724.png)

##### ServletFIleUpload

用于解析上传的数据

- `boolean ServletFileUpload.isMultipartContent(HttpServletRequest request);`

  判断当前上传的数据格式是否是多段的格式

- `public List parseRequest(HttpServletRequest request`

  解析上传的数据，放入`List<FileItem>`中

##### FileItem

表示每一个表单项

|              方法              |                         作用                          |
| :----------------------------: | :---------------------------------------------------: |
| boolean FileItem.isFormField() | true 表示普通类型的表单项<br />false 表示上传的文件类 |
| String FileItem.getFieldName() |               获取表单项的 name 属性值                |
|  String FileItem.getString()   |                  获取当前表单项的值                   |
|   String FileItem.getName()    |                   获取上传的文件名                    |
| void FileItem.write(File file) |        将上传的文件写到 file 所指向的硬盘位置         |

##### 使用

1. 判断上传的数据是否多段数据
2. 创建`FileItemFactory`工厂实现类
3. `FileItemFactory作形参`创建用于解析上传数据的工具类`ServletFileUpload`类
4. 调用`ServletFileUpload`的`parseRequest`，解析上传的数据，得到每一个表单项`FileItem`
5. 循环判断，每一个表单项，是普通类型，还是上传的文件
6. 如果是文件则调用`fileItem`的`write()`上传文件

```Java
@Override
protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    //1 先判断上传的数据是否多段数据（只有是多段的数据，才是文件上传的）
    if (ServletFileUpload.isMultipartContent(req)) {
        // 创建FileItemFactory工厂实现类
        FileItemFactory fileItemFactory = new DiskFileItemFactory();
        // 创建用于解析上传数据的工具类ServletFileUpload类
        ServletFileUpload servletFileUpload = new ServletFileUpload(fileItemFactory);
        try {
            // 解析上传的数据，得到每一个表单项FileItem
            List<FileItem> list = servletFileUpload.parseRequest(req);
            // 循环判断，每一个表单项，是普通类型，还是上传的文件
            for (FileItem fileItem : list) {
                if (fileItem.isFormField()) {
                    // 普通表单项
                    System.out.println("表单项的name属性值：" + fileItem.getFieldName());
                    // 参数UTF-8.解决乱码问题
                    System.out.println("表单项的value属性值：" + fileItem.getString("UTF-8"));
                } else {
                    // 上传的文件
                    System.out.println("表单项的name属性值：" + fileItem.getFieldName());
                    System.out.println("上传的文件名：" + fileItem.getName());
                    // 保存位置
                    fileItem.write(new File("e:\\" + fileItem.getName()));
                }
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```



#### 下载

1. 获取要下载的文件的名字

2. 读取要下载的文件内容(通过ServletContext对象可以读取)：
   `getServletContext()`

3. 获取要下载的文件类型：
   `servletContext.getMimeType("/file/" + downloadFileName)`

4. 设置响应头告诉客户端返回的数据类型
   `resp.setContentType(mimeType);`

5. 告诉客户端收到的数据是用于下载使用，(可选)根据浏览器设置编码

   - 下载的文件是**中文名**的话，无法显示出正确的中文名。因为在`响应头`中，`不能包含有中文字符`，`只能包含ASCII码`。

   - 最简单
     `resp.setHeader("Content-Disposition", "attachment; filename=" + downloadFileName);`
   - IE与Google
     `resp.setHeader("Content-Disposition", "attachment; filename=" + URLEncoder.encode("中国.jpg", "UTF-8"));`
   - 火狐
     `resp.setHeader("Content-Disposition", "attachment; filename==?UTF-8?B?" + new BASE64Encoder().encode("中国.jpg".getBytes("UTF-8")) + "?=");`
     filename=`=?` + 字符集 + `?B?` + BASE64编码后的内容 + `?=`
     最后的`?=`表示编码内容的介绍

6. 获取文件输入流
   `servletContext.getResourceAsStream("/file/" + downloadFileName);`

7. 获取响应的输出流
   `resp.getOutputStream();`

8. 把下载的文件内容回传给客户端

   `IOUtils.copy(resourceAsStream, outputStream);`

```java
@Override
protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    // 1、获取要下载的文件名
    String downloadFileName = "2.jpg";
    // 2、读取要下载的文件内容 (通过ServletContext对象可以读取)
    ServletContext servletContext = getServletContext();
    // 获取要下载的文件类型
    String mimeType = servletContext.getMimeType("/file/" + downloadFileName);
    System.out.println("下载的文件类型：" + mimeType);
    // 4、在回传前，通过响应头告诉客户端返回的数据类型
    resp.setContentType(mimeType);
    // 5、还要告诉客户端收到的数据是用于下载使用（还是使用响应头）
    // Content-Disposition响应头，表示收到的数据怎么处理
    // attachment表示附件，表示下载使用
    // filename= 表示指定下载的文件名
    // url编码是把汉字转换成为%xx%xx的格式
    if (req.getHeader("User-Agent").contains("Firefox")) {
        // 如果是火狐浏览器使用Base64编码
        resp.setHeader("Content-Disposition", "attachment; filename==?UTF-8?B?" + new BASE64Encoder().encode("中国.jpg".getBytes("UTF-8")) + "?=");
    } else {
        // 如果不是火狐，是IE或谷歌，使用URL编码操作
        resp.setHeader("Content-Disposition", "attachment; filename=" + URLEncoder.encode("中国.jpg", "UTF-8"));
    }
    /**
     * /斜杠被服务器解析表示地址为http://ip:prot/工程名/  映射 到代码的Web目录
     */
    InputStream resourceAsStream = servletContext.getResourceAsStream("/file/" + downloadFileName);
    // 获取响应的输出流
    OutputStream outputStream = resp.getOutputStream();
    //        3、把下载的文件内容回传给客户端
    // 读取输入流中全部的数据，复制给输出流，输出给客户端
    IOUtils.copy(resourceAsStream, outputStream);
}
```

### 参数注入JavaBean

使用BeanUtils包，需要依赖logging包，因此需要导入两个jar包

`commons-beanutils-1.8.0.jar`与`commons-logging-1.1.1.jar`

可能需要额外导的包：commons-collections-3.2.2.jar

> `populate(bean,value)方法`底层调用对应Java对象的`set方法`来设置对象属性

```Java
//使用：
User user = WebUtils.copyParamToBean(req.getParameterMap(), new User());

public class WebUtils {
    /**
     * 把Map中的值注入到对应的JavaBean属性中。
     * @param value
     * @param bean
     */
    public static <T> T copyParamToBean( Map value , T bean ){
        try {
            System.out.println("注入之前：" + bean);
            /**
             * 把所有请求的参数都注入到user对象中
             */
            BeanUtils.populate(bean, value);
            System.out.println("注入之后：" + bean);
        } catch (Exception e) {
            e.printStackTrace();
        }
        return bean;
    }
}
```

### <a id="kaptcha">谷歌kaptcha验证码</a>

`kaptcha-2.3.2.jar`

#### 使用步骤

1. 在web.xml中去`配置`用于生成验证码的Servlet程序

   ```xml
   <servlet>
           <servlet-name>KaptchaServlet</servlet-name>
           <servlet-class>com.google.code.kaptcha.servlet.KaptchaServlet</servlet-class>
   </servlet>
   <servlet-mapping>
           <servlet-name>KaptchaServlet</servlet-name>
           <url-pattern>/kaptcha.jpg</url-pattern>
   </servlet-mapping>
   ```

2. 在表单中使用`img标签`去显示验证码图片并使用它

   ```html
   <img id="code_img" src="http://localhost:8080/工程名/kaptcha.jpg" style="">
   ```

3. 验证码绑定单击切换事件

   ```JavaScript
   $(function () {
       $("#code_img").click(function () {
           this.src = "http://localhost:8080/工程名/kaptcha.jpg?d=" + new Date();
       })
   })
   ```

4. 在`服务器获取谷歌生成的验证码`和`客户端发送过来的验证码`**比较**使用

   ```Java
   public class RegistServlet extends HttpServlet{
   
       @Override
       protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
           // 获取Session中的验证码
           String token = (String) req.getSession().getAttribute(KAPTCHA_SESSION_KEY);
           // 删除 Session中的验证码
           req.getSession().removeAttribute(KAPTCHA_SESSION_KEY);
   
           String code = req.getParameter("code");
           // 获取用户名
           String username = req.getParameter("username");
           if (token != null && token.equalsIgnoreCase(code)) {
               System.out.println("保存到数据库：" + username);
               resp.sendRedirect(req.getContextPath() + "/ok.jsp");
           } else {
               System.out.println("请不要重复提交表单");
           }
       }
   }
   ```

#### 常用参数

| 参数                             | 说明                                                         | 默认值                                                |
| -------------------------------- | :----------------------------------------------------------- | ----------------------------------------------------- |
| kaptcha.border                   | 图片边框，合法值：yes , no                                   | yes                                                   |
| kaptcha.border.color             | 边框颜色，合法值：<br />r,g,b (and optional alpha) 或white,black,blue. | black                                                 |
| kaptcha.border.thickness         | 边框厚度，合法值：>0                                         | 1                                                     |
| kaptcha.image.width              | 图片宽                                                       | 200                                                   |
| kaptcha.image.height             | 图片高                                                       | 50                                                    |
| kaptcha.producer.impl            | 图片实现类                                                   | com.google.code.kaptcha.impl.DefaultKaptcha           |
| kaptcha.textproducer.impl        | 文本实现类                                                   | com.google.code.kaptcha.text.impl.DefaultTextCreator  |
| kaptcha.textproducer.char.string | 文本集合，验证码值从此集合中获取                             | abcde2345678gfynmnpwx                                 |
| kaptcha.textproducer.char.length | 验证码长度                                                   | 5                                                     |
| kaptcha.textproducer.font.names  | 字体                                                         | Arial, Courier                                        |
| kaptcha.textproducer.font.size   | 字体大小                                                     | 40px.                                                 |
| kaptcha.textproducer.font.color  | 字体颜色，合法值：<br />r,g,b 或者 white,black,blue.         | black                                                 |
| kaptcha.textproducer.char.space  | 文字间隔                                                     | 2                                                     |
| kaptcha.noise.impl               | 干扰实现类                                                   | com.google.code.kaptcha.impl.DefaultNoise             |
| kaptcha.noise.color              | 干扰颜色，合法值：<br />r,g,b 或者 white,black,blue.         | black                                                 |
| kaptcha.obscurificator.impl      | 图片样式：<br />水纹com.google.code.kaptcha.impl.WaterRipple <br />鱼眼com.google.code.kaptcha.impl.FishEyeGimpy <br />阴影com.google.code.kaptcha.impl.ShadowGimpy | com.google.code.kaptcha.impl.WaterRipple              |
| kaptcha.background.impl          | 背景实现类                                                   | com.google.code.kaptcha.impl.DefaultBackground        |
| kaptcha.background.clear.from    | 背景颜色渐变，开始颜色                                       | light grey                                            |
| kaptcha.background.clear.to      | 背景颜色渐变，结束颜色                                       | white                                                 |
| kaptcha.word.impl                | 文字渲染器                                                   | com.google.code.kaptcha.text.impl.DefaultWordRenderer |
| kaptcha.session.key              | session key                                                  | KAPTCHA_SESSION_KEY                                   |
| kaptcha.session.date             | session date                                                 | KAPTCHA_SESSION_DATE                                  |



#### 成品示例

```xml
<servlet>
    <servlet-name>KaptchaServlet</servlet-name>
    <servlet-class>com.google.code.kaptcha.servlet.KaptchaServlet</servlet-class>
    <!--验证码宽度-->
    <init-param>
        <param-name>kaptcha.image.width</param-name>
        <param-value>120</param-value>
    </init-param>
    <!-- 验证码高度-->
    <init-param>
        <param-name>kaptcha.image.height</param-name>
        <param-value>50</param-value>
    </init-param>
    <!--验证码字体颜色-->
    <init-param>
        <param-name>kaptcha.textproducer.font.color</param-name>
        <param-value>blue</param-value>
    </init-param>
    <!--验证码背景颜色-->
    <init-param>
        <param-name>kaptcha.background.clear.from</param-name>
        <param-value>white</param-value>
    </init-param>
    <init-param>
        <param-name>kaptcha.background.clear.to</param-name>
        <param-value>white</param-value>
    </init-param>
    <!--去除干扰线的颜色-->
    <init-param>
        <param-name>kaptcha.noise.impl</param-name>
        <param-value>com.google.code.kaptcha.impl.NoNoise</param-value>
    </init-param>
</servlet>
<servlet-mapping>
    <servlet-name>KaptchaServlet</servlet-name>
    <url-pattern>/kaptcha.jpg</url-pattern>
</servlet-mapping>
```

### <a id="gson">JSON操作</a>

谷歌`gson-2.2.4.jar`

#### JavaBean与JSON互转

1. 创建Gson对象实例

   `Gson gson = new Gson();`

2. - 对象转字符串

     **`gson.toJson(Object src)`**

   - 字符串转对象

     **`gson.fromJson(String json, Class<T> classOfT)`**
     第一个参数：json字符串
     第二个参数：转换回去的Java对象的Class对象：Xxx.class

#### List与JSON互转

1. 创建Gson对象实例

   `Gson gson = new Gson();`

2. - List转字符串

     **`gson.toJson(Object src)`**

   - 字符串转List

     **`gson.fromJson(String json, Type typeOfT)`**
     第一个参数：json字符串
     第二个参数：`new TypeToken<ArrayList<Xxx>>(){}.getType()`

> 第二个参数正常要创建一个类继承TypeToken<对应类型>，然后第二个参数写作new继承类.getType()，但要新建Java类过于臃肿，可采用匿名子类直接使用

#### Map与JSON互转

1. 创建Gson对象实例

   `Gson gson = new Gson();`

2. - Map转字符串

     **`gson.toJson(Object src)`**

   - 字符串转Map

     **`gson.fromJson(String json, Type typeOfT)`**
     第一个参数：json字符串
     第二个参数：`new TypeToken<HashMap<Xxx, Xxx>>(){}.getType()`

> 第二个参数正常要创建一个类继承TypeToken<对应类型>，然后第二个参数写作new继承类.getType()，但要新建Java类过于臃肿，可采用匿名子类直接使用

## Tomcat

 Tomcat 版本对应的 zip 压缩包，解压到需要安装的目录即可

tomcat由java和C写的，所以需要JRE，`需要配置JAVA_HOME`

- `bin`：专门用来存放 Tomcat 服务器的可执行程序
- `conf`：专门用来存放 Tocmat 服务器的配置文件
- `lib`：专门用来存放 Tomcat 服务器的 jar 包
- `logs`：专门用来存放 Tomcat 服务器运行时输出的日记信息
- `temp `：专门用来存放 Tomcdat 运行时产生的临时数据
- `webapps`：专门用来存放部署的 Web 工程
- `work`：是 Tomcat 工作时的目录，用来存放 Tomcat 运行时 jsp 翻译为 Servlet 的源码，和 Session 钝化的目录

### 版本

| Tomcat | JAVA |
| :----: | :--: |
| 9.0.x  |  8+  |
| 8.5.x  |  7+  |
| 8.0.x  |  7+  |
| 7.0.x  |  6+  |
| 5.5.x  |  4+  |
| 4.1.x  |  3+  |
| 3.3.x  |  1+  |

### 启动

- 找到Tomcat目录下的bin目录下的`startup.bat`文件，双击，就可以`启动`Tomcat服务器

  - 访问地址如：http://ip:port/ ，即没有工程名的时候，默认访问的是ROOT工程

  - 访问地址如：[http://ip:port/工程名/ ]()，即只有工程名没有资源名，默认访问`index.html`页面

- 打开`命令行`，cd到你的Tomcat的bin目录，敲入启动命令：`catalina run`



### 关闭

1. 点击 tomcat 服务器窗口的 x `关闭`按钮
2. 把 Tomcat 服务器窗口置为当前窗口，然后按快捷键 `Ctrl+C`
3. 找到 Tomcat 的 bin 目录下的 `shutdown.bat` 双击，就可以停止 Tomcat 服务

### 修改端口号

Mysql 默认的端口号是：3306

Tomcat 默认的端口号是：8080

找到 Tomcat 目录下的 `conf` 目录，找到 `server.xml` 配置文件，修改端口号

> HTTP 协议`默认的端口号`是：`80`
>
> 看不到端口号的链接端口就是80
>
> 如上百度[https://www.baidu.com:80]()

### 工程部署(deploy)

#### 直接部署

只需要把 web 工程的目录拷贝到 Tomcat 的 webapps 目录下即可：

1. 在 webapps 目录下创建一个工程(文件夹），名字任意。该文件夹即为context root
2. 该工程下新建名为`WEB-INF`的文件夹
3. 该工程下放入资源（与WEB-INF同级）

#### 间接部署

找到 Tomcat 下的`conf目录\Catalina\localhost\ 下`，创建如下的配置文件：

```xml
<!-- Context 表示一个工程上下文
path 表示工程的访问路径:/abc
docBase 表示你的工程目录在哪里
-->
<Context path="/abc" docBase="E:\book" /
```

## IDEA整合Tomcat

IDEA项目部署位置`不在tomcat文件夹内部`，而在[当前工程\\out\\artifacts\\]()下

IDEA整合Tomcat后拷贝一些副本内容到以下位置：[C:\Users\14412\AppData\Local\JetBrains\IntelliJIdea2020.1\tomcat\XXXXX]()

然后采用工程部署中间接部署的方式，path=/工程名，docBase=项目部署位置
即[XXXXX\\当前工程\\out\\artifacts\\06_servlet_war_exploded]()



1. [File | Settings | Build, Execution, Deployment | Application Server]()

   选择`Tomcat server`

2. `Tomcat Home`选择到`apache-tomcat-8.0.50`

3. 设置tomcat如下：

   ![](https://cdn.jsdelivr.net/gh/6hqt9/TyporaNotes/img/202210211135585.png)

   ![](https://cdn.jsdelivr.net/gh/6hqt9/TyporaNotes/img/202210211135870.png)

### 文件说明

<img src="C:\BaiduSyncdisk\Doc\Markdown\img\Java基础\tomcat5.png" style="zoom:150%;" />

**src**：java源代码

**web**：web工程的资源文件

**WEB-INF**：受服务器保护的目录，浏览器`无法访问`，里面放lib

**lib**：第三方jar包

**xxx.iml**：整个web工程的配置部署描述文件

> web.xml中可以设置`<welcome-file-list>`标签来设置启动tomcat后默认访问页面（index)
>

### 常用设置位置

绝大多数项目相关设置在以下两个地方：

![](https://cdn.jsdelivr.net/gh/6hqt9/TyporaNotes/img/202210211135142.png)

Edit Configuration就是上面整合界面，另外一个常用如下：

![](https://cdn.jsdelivr.net/gh/6hqt9/TyporaNotes/img/202210211135017.png)

1. 新建module
2. facets
3. artifact
4. 配置libraries与dependencies
5. edit configurations
6. 有问题点fix

## Servlet

JavaWeb三大组件之一

Servlet是运行在Web服务器中的小型Java程序，通常通过HTTP(超文本传输协议)接收和响应来自Web客户端的请求

1. 编写一个类去`实现Servlet接口`

2. 实现service方法，处理请求，并响应数据

3. 在`web.xml`中配置servlet程序的访问地址

   ```java
   @Override
   public void service(ServletRequest servletRequest, ServletResponse servletResponse) throws ServletException, IOException {
       System.out.println("3 service === Hello Servlet 被访问了");
       // 类型转换（因为它有getMethod()方法）
       HttpServletRequest httpServletRequest = (HttpServletRequest) servletRequest;
       // 获取请求的方式
       String method = httpServletRequest.getMethod();
       if ("GET".equals(method)) {
           doGet();
       } else if ("POST".equals(method)) {
           doPost();
       }
   }
   ```

   > `两个形参分`别为`请求`与`响应`

### 生命周期

1. 执行 Servlet 构造器方法

2. 执行 init 初始化方法

   第一、二步，`只在第一次访问`的时候创建 Servlet 程序会`调用`

3. 执行 service 方法

   第三步，`每次访问都会调用`

4. 执行 destroy 销毁方法

   第四步，在 web 工程`停止的时候调用`

### HttpServlet

Servlet接口实现类（GenericServlet）的子类

- Servlet接口只负责定义Servlet程序的访问规范

  - GenericServlet实现Servlet接口，做了很多空实现，并有一个ServletConfig类的引用，并对ServletConfig的使用做一些方法

    - HttpServlet抽取类实现了service()方法，并实现了请求的`分发处理`

      > 通过`req.getMethod()`方法
      
      ```Java
      String method = req.getMethod();
      if (method.equals(METHOD_GET)) {
      	......
          doGet(req, resp);   
          ......
      } else if(......)
      ......
      ```
      
      

一般在实际项目开发中，都是使用`继承 HttpServlet 类的方式去实现 Servlet 程序`

1. 编写一个类去继承 HttpServlet 类

   ```Java
   public class HelloServlet2 extends HttpServlet {
       /**
       * doGet（）在 get 请求的时候调用
       * @param req
       * @param resp
       * @throws ServletException
       * @throws IOException
       */
       @Override
       protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException,
       IOException {
           System.out.println("HelloServlet2 的 doGet 方法");
       }
       /**
       * doPost（）在 post 请求的时候调用
       * @param req
       * @param resp
       * @throws ServletException
       * @throws IOException
       */
       @Override
       protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException,
       IOException {
           System.out.println("HelloServlet2 的 doPost 方法");
       }
   }
   ```

   > `两个形参`分别是`Servlet`中`service()方法中两个形参的子接口`

2. 根据业务需要重写 doGet 或 doPost 方法

3. 在web.xml中配置 Servlet 程序的访问地址

   ```xml
   <servlet>
       <servlet-name>HelloServlet2</servlet-name>
       <servlet-class>com.atguigu.servlet.HelloServlet2</servlet-class>
   </servlet>
   <servlet-mapping>
       <servlet-name>HelloServlet2</servlet-name>
       <url-pattern>/hello2</url-pattern>
   </servlet-mapping>
   ```

   > 访问**url**时，根据**url**获取**name**，再根据**name**获得**class**，再到对应class中执行任务

#### HttpServletRequest

继承HttpServlet后`doGet()`与`doPost()`方法的`形参`之一，代表请求数据，是继承Servlet后service()方法中形参之一`ServletRequest`接口的`子接口`

每次只要有请求进入Tomcat服务器，Tomcat服务器就会把请求过来的`HTTP协议信息`解析好`封装到Request对象`中，然后`传递到service()方法`（`doGet()`和 `doPost()`）中给我们使用。我们可以`通过HttpServletRequest对象`，`获取到所有请求的信息`

##### 常用方法

|           方法           |                  作用                  |
| :----------------------: | :------------------------------------: |
|       getMethod()        |       获取请求的方式 GET 或 POST       |
|     getRequestURI()      |           获取请求的资源路径           |
|     getRequestURL()      |  获取请求的统一资源定位符（绝对路径）  |
|     getRemoteHost()      |          获取客户端的 ip 地址          |
|  getHeader(String name)  |               获取请求头               |
|      getParameter()      |             获取请求的参数             |
|   getParameterValues()   | 获取请求的参数（多个值时使用如多选框） |
| setAttribute(key, value) |               设置域数据               |
|    getAttribute(key)     |               获取域数据               |
|  getRequestDispatcher()  |            获取请求转发对象            |

##### 乱码问题

获取字符集：`resp.getCharacterEncoding()`

> 默认字符集为ISO-8859-1

###### Get

1. 先以iso8859-1进行编码
2. 再以utf-8进行解码

```java
@Override
protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    System.out.println("-------------doGet------------");
    // 获取请求参数
    //1 先以iso8859-1进行编码
    //2 再以utf-8进行解码
    username = new String(username.getBytes("iso-8859-1"), "UTF-8");
    String username = req.getParameter("username");
    String password = req.getParameter("password");
    String[] hobby = req.getParameterValues("hobby");
    System.out.println("用户名：" + username);
    System.out.println("密码：" + password);
    System.out.println("兴趣爱好：" + Arrays.asList(hobby));
}
```

###### Post

设置请求体的字符集为 UTF-8，从而解决 post 请求的中文乱码问题

**必须在首次请求参数前设置字符集**

```java
@Override
protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    // 设置请求体的字符集为UTF-8，从而解决post请求的中文乱码问题
    // 也要在获取请求参数之前调用才有效
    req.setCharacterEncoding("UTF-8");
    System.out.println("-------------doPost------------");
    // 获取请求参数
    String username = req.getParameter("username");
    String password = req.getParameter("password");
    String[] hobby = req.getParameterValues("hobby");
    System.out.println("用户名：" + username);
    System.out.println("密码：" + password);
    System.out.println("兴趣爱好：" + Arrays.asList(hobby));
}
```

#### 请求转发

请求转发是指，服务器`收到请求`后，从一个资源`跳转`到另一个资源的操作叫请求转发

##### 特点

1. 浏览器`地址栏没有变化`

2. 两次请求是`同一次请求`

3. `共享`Request域中的`数据`（setAttribute）

4. #### `可以转发到WEB-INF目录下`

5. `不可以`访问`工程以外的资源`

   > 123可以归结于`两次请求`（一次请求一次转发请求）所用`形参`都是`相同`的`HttpServletRequest`与`HttpServletRespons`

##### 步骤

1. 获取请求的参数
2. 设置参数（作为证明）：`req.setAttribute`
3. 以目的地路径为参数，实例化`RequestDispatcher`：`req.getRequestDispatcher("/servlet2");`
4. RequestDispatcher对象将HttpServletRequest与HttpServletResponse两个形参作为参数传递到上面设置的目的地处：`requestDispatcher.forward(req, resp);`

```Java
public class Servlet1 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        // 获取请求的参数（办事的材料）查看
        String username = req.getParameter("username");
        System.out.println("在Servlet1（柜台1）中查看参数（材料）：" + username);
        // 给材料 盖一个章，并传递到Servlet2（柜台 2）去查看
        req.setAttribute("key1", "柜台1的章");
        // 问路：Servlet2（柜台 2）怎么走
        /**
         * 请求转发必须要以斜杠打头，/ 斜杠表示地址为：http://ip:port/工程名/ , 映射到IDEA代码的web目录<br/>
         */
//        RequestDispatcher requestDispatcher = req.getRequestDispatcher("/servlet2");
        RequestDispatcher requestDispatcher = req.getRequestDispatcher("/WEB-INF/form.html");
//        RequestDispatcher requestDispatcher = req.getRequestDispatcher("http://www.baidu.com");
        // 走向Sevlet2（柜台 2）
        requestDispatcher.forward(req, resp);
    }
}

```

```Java
public class Servlet2 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        // 获取请求的参数（办事的材料）查看
        String username = req.getParameter("username");
        System.out.println("在Servlet2（柜台2）中查看参数（材料）：" + username);
        // 查看 柜台1 是否有盖章
        Object key1 = req.getAttribute("key1");
        System.out.println("柜台1是否有章：" + key1);
        // 处理自己的业务
        System.out.println("Servlet2 处理自己的业务 ");
    }
}
```



#### HttpServletResponse

继承HttpServlet后`doGet()`与`doPost()`方法的`形参`之一，代表响应数据，是继承Servlet后service()方法中形参之一`ServletResponse`接口的`子接口`

HttpServletResponse 类和 HttpServletRequest 类一样。每次请求进来，Tomcat 服务器都会`创建一个Response对象传递给Servlet程序`去使用。`HttpServletRequest`表示`请求过来的信息`，`HttpServletResponse`表示所有`响应的信息`，我们如果需要`设置返回给客户端的信息`，都可以通过HttpServletResponse对象来进行设置

##### 输出流

- **字节流**：`getOutputStream()`

  常用于`下载`（传递二进制数据）

- **字符流** `getWriter()`;

  常用于`回传字符串`（**常用**）

> 两个流同时`只能使用一个`
> 使用了字节流，就不能再使用字符流，反之亦然，否则就会报错

##### 回传数据

- 回传字符串数据：`write()方法`

  ```Java
  public class ResponseIOServlet extends HttpServlet {
      @Override
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
  //        System.out.println( resp.getCharacterEncoding() );//默认ISO-8859-1
  //        // 设置服务器字符集为UTF-8
  //        resp.setCharacterEncoding("UTF-8");
  //        // 通过响应头，设置浏览器也使用UTF-8字符集
  //        resp.setHeader("Content-Type", "text/html; charset=UTF-8");
          // 它会同时设置服务器和客户端都使用UTF-8字符集，还设置了响应头
          // 此方法一定要在获取流对象之前调用才有效
          resp.setContentType("text/html; charset=UTF-8");
  //        System.out.println( resp.getCharacterEncoding() );
  //        要求 ： 往客户端回传 字符串 数据。
          PrintWriter writer = resp.getWriter();
          writer.write("到此一游");
      }
  }
  ```

##### 乱码问题

获取字符集：`resp.getCharacterEncoding()`

> 默认字符集为ISO-8859-1

- 方案一（不推荐）

  ```Java
  // 设置服务器字符集为 UTF-8
  resp.setCharacterEncoding("UTF-8");
  // 通过响应头，设置浏览器也使用 UTF-8 字符集
  resp.setHeader("Content-Type", "text/html; charset=UTF-8");
  ```

- **方案二（推荐）**

  ```Java
  // 它会同时设置服务器和客户端都使用 UTF-8 字符集，还设置了响应头
  // 此方法一定要在获取流对象之前调用才有效
  resp.setContentType("text/html; charset=UTF-8");
  ```

#### 请求重定向

请求重定向：

1. 客户端给服务器发送`请求`
2. 服务器`响应码302`，设置`响应头Location`告诉客户端`新地址`（因为之前的地址可能已经被废弃）
3. 然后客户端根据获取的响应头得到新地址，并`重新访问新地址`

##### 特点

1. 浏览器`地址栏`会`发生变化`

2. 客户端进行`两次请求`

3. `不共享`Request域中的`数据`

4. `不能`访问`WEB-INF下的资源`

5. #### `可以访问工程以外的资源`

   > 1234可以归结于`两次请求`，即2
   > 5例如重定向到百度

##### 步骤

- 方案一（不推荐）

  1. 设置响应码302表示重定向：`resp.setStatus(302);`

  2. 设置响应头，说明新地址在哪里：`resp.setHeader("Location", "http://localhost:8080/07_servlet/response2");`

     ```Java
     // 设置响应状态码302 ，表示重定向，（已搬迁）
       resp.setStatus(302);
     // 设置响应头，说明 新的地址在哪里
       resp.setHeader("Location", "http://localhost:8080/07_servlet/response2");
       resp.setHeader("Location", "http://localhost:8080");
     ```

- **方案二（推荐）**

  直接调用`resp.sendRedirect("URL");`

  ```Java
  resp.sendRedirect("http://localhost:8080");
  ```

  

### ServletConfig

- ServletConfig 类从类名上来看，就知道是` Servlet程序`的`配置信息类`
- Servlet 程序和 ServletConfig 对象都是由 Tomcat 负责创建，我们负责使用
- Servlet 程序默认是第一次访问的时候创建，ServletConfig 是`每个 Servlet 程序`创建时，就创建`一个对应的 ServletConfig 对象`

> ServletConfig与Servlet程序`一一对应`

#### 获取与使用

通过`getServletConfig()`可以获取到ServletConfig实例，此方法由Servlet一路继承而来

- 继承Servlet

  init()方法中，ServletConfig作为形参出现以调用

- 继承HttpServlet

  init()方法中，ServletConfig作为形参出现以调用，但`必须调用super.init(config)`

  子类与父类都有init()方法，调用时调用HttpSevlet的init()(`未保存config`)而不是GenericServlet的init()(`保存了config`)

#### 三大作用

1. 可以获取 Servlet 程序的`别名` `servlet-name` 的值

   ```java
   servletConfig.getServletName()//HelloServlet
   ```

2. 获取`初始化参数` `init-param`

   ```java
   servletConfig.getInitParameter("username")//root
   ```

3. 获取 `ServletContext`

   ```java
   servletConfig.getServletContext()
   //org.apache.catalina.core.StandardWrapperFacade@72be5b8（context对象的地址）
   ```

```xml
<!-- servlet标签给Tomcat配置Servlet程序 -->
<servlet>
    <!--servlet-name标签 Servlet程序起一个别名（一般是类名） -->
    <servlet-name>HelloServlet</servlet-name>
    <!--servlet-class是Servlet程序的全类名-->
    <servlet-class>com.atguigu.servlet.HelloServlet</servlet-class>
    <!--init-param是初始化参数-->
    <init-param>
        <!--是参数名-->
        <param-name>username</param-name>
        <!--是参数值-->
        <param-value>root</param-value>
    </init-param>
    <!--init-param是初始化参数-->
    <init-param>
        <!--是参数名-->
        <param-name>url</param-name>
        <!--是参数值-->
        <param-value>jdbc:mysql://localhost:3306/test</param-value>
    </init-param>
</servlet>
<!--servlet-mapping标签给servlet程序配置访问地址-->
<servlet-mapping>
    <!--servlet-name标签的作用是告诉服务器，我当前配置的地址给哪个Servlet程序使用-->
    <servlet-name>HelloServlet</servlet-name>
    <!--
        url-pattern标签配置访问地址
           / 斜杠在服务器解析的时候，表示地址为：http://ip:port/工程路径
           /hello 表示地址为：http://ip:port/工程路径/hello
    -->
    <url-pattern>/hello</url-pattern>
</servlet-mapping>
```

### ServletContext

1. ServletContext 是一个接口，它表示 Servlet 上下文对象
2. `一个 web 工程，只有一个 ServletContext 对象实例`
3. ServletContext 对象是一个`域对象`
4. ServletContext 是在`web工程部署启动`的时候`创建`。在`web工程停止`的时候`销毁`

> `域对象`：可以像Map一样<a id="servletcontext">存取数据</a>的对象，叫域对象。 这里的域指的是存取数据的操作范围，整个web工程

|        |     存数据     |     取数据     |     删除数据      |
| :----: | :------------: | :------------: | :---------------: |
|  Map   |     put()      |     get()      |     remove()      |
| 域对象 | setAttribute() | getAttribute() | removeAttribute() |

#### 获取

- 方式一

  ```Java
  ServletContext context = getServletConfig().getServletContext();//先由GenericServlet得到config对象，再由config得到context
  ```

- 方式二

  ```Java
  ServletContext context = getServletContext();//GenericServlet提供
  ```

#### 四大作用

1. `获取`web.xml中配置的`上下文参数context-param`

   ```Java
   context.getInitParameter("username")// context
   ```

2. `获取`当前的`工程路径`，格式：`/工程路径`

   ```Java
   context.getContextPath()// /06_servlet
   ```

3. `获取`工程部署后在服务器硬盘上的`绝对路径`

   ```Java
   //斜杠被服务器解析地址为:http://ip:port/工程名/  映射到IDEA代码的web目录
   System.out.println("工程部署的路径是:" + context.getRealPath("/")） //C:\BaiduSyncdisk\Code\Java\JavaWebLearning\out\artifacts\06_servlet_war_exploded\
   System.out.println("工程下css目录的绝对路径是:" + context.getRealPath("/css"));
   //C:\BaiduSyncdisk\Code\Java\JavaWebLearning\out\artifacts\06_servlet_war_exploded\css    
   System.out.println("工程下imgs目录1.jpg的绝对路径是:" + context.getRealPath("/imgs/1.jpg"));C:\BaiduSyncdisk\Code\Java\JavaWebLearning\out\artifacts\06_servlet_war_exploded\imgs\1.jpg
   ```

4. 像 Map 一样`存取数据`

   存、取、删除[三个方法](#servletcontext)均由context对象调用

   > 因为ServletContext在一个工程中只有一个且停止时才销毁，故存放的数据在启动期间`一直存在`且不同Servlet之间`共用`

```xml
<!--context-param是上下文参数(它属于整个web工程)-->
<context-param>
    <param-name>username</param-name>
    <param-value>context</param-value><!--value是name的值-->
</context-param>
<!--context-param是上下文参数(它属于整个web工程)-->
<context-param>
    <param-name>password</param-name>
    <param-value>root</param-value><!--value是name的值-->
</context-param>
```

### BaseServlet

其他具体业务的Servlet`继承BaseServlet`这个抽象类，因此调用时实际上是`具体Servlet类调用`继承的doGet()与doPost()方法，对应的`this是具体Servlet实例`，所以通过反射获取并调用的是`具体Servlet的，与请求参数action同名的方法`（具体Servlet类中）

```Java
public abstract class BaseServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doPost(req, resp);
    }
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        // 解决post请求中文乱码问题
        // 一定要在获取请求参数之前调用才有效
        req.setCharacterEncoding("UTF-8");
        // 解决响应的中文乱码
        resp.setContentType("text/html; charset=UTF-8");
        String action = req.getParameter("action");
        try {
            // 获取action业务鉴别字符串，获取相应的业务 方法反射对象
            Method method = this.getClass().getDeclaredMethod(action, HttpServletRequest.class, HttpServletResponse.class);
//            System.out.println(method);
            // 调用目标业务 方法
            method.invoke(this, req, resp);
        } catch (Exception e) {
            e.printStackTrace();
            // 把异常抛给Filter过滤器（通过ThreadLocal与Filter优化后添加）
            throw new RuntimeException(e);
        }
    }
}
```



## Filter

Filter：`过滤器`

1. Filter过滤器是JavaWeb 的三大组件之一。三大组件分别是：Servlet程序、Listener监听器、Filter过滤器
2. Filter过滤器是 JavaEE 的规范。也就是接口
3. Filter过滤器的作用是：**`拦截请求`**，**过滤响应**

拦截请求**常见的应用场景**：

1. 权限检查

2. 日记操作

3. 事务管理

   ……等等

### 生命周期

1. 构造器方法
2. init 初始化方法
   第 1，2 步，在`web工程启动的时候执行`(Filter已经创建)
3. doFilter 过滤方法
   第 3 步，每次`拦截到请求`，就会执行
4. destroy 销毁
   第 4 步，`停止web工程`的时候，就会执行(停止web工程，也会销毁Filter过滤器)

### 使用步骤

1. 编写一个类去`实现Filter接口`

2. 实现过滤方法`doFilter()`

   ```java
   public class AdminFilter implements Filter {
       /**
       * doFilter 方法，专门用于拦截请求。可以做权限检查
       */
       @Override
       public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
           HttpServletRequest httpServletRequest = (HttpServletRequest) servletRequest;
           HttpSession session = httpServletRequest.getSession();
           Object user = session.getAttribute("user");
           // 如果等于 null，说明还没有登录
           if (user == null) {
               servletRequest.getRequestDispatcher("/login.jsp").forward(servletRequest,servletResponse);
               return;
           } else {
               // 让程序继续往下访问用户的目标资源
               filterChain.doFilter(servletRequest,servletResponse);
           }
   	}
   }
   ```

3. 到web.xml中去`配置Filter`
   `拦截地址可以写多个`

   ```xml
   <!--filter 标签用于配置一个 Filter 过滤器-->
   <filter>
       <!--给 filter 起一个别名-->
       <filter-name>AdminFilter</filter-name>
       <!--配置 filter 的全类名-->
       <filter-class>com.atguigu.filter.AdminFilter</filter-class>
   </filter>
   <!--filter-mapping 配置 Filter 过滤器的拦截路径-->
   <filter-mapping>
       <!--filter-name 表示当前的拦截路径给哪个 filter 使用-->
       <filter-name>AdminFilter</filter-name>
       <!--
   	url-pattern 配置拦截路径
       / 表示请求地址为：http://ip:port/工程路径/ 映射到 IDEA 的 web 目录
       /admin/* 表示请求地址为：http://ip:port/工程路径/admin/*
       -->
       <url-pattern>/admin/*</url-pattern>
   </filter-mapping>
   ```

对应的Servlet：

```Java
public class LoginServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException,
    IOException {
        resp.setContentType("text/html; charset=UTF-8");
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        if ("wzg168".equals(username) && "123456".equals(password)) {
            req.getSession().setAttribute("user",username);
            resp.getWriter().write("登录 成功！！！");
        } else {
            req.getRequestDispatcher("/login.jsp").forward(req,resp);
    }
    }
}
```

### 拦截路径

- Filter过滤器只关心请求的`地址是否匹配`，不关心请求的资源是否存在

- `拦截地址可以写多个`

#### 精确匹配

```xml
<url-pattern>/target.jsp</url-pattern>
```

以上配置的路径，表示请求地址必须为：[http://ip:port/工程路径/target.jsp]()

#### 目录匹配

```xml
<url-pattern>/admin/*</url-pattern>
```

以上配置的路径，表示请求地址必须为：[http://ip:port/工程路径/admin/*]()

#### 后缀名匹配

```xml
<url-pattern>*.html</url-pattern>
<!--以上配置的路径，表示请求地址必须以.html 结尾才会拦截到-->
<url-pattern>*.do</url-pattern>
<!--以上配置的路径，表示请求地址必须以.do 结尾才会拦截到-->
<url-pattern>*.action</url-pattern>
<!--以上配置的路径，表示请求地址必须以.action 结尾才会拦截到-->
```

### FilterConfig

- Filter过滤器的配置文件类
- Tomcat每次创建Filter的时候，也会同时创建一个FilterConfig类，这里包含了 Filter 配置文件的配置信息

#### 三大作用

1. 获取 Filter 的名称 filter-name 的内容

   ```Java
   filterConfig.getFilterName()//AdminFilter
   ```

2. 获取在 Filter 中配置的 init-param 初始化参数

   ```Java
   filterConfig.getInitParameter("username")//root
   ```

3. 获取 ServletContext 对象

   ```Java
   filterConfig.getServletContext()
   //org.apache.catalina.core.StandardWrapperFacade@72be5b8（context对象的地址）
   ```

```xml
<!--filter 标签用于配置一个 Filter 过滤器-->
<filter>
    <!--给 filter 起一个别名-->
    <filter-name>AdminFilter</filter-name>
    <!--配置 filter 的全类名-->
    <filter-class>com.atguigu.filter.AdminFilter</filter-class>
    <init-param>
        <param-name>username</param-name>
        <param-value>root</param-value>
    </init-param>
    <init-param>
        <param-name>url</param-name>
        <param-value>jdbc:mysql://localhost3306/test</param-value>
    </init-param>
</filter>
```

### FilterChain

doFilter()方法的形参之一

- **`使用`**：

  调用`filterChain.doFilter(servletRequest,servletResponse)`方法

- **`作用`**：
  1. 调用`下一个Filter`过滤器（如果`有`下一个的话）
  2. 调用目标资源`（`没有`下一个的话）
- **`顺序`**
  - **代码执行顺序**
    - 前置代码1
    - 前置代码2
    - ......
    - 前置代码n
    - 后置代码n
    - ......
    - 后置代码2
    - 后置代码1
  - **Filter执行顺序**
    - 根据web.xml中`从上往下`顺序
- **`特点`**：
  1. 所有Filter和目标资源都默认执行在同一个线程中
  2. 多个Filter共同执行时，共用同一个Request对象



## Listener

1. Listener监听器是JavaWeb的三大组件之一。JavaWeb的三大组件分别是：Servlet 程序、Filter 过滤器、Listener 监听器
2. Listener是JavaEE 的规范，就是接口
3. 监听器的作用是，监听某种事物的变化。然后通过回调函数，反馈给客户（程序）去做一些相应的处理

监听器共有8个，绝大多数用不上，只剩`ServletContextListener`有用

### ServletContextListener

- ServletContextListener 它可以监听`ServletContext`对象的`创建`和`销毁`

- ServletContext对象在web工程启动的时候创建，在web工程停止的时候销毁

- `监听到创建和销毁`之后都会分别`调用`ServletContextListener监听器的`方法`反馈

  ```Java
  public interface ServletContextListener extends EventListener {
      /**
      * 在 ServletContext 对象创建之后马上调用，做初始化
      */
      public void contextInitialized(ServletContextEvent sce);
      /**
      * 在 ServletContext 对象销毁之后调用
      */
      public void contextDestroyed(ServletContextEvent sce);
  }
  ```

#### 使用步骤

1. 编写一个类去实现 ServletContextListener
2. 实现其两个回调方法
3. 到 web.xml 中去配置监听

```java
public class MyServletContextListenerImpl implements ServletContextListener {

    @Override
    public void contextInitialized(ServletContextEvent sce) {
        System.out.println("ServletContext对象被创建了");
    }

    @Override
    public void contextDestroyed(ServletContextEvent sce) {
        System.out.println("ServletContext对象被销毁了");
    }
}
```

```xml
<!--配置监听器-->
    <listener>
        <listener-class>com.atguigu.listener.MyServletContextListenerImpl</listener-class>
    </listener>
```

## Cookie

1. Cookie翻译过来是饼干的意思
2. Cookie是服务器通知`客户端保存键值`对的一种技术
3. 客户端有了Cookie后，`每次请求都发送给服务器`
4. 每个Cookie的`大小不能超过4kb`

### 创建

1. 创建Cookie对象：`new Cookie("key", "value")`

2. 通知客户端保存Cookie：`resp.addCookie(cookie1);`

   ```Java
   protected void createCookie(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
       //1 创建Cookie对象
       Cookie cookie = new Cookie("key4", "value4");
       //2 通知客户端保存Cookie
       resp.addCookie(cookie);
       //1 创建Cookie对象
       Cookie cookie1 = new Cookie("key5", "value5");
       //2 通知客户端保存Cookie
       resp.addCookie(cookie1);
       resp.getWriter().write("Cookie创建成功");
   }
   ```

### 常用方法

|             方法             |                             作用                             |
| :--------------------------: | :----------------------------------------------------------: |
|       req.getCookies()       |                       返回Cookie[]数组                       |
|    resp.addCookie(cookie)    |                          创建Cookie                          |
|       cookie.getName()       |                     获取Cookie的key(名)                      |
|      cookie.getValue()       |                    获取Cookie的Value(值)                     |
|      cookie.setValue()       |                    修改Cookie的Value(值)                     |
| cookie.setMaxAge(int expiry) | 设置Cookie的生命(秒)<br />为0代表立刻删除<br />为负代表关闭浏览器删除 |
|  cookie.setPath(String url)  |                 设置Cookie只发送到对应路径下                 |

## Session

1. Session 就一个接口（HttpSession）
2. Session 就是`会话`。它是用来维护一个客户端和服务器之间关联的一种技术
3. 每个客户端都有自己的一个 Session 会话
4. Session 会话中，我们经`常用来保存用户登录之后的信息`

- 服务器端`没`调用`request.getSession()`方法：什么都不会发生
- 服务器端调用了`request.getSession()`方法
  - 服务器端`检查`当前请求中是否携带了`JSESSIONID`的`Cookie`
    - **有**：根据JSESSIONID在服务器端`查找`对应的`HttpSession对象`
      - **能找到**：将找到的HttpSession对象作为request.getSession()方法的返回值返回
      - **找不到**：服务器端`新建一个HttpSession对象`作为request.getSession()方法的返回值返回
    - **无**：服务器端`新建一个HttpSession对象`作为request.getSession()方法的返回值返回

### 创建

`request.getSession()`

### 常用方法

|               方法               |                             作用                             |
| :------------------------------: | :----------------------------------------------------------: |
|       request.getSession()       | 第一次调用是：创建 Session 会话<br />之后调用都是：获取前面创建好的 Session 会话对象。 |
|         request.isNew()          |                  判断到底是不是刚创建出来的                  |
|         session.getId()          |           得到 Session 的会话 id 值(每个回话唯一)            |
| session.getMaxInactiveInterval() |          获取session无操作时的持续时间(默认30分钟)           |
| session.getMaxInactiveInterval() |                设置session无操作时的持续时间                 |
|       session.invalidate()       |                        强制让会话失效                        |
|               ....               |                             ....                             |

> 设置超时时间为负数表示永不超时（极少使用）

Tomcat服务器的配置文件web.xml中默认有以下的配置，就表示配置了当前Tomcat服务器下所有的Session超时配置默认时长为：30分钟，可以进行修改

```xml
<!--表示当前 web 工程。创建出来 的所有 Session 默认是 20 分钟 超时时长-->
<session-config>
	<session-timeout>20</session-timeout>
</session-config>
```

### Session域

用于存储数据

在Session域中存储数据，显而易见，里面存储的数据是每个`Session(会话)独有的`，`Session是谁的数据就是谁的`，`不能获取其他Session的域数据`

- 存数据

  `req.getSession().setAttribute("key", "value");`

- 取数据

  `req.getSession().getAttribute("key");`

- 删数据

  `req.getSession().removeAttribute("key");`

### 与Cookie联系

1. 客户端`第一次`访问没有Cookie时，服务器会通过getSession()`创建Session`对象
2. 而创建Session对象时，都会`创建一个Cookie对象`
   这个Cookie对象的`key`=**JSESSIONID**，`value`=**Session的ID**
3. 服务器通过响应让`客户端创建Cookie对象`
4. 之后`客户端`每次请求都将这个包含SessionID的`Cookie发送给服务器`
5. 服务器之后会`通过Cookie的id`值找到创建的`Session对象`并返回
6. 如果这个Cookie被删除，就会创建新的Session对象，依此循环

## ThreadLocal

- `ThreadLocal`的作用，它可以解决多线程的数据安全问题
- `ThreadLocal`它可以**`给当前线程关联一个数据`**（可以是普通变量，可以是对象，也可以是数组，集合）

ThreadLocal 的特点：

1. ThreadLocal可以为`当前线程关联一个数据`（它可以像 Map 一样存取数据，key 为当前线程）
2. 每`一个 hreadLocal对象`，只能为当前线程关联`一个数据`，如果要为当前线程关联`多个数据`，就需要使用`多个ThreadLocal对象`实例
3. 每个 ThreadLocal 对象实例定义的时候，一般都是`static`类型
4. ThreadLocal中保存数据，在线程销毁后。会由JVM虚拟机自动释放

### 常用方法

- `threadLocal.set(T value)`：保存数据
- `threadLocal.get()`：获取数据
- `threadLocal.remove()`：删除数据

### 优化数据库事务

考虑数据库事务，就要保证事务中的操作使用同一个连接，所有操作都正常完成就提交事务，否则就回滚数据。

因此，使`用ThreadLocal，为每个线程绑定一个连接`（同一个客户端请求下是一个线程）

#### JdbcUtils

主要优化连接的**获取**（使用ThreadLocal）与**关闭**（考虑事务）

```java
public class JdbcUtils {
    private static DruidDataSource dataSource;
    private static ThreadLocal<Connection> conns = new ThreadLocal<Connection>();

    static {
        try {
            Properties properties = new Properties();
            // 读取 jdbc.properties属性配置文件
            InputStream inputStream = JdbcUtils.class.getClassLoader().getResourceAsStream("jdbc.properties");
            // 从流中加载数据
            properties.load(inputStream);
            // 创建 数据库连接 池
            dataSource = (DruidDataSource) DruidDataSourceFactory.createDataSource(properties);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
    /**
     * 获取数据库连接池中的连接
     * @return 如果返回null, 说明获取连接失败<br />有值就是获取连接成功
     */
    public static Connection getConnection() {
        Connection conn = conns.get();
        if (conn == null) {
            try {
                conn = dataSource.getConnection();//从数据库连接池中获取连接
                conns.set(conn); // 保存到ThreadLocal对象中，供后面的jdbc操作使用
                conn.setAutoCommit(false); // 设置为手动管理事务
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
        return conn;
    }
    /**
     * 提交事务，并关闭释放连接
     */
    public static void commitAndClose() {
        Connection connection = conns.get();
        if (connection != null) { // 如果不等于null，说明 之前使用过连接，操作过数据库
            try {
                connection.commit(); // 提交 事务
            } catch (SQLException e) {
                e.printStackTrace();
            } finally {
                try {
                    connection.setAutoCommit(true);// 位置不一定正确
                    connection.close(); // 关闭连接，资源资源
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
        }
        // 一定要执行remove操作，否则就会出错。（因为Tomcat服务器底层使用了线程池技术）
        conns.remove();
    }

    /**
     * 回滚事务，并关闭释放连接
     */
    public static void rollbackAndClose() {
        Connection connection = conns.get();
        if (connection != null) { // 如果不等于null，说明 之前使用过连接，操作过数据库
            try {
                connection.rollback();//回滚事务
            } catch (SQLException e) {
                e.printStackTrace();
            } finally {
                try {
                    connection.setAutoCommit(true);// 位置不一定正确
                    connection.close(); // 关闭连接，资源资源
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
        }
        // 一定要执行remove操作，否则就会出错。（因为Tomcat服务器底层使用了线程池技术）
        conns.remove();
    }
```



#### BaseDAO

要抛异常以便tomcat捕获到异常（try-catch会将异常处理掉）

```Java
public abstract class BaseDao {
    //使用DbUtils操作数据库
    private QueryRunner queryRunner = new QueryRunner();
    /**
     * update() 方法用来执行：Insert\Update\Delete语句
     * @return 如果返回-1,说明执行失败<br/>返回其他表示影响的行数
     */
    public int update(String sql, Object... args) {

        System.out.println(" BaseDao 程序在[" +Thread.currentThread().getName() + "]中");
        Connection connection = JdbcUtils.getConnection();
        try {
            return queryRunner.update(connection, sql, args);
        } catch (SQLException e) {
            e.printStackTrace();
            throw new RuntimeException(e);
        }
    }
    /**
     * 查询返回一个javaBean的sql语句
     * @param type 返回的对象类型
     * @param sql  执行的sql语句
     * @param args sql对应的参数值
     * @param <T>  返回的类型的泛型
     * @return
     */
    public <T> T queryForOne(Class<T> type, String sql, Object... args) {
        Connection con = JdbcUtils.getConnection();
        try {
            return queryRunner.query(con, sql, new BeanHandler<T>(type), args);
        } catch (SQLException e) {
            e.printStackTrace();
            throw new RuntimeException(e);
        }
    }
    /**
     * 查询返回多个javaBean的sql语句
     * @param type 返回的对象类型
     * @param sql  执行的sql语句
     * @param args sql对应的参数值
     * @param <T>  返回的类型的泛型
     * @return
     */
    public <T> List<T> queryForList(Class<T> type, String sql, Object... args) {
        Connection con = JdbcUtils.getConnection();
        try {
            return queryRunner.query(con, sql, new BeanListHandler<T>(type), args);
        } catch (SQLException e) {
            e.printStackTrace();
            throw new RuntimeException(e);
        }
    }
    /**
     * 执行返回一行一列的sql语句
     * @param sql   执行的sql语句
     * @param args  sql对应的参数值
     * @return
     */
    public Object queryForSingleValue(String sql, Object... args){
        Connection conn = JdbcUtils.getConnection();
        try {
            return queryRunner.query(conn, sql, new ScalarHandler(), args);
        } catch (SQLException e) {
            e.printStackTrace();
            throw new RuntimeException(e);
        }
    }
}

```

#### Filter处理异常

##### 异常处理类

让系统中的所有请求都经过doFilter()，而doFilter()这个方法的调用代表了后面的数据库操作，因此可以对doFilter()进行try-catch操作，一次性为所有请求都加上

```Java
public class TransactionFilter implements Filter {
    @Override
    public void init(FilterConfig filterConfig) throws ServletException {

    }
    @Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
        try {
            filterChain.doFilter(servletRequest,servletResponse);
            JdbcUtils.commitAndClose();// 提交事务
        } catch (Exception e) {
            JdbcUtils.rollbackAndClose();//回滚事务
            e.printStackTrace();
            throw new RuntimeException(e);//把异常抛给Tomcat管理展示友好的错误页面
        }
    }
    @Override
    public void destroy() {

    }
}
```

##### 配置文件

```xml
<filter>
    <filter-name>TransactionFilter</filter-name>
    <filter-class>com.atguigu.filter.TransactionFilter</filter-class>
</filter>
<filter-mapping>
    <filter-name>TransactionFilter</filter-name>
    <!-- /* 表示当前工程下所有请求 -->
    <url-pattern>/*</url-pattern>
</filter-mapping>
```

## 错误页面

 `web.xml`中可以通过错误页面配置来进行管理

```xml
<!--error-page标签配置，服务器出错之后，自动跳转的页面-->
<error-page>
    <!--error-code是错误类型-->
    <error-code>500</error-code>
    <!--location标签表示。要跳转去的页面路径-->
    <location>/pages/error/error500.jsp</location>
</error-page>
<!--error-page标签配置，服务器出错之后，自动跳转的页面-->
<error-page>
    <!--error-code是错误类型-->
    <error-code>404</error-code>
    <!--location标签表示。要跳转去的页面路径-->
    <location>/pages/error/error404.jsp</location>
</error-page>
```

## JSON

**`JSON`**(`JavaScript Object Notation`) 是一种**轻量级的数据交换格式**(相比xml)。易于人阅读和编写。同时也易于机器解析和生成。JSON 采用完全独立于语言的文本格式，而且很多语言都提供了对 json的支持（包括 C, C++, C#, Java, JavaScript, Perl, Python 等）。 这样就使得 JSON 成为理想的数据交换格式(客户端与服务器之间业务数据交换)

### 如何定义

json是由键值对组成，并且由`{}`包围。每个键由`""`引起来，键和值之间使用`:`进行分隔， 多组键值对之间使用`,`进行分隔。

值可以是各种基本数据类型，也可以是数组，json等。例如：

```json
var jsonObj = {
	"key1":12,
	"key2":"abc",
	"key3":true,
	"key4":[11,"arr",false],
	"key5":{
		"key5_1" : 551,
		"key5_2" : "key5_2_value"
	},
	"key6":[{
		"key6_1_1":6611,
		"key6_1_2":"key6_1_2_value"
	},{
		"key6_2_1":6621,
		"key6_2_2":"key6_2_2_value"
	}]
};
```

### 如何访问

`jsonObj.key`：获取key对应的value

### 格式转换

json 的存在有两种形式：

- 对象的形式存在，我们叫它`json对象`
- 字符串的形式存在，我们叫它`json字符串`

> 一般我们要`操作json中的数据`的时候，需要`json对象`的格式。一般我们要在客户端和服务器之间进行`数据交换`的时候，使用`json字符串`

- **`JSON.stringify(jsonObj)`**

  把**json对象**转换成为**json字符串**

- **`JSON.parse(jsonObjString)`**

  把**json字符串**转换成为**json对象**

### Java使用JSON

[使用Gson jar包实现](#gson)



## AJAX

**`AJAX`**(`Asynchronous Javascript And XML`)（异步JavaScript和XML），是指一种创建交互式网页应用的网页开发技术

### 特点

- ajax 是一种浏览器通过js异步发起请求，局部更新页面的技术
- 浏览器地址栏不会发生变化
- 局部更新不会舍弃原来页面的内容

> **`同步`**：如果在一段代码的中间向服务器发起请求，会`等待服务器响应`后再继续执行请求后面的内容
>
> **`异步`**：如果一段代码的中间向服务器发起请求，`不会等待服务器响应`，而是直接执行后面的内容

### 原生AJAX

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
    <meta http-equiv="pragma" content="no-cache"/>
    <meta http-equiv="cache-control" content="no-cache"/>
    <meta http-equiv="Expires" content="0"/>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <title>Insert title here</title>
    <script type="text/javascript">
        // 在这里使用javaScript语言发起Ajax请求，访问服务器AjaxServlet中javaScriptAjax
        function ajaxRequest() {
// 				1、我们首先要创建XMLHttpRequest 
            var xmlhttprequest = new XMLHttpRequest();
// 				2、调用open方法设置请求参数
            xmlhttprequest.open("GET", "http://localhost:8080/16_json_ajax_i18n/ajaxServlet?action=javaScriptAjax", true);//true代表异步,false代表同步
// 				3、在send方法前绑定onreadystatechange事件，处理请求完成后的操作。
            xmlhttprequest.onreadystatechange = function () {
                if (xmlhttprequest.readyState == 4 && xmlhttprequest.status == 200) {
                    alert("收到服务器返回的数据：" + xmlhttprequest.responseText);
                    var jsonObj = JSON.parse(xmlhttprequest.responseText);
                    // 把响应的数据显示在页面上
                    document.getElementById("div01").innerHTML = "编号：" + jsonObj.id + " , 姓名：" + jsonObj.name;
                }
            }
// 				4、调用send方法发送请求
            xmlhttprequest.send();


//            alert("我是最后一行的代码");

        }
    </script>
</head>
<body>
<!--		<a href="http://localhost:8080/16_json_ajax_i18n/ajaxServlet?action=javaScriptAjax">非Ajax</a>-->
<button onclick="ajaxRequest()">ajax request</button>
<button onclick="ajaxRequest()">ajax request</button>
<button onclick="ajaxRequest()">ajax request</button>
<button onclick="ajaxRequest()">ajax request</button>
<button onclick="ajaxRequest()">ajax request</button>
<div id="div01">
</div>
<table border="1">
    <tr>
        <td>1.1</td>
        <td>1.2</td>
    </tr>
    <tr>
        <td>2.1</td>
        <td>2.2</td>
    </tr>
</table>
</body>
</html>
```

### JQurey&AJAX

$.ajax({

​	url:				请求的地址

​	type:		 	请求的类型 GET 或 POST 请求

​	data:		 	发送给服务器的数据

​								格式一：name=value&name=value

​								格式二：{key:value}

​	success:		请求成功，响应的回调函数

​	dataType:	 响应的数据类型。常用类型：

​								text：纯文本

​								xml：xml 数据 

​								json：json 对象

});

```javascript
<script type="text/javascript">
    $(function () {
        // ajax请求
        $("#ajaxBtn").click(function () {
            $.ajax({
                url: "http://localhost:8080/16_json_ajax_i18n/ajaxServlet",
                // data:"action=jQueryAjax",
                data: {action: "jQueryAjax"},
                type: "GET",
                success: function (data) {
                    // alert("服务器返回的数据是：" + data);
                    // var jsonObj = JSON.parse(data);
                    $("#msg").html(" ajax 编号：" + data.id + " , 姓名：" + data.name);
                },
                dataType: "json"
            });
        });
    	//							   成功回调函数↓
        // ajax--get请求	$.get(url,data,function(data),dataType)
        $("#getBtn").click(function () {
            $.get("http://localhost:8080/16_json_ajax_i18n/ajaxServlet", "action=jQueryGet", function (data) {
                $("#msg").html(" get 编号：" + data.id + " , 姓名：" + data.name);
            }, "json");
        });
    
        //							     成功回调函数↓
        // ajax--post请求	 $.post(url,data,function(data),dataType)
        $("#postBtn").click(function () {
            // post请求
            $.post("http://localhost:8080/16_json_ajax_i18n/ajaxServlet", "action=jQueryPost", function (data) {
                $("#msg").html(" post 编号：" + data.id + " , 姓名：" + data.name);
            }, "json");
        });
        //							           成功回调函数↓
        // ajax--getJson请求  $.getJSON(url,data,function(data))
        $("#getJSONBtn").click(function () {
            $.getJSON("http://localhost:8080/16_json_ajax_i18n/ajaxServlet", "action=jQueryGetJSON", function (data) {
                $("#msg").html(" getJSON 编号：" + data.id + " , 姓名：" + data.name);
            });
        });
    
        // ajax请求
        $("#submit").click(function () {
            // 把参数序列化
            //$("#form01").serialize()	
            //把表单中所有内容获取并以name=value&name=value的形式进行拼接
            $.getJSON("http://localhost:8080/16_json_ajax_i18n/ajaxServlet", "action=jQuerySerialize&" + $("#form01").serialize(), function (data) {
                $("#msg").html(" Serialize 编号：" + data.id + " , 姓名：" + data.name);
            });
        });
    });
</script>
```



## JSP

`java server pages`：Java 的服务器页面

**主要作用**：代替 Servlet 程序回传 html 页面的数据
因为 Servlet 程序回传 html 页面数据是一件非常繁锁的事情。开发成本和维护成本都极高

jsp页面和html页面一样，都是`存放在web目录`下，访问也`和html页面一样`

- servlet回传html数据

  ```Java
  public class PringHtml extends HttpServlet {
      @Override
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
  //       jsp使用 JspWriter 输出
          // 通过响应的回传流回传html页面数据
          resp.setContentType("text/html; charset=UTF-8");
          PrintWriter writer = resp.getWriter();
          writer.write("<!DOCTYPE html>\r\n");
          writer.write("  <html lang=\"en\">\r\n");
          writer.write("  <head>\r\n");
          writer.write("      <meta charset=\"UTF-8\">\r\n");
          writer.write("      <title>Title</title>\r\n");
          writer.write("  </head>\r\n");
          writer.write(" <body>\r\n");
          writer.write("    这是html页面数据 \r\n");
          writer.write("  </body>\r\n");
          writer.write("</html>\r\n");
          writer.write("\r\n");
      }
  }
  ```

### JSP的本质

jsp 页面本质上是一个 Servlet 程序

当我们第一次访问jsp页面的时候。`Tomcat`服务器会把`jsp页面`翻译成为一个`java源文件`，并且对它进行`编译成为.class字节码`程序

[C:\Users\14412\AppData\Local\JetBrains\IntelliJIdea2020.1\tomcat\Tomcat_8_0_50_JavaWebLearning_5\work\Catalina\localhost\08_jsp\org\apache\jsp]()

该源文件的Java`类名`为`jsp文件名`，继承`org.apache.jasper.runtime.HttpJspBase`，而`HttpJspBase`是`HttpServlet`的`子类`

即`jsp就是Servlet程序`

### 语法

#### 头部page指令

jsp 的 page 指令可以修改 jsp 页面中一些重要的属性，或者行为

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
```

|     属性     |                             作用                             |
| :----------: | :----------------------------------------------------------: |
|   language   |        表示 jsp 翻译后是什么语言文件。暂时只支持 java        |
| contentType  | 表示 jsp 返回的编码类型是什么，也是源码中 response.setContentType()参数 |
| pageEncoding |              表示当前 jsp 页面文件本身的字符集               |
|    import    |             跟 java 源代码中一样。用于导包，导类             |
|  autoFlush   | 设置当 out 输出流缓冲区满了之后，是否自动刷新缓冲区<br />默认值是 true |
|    buffer    |              设置 out 缓冲区的大小。默认是 8kb               |
|  errorPage   |     设置当 jsp 页面运行时出错，自动跳转去的错误页面路径      |
| isErrorPage  | 设置当前 jsp 页面是否是错误信息页面<br />默认是 false。如果是 true 可以 获取异常信息 |
|   session    | 设置访问当前 jsp 页面，是否会创建 HttpSession 对象。默认是 true |
|   extends    |            设置 jsp 翻译出来的 java 类默认继承谁             |

#### 常用脚本

##### 声明脚本(极少使用)

**作用**：可以给 jsp 翻译出来的 java 类定义属性和方法甚至是静态代码块、内部类等

**格式**：`<%! 声明 java 代码 %>`

```jsp
<%--1、声明类属性--%>
    <%!
        private Integer id;
        private String name;
        private static Map<String,Object> map;
    %>
<%--2、声明static静态代码块--%>
    <%!
        static {
            map = new HashMap<String,Object>();
            map.put("key1", "value1");
            map.put("key2", "value2");
            map.put("key3", "value3");
        }
    %>
<%--3、声明类方法--%>
    <%!
        public int abc(){
            return 12;
        }
    %>
<%--4、声明内部类--%>
    <%!
        public static class A {
            private Integer id = 12;
            private String abc = "abc";
        }
    %>
```

##### 表达式脚本(常用)

**作用**：在jsp页面上输出数据

**格式**：`<%=表达式%>`（等价于out.print）

**特点**：

1. 所有的表达式脚本都会被翻译到`_jspService()`方法中_
2. 表达式脚本都会被翻译成为`out.print()`输出到页面上
3. 由于表达式脚本翻译的内容都在`_jspService()`方法中,所以`_jspService()`方法中的对象都可以直接使用
4. 表达式脚本中的表达式不能以分号结束

```jsp
<%--
1.输出整型
2.输出浮点型
3.输出字符串
4.输出对象--%>
<%=12 %> <br>
<%=12.12 %> <br>
<%="我是字符串" %> <br>
<%=map%> <br>
<%=request.getParameter("username")%>
```

##### 代码脚本

**作用**：可以在 jsp 页面中，编写我们自己需要的功能（写的是 java 语句）

**格式**：`<% java 语句 %>`

**特点**：

1. 代码脚本翻译之后都在`_jspService` 方法中_
2. 代码脚本由于翻译到`_jspService()`方法中，所以在`_jspService()`方法中的现有对象都可以直接使用
3. 还可以由多个代码脚本块组合完成一个完整的 java 语句
4. 代码脚本还可以和表达式脚本一起组合使用，在 jsp 页面上输出数据

```jsp
<%--1.代码脚本----if 语句--%>
    <%
        int i = 13 ;
        if (i == 12) {
    %>
            <h1>国哥好帅</h1>
    <%
        } else {
    %>
        <h1>国哥又骗人了！</h1>
    <%
        }
    %>
<br>
<%--2.代码脚本----for 循环语句--%>
    <table border="1" cellspacing="0">
    <%
        for (int j = 0; j < 10; j++) {
    %>
        <tr>
            <td>第 <%=j + 1%>行</td>
        </tr>
    <%
        }
    %>
    </table>
<%--3.翻译后java文件中_jspService方法内的代码都可以写--%>
    <%
        String username = request.getParameter("username");
        System.out.println("用户名的请求参数值是：" + username);
    %>
```

#### 常用标签

##### 静态包含

`<%@ include file=""%>`

- file：指定你要包含的jsp页面的路径
- 地址中`第一个斜杠 / `表示为`http://ip:port/工程路径/` 映射到代码的web目录

静态包含的`特点`：

1. 静态包含不会翻译被包含的jsp页面
2. 静态包含其实是把被包含的jsp页面的`代码拷贝到包含的位置执行输出`

```jsp
<%@ include file="/include/footer.jsp"%>
```

##### 动态包含

`<jsp:include page=""></jsp:include>`

- page：指定你要包含的jsp页面的路径
- 动态包含也可以像静态包含一样。把被包含的内容执行输出到包含位置

动态包含的特点：

1. 动态包含会把包含的jsp页面也翻译成为java代码
2. 动态包含底层代码使用如下代码去调用被包含的jsp页面执行输出。
   `JspRuntimeLibrary.include(request, response, "/include/footer.jsp", out, false);`
3. 动态包含，还可以传递参数

##### 转发

`<jsp:forward page=""></jsp:forward>`是请求转发标签，它的功能就是请求转发

- page：设置请求转发的路径

等价于`request.getRequestDispatcher("/").forward(request,response);`

#### 注释

- HTML注释

  ```html
  <!-- 这是html注释  -->
  ```

- Java注释

  ```java
  // 单行java注释
  /*  多行java注释  */
  ```

- jsp注释

  ```jsp
  <%-- 这是jsp注释  --%>
  ```

### 九大内置对象

jsp中的**内置对象**，是指Tomcat在`翻译jsp页面成为Servlet源代码`后，`内部提供的九大对象`，叫**内置对象**

|    对象     |        说明        |
| :---------: | :----------------: |
|   request   |      请求对象      |
|  response   |      响应对象      |
| pageContext |   jsp上下文对象    |
|   session   |      会话对象      |
| application | ServletContext对象 |
|   config    | ServletConfig对象  |
|     out     |   jsp输出流对象    |
|    page     | 指向当前jsp的对象  |
|  exception  |      异常对象      |

#### 四大域对象

- `域对象`是可以像Map一样**存取数据**的对象
- 四个域对象**功能一样**。**不同**的是它们对数据的**存取范围**

九大内置对象中的四个域对象：

|               对象               |                             说明                             |
| :------------------------------: | :----------------------------------------------------------: |
| pageContext (PageContextImpl 类) |                   当前 jsp 页面范围内有效                    |
| request (HttpServletRequest 类)  |                        一次请求内有效                        |
|     session (HttpSession 类)     | 一个会话范围内有效<br />（打开浏览器访问服务器，直到关闭浏览器） |
| application (ServletContext 类)  | 整个 web 工程范围内都有效<br />（只要 web 工程不停止，数据都在 |

> 四个域在使用的时候，`优先顺序`分别是，他们从`小到大`的范围的顺序：
> `pageContext` >>> `request` >>> `session` >>> `application`

#### out与response输出

**结论**：在`jsp页面`中，可以`统一使用out.print()`来进行输出

**out**：jsp中的输出，`out.write` / `out.print`

**response**：`response.getWritter.write()`

> `out.write()`输出字符串没有问题
> `out.print()`输出任意数据都没有问题（都转换成为字符串后调用的 write 输出）

![](https://cdn.jsdelivr.net/gh/6hqt9/TyporaNotes/img/202210211135338.png)

由于jsp翻译之后，底层源代码都是使用 out 来进行输出，所以一般情况下。我们在`jsp页面`中`统一使用out`来进行输出。`避免打乱页面输出内容的顺序`

