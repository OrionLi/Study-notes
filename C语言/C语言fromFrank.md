# 注意事项
## 关于VS2022上的C项目
### main
一个软件只能有一个main（因为main是启动点），所以把另一个源文件的命名为main_1，新建项目的话就不会影响了

### 操作
==记得按ctrl+s保存==
==检查大小括号有没有弄混==（**表现为VS2022要求加分号**）

### 文件
debug：工程文件，生成的exe需要依赖vs2022
release：发行版。切换发行版后点生成——生成解决方案，此时release的exe可独立运行，文件也小些
32位的切完x86，先生成解决方案再生成demo_01<示例>

分享代码：压缩demo_01整个文件夹

## 关于C语言
for后先空格再括号

整理对齐代码：按住ctrl，再依次按a,k,f

=是赋值，==才是等于

变量名命名要让人一眼看出其含义，不要int a或者int b，是啥人家都看不明白，不如sum（求和），temp（临时变量），单词组合可以下划线命名法：sun_flower或驼峰命名法：SunFlowerValues

换行一般用\n，\t是4个空格（和前后连在一起也没什么关系）

---

# 基础内容
快捷一点的变量定义
>int num1 = 1, num2 = 2;

快捷一点的运算
>printf("sum = %d\n", number_1   + number_2);

### printf的使用
>printf("number = %d\n",number);
printf("a = %d, b = %d\n", a, b);

==逗号前面是要输出的内容，后面是要输出的变量==

### scanf_s使用时==记得写&==！（取地址）


## 常量

### 宏定义：给某事物下定义，不用加等号
>#define PI 3.14

### 定义常量
const int SUN_FLOWER = 9999
宏定义和常量命名全大写，用_隔开

---

# 赋值运算符
![](images/2022-08-01-14-58-35.png)

# if的使用
## 基本格式
```c
if ( /*条件*/ ) { //就去执行某个东西
}
```

==如果不带大括号，if的范围只有它这一行和它的下一行==
## 示例
![](images/2022-08-01-15-09-04.png)

## 关系符的嵌套使用关系到程序的可读性
```c
if((age >= 18) && (english_score >= 90 || IQ >= 120)){printf("成年，允许玩！\n")};
```
## “非”的使用
```c
if(!(age >= 18) || !(english_score >= 90 || IQ >= 120)){printf("成年，允许玩！\n")};
```
---
# else的使用
==else总会找离他最近的if做匹配==

---

# 用户的不合法输入
原因是程序的不严谨
## 示例（会产生负数转换出错的bug，待修正）
```c
#include<stdio.h>
int main(void){

   unsigned age //定义age为无符号整数

   printf("Please input your age:\n");
   int age_input_result = scanf_s("%3u", &age); //代表可以输入3位无符号整型的数
   if (age_input_result != 1) {printf("输入数字不合法！只能输入小于三位的正整数！\n");//!=意思为不等于
   }else {
      printf("age = %u\n, age");
   }

   return 0
}

```
>%3u只会获取前三位数字
return 0后，程序结束，不再执行后面语句

# else if：要不然
```c
#include<stdio.h>
int main(void) {

	int age = 0;
	printf("Please input your age\n");
	int age_inpult_result = scanf_s("%2u", &age);
	if (age_inpult_result != 1) {
		printf("您输入的数字不合法！请重新输入\n");
		return 0;
	}
   //如果age=18就执行“满足成年”，否则依次执行
	if (age == 18) {
		printf("恭喜您已成年！\n");
	}
	else if (age >= 70) {
		printf("您是老年人\n");
	}
	else if (age >= 50) {
		printf("您是中年人\n");
	}
	else if (age > 18) {
		printf("您是青年人\n");
	}
	else if (age > 0 && age < 18) {
		printf("您还没成年\n");
	}
	//如果还是不行，那就else收尾
   else{
		printf("您输入的数字不合法！请重新输入\n");
	}

	return 0;
}
```
---
# switch语句
当对同一个变量进行判断操作，选择某些条件的时候，此时switch可能是最佳选择（一个变量满足多种判断）
写法：每写一个case后面都要跟一个break
## 示例
```c
#include<stdio.h>
int main(void) {
	unsigned floor = 1;

	printf("Please inpult your munber:(type integer):\n");
	scanf_s("%3u", &floor);//保证楼层合法且不为负数

	//switch就像一个电梯，age是载客，输入谁找谁
	switch (floor) {
		case 4:
			printf("You are on the fourth floor!\n");
			break;//break：到了，出去了。没有break就相当于按了电梯，但是到了该到的楼层不出去

		case 5:
			printf("You are on the fifth floor!\n");
			break;

		case 6:
			printf("You are on the sixth floor!\n");
			break;

		default://只有6层，去其他楼层滚！(作为一个提醒，它对用户是必要的）
			printf("Fuck off!");
			break;

	}
	
	return 0;
}
```
---
# 三元运算符
```c
#include<stdio.h>
int main(void) {
	int num;
	printf("Please input a number\n");
	scanf_s("%d", &num);
   //对就执行没毛病，错就执行有毛病
	(num == 10) ? printf("没毛病！") : printf("有毛病\n");
	return 0;
}

```

