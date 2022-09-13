# 格式
Java每个文件命名一定是开头大写
```java
public class Main {
    public static void main(String[] args){
        System.out.println("Hello");
    }
}
```
菜鸟教程增补：
> 基本语法
编写 Java 程序时，应注意以下几点：
    * 大小写敏感：Java 是大小写敏感的，这就意味着标识符 Hello 与 hello 是不同的。
    * 类名：对于所有的类来说，类名的首字母应该大写。如果类名由若干单词组成，那么每个单词的首字母应该大写，例如 MyFirstJavaClass 。
    * 方法名：所有的方法名都应该以小写字母开头。如果方法名含有若干单词，则后面的每个单词首字母大写。
    * 源文件名：源文件名必须和类名相同。当保存文件的时候，你应该使用类名作为文件名保存（切记 Java 是大小写敏感的），文件名的后缀为 .java。（如果文件名和类名不相同则会导致编译错误）。
    * 主方法入口：所有的 Java 程序由 public static void main(String[] args) 方法开始执行。
# 运行
class文件通过Java虚拟机实现跨平台运行，包名命名时，一个.就是一个文件夹

# 第一个程序
输出：sout加Tab键
for循环：fori然后回车
> for循环中length是变量不是函数，不用加括号
侧栏展开：alt+1
快速对齐：Ctrl+Alt+L
快速生成变量：CTRL+ALT+V或者在没加分号时句末加.var
主函数：psvm或者main
输出离它最近的那个变量：soutv+回车
多行注释：/*+回车
快捷注释：ctrl+/
方法注释：/**+回车
撤回：ctrl+z
```java
package com.google;//用来定位Main文件在哪

//公共的 类  类名
public class Main {//win上新建类ctrl+alt+insert

    //main函数：程序入口点
    public static void main(String[] args) {
        int number_a = 1, number_b = 2;
        int sum = sum(number_a, number_b);//在写完sum(number_a, number_b);后再按一下CTRL+ALT+V
        System.out.println("sum = " + sum);
        System.out.println("Hello");
    }

    public static int sum(int number_a, int number_b) {
        return number_a + number_b;
    }
    
}
```

# 注释和文档
**文档要在指定的目录生成，别在原文档生成**
说“方法”不说“函数”
快速文档：ctrl+q
```java
//类注释示例
/**
 * 该方法传递两个int类型参数，用来求和
 * @param number_a 第一个加数
 * @param number_b 第二个加数
 * @return 返回一个求和后的结果
 */
public static int sum(int number_a, int number_b) {
    return number_a + number_b;
}
```

# 一带而过
常量定义；
> final int a = 1；

# 字符串演示
## 字符串语法
可以通过提供一个字符数组参数来初始化字符串
```java
public class StringDemo{
   public static void main(String args[]){
      char[] helloArray = { 'r', 'u', 'n', 'o', 'o', 'b'};
      String helloString = new String(helloArray);  
      System.out.println( helloString );
   }
}
```
**注意**:==String 类是不可改变的==，所以你一旦创建了 String 对象，那它的值就无法改变了

如果需要对字符串做很多修改，那么应该选择使用 StringBuffer & StringBuilder 类

## StringBuffer 和 StringBuilder 
![](images/2022-09-12-09-49-13.png)

## .length()的使用
==for循环中length是变量不是函数，不用加括号==
```java
public class Main {
    public static void main(String[] args){
        String str_1 = "hello";
        String str_2 = "world";

        System.out.println("str_1 -> length : " + str_1.length());
        for (int i = 0;i<str_1.length();i++){
            
        }
    }
}
```

## 连接字符串
> "hello" + "world"

# 导包(在class上面导)
> import com.microsoft.tools.Student//精确到类来告诉程序你想用谁家的Student
> ......tools.*//代表tools下面的所有包

包用到时会自动导，但要注意有没有导对

# 数组
不输值默认0
## 静态数组
```java
//法一：初始化
int[] arr_1 = {1,2,3,4};
//法二：分配空间
int[] arr_1 = new int[5];
arr_1[0] = 1;
arr_1[1] = 2;
```
### 增强for循环：for each
```java
double[] mylist = {1.9, 2.9, 3.9, 4.9};
//打印所有数组元素
//每个元素类型 element: 数组名
for (double element: mylist) {
    System.out.println(element);
}
```
## Arrays（util的）
### sort排序
```java
int[] arr_1 = {1426, 42, 53, 4, 5, 365, 67, 70};
Arrays.sort(arr_1);//排序

//for each遍历
for(int element: arr_1) {
    System.out.println(element);
    }
```
### search二分查找(要先排序)
```java
package com.google;

import java.util.Arrays; 

