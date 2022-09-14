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

public class Application {
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
封装好让大家直接用，但又不能提供过多的权限导致安全问题
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
    /* 
    this.age是上面private的age，
    详细来说作用对象zhangDog的age（因为传的是zhangDog）,
    int age是用户传进来的age
    */
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

public class Application {
    public static void main(String[] args) {
        Dog zhangDog = new Dog();
        zhangDog.setAge(14);
        System.out.println("zhangDog age = " + zhangDog.getAge());
    }
}

```

## Lombok(==这只是工具，不要忘了getset怎么写==)
```java
package com.microsoft.bean;

//下面两行开始时是没有的

import lombok.Getter;
import lombok.Setter;

//看下面！（这俩建议写类上面）
@Getter
/*
先在最大的文件夹下新建个目录叫jar，
拖lombok...jar文件进去，右键添加为库，
ok，alt+shift+回车
*/
@Setter//现在按alt + 回车

public class Dog {
    // 狗名字
    private String name;
    // 狗种类
    private String variety;
    // 狗年龄
    private int age;

    //特殊的单独写就行了：方法的重写
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

}

```
```java
import com.microsoft.bean.Dog;

public class Application {
    public static void main(String[] args) {
        Dog zhangDog = new Dog();
        zhangDog.setAge(-14);
        System.out.println("zhangDog age = " + zhangDog.getAge());
    }
}

```

## toString()
Dog模块
法一（不依赖Lombok）
```java
package com.microsoft.bean;

import lombok.Getter;
import lombok.Setter;

@Getter
@Setter

public class Dog {
    // 狗名字
    private String name;
    // 狗种类
    private String variety;
    // 狗年龄
    private int age;
    private String food;

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

    //alt + insert选toString
    //@符号后面添加的叫注解
    @Override//重写，后面会讲
    public String toString() {
        return "Dog{" +
                "name='" + name + '\'' +
                ", variety='" + variety + '\'' +
                ", age=" + age +
                ", food='" + food + '\'' +
                '}';
    }
}

```
法二：利用Lombok的@
```java
package com.microsoft.bean;

import lombok.Getter;
import lombok.Setter;
import lombok.ToString;

@Getter
@Setter
@ToString //看这里！如果还想加上equals()、hashCode()那就直接写@Data

public class Dog {
    // 狗名字
    private String name;
    // 狗种类
    private String variety;
    // 狗年龄
    private int age;
    private String food;

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
    //后面就不用啦
}

```
Application模块
```java
import com.microsoft.bean.Dog;

public class Application {
    public static void main(String[] args) {
        Dog zhangDog = new Dog();
        zhangDog.setName("Jerry");
        zhangDog.setVariety("拉布拉多");
        zhangDog.setAge(10);
        System.out.println("zhangDog = " + zhangDog);//这里直接println zhangDog
    }
}

```

## 构造方法（构造器是为了初始化对象）
* 初始化 定义+使用
  ```java
    int[] arrDogs = {1,2,3,4};
  ```
* 先定义后使用
  ```java
    int[] arr = new int[4];
    arr[0] = 1;
  ```

### 示例
* ```java
    public void Dog() {
        //空参的构造函数，什么都不传
    }
    ```
* ```java
    package com.microsoft.bean;

    import lombok.Getter;
    import lombok.Setter;
    import lombok.ToString;

    @Getter
    @Setter
    @ToString//看这里！

    public class Dog {
        private String name;
        private String variety;
        private int age;
        private String food;

        // 构造方法别加类型，所以也别加void
        //可能会有人啥都不想填，所以先留着
        public Dog() {

        }
        /*
        只要创建类如Dog zhangDog = new Dog()，
        就默认无参数构造上面这种函数,又称无参构造器
        但此例下面还写了个有参构造器，所以必须创建
        */

        //下面这里，alt + insert构造函数
        public Dog(String name, String variety, int age, String food) {
            this.name = name;
            this.variety = variety;
            this.age = age;
            this.food = food;
        }
    }

    ```
    ```java
    //可以注册完成之后，再补充资料
    import com.microsoft.bean.Dog;

    public class Application {
        public static void main(String[] args) {
        
            Dog zhangDog = new Dog();
            zhangDog.setName("Jerry");
            zhangDog.setVariety("拉布拉多");
            zhangDog.setAge(10);

            System.out.println("zhangDog = " + zhangDog);
        }
    }

    //也可以一开始就写资料
    import com.microsoft.bean.Dog;

    public class Application {
        public static void main(String[] args) {
            Dog zhangDog = new Dog("Jerry","拉布拉多",2,"null");
            System.out.println("zhangDog = " + zhangDog);
        }
    }

    ```
还有件事，看出来下面是啥了吗
没错，就是==重载==，构造方法也可以重载的
```java
public Dog() {

}
public Dog(String food) {
    this.food = food;
}

public Dog(String name, String variety, int age, String food) {
    this.name = name;
    this.variety = variety;
    this.age = age;
    this.food = food;
}
```
## 关于this
**this指的就是对象**,你不写也行，写了也直接相当于eat=eat，
前面是private的eat，后面是传进来的eat
* > this.age是上面private的age，
    详细来说作用对象zhangDog的age（因为传的是zhangDog）,
    int age是用户传进来的age
    
    详细用法在OOP封装那节
* 想要在eat()里调用上面的sleep()
  ```java
    public void sleep(){
        System.out.println(name + "正在睡觉");
    }
    
    public void eat(){
        System.out.println(name + "正在吃饭");
        this.sleep();
    }
  ```

## 垃圾回收
前文zhangDog = null;的做法并不能真正释放掉
一般都是自动垃圾回收
手动需要用System.gc();

## 静态变量和静态方法（立围墙区分自家小区和外来狗）
静态的东西用户是没法主动获取的
静态的好处是建立在class类上层的，和它的对象根本没关系
[Java static关键字（静态变量和静态方法）](https://ock.cn/qdirf)
[比喻版](https://www.zhihu.com/answer/28422467)
```java
package com.microsoft.bean;

public class Dog {
    //小区名,不加public那边看不到
    public static String plot = "NanG";
    /*
    现在用Application的都是NanG小区的，
    就算没有狗了也会说明系统是给小区用的
    这就是静态变量
     */

    //静态方法：小区里所有狗都得打针，王大爷不愿意也得让他的狗打
    public static void injection(){
        System.out.println("所有的狗，月底打针");
    }
}
```
```java
import com.microsoft.bean.Dog;

public class Application {
    public static void main(String[] args) {

        System.out.println("Dog.plot = " + Dog.plot);//类名.静态属性
        Dog.injection();
        /*
        静态的直接用类名访问，不用加对象了
        不用像eat(),sleep()那样new个Dog
         */
    }
}
```
## private static
如果在Application模块，有人加入了以下代码，那事儿就大了
```java
Dogs.plot = "The hackers came";
```
所以还得是private，此时还想发挥静态类名访问的优势，就要这样
```java
package com.microsoft.bean;

public class Dog {

    private static String plot = "NanG";
    
    public static String getPlot(){
        return plot;//静态的就不用写this了，程序知道就这一个
    }
}
```
```java
import com.microsoft.bean.Dog;

public class Application {

    //现在只能获取了，禁止操作小区
    public static void main(String[] args) {

        System.out.println("Dog.plot = " + Dog.getPlot());

    }
}

```

## 静态代码块
用途不多，看书，static包个代码块且只加载一次

## static单例模式
？？？？



















## 内部类（看书，开发基本不会这么写）
==一个文件只能有一个public的class，所以直接写class==
想要让外部访问要加public

##