# 									c语言

## 1. 常用指令

1. sudo apt-get  update // 更新最新资源地址  (sudo 为使用管理员权限)

2. sudo apt-get  inatall vim //安装vim

3. cc -v 或gcc -v // 检查编译器

4. pwd // 当前目录

5. #include <库名> // 导入库

   如： #include <stdio.h> // 导入stdio.h库  

   stdio.h // 标准输入输出流

   #include + <>  表示操作系统预装的库 	表示在系统目录或环境变量目录下

   #include + "" 表示在当前项目目录中查找

   

6. –rwxr-xr-x  执行权限/home/yao/图片/执行.png![执行](/home/yao/图片/执行.png)

7. vim同时打开多个文件命令 

   如 （：sp max.c）ctrl+w+上下方向键    为切换文件

8.  :wqa 保存所以u文件并推出

9. gcc 文件名1 文件名2 -o 需要输出的文件名 如：gcc a.c b.c -o main.out

10. cat 文件名  表示查看文件内容 

11. gcc -c max.c -o max.o  编译为max.o文件   有利于代码执行速度

## 5. makeFile的编写与使用

1. 检查系统是否装载make    //   make -v

2. 安装方法： apt-get install make

3. 编译 

   如：# this is make file （#为注释）

   mian.out:max.o min.o main.c
           gcc max.o min.o main.c -o main.out
   max.o:max.c
           gcc -c max.c
   min.o:min.c
           gcc -c min.c

#### makeFile的编写与使用

1. gcc main.c -o main.out && ./main.out    //表示为在编译成功的基础上去执行
2. echo $?  查看程序是否正常执行，输出0为正常执行



## 6. main函数详解

### Linux C语言] main函数中的return 

### Linux C语言] main函数中的参数 *****

1. argc 是指命令行输入参数的个数，argv存储了所有的命令行参数