---
# while循环
当while里面为假时才不会执行循环
## 示例
```c
#include <stdio.h>
#define ONE_KILOMETER 1000

int main(void){
	int run_meter = 0;
	while (run_meter < ONE_KILOMETER) {
		printf("已经跑了%d米\n",run_meter);
		run_meter += 1;
	}
	printf("1000米跑完了！\n");

	return 0;
}
```
%d用于显示一个值（后面的run_meter)
==当（）内内容成立，则执行{}内内容==
每次跑1米，跑完去找体育老师判断跑了1000米没有，没有就接着去跑（由于跑完1000不循环了，所以建议printf告诉用户跑完了）

## 循环条件
1. 判断条件是否满足条件（证明跑了1000米）
2. 一定要有自增衡量变量，可能会有界限，突破界限时退出循环（向前迈出步子）
3. 可能会存在初始化的量（这个量从哪开始，这个人从哪开始跑） 

## 死循环
必要的：银行运作、高并发
   >简单来说，四核CPU 一核微信 一核QQ，俩都是==像==while死循环跑着，所以要理解==何时利用死循环==

---

# continue：跳过

```c
#include <stdio.h>
#define GOLD 1000

int main(void) {
	int rush = 0;
	while (rush <= GOLD) {

		if (rush == 500) {
			printf("挖到铁矿，扔掉不要！\n");
			rush++;//碰到不挖了，跳下一个
			/*满足一定要求的时候，如果使用continue语句，就代表
			我不要满足条件中的内容，但是我还是要继续干（还是要
			继续执行循环，但是要注意，一定要在continue之前rush++）*/
			continue;
		}

		printf("已经跑了%d米\n", rush);
		rush += 1;
	}
	printf("1000米跑完了！\n");

	return 0;
}

```
==注意不要遗漏自增变量==，挖到了不加的话rush就一直在500循环，+1继续就可以跳出if循环

---

# break：中断
只能断离他最近的那一层while循环

---

# continue和break总结
==continue和break只能在循环中使用==
break还可以在switch语句中使用

---

# do...while语句（工作很少用）
==先干活（循环），再判断==，若为true，继续do-while循环
与while的区别:
>while(){}
>do{}while;

==有分号！==

### 简单举个例
```c
#include <stdio.h>
#define GOLD 1000

int main(void) {
	int rush = 1;
	do
	{
		rush++;
		printf("rush = %d\n", rush);

	}while(rush <= 1000);//记得这里加分号！
	
	return 0;
}
```

---

# for循环(比while灵活些)
先来过一遍循环三要素（非必选，若没有可能会出问题，除非是业务要求）
1. 初始化的变量
2. 判断条件（满足或不满足）
3. 自增衡量变量
```c
#include <stdio.h>
#define GOLD 1000

int main(void) {
	int rush;
	//C primer Plus 定义变量不赋值叫“声明”
	for (rush = 1; rush <= GOLD; rush++)
	{
		printf("rush = %d\n", rush);
	}
	printf("挖完了！\n");

	return 0;
}
```
for循环，**第一个分号前面的东西只会执行一次**，通常拿来初始化值
>rush = 1

**第二个分号前面内容执行完后，会先执行大括号内内容，再到第三个分号前面内容**

