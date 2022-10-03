递归：[必备基本算法 — 递归（详解、解题思路剖析、案例分析） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/338302261)

例题：[面向对象实战：递归程序设计_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1YP4y1o75f/?p=70&spm_id_from=pageDriver&vd_source=5322c4cb2cc6b441eeb5b161fd4f2ce6)

```java
package com.google;

public class Main {
    public static void main(String[] args) {
        System.out.println(jump(6));
    }

    public static int jump(int n) {
        if (n==0 || n == 1) return 1;
        return jump(n-1)+jump(n-2);
        /*
        =.(5)+(4)=.(4)+.(3)+(4)=.(3)+.(2)+(3)+(4)=.(2)+.(1)+......
         */
    }
}
```

递归二分查找

![image-20221001124910158](C:\Users\84185\AppData\Roaming\Typora\typora-user-images\image-20221001124910158.png)

  * Integer

    ```java
    Integer i = new Integer("666");
    //或者
    Integer i = Integer.valueOf("5555");
    ```

* String

  * str.length()

    ```java
    public static void main(String[] args) {
        System.out.println("Hello World".length());   //虽然看起来挺奇怪的，但是确实支持这种写法
    }
    ```

  * str.contains("ab")

  * substring切割

    ```java
    public static void main(String[] args) {
        String str = "Hello World";
        String sub = str.substring(0, 3);   //分割字符串，并返回一个新的子串对象
        System.out.println(sub);
    }
    ```

  * split分割

    ```java
    public static void main(String[] args) {
        String str = "Hello World";
        String[] strings = str.split(" ");   //使用split方法进行字符串分割，比如这里就是通过空格分隔，得到一个字符串数组
        for (String string : strings) {
            System.out.println(string);
        }
    }
    ```

  * 字符串转字符数组

    ```java
    public static void main(String[] args) {
        String str = "Hello World";
        char[] chars = str.toCharArray();
        System.out.println(chars);
    }
    ```

  * 字符数组转字符串

      ```java
      public static void main(String[] args) {
          char[] chars = new char[]{'奥', '利', '给'};
          String str = new String(chars);
          System.out.println(str);
      }
      ```

  * 快速获得某个位上的字符
  
      > str.charAt(0)
  
  
    * 第一次出现的下标位置
  
      > str.indexOf("Hello")
      
    * 最后一次出现的下标位置
  
      > str.lastIndexOf("Hello")
      
    * 判断是否为空串""
  
      > str.isEmpty()
      
    * 字符串A.equals(字符串B)
  
      > equals()方法再String被重写为比较值是否相同，重写前equals作用和==等价，对引用类型用就是比较二者地址
  


* Arrays

  * Arrays.toStrings(数组名) -> 来以字符串形式输出数组arr

  * Arrays.sort(数组名) -> 用来排序

  * Arrays.binarySearch(数组名,要查找的元素) -> 二分查找，要先排序

  * Arrays.equals(数组A,数组B) -> ctrl+alt+v再按回车

    >  boolean b = Arrays.equals(arr_1, arr_2);

  * Arrays.fill(array, 3, 6, 50); -> fill填充，下标3到6换成50

* Getter和Setter

