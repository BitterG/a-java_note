# String转换为基本类型

```java
String s5 = "123";
//	String类 类型转化为基本类型
int num1 = Integer.parseInt(s5);
double num2 = Double.parseDouble(s5);
Float num3 = Float.parseFloat(s5);
long num4 = Long.parseLong(s5);
byte num5 = Byte.parseByte(s5);
boolean nums6 = Boolean.parseBoolean("true");
short num7 = short.parseShort(s5);

System.out.println(s5.charAt(0)); // 取出字符串中的第()个字符
```

# 除法/

```java
System.out.println(10 / 4);	// java整数int 除 整数int 结果为 整数int
// 输出： 2
System.out.println(10.0 / 2);	// float / int == float
// 输出： 2.5
```

# 取数%

```java
System.out.println(10 % 3);
// 1
System.out.println(10 % -3);
// 1
System.out.println(-10 / 3);
// -1
// java中 取余遵循的公式 a % b == a - a / b * b
```

# 逻辑运算符

```java
int age = 50;
if (age > 20 && age < 90) {
    System.out.println("OK");
}
if (age > 20 & age < 90) {
    System.out.println("OK");
}
// 区别 && 短路与 若&&前的条件为false则不会判断后者，效率更高
// 	   &  逻辑与 不管第一个条件是否为false，都会判断第二个条件，效率低
// 一般都用效率高的 && 而不是 &
//	|| 短路或 | 逻辑或 和&&/&一致||效率更高
! // 取反 本身条件成立，结果为flase，否则为true
^ //逻辑异或，当a和b不同时，则结果为true，否则为false
  // System.out.println((4 < 1) ^ (6 > 3));
```

# 三元运算符

```java
符号： ?
int a = 10;
int b = 99;
int result = a > b ? a++ : b--;
System.out.println(result);
// ? 前条件为真则执行第一个语句，否则执行后者
// 输出为 99
```

# import

```java
import java.util.Scanner; // 表示把java.util下的Scanner类导入
```

## Scanner

```java
import java.util.Scanner;	// 导入包

Scanner 对象名称 = new Scanner(System.in);	// 创建Scanner对像，new创建一个
String name = 对象名称.next();	// 接收用户输入，next()方法表示接收
```

# 原码、反码、补码*

1. 二进制的最高位是符号位；0表示正数，1表示负数

2. 正数的原码，反码，补码一致（三码合一）

3. 负数的反码=它的原码符号位不变，其他位取反（0->1,1->0）

4. 负数的补码=它的反码 + 1，负数的反码=负数的补码 - 1

5. 0的反码、补码都是0

6. java没有无符号数，换言之，java中的数都是有符号的
7. 在计算机运算的时候，都是以补码的方式来运算的
8. 当我们看运算结果时，要看它的原码*

## 位运算符号

java中有7个位运算符号（&、|、^、~、>>、<<、>>>）

按位与&、按位或|、按位异或^、按位取反~

运算规则：

​	按位与&		：	两个全为1，结果为1，否则为0

​	按位或|		：	两位有一个为1，结果为1，否则为0

​	按位异或^	：	两位一个位0，一个为1，结果为1，否则为0

​	按位取反~	：	0->1，1->0

​	算数右移>> :		低位溢出，符号位不变，并用符号位补溢出的高位

​	算术左移<< :		符号位不变，低位补0

​	逻辑右移>>>:		也叫无符号右移，位运算规则是:低位溢出，高位补0

```java
// 案例： 

​	int a = 1 >> 2; // 1 => 00000001 => 00000000 本质 1 / 2 / 2 = 0
​	int b = 1 << 2; // 1 => 00000001 => 00000100 本质 1 * 2 * 2 = 4
```

# switch-case

```java
int a = 1;
switch(a) {
    case 1:
        System.out.println("第一个");
        break;
    case 2:
        System.out.println("第二个");
        break;
    default:
        System.out.println("默认");
        break;
// 细节1：表达式数据类型，应和case后的常量保持一致，
// 或者是可以自动转换相互比较的类型
// 细节2：switch（表达式）中表达式的返回值必须是：
// (byte,short,int,char,enum[枚举]，String)
// 细节3：case句子中的值必须是常量或表达式，而不能是变量
// 细节4：default是可选的，没有匹配case时执行default
// 细节5：break语句用来在执行完一个case分支后使程序跳出switch语句块
// 若没有break。程序会顺序执行到switch结尾
```

