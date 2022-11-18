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
> 编写 Java 程序时，应注意以下几点：
>   * 大小写敏感：Java 是大小写敏感的，这就意味着标识符 Hello 与 hello 是不同的。
>   * 类名：对于所有的类来说，类名的首字母应该大写。如果类名由若干单词组成，那么每个单词的首字母应该大写，例如 MyFirstJavaClass 。
>   * 方法名：所有的方法名都应该以小写字母开头。如果方法名含有若干单词，则后面的每个单词首字母大写。
>   * 源文件名：源文件名必须和类名相同。当保存文件的时候，你应该使用类名作为文件名保存（切记 Java 是大小写敏感的），文件名的后缀为 .java。（如果文件名和类名不相同则会导致编译错误）。
>   * 主方法入口：所有的 Java 程序由 public static void main(String[] args) 方法开始执行。
> 只有和文件名一致的类才能是public，其他的都是default（默认）
>   * 用驼峰命名法定义变量的原因是$符号是给内部类用的，_是给常量用的

==default别乱用！等用到接口再说==

# 运行
class文件通过Java虚拟机实现跨平台运行，包名命名时，一个.就是一个文件夹

# 第一个程序
输出：sout加Tab键
for循环：fori然后回车
> for循环中length是变量不是函数，不用加括号
> 侧栏展开：alt+1
> 快速对齐：Ctrl+Alt+L
> 快速生成变量：CTRL+ALT+V或者在没加分号时句末加.var
> 主函数：psvm或者main
> 输出离它最近的那个变量：soutv+回车
> 多行注释：/*+回车
> 快捷注释：ctrl+/
> 方法注释：/**+回车
> 撤回：ctrl+z
>
> 提示构造方法内容：ctrl + p
>
> 批量修改：shift + f6
>
> 替换：ctrl + r
>
> xml快捷注释：ctrl + shift + /
>
> 大纲视图：alt + 7，可以点边栏右上角设置移到右边去
>
> 换行也可以直接来一行sout（啥都不加）
>
> int类型不赋值默认0，String类型不赋值默认null
>
> ctrl + f12：出现这个类的详细列表（红色m图标是方法，黄色的f是属性也就是成员变量，蓝色的c是内部类）
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
        for (int i = 0;i<str_1.length;i++){
            
        }
    }
}
```

## .contains()

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        String str = "abcd";
        System.out.println(str.contains("ab"));
    }
}
```

输出为true

## .equals()

如果不是基本类型，那就是引用类型，如果用==判断引用类型，那就是判断它们是不是同一个对象（当然不是，但jvm底层优化了才返回true）

比较String字符串是不是一样的话，推荐equals

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        String str1 = "abcd";
        String str2 = "abcd";
        System.out.println(str1.equals(str2));
    }
}
```

结果为true

## 连接字符串

> "hello" + "world"

# 导包(在class上面导)
> import com.microsoft.tools.Student//精确到类来告诉程序你想用谁家的Student
> ......tools.*//代表tools下面的所有包

包用到时会自动导，但要注意有没有导对

# 数组
不输值默认0

基本类型的数组存的就是数字（如int[]），引用类型的数组存的就是引用

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
而对于二维数组

```java
int[][] arr = new int[][]{{1,2}
                          {3,4}
                          {5,6}};//记得加分号
//先剥出每个数组，再剥出每个数组中的元素
for(int[] i : arr){
    for(int a : i){
        System.out.println(a);
    }
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

# 面向对象：封装、继承、多态

```java
Student student = new student();
```

引用类型(如String、Student) + 名称 = new 对象

大写开头的才是引用类型，引用类型其实就相当于指针

然后名称就指向这个新创建的对象了

```java
/*
这个举例的方法是没用的，我只是想说明我可以传类进去
因为类也是引用类型
*/
void a(Student s){
    s.name = "Tom";
}
```



只有实在存在的对象（对象是月饼，类是模具）我们才可以给他起名字，我们可以通过.来访问成员变量

由于等号左右东西一样，所以我们也可以

```java
new student().swap(1,3);
```



```java
package com.microsoft.bean;

