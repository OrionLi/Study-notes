# 注意事项
## 关于VS2022上的C项目
### main
一个软件只能有一个main（因为main是启动点），所以把另一个源文件的命名为main_1，新建项目的话就不会影响了

### 操作
==记得按ctrl+s保存==

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
### 基本格式
```c
if ( /*条件*/ ) { //就去执行某个东西
}
```

==如果不带大括号，if的范围只有它这一行和它的下一行==
### 示例
![](images/2022-08-01-15-09-04.png)

### 关系符的嵌套使用关系到程序的可读性
```c
if((age >= 18) && (english_score >= 90 || IQ >= 120)){printf("成年，允许玩！\n")};
```
### “非”的使用
```c
if(!(age >= 18) || !(english_score >= 90 || IQ >= 120)){printf("成年，允许玩！\n")};
```
---
# else的使用
==else总会找离他最近的if做匹配==

---

# 用户的不合法输入
原因是程序的不严谨
### 示例（会产生负数转换出错的bug，待修正）
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
### 示例
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

# do...while语句