# for循环

细节：

1. 循环条件是一个返回布尔值的表达式

2. for ( ;循环判断条件; ) 中的初始化变量迭代可以写到其他地方，但是两边的分号不能省略

3. 循环初始值可以有多条初始化语句，但要求类型一样，并且中间用逗号隔开，

   循环变量迭代也可以有多条变量迭代语句，中间用逗号隔开

4. for ( ; ; ) { } 无限循环

# 跳转控制语句-break

注意事项和细节:

1. break语句出现多层嵌套的语句块中时，可以通过标签指明要终止的是哪一层语句块
2. 标签的基本使用

```java
			label1: {	......
			label2:		{	......
    		 label3:			{	......                 
            											......
														break label2;
														......
    			 }
			}
		}
```

1. break 语句可以指定退出哪层
2. label 是标签，名字可自定义
3. break 后指定到哪个label就退出到哪里
4. 实际开发中尽量不要使用标签
5. 如果没有指定break，默认退出最近的循环体

# 跳转控制语句-return

return使用在方法，表示跳出所在方法。若return写在main方法里表示退出程序

# 数组array

一种数据类型，是引用类型。可通过for循环遍历

```java
//定义一个数组 (静态初始化)
double[] name = {1, 2, 3.4, 6.7, 3, 9};
// 语法： 数据类型 数组名[]= {元素值, 元素值......};

// 定义数组 (动态初始化)
// 数据类型 数组名[] = new 数据类型[数组大小]
double name[] = new double[5];	// 等同于
double name[];	// 声明数组，此时name是nul
name = new double[5]; // 分配内存空间，可以存放数据

//语法 数据类型 数组名[]; 或 数据类型[] 数组名;
// int a[]; 或 int[] a;
```

## 数组拷贝

```java
// 数组引用拷贝
int[] arr1 = {10, 20, 30}; // 静态定义数组
int[] arr2 = arr1;	// arr1数组的地址会拷贝给arr2，修改arr2时arr1同时改变

// 数组值拷贝
int[] arr1 = {10, 20 ,30};
int arr2 = new int[arr1.length];	// 定义数组长度
for (int i; i < arr1.length; i++) {	// 利用for循环树数值拷贝
    arr2[i] = arr1[i];
}
```

# 冒泡排序

```java
int[] arr = {1, 456, 65, 78, 34, 8, 90, 1};
        int temp=0;
        for (int i = 0; i < arr.length -1; i++) {
            for (int j=0; j < arr.length -1 -i; j++) {	// 区域缩减
                if (arr[j] > arr[j+1]) {	// 比较大小，变量交换
                    temp = arr[j];	
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
           if (temp == 0) {	// 优化部分 排序一遍后temp未被赋值则已是有序数组直接退出循环
                break;
            } 
        }
        for (int n=0; n < arr.length; n++) {	// 排序完毕输出结果
            System.out.print(arr[n]+" ");
        }
```

# 二维数组

```java
int[][] arr = {{0, 0, 0},{0, 0, 0},{0, 0, 0}}; // 定义二维数组
```

```java
// 动态定义二维数组
int name[][] // 先声明
name = int[3][3]	// 再分配空间 再赋值
```

# 面向对象

```java
// 类的创建
class Cat {
    // 属性
    String name;
    int age;
    String color;
}

// 创建对象
Cat cat1 = new Cat();
cat1.name = "小白"；
cat1，age = 3;
cat1.color = "白色";

Cat cat2 = new Cat();
cat2.name = "小花"；
cat2，age = 7;
cat2.color = "花色";

System.out.println("第一只猫信息："+"nane="+cat1.name+"年龄="+cat1.age+"颜色="+cat1.color);
```

1. 类时抽象的，概念的，代表一类事物
2. 对象时具体的，实际的，代表一个具体事物，即实例
3. 类时对象的模板，对象是类的一个 个体，对应一个实例
4. 属性时类的一个组成部分，一般是基本数据类型，也可以是引用类型(对象，数组)

