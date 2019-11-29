---
title: green hand to learn c++
date: 2019-11-13 22:48:37
tags: c++
categories: programming

---





#                                 c++

## ~~作者~~菜鸟序

虽然我很菜,但是毕竟也学过了一点c语言,所以和c比较相似的内容就简略了.

<!--more-->

1. ## 开始学习c++

   *    注:(1)c++对大小写敏感,所以在编写程序时要注意区分大小写；(2)     在c++中也可以使用c的输入和输出函数,只需头文件包括stdio.hjike.

        ##### 1.main()函数  
    	(暂时省略)

        #####  2.c++注释

     	以//打头,到行尾结束 ​				

        ##### 3.c++预处理器以及iostream文件

        ​	(暂时省略)    使用cin和cout函数时必须包括头文件iostream.  

        ##### 4.头文件名

        ​  (暂时省略)   包括对c语言风格的改变

        ##### 5.名称空间(此乃c++特性)

        ​如果使用iostream,而不是iostream.h,则应该在函数体中使用下面的名称空间编译指令来使iostream中的定义对程序有用:`using namespace std;`

        eg:  
          `Microflop::wanda("go dasncing?");     //use Microflop namespace version      
	   Piscine::wanda("fish named Desie");    //use Piscine namespace version`   
   
        这两种情况是两个以封装好的产品包含一个名字相同的函数,运用名称空间可以区分不同的版本.
 因此定义在iostream中的用于输出的cout变量实际上是std::cout,为了在每次输得时候省略名称空间,在主程序前加上  using namespace std;
	
        ##### 6.使用cout进行C++输出  
		`cout <<"Come up and C++ me some time."；`  
		在该语句中双引号括起得部分叫做字符串(同c).<<符号表示把字符串发送给cout--该符号指出了信息流动得路径.  
		cout是一个预定义的对象,其对象属性包括一个插入运算符(<<),它可以将其右侧的信息插入到流中；然后cout进行输出.(对于对象之后进行讨论).
		* 控制符 endl  
		  endl表示重启一行:在输出流中插入endl将导致屏幕光标移到下一行开头.如果没有endl,每条cout语句的输出从前一个输出的,末尾开始.
		* 换行符  
		  即"\n";
		##### 7. C++源代码的格式化  
		(暂时省略)  

2. ## C++语句
	* ```Cpp
	  #include <iostream>
	  int main()
	  {
	 	 using namespace std;
	  	int carrots;
	  	 carrots = 25;
	  	cout << "I have ";
	 		 cout << carrots;    //display the value to the variable
	  	cout << " carrots.";
	  	cout <<endl;
	 		 carrots = carrots - 1;
	 		 cout << "Crunch, crunch. Now I have " << carrots << " carrots." << endl;
	  	return 0;
	  }
	  
	 输出:
	 I have 25 carrots.  
	 Crunch, crunch. Now I have 24 carrots.
	 1. **声明语句和变量**  
	    (见C语言)
	 2. **赋值语句**  
	    C++可以连续使用赋值运算符(与C不同).  
	    eg:
   	    ```Cpp
	       int steinway;
	       int baldwin;
	       int yamaha;
	       yamaha = baldwin = steinway =88;
	       ```
	    该代码是合法的.  
	    此时赋值从右向左进行.
	 3. **cout的新花样**  
	    在本节最开始的程序中,有用cout来打印变量,该变量的值是一个整数:  
	    ` cout << carrots; `  
	    程序并没有打印"carrots",而是打印了储存在其中的值.该语句其实把两个操作合并了:首先把carrots替换为其当前值,再把值转化为合适的输出**字符**(在打印之前将整数形式的数字转换为字符串形式).
3. ## 其他C++语句
	* ```Cpp
	   eg:
	     #include <iostream>
	     int main()
	     {
	     	using namespace std;
			int carrots;
			cout << "How many carrots do you have?" << endl;
			cin >> carrots;		//C++ input
			cout << "Here are two more. ";
			carrots = carrots +2;
			cout << "Now you have " << carrots << "carrots." << endl;
			return 0;
		}
		```
		程序运行情况:  
		How many carrots do you have?  
		12  
		Here are two more. Now you have 14 carrots.
	1. **使用cin**  
	   `cin >> carrots;`  
	   C++将输入看作是流入程序的字符流.cin则为一个表示这种流的对象.输入时,cin 用>>运算符从输入流中抽取**字符**(类似cout),通常在右侧提供变量接受抽取的信息.
	2. **使用cout进行拼接**  
	   以下三种方式都可行  
	   * `cout << "Now you have " << carrots << " carrots." << endl;`
	   * ```Cpp
	     cout << "Now you have ";
	     cout << carrots;
	     cout << " carrots.";
	     cout << endl;
	     ```
	   * ```Cpp
	     cout << "Now you have "
	          << carrots
		      << " carrots."
		      << endl;
	     ```
	3. **类简介**  
	   详见[C++ Primer Plus 2.3.3](~/下载/C++)
	4. **函数**  
	   * (在这介绍简单的基础知识,在之后详细讨论)  
	     (大致与C语言相同)  
	     有稍微一点不同:在描述函数原型时可以` double pow(double, double);` 在参数表内可以不写参数的变量名,只写参数的数据类型.但是在函数头内要写.  
	   * 在多函数程序中使用using编译指令  
	     将编译指令放在所有函数的外面,且位于函数的前面.
	    
	    

