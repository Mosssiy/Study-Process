# Java Fundamentals - 1



## Common

### 转换：小转大（自动）

```java
int i = 1500;
j = =(byte) i` 						//使用Alt + Enter可以自动补代码

double score =  99.5;
int number = (int) score;  			//浮点型小数强制转化成整数时会直接丢到小数部分，返回整数
```

### "+"符号可以做连接符

```java
int a = 6;
System.out.println("mosiy"+ a +'a');			//Java 发现最左边是一个字符串（String）：
/*第一步（"mosiy" + a）： 字符串  "mosiy" 遇到了整型 a (6)。在 Java 中，任意数据类型和字符串相加，都会自动转换成字符串拼接。所以这一步得到了字符串 "mosiy6"。
第二步（"mosiy6" + 'a'）： 现在的左边依然是一个新字符串 "mosiy6"，它再遇到字符 'a' 时，同样执行字符串拼接。
最终结果： mosiy6a */

int a = 6;
System.out.println(a +'a'+"mosiy");				//Java 发现最左边是两个数值类型：
/*第一步（a + 'a'）： a 是数字 6，'a' 是单引号包裹的字符（char）。当数字和字符直接相加时，字符 'a' 会自动转换为它对应的 ASCII 码值（'a' 的 ASCII 码是 97）。实际计算：$6 + 97 = 103$此时结果是一个数字 103。第二步（103 + "mosiy"）： 此时数字 103 遇到了右边的字符串 "mosiy"。正如前面所说，任何东西遇到字符串都会变成字符串拼接。最终结果： 103mosiy */
```

### 打印个位数、十位数、百位数

```java
int num = 896 ;
int ge = num % 10 ;
System.out.println(ge);
int shi = num / 10 % 10 ;
System.out.println(shi);
int bai = num /100 ;
System.out.println(bai);
/*输出结果为:			6
                         9
                         8
*/                         
```





## 运算

#### 赋值运算

`e.g.		i  +=  j;     	-------------------------->等价于i  =  (i 的类型)  (i  +  j)`

**注意：自带了一个强制转换**

e.g.

```java
byte t1 = 110 ;
byte t2 = 120 ;
                //byte t3 = t2 + t1    会报错，因为t1 t2 默认转为了int型
使用：t1 += t2;       //等价于 t1 =(byte)(t1 + t2);
```

#### 关系运算

```java
int i = 10 ;
int j = 10 ;
System.out.println(i < j);
System.out.println(i <= j);
System.out.println(i == j);
//输出结果为：  false     true    true
```

#### 逻辑运算符

​	&    逻辑与     多个条件中只要有一个是false，结果就是false    e.g.	2 > 1 & 3 > 2 

​	|     逻辑或     多个条件中只要有一个是true，结果就是true    e.g.	2 > 1 | 3 < 5

​	!	 逻辑非 	取反	e.g.	! (2 > 1)

​	^	逻辑异或	前后结果相异为true，相同为false

​	&&	短路与	用法类比 & ，但左边为false 则右边则不执行

​	 ||	 短路或	 用法类比  |  ，但左边为true 则右边不执行

#### 三元运算符

​	？	：

```java
int max = (i > j) ? (i > k ? i : k) :(j > k ? j : k);		//输出 i j k中最大的
```





## 扫描器

​		Scanner sc = new Scanner(System.in);

​		可以接收大部分类型的数据：

​			基础数字：`.nextInt()`, `.nextLong()`, `.nextFloat()`, `.nextDouble()`, `.nextShort()`, `.nextByte()`

​			布尔真假：`.nextBoolean()` （键盘输入 `true` 或 `false`）

​			各种字符串：`.next()`（不带空格的词）, `.nextLine()`（整整一行话）

```java
package com.itheima.scanner;
// 1、导包：告诉我们的程序，sun公司写好的Scanner程序在哪里。
import java.util.Scanner;

public class ScannerDemo1 {
    public static void main(String[] args) {
        // 目标：理解键盘录入数据： Scanner程序
        // 2、创建扫描器对象（得到一个扫描器东西）
        Scanner sc = new Scanner(System.in);		// 3、使用扫描器 去接收用户键盘输入的数据
        System.out.println("请您输入年龄：");
        int age = sc.nextInt(); // 暂停等待用户输入一个整数，直到用户按了回车键，才会拿到数据往下走。
        System.out.println("您今年：" + age + "岁！");
        System.out.println("请您输入您的名字：");
        String name = sc.next(); // 暂停等待用户输入一个字符串，直到用户按了回车键，才会拿到数据往下走。
        System.out.println("欢迎您：" + name);
    }
}
```





## 分支

### if	else		多用于区间

### switch		多用于值匹配		

​	e.g.

```java 
package first1.hello.demo;

import java.util.Scanner;

public class demo1 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("输入周几：");
        String weekday = sc.next();
        switch (weekday){
            case "周一":
                System.out.println("加油！");
                break;
            case "周二":
                System.out.println("继续努力");
                break;
            default:
                System.out.println("输入错误");
        }
    }

}
```

**Tip : switch表达式类型不支持小数**

​	    **case给出的值不允许重复，且只能是字面量，不能是变量**

​		**无break，会穿透**

### 水仙花数

```Java
int count = 0;					//计数
for (int i = 100; i <=999; i++) {
    int ge = i %10 ;
    int shi = i /10 % 10 ;
    int bai = i/100 ;
    if (i == (ge*ge*ge + shi*shi*shi + bai*bai*bai)){		//水仙花数指 个十百位立法的和等于本身数
        System.out.println(i);			//System.out.print(i + " "); 指不换行输出 输出结果用空格间隔
        count ++;
    }
}
											 //System.out.println();指上面输出完后换行
System.out.println("水仙花的个数为：" + count);    // System.out.print("水仙花的个数为：" + count);

```





## 循环

```java
for					while				do while
```

### 死循环

```java
for( ; ; ){}
while(true){}
do {}while(true);
```

### break

​	跳出并结束当前所在循环的执行				*只能用于结束所在循环，或者结束所在switch分支的执行*

### continue

​	跳出当前循环的当次执行，直接进入循环的下一次执行 		*只能在循环中进行使用*

### Random 		

#### 	边界值bound包前不包后

```java
Random r = new Random();
int number = r.nextInt(10);
System.out.println(number);				//生成0-9的随机数
								 	 //nextInt(n) 功能只能生成 0至n-1之间的随机数，不包括 n
```

#### Random生成指定区间随机数

##### *法一：必须基于JDK17 开始之后*  		*e.g.*

```java
int number = r.nextInt(1,11);			//生成1-10之间的随机数					
```

##### *法二：减加法（先减后加）*

```java
//生成 3 - 17之间的随机数
int number = r.nextInt(15) + 3 ;		//先减为 0 - 14 (bound:15)，再加 3
```





## **程序：**综合运用：随机生成1-100的数字，猜大小		e.g.

```java
package first1.hello.demo;

import java.util.Random;
import java.util.Scanner;

