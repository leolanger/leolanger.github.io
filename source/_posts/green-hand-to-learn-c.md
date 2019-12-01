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

	1. ### C++语句
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
	 	1. **赋值语句**  
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
	 	1. **cout的新花样**  
	    在本节最开始的程序中,有用cout来打印变量,该变量的值是一个整数:  
	    ` cout << carrots; `  
	    程序并没有打印"carrots",而是打印了储存在其中的值.该语句其实把两个操作合并了:首先把carrots替换为其当前值,再把值转化为合适的输出**字符**(在打印之前将整数形式的数字转换为字符串形式).
	2. ### 其他C++语句
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
2. ## 处理数据  
	>  面向对象编程的本质是设计并扩展自己的数据类型.在创建自己的类型之前,必须了解C++内置的类型.  
	内置的C++类型分为:基本类型和复合类型.  
	1. ### 简单变量
		1. **变量名**  
		   (命名方案与C语言较为相似)但是以两个下划线或下划线和大写字母打头将被保留给实现(编译器自带的名称)使用,将导致结果的不确定性.
		2. **整型**  
		3. **整型short,int,long,long long**  
		   (这两节参考C语言,暂省略)  
		   C++有C语言没有的初始化语法  
		   `int owls = 101；		// traditional C initialization, sets owls to 101 `
		   `int werns(142)；	//alternative C++ syntax,set werns to 432`
		   `int hamburgers = {24};  // set hamburgers to 24`  
		   `int emus{7;	//set emus to 5`  
		   `int rheas = {12}; // set rheas to 12`  
		   `int rocs = {};	//set rocs to 0`  
		   `int psychis{};	//set psychis to 0`  
		4. **无符号类型**  
		   在这讨论超越限制的情况.[image](~/leolanger/图片/Screenshot_20191129_215530.png)
		5. **选择整型类型**  
		6. **整型字面值**  
		   (参考C表示进制)  
		   ```Cpp
		   #include <iostream>
		   int main()
		   {
		      using namespace std;
		      int chest = 42;	//decimal integer literal
		      int waist = 0x42;	//hexadecimal integer literal
		      int inseam = 042;	// octal integer literal
		      cout << "Monsieur cuts a striking figure!\n";
		      cout << "chest = " << chest << : (42 in decimal)\n";
		      cout << "waist = " << waist << " (0x42 in hex)\n";
		      cout << "inseam = " << inseam << " (octal for 42)\n";
		      return 0;
		   }
		   
		   output:
		   	Monsieur cute a striking figure!
				chest = 42 (42 in decimal)
				waist = 66 (0x42 in hex)
				inseam = 34 (042 in octal)
			```
			在默认情况下,cout以十进制格式显示整数,而不管这些整数在程序中如何书写.  
	但是,在头文件iostream,中提供了控制符dec,hex和oct用以输出不同进制显示的整数.
			```Cpp
		   #include <iostream>
		   int main()
		   {
		      using namespace std;
		      int chest = 42;
		      int waist = 42;
		      int inseam = 42;	
		      cout << "Monsieur cuts a striking figure!\n";
		      cout << "chest = " << chest << : (decimal for 42)\n";
		      cout << hex;	//manipulator for changing number base
		      cout << "waist = " << waist << " (hexadecimal for 42)\n";
		      cout << oct;	//manipulator for changing number base
		      cout << "inseam = " << inseam << " (octal for 42)\n";
		      return 0;
		   }
		   output :
		   Monsieur cuts a striking figure!
		   chest = 42 (decimal for 42)
		   waist = 2a (hexadecimal for 42)
		   inseam = 52 (octal for 42)
	 		```  
		 7. **C++如何确定常量的类型**
	  	 `cout << "Year = " <<1492 << "\n";`  
	  	 程序会把1492存储为int型.  
	  	 而将整型常量存储为其他类型的条件:
	   		* 使用特殊后缀来表示特定类型
			* 值太大  
		8. **char类型:字符和小整数**  
	   	其内部通过ASCII码存储字符,因此char类型是另一种整型,可以用做比short更小的整型.一般定义为char类型时:输入字符,cout将字符转化为数字编码；输出时cin再转化为字符.
	 	  ```Cpp
	 	  #include <iostream>
	 	  int main ( )
	  	 {
	   	   using namespace std;
	    	  char ch;
	   	   cout << "Enter a character: " <<endl;
	   	   cin >> ch;
	   	   cout << "Hola! ";
	   	   cout << "Thank you for the "" << ch << " charcater." << endl;
	    	  return 0;
	 	  }
	 	  output:
	  	 Enter a character:
	 	  M
	 	  Hola! Thank you for the M charcater. 
	  	 ```
	  	 但是如果将M的ASCII码,存储在int类型中,将输出77(cout将显示两个字符7).
	  	 ```Cpp
	 	  #include <iostream>
	 	  int main( )
	 	  {
	  	    using namespace std;
	    	  char ch ='M';	//assign ASCII code for M to ch.
	    	  int i = ch;	//store same code in an int.
	    	  cout << "The ASCII code for " << ch << " is " << i << endl;
	    	  //using the cout.put() member function to display a char
	    	  cout << "Displaying a char ch using cout.put(ch): ";
	   	   cout.put(ch);
	   	   cout.put('!');
	   	   return 0;
	 	  }
	  	 output:
	   	The ASCII code for M is 77
	   	Displaying char ch using cout.put(ch): M!
	  	 ```
	   	* 成员函数cout.put()  
		  cout.put()是一个重要的面向对象概念---成员函数的例子.类定义了如何表示和控制数据:其中类也定义了一个个函数(即成员函数).类中的数据或函数只能通过类的对象来使用.在使用时需加上'.'句点即成员运算符.(详细在之后讲).
		* char字面值  
		  在C++中对于常规字符,最简单的方法是将字符用单引号括起,这种表示法代表的是字符的数值编码.对于无法表示的字符可以用转义序列(同C).
		9. **bool**类型  
		  在计算中其值可以是true或false.
		  `bool is_ready = true；`  
		  字面值true和false可以转化为int类型,true转换为1,false转换为0.  
		  `int ans = true;	//ans assigned 1`  
		  任何数字值和指针值都可以被隐式转换为bool值.零值为false,其余为true.  
	2. ### const限定符  
	   应在声明中就对const进行初始化.以下代码不好:  
	   `const int toes；`  
	   `toes = 10；	//too late`  
	   这种情况,常量的值不确定,且无法修改.  
	   (暂时省略)
	3. ### 浮点数
		1. **书写浮点数**  
		2. **浮点类型**
		3. **浮点常量**
		4. **浮点数的优缺点**  
		   (暂时省略)
	4. ### C++算数运算符  
		1. **运算符优先级和结合型**
		2. **除法分支**
		3. **求模运算符**
		4. **类型转换**  
			1. 初始化和赋值时进行的转换  (暂省)
			2. 以{}方式初始化时进行的转换  
			   C++11将这种初始化成为列表初始化,因为这种初始化常用于给复杂的数据类型提供值列表.这种方式下赋值时不允许缩窄,例不允许将浮点型转换为整型.
			3. 表达式中的转换
			4. 传递参数时的转换
			5. 强制类型转换
3. ## 复合类型
	   
	
	      
	 
	
	