public class Main {
    public static void main(String[] args){
        int[] arr_1 = {1426, 42, 53, 4, 5, 365, 67, 70};
        Arrays.sort(arr_1);//排序
        //for each遍历
        for(int e
                : arr_1) {
            System.out.println(e);
        }
        //二分查找
        int result_index = Arrays.binarySearch(arr_1,1426);
        System.out.println("result_index = " + result_index);
    }
}
```
### 相等
```java
package com.google;
import java.util.Arrays;
public class Main {
    public static void main(String[] args){

        //相同顺序且相同元素
        int[] arr_1 = {1,2,3};
        int[] arr_2 = {1,2,3};
        
        boolean b = Arrays.equals(arr_1, arr_2);//按完Arrays.equals(arr_1, arr_2)按ctrl+alt+v再按回车
        System.out.println("b = " + b);

    }
}
```
### fill填充
```java
package com.google;

import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int array[] = new int[6];//建数组
        Arrays.fill(array, 100);//数组每个数填成100

        for (int i = 0; i < array.length; i++) {
            System.out.println(array[i]);
        }

        System.out.println();

        Arrays.fill(array, 3, 6, 50);//下标3到6换成50

        for (int i = 0, n = array.length; i < n; i++) {
            System.out.println(array[i]);
        }
    }
}
```

# 方法的重载（方法名复用性）
1. 方法名相同
2. 参数个数和参数类型不相同
==只要符合以上条件，系统就可以自选符合的方法调用==

```java
public class Main {
    public static void main(String[] args) {

        //方法的重载
        int sum1 = sum(1, 2);
        double sum2 = sum(1.2, 3.4);
        System.out.println("sum1 = " + sum1);
        System.out.println("sum2 = " + sum2);
    }

    public static int sum(int x, int y) {
        return x + y;
    }

    public static double sum(double x, double y) {
        return x + y;
    }
}
```
从Java中数组中也可见一斑
> Arrays.sort()中括号填什么类型都可以

---

* 面向过程(POP)：你想去做什么的时候，然后去做了，这就是过程
  走一步看一步，目标不明确，不适用大众
* 面向对象(OOP)：大众化，有目标，不强调过程
  设计思维：先考虑共性：所有该种类都具备的东西

---

# 面向对象
```java
package com.microsoft.bean;

// 狗都有这些
// 类当中的变量和方法都统称为属性（共性、特性）
public class Dog {
    // 下面几个是成员变量，他们组成了类，他们也是属性
    // 狗名字
    public String name;// 加public让大家都能填

    // 狗种类
    public String variety;

    // 狗年龄
    public int age;

    // 这些方法在类当中都叫行为
    public void eat(){
        System.out.println(name + "正在吃饭");
    }

    public void sleep(){
        System.out.println(name + "正在睡觉");
    }

    public void sick(){
        System.out.println(name + "在生病");
    }
}
```
```java
import com.microsoft.bean.Dog;

public class ApplicationRun {
    public static void main(String[] args) {
        // 张大爷注册
        Dog zhangDog = new Dog();

        // 设置狗的信息
        zhangDog.name = "Jerry";
        zhangDog.age = 2;
        zhangDog.variety = "拉布拉多";

        //王阿姨注册
        Dog wangDog = new Dog();

        wangDog.name = "Tom";
        wangDog.age = 2;
        wangDog.variety = "藏獒";

        System.out.println("张大爷的狗叫" + zhangDog.name);
        System.out.println("王阿姨的狗叫" + wangDog.name);

        //张大爷的狗睡觉了
        zhangDog.sleep();//看到sleep()先找Dog这个类，再找sleep()这个函数
        //王阿姨的狗在吃饭
        wangDog.eat();
    }

}

```
## 注销账户和null空指针异常
对象(zhangDog)都没了，如果还操作人家的属性(println name)，那就会NullPointerException，解决办法是不输出它的名字了

## OOP封装(Getter and Setter)
```java
package com.microsoft.bean;

public class Dog {
    // 狗名字
    private String name;// 加private让用户不能为所欲为
    // 狗种类
    private String variety;
    // 狗年龄
    private int age;


    // 我们要让用户一个能设置，能获取但不能瞎搞 -> getset
    // this.age是上面private的age，作用对象是zhangDog,int age是用户传进来的age
    public void setAge(int age) {
        if (age < 0 || age > 34) {
            System.out.println("您输入的数据不合法，已经默认清零！");
            this.age = 0;
        } else {
            this.age = age;
        }
    }

    public int getAge() {
        return this.age;
    }

    /*
    此时，为了方便给每个成员设置getset，可以使用自动生成的方式
    alt+insert -> Getter and Setter -> ctrl+a全选 -> 回车

    以下是生成效果
     */

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getVariety() {
        return variety;
    }

    public void setVariety(String variety) {
        this.variety = variety;
    }
}

```
```java
import com.microsoft.bean.Dog;

public class ApplicationRun {
    public static void main(String[] args) {
        Dog zhangDog = new Dog();
        zhangDog.setAge(14);
        System.out.println("zhangDog age = " + zhangDog.getAge());
    }
}

```

## 内部类（看书，开发基本不会这么写）
想要让外部访问要加public