// 狗都有这些
// 类当中的变量和方法都统称为属性（共性、特性）
public class Dogs {
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
import com.microsoft.bean.Dogs;

public class Application {
    public static void main(String[] args) {
        // 张大爷注册
        Dogs zhangDog = new Dogs();

        // 设置狗的信息
        zhangDog.name = "Jerry";
        zhangDog.age = 2;
        zhangDog.variety = "拉布拉多";

        //王阿姨注册
        Dogs wangDog = new Dogs();

        wangDog.name = "Tom";
        wangDog.age = 2;
        wangDog.variety = "藏獒";

        System.out.println("张大爷的狗叫" + zhangDog.name);
        System.out.println("王阿姨的狗叫" + wangDog.name);

        //张大爷的狗睡觉了
        zhangDog.sleep();//看到sleep()先找Dogs这个类，再找sleep()这个函数
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

public class Dogs {
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
import com.microsoft.bean.Dogs;

public class Application {
    public static void main(String[] args) {
        Dogs zhangDog = new Dogs();
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

public class Dogs {
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
import com.microsoft.bean.Dogs;

public class Application {
    public static void main(String[] args) {
        Dogs zhangDog = new Dogs();
        zhangDog.setAge(-14);
        System.out.println("zhangDog age = " + zhangDog.getAge());
    }
}

```

## toString()
Dogs类
法一（不依赖Lombok）
```java
package com.microsoft.bean;

import lombok.Getter;
import lombok.Setter;

@Getter
@Setter

public class Dogs {
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
        return "Dogs{" +
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

public class Dogs {
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
Application类
```java
import com.microsoft.bean.Dogs;

public class Application {
    public static void main(String[] args) {
        Dogs zhangDog = new Dogs();
        zhangDog.setName("Jerry");
        zhangDog.setVariety("拉布拉多");
        zhangDog.setAge(10);
        System.out.println("zhangDog = " + zhangDog);//这里直接println zhangDog
    }
}

```

## 构造方法（构造器是为了初始化对象）

对于

```java
public class Student{}
```

其class文件反编译后结果是

```java
public class Student{
    public Student() {
    }
}
```

这就是构造方法，啥都不编写，编译时默认自带一个无参的构造方法

new + 你想要使用的构造方法 就能创建出对应类型的对象，并将它的引用交给左边；或者也直接用new。。。访问

没有返回类型的方法（包括void）就是构造方法

在Student里面用构造方法，然后main方法里面在new的时候就输入变量的值

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
    public void Dogs() {
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
    
    public class Dogs {
        private String name;
        private String variety;
        private int age;
        private String food;
    
        // 构造方法别加类型，所以也别加void
        //可能会有人啥都不想填，所以先留着
        public Dogs() {
    
        }
        /*
        只要创建类如Dogs zhangDog = new Dogs()，
        就默认无参数构造上面这种函数,又称无参构造器
        但此例下面还写了个有参构造器，所以必须创建
        */
    
        //下面这里，alt + insert构造函数
        public Dogs(String name, String variety, int age, String food) {
            this.name = name;
            this.variety = variety;
            this.age = age;
            this.food = food;
        }
    }
    
    ```
    ```java
    //可以注册完成之后，再补充资料
    import com.microsoft.bean.Dogs;
    
    public class Application {
        public static void main(String[] args) {
        
            Dogs zhangDog = new Dogs();
            zhangDog.setName("Jerry");
            zhangDog.setVariety("拉布拉多");
            zhangDog.setAge(10);
    
            System.out.println("zhangDog = " + zhangDog);
        }
    }
    
    //也可以一开始就写资料
    import com.microsoft.bean.Dogs;
    
    public class Application {
        public static void main(String[] args) {
            Dogs zhangDog = new Dogs("Jerry","拉布拉多",2,"null");
            System.out.println("zhangDog = " + zhangDog);
        }
    }
    
    ```
    还有件事，看出来下面是啥了吗
    没错，就是==重载==，构造方法也可以重载的
    
    你不构造方法默认不显示就是无参构造，当你决定构造方法时候，你构造的方法会把默认值替换了
```java
public Dogs() {

}
public Dogs(String food) {
    this.food = food;
}

public Dogs(String name, String variety, int age, String food) {
    this.name = name;
    this.variety = variety;
    this.age = age;
    this.food = food;
}
```
## 关于this
**this指的就是对象**，不能指类！，你不写也行，写了也直接相当于eat=eat，
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
成员对象（name、age）属于对象的，静态的东西属于类，属于谁从谁调用

静态的东西用户是没法主动获取的
静态的好处是建立在class类上层的，和它的对象根本没关系
[Java static关键字（静态变量和静态方法）](https://ock.cn/qdirf)
[比喻版](https://www.zhihu.com/answer/28422467)

```java
package com.microsoft.bean;

public class Dogs {
    //小区名,不加public那边看不到
    public static String community = "NanG";
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
import com.microsoft.bean.Dogs;

public class Application {
    public static void main(String[] args) {

        System.out.println("Dogs.community = " + Dogs.community);//类名.静态属性
        Dogs.injection();
        /*
        静态的直接用类名访问，不用加对象了
        不用像eat(),sleep()那样new个Dogs
         */
    }
}
```
## private static
如果在Application类，有人加入了以下代码，那事儿就大了
```java
Dogs.community = "The hackers came";
```
所以还得是private，此时还想发挥静态类名访问的优势，就要这样
```java
package com.microsoft.bean;

public class Dogs {

    private static String community = "NanG";
    
    public static String getCommunity(){
        return community;//静态的就不用写this了，程序知道就这一个
    }
}
```
```java
import com.microsoft.bean.Dogs;

public class Application {

    //现在只能获取了，禁止操作小区
    public static void main(String[] args) {

        System.out.println("Dogs.community = " + Dogs.getCommunity());

    }
}
```

## 静态代码块
用途不多，看书，static包个代码块且只加载一次

## static单例模式

[几种单例模式](https://zhuanlan.zhihu.com/p/105586046)
贴个流程先
![](images/2022-09-14-17-59-34.png)
```java
package com.microsoft.bean;

public class Earth {
    //单例设计模式
    /*
    在这里自己new自己
    用static保证earth，不提供对外new的方法
     */
    private static Earth earthInstance = new Earth();//shift+f6改名

    //alt+insert构造，换private
    //因为下面private了所以Application new不了了
    private Earth() {
    }//禁止new Earth();

    public static Earth getEarthInstance() {
        return earthInstance;
    }

    public void hello() {
        System.out.println("hello");
    }
}
```
```java
import com.microsoft.bean.Dogs;
import com.microsoft.bean.Earth;

public class Application {
    public static void main(String[] args) {

        Earth earthInstance = Earth.getEarthInstance();

        earthInstance.hello();

    }
}
```

## 内部类（看书，开发基本不会这么写）
==一个文件只能有一个public的class，所以直接写class==
想要让外部访问要加public

## 需求重定义 -> 继承
如果养猫的和养老鼠的也想让系统管管
产生矛盾：
* 用一个类—>有特性
* 不用一个类->有共性
Animal类
```java
package com.microsoft.bean;

import lombok.Getter;
import lombok.Setter;
import lombok.ToString;

@Getter
@Setter
@ToString
public class Animal {
    private String name;

    private String variety;

    private int age;

    private String food;

    public void eat() {
        System.out.println(name + "正在吃饭");
    }

    public void sleep() {
        System.out.println(name + "正在睡觉");
    }

    public void sick() {
        System.out.println(name + "在生病");
    }

    private static String community = "NanG";

    public static String getCommunity() {
        return community;//静态的就不用写this了，程序知道就这一个
    }

    public static void injection() {
        System.out.println("所有的动物，月底打针");
    }
}
```
Dogs类
```java
package com.microsoft.bean;
//继承
//子类 extends 父类
public class Dogs extends Animal {

}
```
Cats类
```java
package com.microsoft.bean;

public class Cats extends Animal {
     
}
```
Application类
```java
import com.microsoft.bean.Cats;
import com.microsoft.bean.Dogs;

public class Application {
    public static void main(String[] args) {
        Dogs zhangDog = new Dogs();
        zhangDog.setName("Jerry");
        zhangDog.setAge(2);
        System.out.println("zhangDog = " + zhangDog);

        Cats liCat = new Cats();
        liCat.setName("Tom");
        liCat.setAge(3);
        System.out.println("liCat = " + liCat);

        zhangDog.sleep();
        liCat.eat();
    }
}
```
## 多层继承
==只能爹继承爷，儿子继承爹，不能儿子同时继承爷和爹==
Larbrador
```java
package com.microsoft.bean;

public class Labrador extends Dogs{
}

```
Application
```java
import com.microsoft.bean.Labrador;

public class Application {
    public static void main(String[] args) {

        Labrador labrador = new Labrador();
        labrador.setAge(5);
        System.out.println("labrador = " + labrador);

    }
}
```
## 方法的重写
参数类型或数量不同才是重载
和继承有关的才是重写，好处是可以让子类创造出不同于父类的、而是自己的方法
Animal类
```java
package com.microsoft.bean;

import lombok.Getter;
import lombok.Setter;
import lombok.ToString;

@Getter
@Setter
@ToString
public class Animal {
    private String name;

    private String food;

    public void eat() {
        System.out.println(name + "正在吃饭，吃的是" + this.food);
    }

    public void barking() {
        System.out.println("动物在叫");
    }

}

```
Dogs类
```java
package com.microsoft.bean;
//继承
//子类 extends 父类
public class Dogs extends Animal {
    //alt + insert，重写方法

    /*
    在子类中，凡是有@Override的标签，
    那它下面的方法一定是来自它父类的，但又不学它的父亲
    这是它自己拥有的特性，是它自己的，它革新了
    革新的内容就是方法体，override就是重写
    */
    @Override
    public void barking() {
//        super.barking();
        System.out.println("汪汪！");
    }
}
```
Cats类
```java
package com.microsoft.bean;

public class Cats extends Animal {
    @Override
    public void barking() {
//        super.barking();
        System.out.println("喵喵喵");
    }
}

```
Application类
```java
import com.microsoft.bean.Cats;
import com.microsoft.bean.Dogs;

public class Application {
    public static void main(String[] args) {

        Dogs zhangDog = new Dogs();
        zhangDog.setName("Jerry");
        zhangDog.setFood("狗粮");
        zhangDog.eat();

        Cats liCat = new Cats();
        liCat.setName("Tom");
        liCat.setFood("猫粮");
        liCat.eat();

        zhangDog.barking();
        liCat.barking();

    }
}

```

## super啃老
[java中子类构造方法和父类构造方法](https://blog.csdn.net/DTEzhihao/article/details/86765119)
[Java子类的构造方法](https://blog.csdn.net/Soilerest/article/details/85610886)
[Java构造方法和子类构造方法](https://blog.csdn.net/du_du1/article/details/91383128)
[为什么创建了一个子类对象会调用其父类的构造方法](https://www.jianshu.com/p/9e7b6e2ffc8f)
方法重写了，假如又想用回父类的方法，那就用@Override自带的super
(该例中其余类与前例相同)
Cats类
```java
package com.microsoft.bean;

public class Cats extends Animal {
    @Override
    public void barking() {
        super.barking();
//        System.out.println("喵喵喵");
    }
}
```
我们会发现
```java
Dogs wangDog = new dog("Jerry",2);//error，不可以！
```
而
```java
Animal animal = new Animal;//可以的
```
**这是因为父类构造方法是绝对不能被子类继承的。**

子类构造方法调用父类的构造方法重点是：**子类构造方法无论如何都要调用父类的构造方法。**
子类构造方法要么调用父类无参构造方法（包括当父类没有构造方法时。系统默认给的无参构造方法），要么调用父类有参构造方法。

Dogs类
```java
package com.microsoft.bean;

public class Dogs extends Animal {

    //alt + insert构造函数，这下就可以用父类的构造方法了
    public Dogs() {
    }

    public Dogs(String name, String variety, int age, String food) {
        super(name, variety, age, food);//看到没，自动生成就有super
    }

    @Override
    public void barking() {
//        super.barking();
        System.out.println("汪汪！");
    }
}
```

## final
不要忘了Java开发手册的要求
> 常量命名全部大写，单词间用下划线隔开，力求语义表达完整清楚，不要嫌名字长
```java
public static final String TEXT_COMMUNITY_NAME = "NanG";
```
Animal类
```java
package com.microsoft.bean;

public class Animal {

    public static final String COMMUNITY_NAME = "NanG";
    
    public void barking() {
        System.out.println("动物在叫");
    }

}
```
Dog类
```java
package com.microsoft.bean;

public class Dogs extends Animal {

    //反例:若下面方法boolean前加final，则Labrador类无法重写
    //final 方法 不能被子类继承或者重写 想为所欲为操作遗产不可能，但可以用用返回值
    //final修饰变量时，此变量永远不能改，放static后，String前
    public boolean isGuideBlindness(){
        return false;
    }
}
```
Labrador类
```java
package com.microsoft.bean;

//拉布拉多是最下层了，后面没人继承它了
//final 最终 分不了了
/*
1. 遗产没人继承，也不可能被继承
 */
public final class Labrador extends Dogs{
    @Override
    public boolean isGuideBlindness() {
        return true;
    }
}

```
Application类
```java
import com.microsoft.bean.Labrador;

public class Application {
    public static void main(String[] args) {

        Labrador labrador = new Labrador();
        System.out.println(labrador.isGuideBlindness());

    }
}

```

## 新的问题：
* Animal没用，它是个抽象的东西，只能被继承（new Animal没有价值）
* 万一后面新增子类忘重写了某方法咋办

## 抽象类
Animal本质上来说是没有人用的，它是一个抽象的，他抽取了这些猫狗的共性，作为使用
抽象-----具体
动物-----狗
抽象的目的是为了解释（概括）具体的共性
Animal animal = new Animal();  ×
**所以，Animal类应该是这样的**
```java
//我们让Animal变成抽象类
public abstract class Animal {

}//现在开始，不能new Animal()了，因为没意义
```

## 抽象方法 ———— 不能有实际的意义 -> 你不知道Animal怎么叫的
**动物叫声太多了，你==没法具体到某一个指定的叫声==**
所以抽象方法不能加大括号
```java
public abstract void barking();
```
==如果写了抽象方法，那这个类必须是抽象类==
==现在开始，不能写super了，所有继承Animal的类，必须重写抽象的方法==
Animal类
```java
package com.microsoft.bean;

public abstract class Animal {

    public static final String COMMUNITY_NAME = "NanG";

    public abstract void barking();

}

```
Hamster类
```java
package com.microsoft.bean;

// 当一个类继承一个抽象类，此时该子类必须重写父类中所有抽象方法
public class Hamsters extends Animal {

    @Override
    public void barking() {
        System.out.println("吱吱吱");
    }
}

```
Application类
```java
import com.microsoft.bean.Hamsters;

public class Application {
    public static void main(String[] args) {
        Hamsters hamsters = new Hamsters();
        hamsters.barking();
    }
}

```

## 接口
如果Animal中所有的方法都是抽象的，那就没必要写抽象类了，
因为有个更好的东西：接口

Human接口
```java
//知道怎么用就行，后面Dao Service会学
package com.microsoft.bean;

//接口
//里面所有的方法都是抽象的
public interface Human { 

    public void eat();

    public void run();

}
```
Chinese类
```java
package com.microsoft.bean;

// 实现接口
//划红波浪线了，alt + 回车，实现方法

// 类中的方法我们可以叫重写
// 但在接口中，我们叫：实现
public class Chinese implements Human{
    @Override
    public void eat() {
        System.out.println("吃中餐");
    }

    @Override
    public void run() {
        System.out.println("养生跑");
    }
}
```
Westerner类
```java
package com.microsoft.bean;

public class Westerner implements Human{
    @Override
    public void eat() {
        System.out.println("吃西餐");
    }

    @Override
    public void run() {
        System.out.println("小跑");
    }
}
```
```java
import com.microsoft.bean.Chinese;
import com.microsoft.bean.Westerner;

public class Application {
    public static void main(String[] args) {
        Chinese chinese = new Chinese();
        chinese.eat();
        chinese.run();

        Westerner westerner = new Westerner();
        westerner.eat();
        westerner.run();
    }
}
```

## 接口和抽象类
以Animal为例
* 抽象类是对具体的事物进行抽象，比如Animal始终是类
  > 猫、狗、老鼠
* 接口是对动作、行为的抽象，Human始终是一个接口
  ==不要把它抽象为名词！==
  > 吃、跑、玩、乐
    在接口中，动物是不会有姓名和年龄的

## 多态
1. 一定要有继承关系
2. 向上转型或向下转型

**优势**
1. 她能够先使用父亲的东西
2. 用到自己特性的时候，可以再切换回来
3. 总结来说就是有多个功能
花弧类
```java
package com.microsoft.bean;

// 这是花木兰她爹
public class HuaHu {
    /*
    她爹有她爹的名字，演示方便起见，
    不用private + getset了，public先
     */
    public String name = "HuaHu";
    public int age = 45;

    // 自我介绍
    public static void sayMe() {
//        System.out.println("大家好，我叫" + this.name);哈哈，static不能这么写
        System.out.println("大家好！我叫HuaHu，今年45");
    }

    public void fight() {
        System.out.println("干架！");
    }
}

```
花木兰类
```java
package com.microsoft.bean;

public class HuaMuLan extends HuaHu {
    public String name = "HuaMuLan";
    public int age = 19;

    public void dressing() {
        System.out.println("HuaMuLan化妆...");
    }
}

```
Application
```java
import com.microsoft.bean.HuaHu;
import com.microsoft.bean.HuaMuLan;

public class Application {
    public static void main(String[] args) {
        // 多态

        // 替父从军
        //new的是花木兰，但是给的值是花弧
        //父类new子类->向上转型（替父从军），好处是隐藏自己
        HuaHu huaHu = new HuaMuLan();//对外说是花弧，实际上是花木兰
        //用花弧的方式new花木兰
        //把木兰类型的变量当作花弧来用

        //打着她爹的名义，所以说自己是花弧
        System.out.println(huaHu.name);
        //注解会自动检测，没法讲课，所以不用@ToString
        System.out.println(huaHu.age);

        HuaHu.sayMe();
        HuaMuLan.sayMe();//因为没重写，所以用的是她爹的

        huaHu.fight();//发现花弧不能化妆，只能打架

        System.out.println("--------这是分割线---------");
        //假如仗打完了，做回自己，向下转型
        HuaMuLan huaMuLan = (HuaMuLan) huaHu;//报错，alt + 回车，强制转换
        System.out.println(huaMuLan.name);
        System.out.println(huaMuLan.age);
        huaMuLan.dressing();
    }
}
```

## 匿名内部类

Application类()

```java
public class Main {
    public static void main(String[] args) {
        new Human() {
            @Override
            public void eat() {
                System.out.println("中国人吃中国菜");
            }
        }.eat();
    }
}
```

Lambda表达式下的Application类

```java
public class Main {
    public static void main(String[] args) {
        ((Human) () -> System.out.println("中国人吃中国菜")).eat();
    }
}
```



Human接口

```java
public interface Human {
    public void eat();
}
```

# Java 进阶==练习为重！==

API，应用程序接口，是给客户（开发者用的）

所以Java API就是给Java的开发者用的，方便去给他们开发。只要有API，就应当有相应的API文档

## Base API

* 自己写工具方法就直接static，这样可以直接类名 + . 访问，不用new了

  > 假设类名是螺丝刀，那我要用“拧螺丝”这个方法的时候，我想直接用已有的（static）而不是新买一把（new 一个）

### Scanner,Number,Math,Random

### ThreadLocalRandom

本地，多线程，线程安全，高性能，可以自定义首尾范围的随机方法

==因为这是static方法，所以不用new，直接类名.就可以了==

```java
double i = ThreadLocalRandom.current().nextDouble(0.9,1.5);
```

### Date

 查当前时间

```java
System.out.println(new Date());
```

### DateFormat和SimpleDateFormat

DateFormat是抽象类，不能new，所以要new它的子类

```java
Date date = new Date();
DateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");//dateFormat这个对象现在就跟着括号里这个格式了
//哪怕你后面new再多的Date，也可以用dateFormat这个对象里面的这个format()方法来定制格式 
System.out.println(dateFormat.format(date));
```

![image-20221007095449245](C:\Users\84185\AppData\Roaming\Typora\typora-user-images\image-20221007095449245.png)

### Calendar（推荐使用）

==Calendar类是一个抽象类，所以下面这张图没有new一个Calendar对象！==

![image-20221007101051748](C:\Users\84185\AppData\Roaming\Typora\typora-user-images\image-20221007101051748.png)

当然了，不止get，也可以set

### System

这个类本身就是final，更何况里面的方法全是static，所以直接.就行

#### 获取当前时间戳

```java
System.out println(System.currentTimeMillis());
```

#### 垃圾回收

gc()

#### 退出Java虚拟机

exit(0);

#### 高性能的arraycopy（因为是系统级别的）

![image-20221007192319813](C:\Users\84185\AppData\Roaming\Typora\typora-user-images\image-20221007192319813.png)

## 1.unit test and main function

### 模块化编程是面向对象语言的核心

main是程序的入口点，一个项目只能有一个main方法



以往的工作流程

1. 编写功能函数（方法）

2. 本地测试

3. 在main方法里调用函数测试

4. 控制台看输出是否符合预期

5. 预期结果和测试结果是通过人工计算的

   

企业的工程原则

1. main方法里不应该有太多逻辑性（或功能性）的语句，由于要追求复用性，所以把他们抽离出来

2. 以学生管理系统为例，最后的程序应该是这样的

   ```java
   public class Application {
       public static void main(String[] args) {
           run();
       }
       
       public static void run() {
           sayHello();
           //.....
           //.....
       }
       public static void sayHello(){
           System.out.println("----------欢迎来到学生管理系统---------")
               //....
       }
       //.......
       //......
   }
   ```

   main只是一个起始点，少出现：

   逻辑性语句：如if else

   功能性语句：求和方法什么的

   提示性语句：以print为突出案例

所以，

* 脱离main里啥都写
* 在main里面测试是有问题的，因为main是整个程序的入口点，而不是让你用来测试程序的，处理功能模块的

这就是模块化编程

* 把功能性的抽离出来成为一个方法，然后通过main进行调用

### 那么如果不用main，我们用什么

JUnit，Java语言的一个==单元测试（也叫模块测试）框架==，是给程序员用的（而不是测试人员）

每个理想的测试案例独立于其他案例

### Maven Respository获取JUnit

现在先学jar包（因为构建工具太麻烦了，先凑合着用）

jdk的包不够用了，所以你要引入别人的jar包

### 演示

先在==最上面==的文件夹里建一个目录叫lib，去文件资源管理器把junit-4.13.2.jar和hamcrest-core-1.3.jar包扔进去，右键添加到库

Calc类

```java
package com.google;

public class Calc {
    public static int sum(int numberA, int numberB) {
        return numberA + numberB;
    }

    public static int subtraction(int numberA, int numberB) {
        return numberA - numberB;
    }
}
```

CalcTest类

```java
package com.google;

import org.junit.Assert;
import org.junit.Test;

import java.util.concurrent.ThreadLocalRandom;

public class CalcTest {
//想测谁测谁，方法测试相互独立，可以同时测试不同的解决方案
    @Test
    public void sum() {

        //随机测试，摆脱main和println的操作
        int numberA = ThreadLocalRandom.current().nextInt();
        int numberB = ThreadLocalRandom.current().nextInt();
        int sum = Calc.sum(numberA, numberB);

        //断言
        //肯定是对的，只是演示哈
        Assert.assertEquals(numberA + numberB, sum);
    }

    @Test
    public void subtraction() {

        int numberA = ThreadLocalRandom.current().nextInt();
        int numberB = ThreadLocalRandom.current().nextInt();
        int subtraction = Calc.subtraction(numberA, numberB);

        Assert.assertEquals(numberA - numberB, subtraction);
    }

}
```

## StringBuilder（查文档）

==首先，String的各种方法一定要熟悉==

```java
String s1 = "Hello";
String s2 = "World";
s1 = s1 + s2;//此时s1指向了一块新的内存，原来的废了（成垃圾了），但到底怎么样了就是后话了
```

```java
StringBulider stringBulider = new StringBuilder();
stringBulider.append("Hello");
stringBulider.append("World");
//也可以链式调用
stringBulider.append("Hello").append("World");
stringBulider.reverse();
System.out.println(stringBulider);
//还有很多方法
```

直接toString就变String了

当然，也可以滞空字符串序列（把留的用来缓冲的空去掉）==注意，这不是静态类，是“对象.”不是“类名.”==

```java
stringBulider.trimToSize();
```

## 异常

括号里是蓝色的才跟你有关系，灰色的就不用管了

### try catch（检测异常，不是抛出异常！）

ctrl + alt + t选择try catch包裹，把catch里面的删掉，就可以拿去糊弄毕设（没报错了）==在公司用要被开除的！==

### 为什么要抛出异常

为了避免后续引发一系列程序bug,以及定义文件发生错误的位置

```java
@Test
    public void demo() throws FileNotFoundException//直接全换成Exception也可以
        if(文件不存在){
            throw new FileNotFoundException("文件不存在")
    }
```

也可以自己写一个异常类继承自Exception(编译时检测)（写这个类时记得alt + insert，第一个全选）

后面用到这个方法时就要么捕获异常，要么抛出异常

```java
public int sum(int a,int b) throws FrankException{
        if (a > 10 || b > 10)
            throw new FrankException("数据过大！");
        return  a + b;
    }
```

RunTimeException是运行时检测，但一般不建议

[Java throws与try..catch异常处理_我的猴子的博客-CSDN博客](https://blog.csdn.net/qq_51272114/article/details/125380406)

更详细的回答

[Java 中 try-catch,throw和throws的使用_daxiong0816的博客-CSDN博客_try里面throw](https://blog.csdn.net/daxiong0816/article/details/121868890)

# IO流

## 理解

输入：输进去，也就是获取

所以我们打开一个文件是输入，因为它是相对于我们目前的程序而言的

## FiIeInputStream字节流读取文件