# 方法(函数)

```java
public class test1 {

    public static void main(String[] args) {
        // 方法使用
        // 先创建对象。使用对象去调用方法
        Person p1 = new Person();
        p1.fun_speak();
    }
}

class Person {
    String name;
    int age;
    // 定义方法(成员方法)
    // 1.public表示方法是公开的
    // 2.void表示方法没有返回值
    // 3.fun_speak是方法(函数)的名
    // 4.{}表示方法体，内部为需要执行的代码
    public void fun_speak() {
        System.out.println("我是一个好人");
    }
}
public int getSum(int num1, int num2) {
    // 1.int 表示方法会返回int类型的值
    // 2.()内可以接收两个参数
    // 3.return表示方法执行结束时会返回res，到调用的位置(可选择接收)
    int res = num1 + num2;
    return res;
}
```

![](C:\Users\user\Desktop\Notebook\java笔记\方法调用机制.png)

### 函数访问修饰符: public，protected，默认，private 四种

public 公开级别修饰，对外公开

protected 受保护级别修饰，对子类和同一个包中的类公开

默认级别 无修饰符号，向同一个包的类公开

private 私有级别修饰，只针对类本身可以访问，不对外公开

1. 一个方法最多一个返回值，返回多个值可以使用数组;
2.  方法不能嵌套定义
3. 同一个类中的方法可以直接调用（方法名(参数)）不需要对象

# 递归

###### 斐波那契数列

```java
public int fibonacci(int n) {
    if (n==1 || n==2) {
        return 1;
        } else {
            return fibonacci(n-1) + fibonacci(n-2);
        }
    }
```

# 方法重载Overload

函数名相同，参数不同（位置，类型，数量均可），与返回值类型无关

## 可变参数

例 ：public int  sum(**int... 变量名**) { }

```java
public class Overload {

    public static void main(String[] args) {
        // 主方法
    sum p = new sum();
    System.out.println(p.sum(1, 4, 6, 90));	// 调用函数
    }
}

class sum {
     public int  sum(int... nums) {	// 使用可变参数，构成多个数求和的效果
         int res=0;
         for (int i=0; i < nums.length; i++) {	// 遍历求和
             res += nums[i];
         }
         return res;	// 返回和到调用位置
     }
}
```

1. 可变参数函数    ，名称（类型... 变量名称）， 传输的参数为**数组**，故可使用for便利求和
2. 可变参数，可传入零个至多个参数
3. 可变参数也可以直接传入数组作为参数
4. 一个方法最多出现一个 可变参数
5. 细节：可变参数和普通类型的参数一起放在形参列表时，必须保证可变参数在最后

```java
// 5.细节例子
public void fun(double d1, double... nums) { } // 可变参数nums在最后
// 错误例子
public void fun_(double... nums, double d1) { } // 错误 可变参数不在最后
```

# 作用域（范围）

```java
class sum {
    int a; // 全局变量 范围在整个class中
     public void sum() {
         int b; // 局部变量 范围在所在函数中
         System.out.println(a);	// 若改为b则会报错 ；java: 可能尚未初始化变量b
     }
}
```

全局变量为赋值，使用默认值；

局部变量无法使用默认值，必须初始化后才可以使用

## 就近原则

```java
class sum {
    String a = "全局";
     public void sum() {
         String a = "局部";
         System.out.println(a);
     }
}
// 输出；局部
```

全局变量 和 局部变量 可以重名

方法调用 CSDN网页

```
https://blog.csdn.net/ddu_lmm/article/details/108563700?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165035264016781685399146%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=165035264016781685399146&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-2-108563700.142^v9^control,157^v4^control&utm_term=java%E8%B7%A8%E7%B1%BB%E8%B0%83%E7%94%A8%E6%96%B9%E6%B3%95&spm=1018.2226.3001.4187
```

# 构造器/构造方法

基本语法： [修饰符] 方法名(形参列表) { }

1. 构造器的修饰符可以是默认的
2. 构造器没有返回值
3. 方法名和类名必须一致
4. 参数列表 和 成员方法一样的规则
5. 构造器的调用由系统完成