上述流程执行完后，会执行第一个分号到第二个分号内容，即：判断-执行-增加
判断失败，==直接跳出for循环==

---

# 调试：监听变量每一步是怎么执行的
## 关于使用
调试前先打断点，程序会执行到断点前面，剩下的靠你操作

在第8行前打点，调试开始后按下F11（逐语句执行）开始执行第8行，箭头指向下一行

鼠标可以停在变量上看看它现在值是多少

printf输出每步结果，没有调试工具时要善于利用printf查看每步执行结果
说白了，**输出也是一个不错的“调试工具”**

## 示例
```javascript {.line-numbers}
#include <stdio.h>

int main(void) {
	int index;
	int sum = 0;

	for (index = 0; index < 10; index++) {
		sum += index;
		printf("index = %d, sum = %d\n", index, sum);
	};
	return 0;
	}
```

## 关于效率
==调试完把输出窗口关闭！==

==bug修复完把断点去掉！==**不然会影响运行效率**

==诊断工具没事儿就关掉，耗内存！==，所以没事儿也别点那个已用时间多少ms的灰色字体

# for嵌套
*for、while、do...while都是可以嵌套使用的*

## 演示

在6~11行加断点调试，f11发现第一层for循环进行完之后，会先把第二层for循环进行完，再继续第一层下一次的for循环

再复习一遍执行顺序（按照序号顺序执行）
![](images/2022-08-02-18-04-42.png)

```javascript {.line-numbers}
#include<stdio.h>

int main(void)
{
	int row, column;
	for (row = 1; row <= 9; row++) {
		for (column = 1; column <= 9; column++) {
			printf("%d*%d=%2d\t", row, column, row* column);//%d是一位数，%2d是两位数，这里要注意一下
		}
		printf("\n");//一行column执行完后换下一行
	}

	return 0;
}
```

# 函数：一个复合的，能重复使用的工具
**函数讲究通用性**

## 示例一
```javascript {.line-numbers}
#include<stdio.h>

//main主函数，整个程序的入口点 

//要写一个函数，首先要预定义（预声明）
//声明函数
void sum(int number_1, int number_2);

//函数名：sum
//函数的返回值类型：void
//函数的参数：有两个参数，参数的类型都是int类型
//参数名

int main(void)
{
	sum(96,97);
	return 0;
}

//定义函数
//大括号内的叫函数体
void sum(int number_1, int number_2) {
	printf("Please input your two numbers,(type int,space):\n");
	scanf_s("%d %d", &number_1, &number_2);//这里要注意""的位置和&的添加
	printf("sum=%d\n", number_1 + number_2);
}

```

## 示例二
```javascript {.line-numbers}
//建议通过调试复习执行步骤
#include<stdio.h>
//声明函数
//形参——形式参数
//只有定义或者声明函数的时候，那里的参数才叫实参
int sum(int num1, int num2);
//函数名：sum
//函数的返回值类型：int
//函数的参数：有两个参数，参数的类型都是int类型
//参数名

int main(void) {
	//使用函数---调用函数
	//实参——实际参数（具体的值，输入的值）
	//调用方这边的参数，一定是实参
	int num1, num2;
	printf("输入两个数，中间空格隔开以计算和\n");
	scanf_s("%d %d", &num1, &num2);
	int result = sum(num1, num2);
	printf("result=%d\n", result);
	return 0;
}
//定义函数
//大括号内叫函数体
int sum(int num1, int num2) {
	int score_sum = num1 + num2;
	return score_sum;
}


```

void：什么都不返回
如果是void main()，那就不用写return 0
函数开始时怎么声明的，后面就怎么定义
函数类型一一对应
再强调一遍：==scanf_s后面记得加地址！==

# 函数作用域
辅助理解：域，一个国，上面示例二12行main是一个国，25行sum是另一个国。
一个函数（国家）不能调用另一个函数（国家）的作用域（户口本），因为这个户口本（作用域）没有登记这个人口（如sun_flower）
**也就是说在哪个大括号中定义的变量，只能在这个大括号中访问**

**若想几个函数共用一个变量，请把它定义在函数外面**，此时它不属于任何国家，它属于地球 
## 示例