2. %d是[转义](https://www.baidu.com/s?wd=转义&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)符号，表示整数的意思，一般这样出现
   printf("%d",n);//其中n是[整型变量](https://www.baidu.com/s?wd=整型变量&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)，这样n就打印在屏幕上；

3. %d是[转义](https://www.baidu.com/s?wd=转义&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)符号，表示[十进制](https://www.baidu.com/s?wd=十进制&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)整数。
   在printf[函数](https://www.baidu.com/s?wd=函数&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)中表示以[十进制](https://www.baidu.com/s?wd=十进制&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)整数形式输出一个变量的值。

   &：是地址[操作符](https://www.baidu.com/s?wd=操作符&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)：取变量地址。
   &NUMBER是取变量NUMBER的地址。

4.  格式说明由“％”和格式字符组成，如％d％f等。它的作用是将输出的数据转换为指定的格式输出。格式说明总是由“％”字符开始的。 
   格式字符有d,o,x,u,c,s,f,e,g等。 
   如
   ％d整型输出，％ld长整型输出，
   ％o以八进制数形式输出整数，
   ％x以十六进制数形式输出整数，或输出字符串的地址。
   ％u以十进制数输出unsigned型数据(无符号数)。注意：%d与%u有无符号的数值范围，也就是极限的值，不然数值打印出来会有误。
   ％c用来输出一个字符，
   ％s用来输出一个字符串，
   ％f用来输出实数，以小数形式输出，默认情况下保留小数点6位。
   %.100f用来输出实数，保留小数点100位。
   ％e以指数形式输出实数，
   ％g根据大小自动选f格式或e格式，且不输出无意义的零。

## 7.  输入输出流和错误流

### 1. Linux C语言] 标准输入流输出流以及错误流 

#### 1. scanf()是C语言中的一个输入函数。与[printf](https://baike.baidu.com/item/printf/7467706)函数一样，都被声明在[头文件](https://baike.baidu.com/item/头文件/10978258)stdio.h里，因此在使用scanf函数时要加上#include <stdio.h>。（在有一些实现中，printf函数与scanf函数在使用时可以不使用预编译命令#include <stdio.h>。）它是格式输入函数，即按用户指定的格式从键盘上把数据输入到指定的变量之中。

#### 2. C 库函数 - scanf()

[![C 标准库 - ](https://www.runoob.com/images/up.gif) C 标准库 - ](https://www.runoob.com/cprogramming/c-standard-library-stdio-h.html)

##### 描述

C 库函数 **int scanf(const char \*format, ...)** 从标准输入 stdin 读取格式化输入。

##### 声明

下面是 scanf() 函数的声明。

```
int scanf(const char *format, ...)
```

##### 参数

- **format** -- 这是 C 字符串，包含了以下各项中的一个或多个：*空格字符、非空格字符* 和 *format 说明符*。

format 说明符形式为:

```
[=%[*][width][modifiers]type=]
```

具体讲解如下：

| 参数      | 描述                                                         |
| :-------- | :----------------------------------------------------------- |
| *         | 这是一个可选的星号，表示数据是从流 stream 中读取的，但是可以被忽视，即它不存储在对应的参数中。 |
| width     | 这指定了在当前读取操作中读取的最大字符数。                   |
| modifiers | 为对应的附加参数所指向的数据指定一个不同于整型（针对 d、i 和 n）、无符号整型（针对 o、u 和 x）或浮点型（针对 e、f 和 g）的大小： h ：短整型（针对 d、i 和 n），或无符号短整型（针对 o、u 和 x） l ：长整型（针对 d、i 和 n），或无符号长整型（针对 o、u 和 x），或双精度型（针对 e、f 和 g） L ：长双精度型（针对 e、f 和 g） |
| type      | 一个字符，指定了要被读取的数据类型以及数据读取方式。具体参见下一个表格。 |

**scanf 类型说明符：**

| 类型                   | 合格的输入                                                   | 参数的类型     |
| :--------------------- | :----------------------------------------------------------- | :------------- |
| %a、%A                 | 读入一个浮点值(仅 C99 有效)。                                | float *        |
| %c                     | 单个字符：读取下一个字符。如果指定了一个不为 1 的宽度 width，函数会读取 width 个字符，并通过参数传递，把它们存储在数组中连续位置。在末尾不会追加空字符。 | char *         |
| %d                     | 十进制整数：数字前面的 + 或 - 号是可选的。                   | int *          |
| %e、%E、%f、%F、%g、%G | 浮点数：包含了一个小数点、一个可选的前置符号 + 或 -、一个可选的后置字符 e 或 E，以及一个十进制数字。两个有效的实例 -732.103 和 7.12e4 | float *        |
| %i                     | 读入十进制，八进制，十六进制整数 。                          | int *          |
| %o                     | 八进制整数。                                                 | int *          |
| %s                     | 字符串。这将读取连续字符，直到遇到一个空格字符（空格字符可以是空白、换行和制表符）。 | char *         |
| %u                     | 无符号的十进制整数。                                         | unsigned int * |
| %x、%X                 | 十六进制整数。                                               | int *          |
| %p                     | 读入一个指针 。                                              |                |
| %[]                    | 扫描字符集合 。                                              |                |
| %%                     | 读 % 符号。                                                  |                |

- **附加参数** -- 根据不同的 format 字符串，函数可能需要一系列的附加参数，每个参数包含了一个要被插入的值，替换了 format 参数中指定的每个 % 标签。参数的个数应与 % 标签的个数相同。

##### 返回值

如果成功，该函数返回成功匹配和赋值的个数。如果到达文件末尾或发生读错误，则返回 EOF。

##### 实例

下面的实例演示了 scanf() 函数的用法。

##### 实例

\#include<stdio.h> int main(void)  {     int a,b,c;      printf("请输入三个数字：");    scanf("%d%d%d",&a,&b,&c);     printf("%d,%d,%d\n",a,b,c);    return 0;  }

让我们编译并运行上面的程序，这将在交互模式下产生以下结果：

```
请输入三个数字：1 2 3
1,2,3
```

解析说明：

- 1、**&a、&b、&c** 中的 **&** 是地址运算符，分别获得这三个变量的内存地址。
- 2、**%d%d%d** 是按十进值格式输入三个数值。输入时，在两个数据之间可以用一个或多个空格、tab 键、回车键分隔。

如果使用  , 相应的输入时也需要添加**,**

##### 实例

\#include<stdio.h> int main(void) {    int a,b,c;     printf("请输入三个数字：");    scanf("%d, %d, %d",&a,&b,&c);    printf("%d, %d, %d\n",a,b,c);    return 0; }

让我们编译并运行上面的程序，这将在交互模式下产生以下结果：

```
请输入三个数字：1, 2, 3
1, 2, 3
```

**注意：**输入时 **,** 前一定要紧跟在数字后面，数字与 **,** 之间不能有空格。

在用 %c 输入时，空格和"转义字符"均作为有效字符。

##### 实例

\#include<stdio.h> int main(void) {    char a,b,c;     printf("请输入三个字符：");    scanf("%c%c%c",&a,&b,&c);     printf("%c,%c,%c\n", a,b,c);    return 0; }

让我们编译并运行上面的程序，这将在交互模式下产生以下结果：

```
$ ./a.out 
请输入三个字符：run
r,u,n
$ ./a.out 
请输入三个字符：r u n
r, ,u
```

以下实例演示的是接收字符串：

##### 实例

\#include <stdio.h>  int main() {   char str1[20], str2[30];    printf("请输入用户名：");   scanf("%s", str1);    printf("请输入您的网站：");   scanf("%s", str2);    printf("输入的用户名：%s\n", str1);   printf("输入的网站：%s", str2);      return(0); }

让我们编译并运行上面的程序，这将在交互模式下产生以下结果：

```
请输入用户名：admin
请输入您的网站：www.runoob.com
输入的用户名：admin
输入的网站：www.runoob.com
```

[![C 标准库 - ](https://www.runoob.com/images/up.gif) C 标准库 - ](https://www.runoob.com/cprogramming/c-standard-library-stdio-h.html)

 [C 标准库 – ](https://www.runoob.com/cprogramming/c-standard-library-stddef-h.html)

[C 标准库 – ](https://www.runoob.com/cprogramming/c-standard-library-stdlib-h.html) 

##### 篇笔记 写笔记

1. 

     learner

    123***21@163.com

   0

   如上代码，报错：返回值被忽略: **"scanf"**

   解决方案：

   1）把 scanf 换为s canf_s

   2）在前面加上 **#pragma warning(disable:4996)**

   #### 3. 

   int main()

   {

   1. 标准输入流 // stdin   默认是键盘输入

      printf("plesse inout the value a :\n"); 是对fprintf(stdout,"plesse input  the value a :\n"); 的封装

   2. 标准输出流 //  stout    默认是显示器的终端   终端输出

      scanf("%d",&a); 是对 fscanf(stdin,"%d",&a); 的封装
      1. 标准错误流  // stderr    错误输出 

      ​	if(a<0){

      ​		fprintf(stderr,"the value must > 0");

      ​		return 1;

      ​	}

      return 0;

      }

   ### 2.  [Linux C语言] 输入流输出流以及错误流的重定向

   1. 重定向机制：

      （1）输入重定向：

      ./a.out 1>> a.txt  或./a.out >> a.txt    相当于将a.out显示的内容切换现实到a.txt文件中，不会覆盖原来的值

      ./a.out 1> a.txt  或./a.out > a.txt    相当于将a.out显示的内容切换现实到a.txt文件中，会覆盖原来的值

      （2）输出流重定向：

      ./a.out < a.txt    相当于将a.txt显示的内容作为需要输入的内容输入到a.out文件里面，也就是用a.txt中显示的内容替代键盘输入的内容。

      （3）错误流  如下 当j= 0 时 

      #include <stdio.h>

      int main()
      {
          printf("input the int value i:\n");
          int i,j;
          scanf("%d",&i);
          printf("input the int value j:\n");
          scanf("%d",&j);

      ​	if(0 != j){

      ​	    printf("%d / %d=%d\n",i,j,i/j);

      ​	}else{

      ​		fprintf(stderr,"j != 0\n");

      ​		return 1;

      ​	}

      return 0;

      }

   ## 8. [Linux C语言] 管道原理及应用 

   ### 1. 管道： ls /etc / | grep ab 中的竖线，

   ls /etc / | grep ab 表示在etc文件夹下面搜索包含ab的文件放入grep中

   

   ## 9.  [Linux C语言] 打造实用C语言小程序 

   

   

   

   

   

   

    

   

   

   

   

   

   