构造器是类的特殊方法，用于对新对象的初始化

一个类中可有多个 构造器 ，构成构造器的重载，与方法的重载相同

```java
public class Constructor01 {

    public static void main(String[] args) {

        Person p = new Person("苦瓜", 19); // 创建实例化对象直接调用构造器对，实例化对象进行初始化
        System.out.println(p.name +" "+ p.age);	// 输出对象内容
        
        Person p2 = new Person("瓜瓜");
        System.out.println(p2.name +" "+ p2.age);
    }
}

class Person {
    String name;
    int age;

    // 构造器
    // 没有返回值，void也不需要写
    // 构造器和class名一致
    // ()中是构造器的形参列表
    public Person(String pName, int pAge) {	// 由系统自动调用
        System.out.println("构造器被调用"); // 用于查看是否被调用
        name = pName;
        age = pAge;
    }
    public Person(String pName) {	// 第二个构造器
        System.out.println("构造器2被调用");
        name = pName;	// age没有被赋值 使用了默认值
    }
}
```

## 构造器的复用

```java
class Employee {
    String name;
    char gender;
    int age;
    String job;
    double sal; // 工资

    public Employee(String job, double sal) {	// 第一个构造器
        this.job = job;
        this.sal = sal;
    }

    public Employee(String name, char gender, int age) {	// 第二个构造器
        this.name = name;
        this.gender = gender;
        this.age = age;
    }

    public Employee(String name, char gender, int age, String job, double sal) {
        this(name, gender, age);	// 复用了第二个构造器
        this.job = job;	// 第二条语句无法复用 只能在第一条使用 this调用其他构造器（细节）
        this.sal = sal;
    }
}
```



# **this**

```java
public class this01 {

    public static void main(String[] args) {

        Dog p1 = new Dog("祈木兮", -1, "dog");
        p1.info();
    }
}

class Dog {
    String name;
    int age;
    String type;
// =======================================================
    public Dog(String dName, int dAge, String dType) {
        name = dName;	// 不便于阅读（指代dName）
        age = dAge;		// 使用 this
        type = dType;
    }
// =======================================================
    public Dog(String name, int age, String type) {
        this.name = name;	// 修改完成版本
        this.age = age;	// 谁在调用就是谁的对象，无this为局部变量
        this.type = type;
    }
// =======================================================
    public void info() {
        System.out.println("名称："+name +"\t"+"年龄："+age+"\t"+"种类："+type);
    }
}
```

1. this关键字可以用来访问本类的属性、方法、构造器

2. this用于区分当前类的属性和局部变量

3. 访问成员方法的语法: this.方法名(参数列表)

4. 访问构造器语法: this(参数列表); 只能在构造器中使用

   (即在一个构造器中访问另一个构造器)

5. this不能在类定义的外部使用，只能在类定义的方法中使用

```java
public T() {
    this("jack", 100);	 // 一个构造器去访问另一个构造器this要放在第一条
    System.out.println("一号构造器");
}
public T(String name, int age) {
    System.out.println("二号构造器");
}
```

# IDEA

## 常用快捷键

1. ```
   1. 删除当前光标所在行代码 默认是 ctrl + Y
   2. 复制当前行，自行配置
   3. 补全代码 alt + /
   4. 添加注释和取消注释 ctrl + /
   5. 导入该行需要的类 先配置auto import，然后使用 alt + enter 即可
   6. 快速格式化代码 ctrl + alt + L
   7. 快速运行程序 shift + F10
   
   8. 生成构造器 alt + insert
   9. 查看一个类的层级关系 ctrl + H （继承中用到）
   10. 将光标放在一个方法上，输入ctrl + B 可快速定位到方法
   11. 自动分配变量名，通过在后面加 .var 之后回车
   ```

## 模板

file -> Setting -> Editor -> Live templates

查看已有模板和自定义模板，使用模板可以高效开发，提高速度

# 包

1. 区分相同名字的类
2. 类的数量过多，可以很好的管理
3. 控制访问范围

基本语法:  

```java
package com.lsp;
// package 关键字,表示打包
// com.lsp 表示包名
```