public class demo1 {
    public static void main(String[] args) {
        Random r = new Random();
        int number = r.nextInt(100) + 1;
        Scanner sc = new Scanner(System.in);		//实时接收键盘内容 
//Scanner sc = new Scanner(System.in) 在程序只要全局写一次  后面只要调用sc.xxx都会执行 直至写sc.close
        while (true){
            System.out.println("输入大小：");
            int guess = sc.nextInt();				//等待Enter 抓取键盘内容
            if (guess > number){
                System.out.println("太大");
            } else if (guess < number) {
                System.out.println("太小");
            }else{
                System.out.println("猜对了，该数为：" + number);   //一定要用{ }把break扩起来
                break;										  //若不扩起来，输入一个就结束循环
            }

        }
```





## 数组

### 初始化数组

```java
// 完整格式
数据类型[]  数组名 = new 数据类型[]{ 元素1，元素2 ，元素3… };
int[] ages = new int[]{12, 24, 36, 48, 60};
//简化格式
数据类型[]  数组名 = { 元素1，元素2 ，元素3，… };
int[] ages = {12, 24, 36, 48, 60};
double[] scores = {89.9, 99.5, 59.5};
```

**Tip** : *数据类型[ ] 数组名 也可写成 	数据类型 数组名[ ]*

​		*什么类型的数组必须存放什么类型的数据*

​		*数组是一种引用数据类型	  数组变量名中存储的是数组在内存中的地址信息*

数组的长度属性：length		`int arr [] = {1 , 2 ,3 };`

​	获取数组的长度（就是数组元素的个数）		`System.out.println(arr.length); `	// 3

​	数组的最大索引	数组名. length – 1 // 前提：元素个数大于0		`System.out.println(arr.length - 1); `

### 数组的遍历

```java
int[] arr = {1,2,3,4};					   //创建一个名为arr的数组
for (int i = 0; i < arr.length; i++) {		//快捷键	arr.fori
    System.out.println(arr[i]);			    //快捷键	arr[i].sout
}
```

### 动态初始化数组

```java
//数据类型[]  数组名 = new  数据类型[长度]
String[] names = new String[50];
int[] ages = new int[50];
//动态初始化数组 -----> 相当于定了个空间 但没有数据
```

**静态初始化和动态初始化数组的写法是独立的，不可以混用**

```java
int[] arr = new int[3]{30，40,50};			//	报错 
```

#### 动态初始化数组元素默认值规则

byte	short	char	int	long			默认值			0

float	double								   	默认值			0.0

boolean												默认值			false

#### **程序1:**用动态数组遍历求平均分

```java
package first1.hello.demo;

import java.util.Random;
import java.util.Scanner;

public class demo1 {
    public static void main(String[] args) {
        double[] scores = new double[6];
        Scanner sc = new Scanner(System.in);
        for (int i = 0; i < scores.length; i++) {
            System.out.println("请输入第" + (i + 1) + "个评委打分");
            double score = sc.nextDouble();
            scores[i] = score;
        }
    double sum = 0;
        for (int i = 0; i < scores.length; i++) {
            sum += scores[i];
        }

        System.out.println("平均分为：" + sum /scores.length);
    }
}
```

#### 多个变量指向同一个数组对象

```java
//该程序见下面解析
int[] arr1 = {11, 22, 33};
int[] arr2 = arr1;
System.out.println(arr1);					//[I@10f87f48  存放的是地址
System.out.println(arr2);					//[I@10f87f48  地址相同

arr2[1] = 99 ;
System.out.println(arr1[1]);				//99	arr2的[1]地址指向的数据改了，因为arr1和arr2地址相												  同，所以arr2的[1]指向的数据也同步变化
arr2 = null ;							   //	擦出arr2的栈
System.out.println(arr1[1]);				//99	arr1的栈还存在
System.out.println(arr2);					//null
System.out.println(arr2[1]);				//NullPointerException	报错	空指针异常
```

### **底层核心**

栈里放地址，堆里放数据

【 物理内存条 (RAM) 】
  ├── 1.方法区/代码区    --> 放 `demo1.class` 的代码指令和 `while(true)` 的规矩 	
  ├── 2.栈区 (Stack)    --> 放变量名、放 16 进制地址；方法运行时所进入到=的内存变量也在这里
  └── 3.堆区 (Heap)     --> 放数据，长期驻留；`new `出来的东西会在这块内存中开辟空间并产生地址

解释上述代码：

`int[ ] arr2 = arr1;`		绑定两个栈相同；		

`arr2[1] = 99;` 		修改堆里`arr2[1]`的数据，但`arr1`和`arr2`栈相同，所以arr1数据也发生变化；

`arr2 = null;`		把 `arr2` 的栈切断/清空，里面不存地址了，但 `arr1` 的栈还存在，互不干扰。

​							  **`null` 这个动作，只作用在栈内存上**。它把 `arr2` 这个栈盒子里的地址直接“擦除”了，清空成了零（不							   指向任何地方）。而 `arr1` 的栈完好无损，里面依然指向堆内存

`System.out.println(arr2);`		arr2数组变量没有指向数组对象；可以输出这个变量 null
`System.out.println(arr2[1]);`	但不能用这个数组变量去访问数据或数组长度，会要空指针异常 NullPointerException

#### **程序2：**用数组求最大值

```java
package first1.hello.demo;

public class demo1 {
    public static void main(String[] args) {
        int[] score = new int[]{1,5,15,11,33,2};
        int max = score[0];
        for (int i = 1; i < score.length; i++) {
            int t = score[i];						//用 score[i] 栈放在 t 里  *更加专业 节省资源 
            if (t > max){							//若不用 t  也可以写成 if(score[i] > max);
                max = t ;							//					max = score[i];    费资源
            }
        }
        System.out.println("最大值是："+ max);
    }
}
```

#### **程序3：**数组交换

```java
package first1.hello.demo;

public class demo1 {
    public static void main(String[] args) {
        int[] arr = new int[]{10,20,30,40,50};
                            // i           j
        for (int i = 0,j = arr.length - 1; i < j; i++,j--) {
            int temp = arr[j];
            arr[j] = arr[i];
            arr[i] = temp;
        }
        for (int i = 0; i < arr.length ; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}									//50 40 30 20 10
```

#### **程序4：** *综合运用：*随机排名

```java
import java.util.Random;
import java.util.Scanner;

public class demo1 {
    public static void main(String[] args) {
       int[] codes = new int[5];
        Scanner sc = new Scanner(System.in);
        for (int i = 0; i < codes.length; i++) {
            System.out.println("请输入第" +(i + 1) + "名员工的工号：");
            codes[i] = sc.nextInt();
        }
        Random r = new Random();                    //生成随机数
        for (int i = 0; i < codes.length; i++) {
            int j = r.nextInt(codes.length);        //把随机数赋给j  本题bound为数组长度  5
            int temp = codes[j];                    //把遍历的codes[i]和随机的codes[j]交换顺序  即打乱序
            codes[j] = codes[i];
            codes[i] = temp;
        }
        for (int i = 0; i < codes.length; i++) {    //打印遍历
            System.out.print(codes[i] + " ");

        }
    }
}
```

### Debug

一步一步看运行的信息





## 方法

### 定义和格式

​	方法是一种用于执行特定任务或操作的代码块，就是一个功能，它可以接收数据进行处理，并返回一个处理后的结果

​	Tip：看是否要接收数据	看是否要返回数据

```java
				//四种写法
//完整格式
修饰符  返回值类型  方法名(形参列表){			  
    方法体代码(需要执行的功能代码)
        return 返回值;
}    

//需要接收数据并且不需要返回值
public static void check(int number){}
    
//无参数无返回值的方法
package first1.hello;

public class HelloWorld {
    public static void main(String[] args) {
        print();
    }
    public static void  print(){
        System.out.println("NJZ");
    }
}
```

### 调用方法的方式

```java
有返回值调用方法的3钟方式：

//1、可以定义变量接收结果 
int max = getMax(10,30);
System.out.println("较大值是：" + max);
//2、直接输出调用
System.out.println("较大值是：" + getMax(10,30));
//3、直接调用
getMax();					//跑一遍代码，但不返回值

无返回值调用方法
getMax();
```

### 方法的执行原理

​	方法的运行区域在		栈内存

​	栈的特点		先进后出

​	方法为什么在栈中运行自己		保证一个方法调用完另一个方法后 可以回来

### 	其他细节

#### 基本类型和引用类型的参数传递

​	**都是值传递**
​	基本类型的参数传输存储的数据值	形参拿到的是个数据替身，形参怎么改，都伤不到外面的实参
​	引用类型的参数传输存储的地址值	形参拿到的是**堆内存的钥匙（地址）**。形参顺着钥匙去堆里改了数据，等方															  法结束形参钥匙被销毁了，外面实参拿着同一把钥匙去堆里看，数据也改变了

​	引用类型的参数传递：	对象	数组	集合

#### 	方法重载

​		两同一不同：	（同一个类中，方法名称相同，形参列表必须不同）

​		**Tip：**形参列表不同指的是：个数不同，类型不同，顺序不同。 不管形参的名称

```java
package com.mosiy.overload;

public class MethodOverLoadDemo1 {
    public static void main(String[] args) {
        test();
        test(10);
    }
    public static void test(){
    }
    public static void test(int a){
    }
    public static void test(double a){
    }
    public static void test(int a, double b){
    }
    void test(double b, int a){
    }
//    public static void test(double c, int d){}    		 //不能用  不是方法重载
}
```

#### return关键字(拦截作用)

​	可以用在无返回值的方法中，作用是：立即跳出并结束当前方法的执行。

```java
public static void divide(int a, int b){
    if(b == 0){
        System.out.println("您的除数不能是0！");
        return; 						 // 跳出并理解结束当前方法的执行 （阿里巴巴开发指南）
    }
    int c = a / b;
    System.out.println(c);
}
```

```java
    public static boolean compare(int[] arr1, int[] arr2){
        if(arr1 == null || arr2 == null){
            return false;                		  //层层拦截		少用if else	(阿里开发指南)
        }
        if(arr1.length != arr2.length) {
            return false;
        }

        for (int i = 0; i < arr1.length; i++) {
            if (arr1[i] != arr2[i]) {
                return false;
            }
        }
        return true;                   			//return true	保底
    }
```

#### 快速写代码

```java
Scanner sc = new Scanner(System.in);    //快速写----->= new Scanner(System.in).var
```

```java
Ctrl + Alt + T   					//把选中的地方调用循环
```





## 面向对象编程

### 理解

​	**类名  对象名  =  new  类名( )**

```java
Girl g2 = new Girl("Danielle", 165, 45, "肤白");

// 【对象的实例化】 	 或者叫  	 【创建对象】
```

   `Student s1 = new Student();`
	每次`new Student()`，就是在堆内存中开辟一块内存区域代表一个学生对象。
	`s1`变量里面记住的是学生对象的地址 ------->引用类型

​	**s1在栈中，存放地址；new Student() 在堆中，存放数据；= 为索引，把它们连接起来了**

```java
//成员变量有初始化的默认值  不需要赋初始值
public class Student {
    String name ;
    double chinese;
```

​	类名建议用英文单词，首字母大写，满足驼峰模式，且要有意义，比如：Student、Car

​	类中定义的变量也称为**成员变量**（对象的属性），类中定义的方法也称为**成员方法**（对象的行为）

​	成员变量本身存在默认值，在定义成员变量时一般来说不需要赋初始值（没有意义）

​	一个代码文件中，可以写多个class类，但只能都用public修饰，且public修饰的类名必须成为代码文件名

​	成员变量本身存在默认值，同学们在定义成员变量时一般来说不需要赋初始值（没有意义）

​	一个代码文件中，可以写多个class类，但只能一个用public修饰，且public修饰的类名必须成为代码文件名

​	对象与对象之间的数据不会相互影响，但多个变量指向同一个对象时就会相互影响了

​	如果某个对象没有一个变量引用它，则该对象无法被操作了，该对象会成为所谓的垃圾对象

```java
s1.name = "abc";
//栈的 s1 提供地址 ➔ 闪现到堆 ➔ 发现里面有个坑叫 name（原本装的是默认遗留的 null） ➔ 强行抹杀，塞入 "abc"。
```

### this

​	**this就是一个变量，哪个对象调用这个方法,this就代表哪个对象**

**----> 哪个变量调用的，this 就代表这个变量格子里装的那个堆内存地址；如果没有变量，this 就直接代表 new 出来的那个对象的堆内存地址**

​	this就是一个变量， 可以用在方法中 ，用来拿到当前对象

​	哪个对象调用方法，this就指向哪个对象，也就是拿到哪个对象

​	this 用来解决对象的成员变量与方法内部变量的名称一样时，导致访问冲突问题的。

​	*可以用  this 限定访问当前对象的成员变量*

```java
package com.mosiy.thisdemo;

public class Test {
    public static void main(String[] args) {
        // 目标：认识this关键字。
        Student s1 = new Student();
        System.out.println(s1);
        s1.print();

        System.out.println("---------");

        Student s2 = new Student();
        System.out.println(s2);
        s2.print();

        System.out.println("----------");			//----->以上为测试

        Student s3 = new Student();
        s3.score = 150; //---->提前把s3堆内存的score改为了150，所以后面调用s3.passd的时候 this.score为150
        s3.pass(200);		//------>临时传输 200 这个数据
    }
}
```

```java
package com.itheima.thisdemo;

public class Student {
    double score;							//---->s3.score = 150 ;  即赋给score为 150

    public void print(){
        
       									 // this就是一个变量，哪个对象调用这个方法,this就代表哪个对象
        
        System.out.println("this:" + this);
    }

    // java希望代码的参数能够做到见名知意
    // 但是见名知意很可能引起局部变量与成员变量名称冲突
    // 此时如果希望区分开来，可以在变量的前面加上this,代表访问的是对象的成员变量
    
    public void pass(double score){				//s3 的score已经提前改为150了
        if(this.score >= score) {				//--->this.score为 150 ; score为 200 传过来的数据
            System.out.println("这个学生考上了哈佛大学~~~");
        }else {
            System.out.println("这个学生落榜了，和尚也看不上它~~~");
        }
    }
}
```

### 构造器

`Student s = new Student ();`  -----> 创建对象

`new Student` ----->  创建对象					`()` -----> 通过括号匹配调用无参构造器

e.g.	public Student(String n, double s){}		------> 有参构造器

```java
package com.mosiy.constructor;

public class Test {
    public static void main(String[] args) {
        // 目标：认识构造器，搞清楚其特点和应用场景。
        Student s1 = new Student();

        Student s2 = new Student("Haerin");

        Student s3 = new Student("Danielle", 165);

    }
}
```

```java
package com.mosiy.constructor;

public class Student {
    // 构造器的要求：名称必须与类名一样，不能写返回值类型。
    // 构造器的特点：每次创建对象时，对象会立即调用构造器。
    // 构造器的作用（其中的一个作用）：创建对象时同时为对象赋值
    // 1、无参数构造器
    public Student(){
        System.out.println("==Student的无参数构造器执行了==");
    }

    // 2、有参数构造器
    public Student(String n){
        System.out.println("==Student的有1个参数构造器执行了==");
    }

    public Student(String n, double s){
        System.out.println("==Student的有2个参数构造器执行了==");
    }
}
```

```java
package com.mosiy.constructor;

public class Test2 {
    public static void main(String[] args) {
        // 目标2：构造器的作用
        // 构造器的作用（其中的一个作用）：创建对象时同时为对象赋值.
        // 构造器的注意事项：类默认自带无参数构造器，写不写都有！
        // 但是如果你写了一个有参数构造器，那么默认的无参数构造器就没有了，
        // 此时如果你还要用无参数构造器，就需要自己手动把无参数构造器写出来
        // ------->	企业建议 要么不写 要写有参无参构造器都要写
        Girl g1 = new Girl();
        g1.name = "Haerin";
        g1.height = 164.5;
        g1.weight = 45;
        g1.color = "肤白";
        System.out.println(g1.name);
        System.out.println(g1.height);
        System.out.println(g1.weight);
        System.out.println(g1.color);

        Girl g2 = new Girl("Danielle", 165, 45, "肤白");
        System.out.println(g2.name);
        System.out.println(g2.height);
        System.out.println(g2.weight);
        System.out.println(g2.color);

    }
}
```

```java
package com.mosiy.constructor;

public class Girl {					//-----> 定义一个叫 Gir1 的类
    String name;
    double height;
    double weight;
    String color;

    public Girl(){								//------> 无参的构造器
    }

    public Girl(String name, double height, double weight, String color){  		//有参数的构造器
        this.name = name;			//传过来的数据 name为Danielle，height为165...
        this.height = height;		//this.height指的是 g2的height,还没有数据,要把传过来的											  				    height为165赋值给this.height
        this.weight = weight;
        this.color = color;
    }
}
```

```java
// 1. 你把 g1 的房子精装修了
Girl g1 = new Girl();
g1.name = "Haerin"; 

// 2. 奇迹时刻！我们现在“不调用带参构造器”，直接 new 一个全新的 g3 出来：
Girl g3 = new Girl(); 

// 3. 见证奇迹的打印：
System.out.println(g3.name);
//	打印出来 是null
```

#### **自我理解**

​	有参和无参数的构造器，会自动去 class 里“抄格子”，相当于把格式复制了一份，再自己填内容，但是填的数据只在对应匹配的构造器生效，不会影响class类的格式 一般定义成员变量时不赋初值，有默认值，class的类的格式依旧为默认值 不改变；有参数的构造器会根据创建对象时数据对应的格式来一一匹配；而无参的构造器会自动自动去调用和翻阅 class 类，相当于生成格子，再填内容 

​	构造器在【栈】里开辟的局部变量营地，是“用完即焚”的。每一次调用构造器，都是一次完全独立的生死轮回！它们不仅和 Class 图纸相互独立，和堆内存相互独立，连它们自己前后的每一次调用，数据都是绝对孤立、互不干扰的

### 封装

​	合理隐藏，合理暴露

```java
package com.mosiy.encapsulation;

public class Test {
    public static void main(String[] args) {
        // 目标：认识封装，搞清楚封装的设计规范：合理隐藏，合理暴露。
        Girl g = new Girl();
        g.setAge(18);
        System.out.println(g.getAge());
    }
}
```

```java
package com.mosiy.encapsulation;

public class Girl {			//----> Girl是一个类
    
    private String name; // private 成员变量 name
    // 封装的第一步规范：私有成员变量，使用private修饰
    // 注意：private修饰的成员变量只能在本类中访问，其他地方不能直接访问
    private int age; 
    private double chinese; 
    private double math; 

    // 封装的第二步规范（合理的暴露）：给私有的成员变量提供公开的set方法和get方法。
    // public修饰的成员就是公开的意思，它修饰的成员可以在任意地方直接访问。
    // 赋值：set
    public void setAge(int age){
        if(age > 0 && age <= 150) {
            this.age = age;				// this就是一个变量，哪个对象调用这个方法,this就代表哪个对象
            
        // ----->传过来18 age为18，赋值给this.age，其中this.age的 age 是private int age 的age
            
        }else {
            System.out.println("您的年龄数据有毛病~~~");
        }
    }

    // 取值：get
    public int getAge(){
        return age;				//----->此时 age为18
    }
}
```

### 实体类

#### 	定义

​	实体类指成员变量必须私有，且要为他们提供get、set方法；必须有无参数构造器 
​				  仅仅只是一个用来保存数据的java类，可以用它创建对象，保存某个事物的数据。

​	应用场景：
​					实体类对应的是软件开发里现在比较流行的开发方式，数据和数据的业务处理相分离

#### 	Tip：private Student s

```java
public class Student {}				//自己造了一个名为 Student的类(类型)

private Student s ;					//把Student当做一个类型(如int型), s为Student型
```

#### Sample

```java
package com.mosiy.javabean;
// 实体类
public class Student {
    // 1、私有成员变量
    private String name;
    private char sex;
    private double height;
    private double score;

    // 2、提供公共的无参数构造器（默认存在）
    //快捷键： 右键 Generate > Constructer > Select None
    public Student() {
    }

    //有参构造器
    //快捷键： 右键 > Generate > Constructer > Shift键 鼠标点击全选 > OK
    public Student(String name, char sex, double height, double score) {
        this.name = name;
        this.sex = sex;
        this.height = height;
        this.score = score;
    }

    // 3、提供get set方法
    //快捷键： 右键 > Generate > Getter and Setter > Shift建 鼠标点击全选 > OK
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public char getSex() {
        return sex;
    }

    public void setSex(char sex) {
        this.sex = sex;
    }

    public double getHeight() {
        return height;
    }

    public void setHeight(double height) {
        this.height = height;
    }

    public void setScore(double score) {
        this.score = score;
    }

    public double getScore() {
        return score;
    }
}
```

```java
package com.mosiy.javabean;

public class Test {
    public static void main(String[] args) {
        // 目的：认识实体类，搞清楚实体类的应用场景。
        // 实体类的作用有两个
        // 第一个作用：实体类的对象本身只负责存取对象的数据。
        Student s1 = new Student("徐力鸿", '男', 175.5, 99);
        System.out.println(s1.getName());
        System.out.println(s1.getSex());
        System.out.println(s1.getHeight());
        System.out.println(s1.getScore());

        // 第二个作用（贼难，听不懂，就业班再学）
        // 实体类的对象只负责数据的存和取，对于数据的业务处理应该交给另一个类的对象来处理
        // 这里软件设计中很流行的一种设计思想：分层思想。
        StudentOperator operator = new StudentOperator(s1);
        operator.printPass(); // 业务操作

        //StudentOperator里的代码:  private Student s;  public StudentOperator(Student s){this.s = s;}
        //--->this是谁在调用,就是那个被 new 出来的 正在经历出生过程的新对象自己！即Operator调用的

        //最终版---> this.s，operator调用了这个方法 所以this代表operator这个对象，而operator在StudentOperator这个类里面，而这个类定义了一个private Student s其中Student是一个类型，正好匹配了传过来的s1是Student类型，于是this.s就定位到了private Student s的s；在这之后operator这个对象里面存放的数据也改为了s1的数据 
    }
}
```

```java
package com.itheima.javabean;
// 作为学生对象的业务操作对象
public class StudentOperator {
    // 1、接收到要操作的学生对象
    private Student s;
    public StudentOperator(Student s){
        this.s = s;
    }

    //Test里的代码---> StudentOperator operator = new StudentOperator(s1);
    //--->this是谁在调用,就是那个被 new 出来的 正在经历出生过程的新对象自己！即Operator调用的

    // 2、打印成绩是否及格
    public void printPass() {
        if(s.getScore() >= 60){
            System.out.println(s.getName() + "这哥们及格了~");
        }else {
            System.out.println(s.getName() + "挂科了~~~");
        }
    }
}
```

### 面向对象编程综合案例

#### 	Tip：Alter + Enter

#### 	电影信息系统

​	面向对象综合案例-模仿电影信息系统：展示系统中的全部电影(每部电影展示：名称、价格)。
​    允许用户根据电影编号（id）查询出某个电影的详细信息。

```java
package com.mosiy.demo;

public class Test {
    public static void main(String[] args) {
        // 目标：掌握电影信息的开发。
        // 1、每个电影是一个电影对象，首先要设计电影类，用于创建电影对象，封装电影数据。
        // 2、准备电影对象数据（电影信息）:由一个一个的电影对象存储.
        Movie[] movies = new Movie[5]; // movies = [null, null, null, null, null]
        movies[0] = new Movie(1,"热辣滚烫", 46.5, "贾玲");
        movies[1] = new Movie(2,"飞驰人生", 49.9, "沈腾");
        movies[2] = new Movie(3,"非诚勿扰", 9.9, "葛优,舒淇");
        movies[3] = new Movie(4,"第二十条", 87.4, "雷佳音，赵丽颖");
        movies[4] = new Movie(5, "熊出没",35.5,"光头强");
        // 3、把电影对象数据交给电影操作对象进行业务处理.
        MovieOperator operator = new MovieOperator(movies);
        operator.showAllMovies();
        operator.getMovieById();
    }
}
```

```java
package com.mosiy.demo;

public class Movie {
    private int id;
    private String name;
    private double price;
    private String actor;

    public Movie() {
    }

    public Movie(int id, String name, double price, String actor) {
        this.id = id;
        this.name = name;
        this.price = price;
        this.actor = actor;
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

    public String getActor() {
        return actor;
    }

    public void setActor(String actor) {
        this.actor = actor;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }
}
```

```java
package com.mosiy.demo;

import java.util.Scanner;

// 电影操作对象
public class MovieOperator {
    // 1、获取到全部电影对象
    private Movie[] movies;
    public MovieOperator( Movie[] movies){
        this.movies =  movies;
    }

    // 2、提供方法，展示全部电影，根据id查询电影对象。
    public void showAllMovies() {
        System.out.println("==全部电影信息如下===");
        for (int i = 0; i < movies.length; i++) {
            // 得到当前电影
            Movie m = movies[i];
            System.out.println(m.getId() + "\t" + m.getName()+ "\t" + m.getPrice() + "\t" +m.getActor());
        }
    }

    public void getMovieById() {
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入您要查询的电影id:");
        int id = sc.nextInt();
        System.out.println("您要查询的电影信息如下：");
        for (int i = 0; i < movies.length; i++) {
            // 得到当前电影
            Movie m = movies[i];
            if(m.getId() == id){
                System.out.println(m.getId() + "\t" + m.getName()+ "\t" + m.getPrice() + "\t" +m.getActor());
                return;
            }
        }
        System.out.println("查无此电影！");
    }
}
```





## API

### 	定义

​	（全称 Application Programming Interface：应用程序编程接口）	就是别人写好的程序 可以直接调用

**在自己程序中调用其他包下的程序的注意事项**
	*如果当前程序中，要调用自己所在包下的其他程序，可以直接调用。（同一个包下的类，互相可以直接调用）*
	*如果当前程序中，要调用其他包下的程序，则必须在当前程序中导包, 才可以访问！导包格式：import 包名.类名;*
	*如果当前程序中，要调用Java提供的程序，也需要先导包才可以使用；但是Java.lang包下的程序是不需要我们导包的，可以直接使用。*
	*如果当前程序中，要调用多个不同包下的程序，而这些程序名正好一样，此时默认只能导入一个程序，另一个程序必须带包名访问。*	   	e.g. `com.mosiy.pkg2.Car t2 = new com.mosiy.pkg2.Car();`

### String

​	String创建对象封装字符串数据的方式：

```java
// 1、方式一：直接“内容”就可以得到字符串对象，封装字符串数据了。 （推荐方案）
String name = "Mosiy";
String schoolName = "哈佛大学";

// 2、方式二：通过调用构造器初始化字符串对象，封装字符串数据。（了解）
String s1 = new String(); // 等同于s1 = "";
System.out.println(s1);

String s2 = new String("加油努力"); // 等同于s2 = "加油努力"
System.out.println(s2);

char[] chars = {'a', 'b', 'c', '中', '国'};
String s3 = new String(chars);
System.out.println(s3); // 输出 abc中国

byte[] bytes = {97, 98, 99, 65, 66, 67};
String s4 = new String(bytes);
System.out.println(s4); // 输出 abcABC
```

```java
package com.mosiy.string;

public class StringDemo2 {
    public static void main(String[] args) {
        // 目标：快速熟悉String提供的处理字符串的常用方法。
        String name = "ab沫汐666";

        // 1、获取字符串的长度(字符个数)
        System.out.println("长度：" + name.length());	//----> 7

        // 2、提取字符串中某个索引位置处的字符
        System.out.println(name.charAt(2));         // ----> 沫

        System.out.println("------------------------");

        // 字符串的遍历。
        for (int i = 0; i < name.length(); i++) {
            char c = name.charAt(i);
            System.out.println(c);
        }

        System.out.println("------------------------");

        // 3、把字符串转换成字符数组，再进行遍历
        char[] chars = name.toCharArray();
        for (int i = 0; i < chars.length; i++) {
            char c = chars[i];
            System.out.println(c);                  //----> 输出一个一个字符
        }

        // 4、equals: "判断字符串内容"，内容一样就返回true (重点)
        String s1 = new String("沫汐666");
        String s2 = new String("沫汐666");
        System.out.println(s1 == s2); // false  	----> == 是用来比较地址的
        System.out.println(s1.equals(s2)); // true

        // 5、忽略大小写比较字符串内容(常用于验证码的比较)
        String t1 = "a6GFo";
        String t2 = "A6gfo";
        System.out.println(t1.equals(t2)); // false
        System.out.println(t1.equalsIgnoreCase(t2)); // true

        // 6、截取字符串内容 (包前不包后的)
        String st = "沫汐程序员999";
        String rs = st.substring(0, 2);         //----> 沫是0 汐是1 包前不包后 所以要填2
        System.out.println(rs);                 //----> 打印出 沫汐

        // 7、从当前索引位置一直截取到字符串的末尾
        String rs2 = st.substring(2);           //----> 程是2  从2截取到字符串末尾
        System.out.println(rs2);                //----> 输出 程序员999

        // 8、把字符串中的某个内容替换成新内容，并返回新的字符串对象给我们
        String info = "这个游戏简直是个垃圾，还我血汗钱，sb！";
        String rs3 = info.replace("垃圾", "**").replace("sb", "xx");      //----> 链式编程
        System.out.println(rs3);

        // 9、判断字符串中是否包含某个关键字.
        String st2 = "沫汐程序员999";
        System.out.println(st2.contains("沫汐"));	// true
        System.out.println(st2.contains("程序员"));// true
        System.out.println(st2.contains("99"));     //true
        System.out.println(st2.contains("996")); // false

        // 10、判断字符串是否以某个字符串开头。
        // startsWith 判断是否以什么内容开头
        System.out.println(st2.startsWith("沫汐")); // true
        System.out.println(st2.startsWith("沫汐2")); // false
        System.out.println(st2.startsWith("沫汐程序员")); // true

        // endsWith 判断是否以什么内容结尾
        System.out.println(st2.endsWith("沫汐")); // false
        System.out.println(st2.endsWith("999")); // true
        System.out.println(st2.endsWith("员999")); // true

        // 11、把字符串按照某个指定内容分割成多个字符串，
        // 放到一个字符串数组中返回给我们。
        String result = "丹妮尔,姜海粼,金玟池";
        String[] names = result.split(",");
        for (int i = 0; i < names.length; i++) {
            System.out.println(names[i]);
        }	//丹尼尔 回车	姜海粼	回车		金玟池
    }
}
```

#### 注意事项

​			String的对象是不可变字符串对象每次试图改变字符串对象实际上是新产生了新的字符串对象了，变量每次都是指向了新的字符串对象，之前字符串对象的内容确实是没有改变的，因此说String的对象是不可变的。

​	● String是不可变字符串对象
​	● 只要是以“.”方式写出的字符串对象，会存储到字符串常量池，且相同内容的字符串只存储一份；
​	● 但通过new方式创建字符串对象，每new一次都会产生一个新的对象放在堆内存中。

#### 	Tip

​	**1.`String s2 = new String("abc");`**

​	这行代码在堆内存里一共会创建 **1 个或 2 个**对象。

【情况 A：如果程序里是第一次出现 `"abc"`】（创建 2 个对象）

- **第 1 个对象：字符串常量池里的实体**
  - 它是： 专门住在“字符串常量池”小仓库里的一个 `String` 对象，里面牢牢锁死着原始数据 `"abc"`。它是用来当共享模板的。
- **第 2 个对象：普通堆内存里的实体**
  - 它是： 因为外面有 `new`，JVM 在常量池外面强行砸出来的一个**全新 `String` 对象**。它里面的内容是拷贝了常量池里 `"abc"` 的数据，而左边的变量名 `s2` 这把钥匙，最终拴住的就是这第 2 个对象。

【情况 B：如果前面早就写过 `"abc"` 了】（创建 1 个对象）

- **唯一创建的对象：普通堆内存里的实体**
  - 它是： 常量池里已经有模板了，动作 ① 直接跳过。JVM 只执行了外面的 `new`，在普通堆内存里强行砸出 **1 个全新的 `String` 对象**，把池子里 `"abc"` 的数据拿过来用。

**左边的 `s2` 只是在栈里记了个名字，根本进不了堆区的对象名单**

**2.`new String();`**

这行代码在堆内存里，雷打不动**只创建 1 个**对象。

- **这唯一的一个对象是：堆内存里的“空字符串实体”**
  - 它是： 一个没有任何文字内容的 `String` 对象（大白话就是 `""`，它的长度是 0）。因为括号里什么都没传，所以它不需要去常量池里找模板，只管在普通堆内存里直接诞生一个空壳实体。

**3.`String s1 = "abc";`**

​	 这行代码，在运行的时候，一共创建了 **0 个或者 1 个**对象。**字符串纯常量赋值**。它到底创不创建对象，完全看字符串常量池（String Pool）的脸色。

【情况 A：如果程序里是第一次出现 `"abc"`】（创建 1 个对象）

- **这唯一的一个对象是：字符串常量池里的实体**
  - **它是：** JVM 看到双引号里的 `"abc"`，发现常量池小仓库里空空如也，于是老老实实在常量池里砸出 **1 个真正的 `String` 对象**，把 `"abc"` 锁在里面当共享模板。
  - **关键动作：** 砸完之后，左边的车钥匙 `s1`，会**直接、精准地拴在常量池里的这个对象身上**！

【情况 B：如果前面早就出现过 `"abc"` 了】（创建 0 个对象）

- **创建的对象是：0 个**
  - **它是：** JVM 瞅了一眼常量池，惊喜地发现：“诶？池子里早就有一个叫 `"abc"` 的老腊肉对象了！”
  - **关键动作：** 既然有了，JVM 连一滴内存都不愿意多花。它**什么新对象都不造**，直接把左边的车钥匙 `s1`，**也栓在常量池里那个早就存在的旧对象身上**！

##### **总结口诀**

-  **双引号 `"abc"`** 它的名字叫 **“常量池模板对象”**（池子里没有就创，有就省了）

- **`new String(...)`** 它的名字叫 **“堆区独立新对象”**（只要有 `new`，就必须原地砸出一个新的）

  *计算出来 拼接出来的放在堆内存里* 	*特例 ：优化机制  会在程序编译时  把"a"+"b"+"c" 直接转成 "abc" 提高性能*

- **`String s1 = "abc";`**  **直奔常量池**。要么创1个(池子里没有要么创0个)（直接白嫖池子里的）。`s1` 直接指向池子

#### **程序1：**String的案例登录

```java
package com.mosiy.string;

import java.util.Scanner;

public class StringTest4 {
    public static void main(String[] args) {
        // 目标：完成用户登录功能。
        // 登录功能是一个独立的功能（独立功能独立成方法）。
        // 最多给用户三次登录机会。
        Scanner sc = new Scanner(System.in);
        for (int i = 1; i <= 3; i++) {
            System.out.println("第" + i + "次登录开始");
            System.out.println("请您输入登录名称：");
            String loginName = sc.next();

            System.out.println("请您输入登录密码：");
            String passWord = sc.next();

            String result = login(loginName, passWord);
            if("success".equals(result)){
                System.out.println("登录成功了，欢迎进入系统~~~");
                break;
            }else {
                System.out.println(result);
            }
        }
    }

    public static String login(String loginName, String passWord){
        // 1、拿到正确的登录名和密码。
        String okLoginName = "itheima";
        String okPassWord = "123456";

        // 2、让用户传进来的登录名和密码与正确的登录名和密码进行对比。
        if(okLoginName.equals(loginName)){
            // 登录名正确了
            // 3、判断密码是否正确。
            if(okPassWord.equals(passWord)) {
                // 4、登录成功了
                return "success";
            }else {
                return "密码错误了，请检查";
            }
        }else {
            return "登录名称有问题，请检查！";
        }
    }
}
```

#### **程序2：**String开发验证码

```java
package com.mosiy.string;

import java.util.Random;

public class StringTest5 {
    public static void main(String[] args) {
        // 目标：String开发验证码
        System.out.println(create(5));
        System.out.println(create(8));
    }

    public static String create(int n){
        String code = ""; // 记住验证码
        String data = "abcdFGHIJKLMNOPQRSTUVWXYZ01234evwxyzABCDfghijklmnopqrstuE56789"; // 全部随机字符
        // 1、直接使用循环控制随机获取多少位字符，然后拼接返回即可。
        Random r = new Random();
        for (int i = 0; i < n; i++) {
            // 2、随机产生一个索引。
            int index = r.nextInt(data.length());
            // 3、提取对应索引位置处的一个字符
            char c = data.charAt(index);
            // 4、拼接给code链接
            code += c;
        }
        return code;
    }
}
```



### ArrayList 集合

#### 	快速入门

​	集合是一种容器，用来存储数据

​	集合的大小可变

`Arraylist` 是集合中最常见的一种，`Arraylist` 是泛型类，可以约束存储的数据类型

​	如何使用：创建对象，调用无参数构造器初始化对象：public Arraylist() ;		调用相应的增删改查数据的方法

```java
//	Arraylist 提供的常用方法

package com.mosiy.arraylist;


import java.util.ArrayList;

public class ArrayListDemo1 {
    public static void main(String[] args) {
        // 目标：掌握ArrayList集合的创建和使用。
        // 1、创建ArrayList集合的对象代表一个容器(大小可变，数据可以重复，有索引)
        // ArrayList<String> list = new ArrayList<String>();
        ArrayList<String> list = new ArrayList<>(); // 只能存 String 类型   JDK7之后后面类型可以不写
                                                    //ArrayList list = new ArrayList(); 任何类型都能存
        list.add("java1");
        list.add("java1");
        list.add("金庸");
        System.out.println(list);        //[java1, java1, 金庸]

        // 2、插入数据
        list.add(1, "嵌入式");             //在第2个位置插入数据
        System.out.println(list);         //[java1, 嵌入式, java1, 金庸]

        // 3、根据索引获取数据 :list = [java1, 嵌入式, java1, 金庸]
        //                            0       1      2     3
        String ele = list.get(3);
        System.out.println(ele);

        // 4、获取集合的大小（元素个数）
        System.out.println("集合的元素个数：" + list.size());  //集合的元素个数：4

        // 5、根据索引删除数据，返回被删除的数据。
        System.out.println(list.remove(1));                 // 嵌入式
        System.out.println(list);                           // [java1, java1, 金庸]

        // 6、直接删除数据，返回真假 , 默认只能删除第一个出现的。     // 该代码只能删除第一个 java1
        System.out.println(list.remove("java1"));           // true
        System.out.println(list);                           // [java1, 金庸]

        // 7、修改某个索引位置处的数据，返回修改前的数据  list = [java1, 金庸]
        System.out.println(list.set(1, "古龙"));             // 金庸
        System.out.println(list);                           // [java1, 古龙]

    }
}
```

#### **程序1：**应用案例：删除指定数据(两种方案)

```java
package com.mosiy.arraylist;

import java.util.ArrayList;

public class ArrayListDemo2 {
    public static void main(String[] args) {
        // 目标：掌握从容器中删除数据的技巧。
        // 1、准备一个集合，存储一堆商品
        ArrayList<String> list = new ArrayList<>();
        list.add("Java入门");
        list.add("宁夏枸杞");
        list.add("黑枸杞");
        list.add("人字拖");
        list.add("特技枸杞");
        list.add("枸杞子");
        System.out.println(list);
        //  list = [Java入门, 宁夏枸杞, 黑枸杞, 人字拖, 特技枸杞, 枸杞子]

        // 遍历集合中的每个数据，只要这个数据包含枸杞，我们就从集合中删除这个数据。
        for (int i = 0; i < list.size(); i++) {
            String name = list.get(i);
            if(name.contains("枸杞")) {
                // 从集合中直接干掉这个数据
                list.remove(name);
                i--; // 解决方案一：删完数据后回退一步，才可以保证成功删除数据，不会漏删
            }
        }
        System.out.println(list);

        System.out.println("-----------------------------------------------------------------------------");

        ArrayList<String> list2 = new ArrayList<>();
        list2.add("Java入门");
        list2.add("宁夏枸杞");
        list2.add("黑枸杞");
        list2.add("人字拖");
        list2.add("特技枸杞");
        list2.add("枸杞子");
        // 解决方案二：从后面倒着遍历并删除就没有问题了。
        // list2 = [Java入门, 宁夏枸杞, 黑枸杞, 人字拖, 特技枸杞, 枸杞子]
        // list2 = [Java入门, 人字拖]
        //             i
        for (int i = list2.size() - 1; i >= 0; i--) {
            String name = list2.get(i);
            if(name.contains("枸杞")) {
                // 从集合中直接干掉这个数据
                list2.remove(name);
            }
        }
        System.out.println(list2);
    }
}
```

#### **程序2：**综合案例：模仿外卖系统中的商家系统

​	Goal：完成菜品的上架、以及菜品信息浏览功能

​	循环快捷键：Ctrl + Alt + T 	(框定需要循环的内容)

```java
package com.mosiy.arraylist;

public class ArrayListTest3 {
    public static void main(String[] args) {
        // 目标：完成菜品上架，浏览功能。结合面向对象编程和ArrayList.
        // 1、每个菜品是一个对象，定义菜品类，用于创建菜品对象封装菜品数据。
        // 2、定义一个菜品操作类，用于创建菜品操作对象负责对菜品数据进行业务处理。
        FoodOperator operator = new FoodOperator();
        operator.start();
    }
}
```

```java
package com.mosiy.arraylist;
// 菜品类
public class Food {
    private String name;
    private double price;
    private String desc; // 描述

    public Food() {
    }

    public Food(String name, double price, String desc) {
        this.name = name;
        this.price = price;
        this.desc = desc;
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

    public String getDesc() {
        return desc;
    }

    public void setDesc(String desc) {
        this.desc = desc;
    }
}
```

```java
package com.mosiy.arraylist;

import java.util.ArrayList;
import java.util.Scanner;

// 菜品操作类
public class FoodOperator {
    // 1、准备一个容器负责存储上架的全部菜品。
    private ArrayList<Food> allFoods = new ArrayList<>();
    private Scanner sc = new Scanner(System.in);

    public void addFood() {
        System.out.println("==============上架菜品==============");
        // a、用户每上架一次菜品实际上就是在集合中新增一个菜品对象。
        Food f = new Food();

        // b、为菜品对象注入菜品的数据。
        System.out.println("菜品名称：");
        String name = sc.next();
        f.setName(name);

        System.out.println("菜品价格：");
        double price = sc.nextDouble();
        f.setPrice(price);

        System.out.println("菜品描述：");
        String desc = sc.next();
        f.setDesc(desc);

        // c、把菜品对象添加到集合容器中去。
        allFoods.add(f);
        System.out.println("菜品上架成功！");
    }

    public void showAllFoods() {
        System.out.println("==============全部菜品==============");
        for (int i = 0; i < allFoods.size(); i++) {         // 快捷键 allFoods.fori
            Food food = allFoods.get(i);                    // 快捷键 allFoods.get(i).var
            System.out.println(food.getName() + "\t" + food.getPrice() + "\t" + food.getDesc());
        }
    }

    public void start() {
        while (true) {
            System.out.println("=============商家管理系统=============");
            System.out.println("1、上架菜品");
            System.out.println("2、下架菜品（还未做）");
            System.out.println("3、展示菜品");
            System.out.println("请您输入操作功能“：");
            int command = sc.nextInt();

            switch (command) {
                case 1:
                    // 上架： 独立功能独立成方法
                    addFood();
                    break;
                case 2:
                    // 下架
                    break;
                case 3:
                    // 展示
                    showAllFoods();
                    break;
                default:
                    System.out.println("输入错误！");
            }
        }
    }
}
```





## **项目：**ATM系统



见	Java Study\Markdown Files\Program code\Stage-1.md





—————————————————————————————————————————————————————

## **★★★ Tip**: (Self-summary)



### 数组

​	`String[] names ={"a","ab","abc"};	` 		则 `names[0] `就是` a` 	`names[1]`就是 `ab`；

​	`int[] ages = {12, 24, 36, 48, 60};`		则`ages[0]` 就是`12`,	`ages[1]`就是  `24`

​	*都是以	,	作为分割符*



### 定义方法和类

**定义方法**一定要有返回值类型

**定义类**必须要有 class

类中可以定义方法  方法中也可以定义类  （但在日常开发中，99% 的情况下都是 *“ **类中定义方法** ”* ）



### **理解 `Student s1 = new Student();`**

​	Student ----> 类型			`s1`----> (变量)			`new Student`----> (创建对象)			() ----> 调用无参构造器 																																	  	(Java会自动创建无参构造器)

​	堆内存这边（构造器干的）`new Student()`：在原本空无一物的堆内存海域里，硬生生圈出一块谁也没用过的、崭新的空地（诞生全新的堆地址，比如 `0x888`），把卡车造在里面。

​	栈内存这边（定义变量干的）`Student s`： 咔哒一声，在当前的栈空间里，硬生生挖出一个崭新的、带名字的格子 `s`，专门用来等候。



### 构造器和类

​	只要构造器能够【顺利、成功地执行完毕】，它就一定会返回一个全新的对象地址给左边的变量

定义时： 构造器和类一样，都不写返回值类型，名字完全一样，只是构造器不写 `class`

运行时： 构造器只要一运转，一定会返回一个全新的对象地址给左边的变量 	e.g. `s1`



### **构造器和方法**

​	构造器**本质上**就是方法

​	构造器它虽然和方法一样是服务于类	但是构造器名字和类名一样	所以通常和类名有关系

​	而方法一般是独立的通用的功能	通常和类名没有很紧密的关系

​	e.g.  方法的名字通常是动词（比如 `study`、`run`、`print`），代表一个独立的功能动作。

​			汽车类（`Car`）里，可以有 `run()` 方法（车会跑）

​			人类（`Person`）里，也可以有 `run()` 方法（人会跑）

​			狗类（`Dog`）里，同样可以有 `run()` 方法（狗也会跑）

​	在 `class` 里定义的 构造器 和 方法 都会去 `class` 里抄 "格子"	------>	即成员变量（实例变量）

#### **深层理解**

​	**构造器** *（专属接生婆）*： 每调用一次 必然在【堆】里砸出一辆**新车（新地址）** $\rightarrow$ 吐出新地址交给【栈】里的新变量。所以，对于某一台特定的车，它只出生了一次（调用唯一一次）。

​	**普通方法** *（全能修理工）*： 每次调用 修理工**临时入栈**  顺着**完全不变的变量钥匙**和**完全不变的堆内存车牌号**  摸到车里去改一下油量或时速（数据） 改完修理工**瞬间出栈消亡**。

​	**因此**： *“每一个独立的对象，它的专属构造器在它自己的一生中，只会被调用唯一一次。”*



### **Java 只有值传递**

​	这里的“值（Value）”，在 JVM 眼里从来不单指具体的数字，它分为两大类：

​		1.直接量的值（基本类型）： 比如 `10`、`true`。

​		2.地址的值（引用类型）： 比如 `0x1122` 		*对 Java 来说，内存地址本身，也是一个“值”*



### **封装**

  *`set` 的意思是：“放进去（修改/写入）”*

  *`get` 的意思是：“拿出来（获取/读取）”*

​	有了封装，以 `id`为例	 只提供了 `getId()` 方法，而不提供 `setId()` 方法  别人无法修改数据

​	如果直接把变量暴露在外面，比如别人一不小心写个 `p.id = 999`，数据就乱套了 被修改了

​	封装**本质上**  是  **调用方法**



### this

```java
Student s1 = new Student("徐力鸿", '男', 175.5, 99);
StudentOperator operator = new StudentOperator(s1);private Student s;

    public StudentOperator(Student s){
      	this.s = s;
        
//this.s本质上是 StudentOperator(s1)的堆内存 s1只是把它索引了 
```

 	**哪个变量调用的，this 就代表这个变量格子里装的那个堆内存地址；如果没有变量，this 就直接代表 new 出来的那个对象的堆内存地址**



—————————————————————————————————————————————————————