4. package 的作用是声明当前类所在的包，需放在类的最上面，一个类中最多只有一句package
5. import 指令 位置放在package的下面，在类定义前面，可以有多句且没有顺序限制

# 封装

步骤:

1. 将属性私有化

2. 提供一个公共的（public）set方法，用于属性判断并赋值

   ```java
   public void setXxx(类型 参数名) { // Xxx 表示某个属性
   	// 加入数据验证的业务逻辑
   	属性 = 参数名；
   }
   ```

3. 提供一个公共的get方法，用于获取属性的值

   ```java
   public 数据类型 XX getXxx() {	// 权限判断
   	return xx
   }
   ```

例

```java
public class encap {
    public static void main(String[] args) {
        Person person = new Person();	// 创建 实例对象
        person.setName("苦瓜啊");
        person.setAge(19);
        person.setSalary(5000);
        System.out.println(person.info());	// 接口 查看信息
        
        // 使用构造器
        System.out.println("====使用构造器的信息显示====如下====");
        Person kugua = new Person("kugua", 888, 50000);
        System.out.println(kugua.info());
    }
}

class Person {
    public String name; // 名字公开
    private int age;    // age私有化
    private double salary; // 工资私有化
    
    public Person(String name, int age, double salary) {    // 构造器
//        this.name = name;
//        this.age = age;
//        this.salary = salary;
        // 以上构造器会绕过方法的校验
        setName(name);
        setAge(age);
        setSalary(salary); // 这样写就一样会调用方法 同样会进行数据骄校验
    }

    // 手动写getXxx 和 setXxx 太慢 使用快捷键 (Generate.Get and set)
    // 根据要求完善代码

    public String getName() {
        return name;
    }

    public void setName(String name) {
        // 限制长度 检验数据合理性
        if (name.length() >= 2 && name.length() <= 6) {
            this.name = name;
        } else {
            System.out.println("名字长度违规，请重新设置");
            this.name = "默认名字";
        }
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        if (age >= 1 && age <= 120) {
            this.age = age;
        } else {
            System.out.println("设置无效，年龄需要在1-120之间");
            this.age = 18; // 给一个默认年龄
        }
    }

    public double getSalary() {
        return salary;  // 可增加权限判断，例如密码
    }

    public void setSalary(double salary) {
        this.salary = salary;
    }

    public String info() {	// 查看信息的接口
        return "信息为"+" 姓名："+name + " 年龄：" + age + " 工资：" + salary;
    }
}
```

# 继承

继承可以解决代码复用，在父类中定义这些相同的属性和方法，

所有的子类不需要重新定义这些属性和方法，

只需要通过**extends**来声明继承父类即可

## 继承的基本语法

class 子类 extends 父类 { }

// java中所有类都是Object的子类，Object是所有类的基类。

1. 子类就会自动拥有父类定义的属性和方法
2. 父类又叫 超类，基类
3. 子类又叫派生类
4. ![](C:\Users\user\Desktop\Notebook\java笔记\继承示意图.png)

​	A类定义B，C(或所有class的)共有的方法和属性 类B，C通过关键字继承了A(父类)的属性和方法，降低了代码复用

​	D，E类也可以通过关键字继承B，C，A任意类。

​	若D继承了B类，则拥有了B类的属性和方法，因B类继承了A类所以D类同时也拥有了A类的方法和属性

```
细节1： 子类继承了所有的属性和方法，但是私有属性和方法不能在子类直接访问，

​				要通过 父类提供的 公共的方法去访问
细节2: 子类必须调用父类的构造器，完成父类的初始化
细节3：当创建子类对象时，不管使用子类的哪个构造器，默认情况下总会去调用父类的无参构造器
	  如果父类没有提供无参构造器，则必须在子类的构造器中用super去指定使用父类的一个构造器
	  完成对父类的初始化工作，否则，编译无法通过
```

### super

super可以指定是父类中的属性，不加super如果子类有名字一样的属性，那就指向了子类自己的属性

### super()

super()只能在构造器中使用，只能放在构造器的第一行与this()一致

```java
public A() {
	super(参数， 参数);	// 会自动调用父类中 参数类型，数量对应的构造器
}
```

