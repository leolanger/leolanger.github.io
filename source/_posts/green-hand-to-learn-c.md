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
          `Microflop::wanda("go dasncing?");     // use Microflop namespace version      
	   Piscine::wanda("fish named Desie");    // use Piscine namespace version`   
   
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
	 			 cout << carrots;    // display the value to the variable
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
			cin >> carrots;		// C++ input
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
		   `int werns(142)；	// alternative C++ syntax,set werns to 432`
		   `int hamburgers = {24};  // set hamburgers to 24`  
		   `int emus{7;	// set emus to 5`  
		   `int rheas = {12}; // set rheas to 12`  
		   `int rocs = {};	// set rocs to 0`  
		   `int psychis{};	// set psychis to 0`  
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
		      int chest = 42;	// decimal integer literal
		      int waist = 0x42;	// hexadecimal integer literal
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
		      cout << hex;	// manipulator for changing number base
		      cout << "waist = " << waist << " (hexadecimal for 42)\n";
		      cout << oct;	// manipulator for changing number base
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
	    	  char ch ='M';	// assign ASCII code for M to ch.
	    	  int i = ch;	// store same code in an int.
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
		  `int ans = true;	// ans assigned 1`  
		  任何数字值和指针值都可以被隐式转换为bool值.零值为false,其余为true.  
	2. ### const限定符  
	   应在声明中就对const进行初始化.以下代码不好:  
	   `const int toes；`  
	   `toes = 10；	// too late`  
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
	1. ### 数组  
	   (类似C)
	2. ### 字符串  
		* C-风格的字符串(暂时省略)
		1. **拼接字符串常量**  
		   以下语句是等价的:  
		   `cout << "I'd give my right arm to be" " a great violinist.\n";`  
		   `cout << "I'd give my right arm to be a great violinist.\n";`  
		   `cout << "I'd give my right ar"`  
		   `"m to be a great violinist.\n";`  
		2. **在数组中使用字符串**  
		   有两种办法:将数组初始化为字符串常量,将建盘或文件输入读入到数组中.  
		   ```Cpp
		   #include <iostream>
		   #include <cstring>	//for the strlen() function
		   int main()
		   {
		      uising namespace std;
		      const int size = 15;
		      char name1[size];
		      char name2[size] = "C++owboy";
		      cout << "Howdy! I'm " << name2;
		      cout << "! What's your name?\n";
		      cin >> name1;
		      cout << "Well, " << name1 << ", your name has ";
		      cout << strlen(name1) << " letters and is stored\n";
		      cout << "in an array of " << sizeof(name1) << "bytes.\n";
		      cout << "Your initial is " << name1[0] << ".\n";
		      name2[3] = '\0';
		      cout << "Here are the first 3 characters of my name: ";
		      cout << name2 << endl;
		      return 0;
		   }
		   
		   output:
		   Howdy! I'm C++owboy! What's your name?
		   **Basicman**
		   Well, Basicman,your name has 8 letters and is stored
		   in an array of 15 bytes.
		   Your initial is B.
		   Here are the first 3 characters of ma name: C++.
		   ```
		   在该程序中strlen()函数返回储存在数组中字符串的长度并且不把空子符计算在内.在输出字符串时遇到空字符就停止.  
		3. **字符串输入**  
		   但前面的程序存在一个缺陷.  
		   ```Cpp
		   #include <iostream>
		   int main()
		   {
		      using namespace std;
		      const int arsize = 20;
		      char name[arsize];
		      char dessert[arsize];
		      cout << "Enter your name:\n";
		      cin >> name;
		      cout << "Enter your favorite dessert:\n";
		      cin >> dessert;
		      cout << name << " like " << dessert << " .\n";
		      
		      output:
		      Enter your name:
		      **Alistair Dreeb**
		      Enter your favorite dessert:
		      Alistair like Dreeb.
		      ```
		      我们甚至没有对输入甜点的提示作出反应,程序便显示了出来,然后立即显示最后一行.因为cin使用空白(空格,制表符和换行符)来确定字符串结束的位置,所以cin读取字符时只读取一个单词.读取后,cin将该字符放到数组中,并在结尾自动添加空字符.  
		4. **每次读取一行字符串输入**  
			1. 面向行的输入: getline()  
			getline()函数读取整行,使用通过回车键输入的换行符来确定输入结尾.调用这种方法,可以使用cin.getline().该函数中有两个参数,第一个是存储输入行的数组的名称,第二个是要读取的字符数(包括空字符).例:`cin.getline(name,20)；`  
			```Cpp
		   #include <iostream>
		   int main()
		   {
		      using namespace std;
		      const int arsize = 20;
		      char name[arsize];
		      char dessert[arsize];
		      cout << "Enter your name:\n";
		      cin.getline(name,arsize);
		      cout << "Enter your favorite dessert:\n";
		      cin.getline(dessert,arsize);
		      cout << name << " like " << dessert << " .\n";
		      
		      output:
		      Enter your name:
		      **Alistair Dreeb**
		      Enter your favorite dessert:
		      **Radish Torte**
		      Alistair Dreeb like Radish Torte.
		      ```
		      getline()函数通过换行符来确定行尾,但不保存换行符,而用空字符来替换换行符.
		      2. 面向行的输入:get() 
		         与getline()不同的是,get虽然通过换行符来判断是否结束,但是不再读取并丢弃换行符,而是将其留在输入队列中.  
			 `cin.get(name,15);`  
			 `cin.get(dessert,15);`  
			 在这种情况下,第二次调用时看到的第一个字符便是换行符,认为以到达行尾.  
			 因此可以在这两个语句中间加上不带任何参数的cin.get()来读取换行符.
			 或者可以用`cin.get(name,15).get();`将两个类成员函数拼接起来.同样的cin.getline()也可如此使用.
			3. 空行和其他问题(暂时省略)
		5. **混合输入字符串和数字**  
		   ```Cpp
		   #include <iostream>
		   int main()
		   {  
		      uisng namespace std;
		      cout << "What year was your house built?\n";
		      int year;
		      cin >> year;
		      cout << "What is its street address?\n";
		      char address[80];
		      cin.getline(address,80);
		      cout << "Year built: " << year << endl;
		      cout << "Address: " << address << endl;
		      cout << "Done!\n";
		      return 0;
		   }
		   
		   output:
		   What year was your house built?
		   **1966**
		   What is its street address?
		   Year built: 1966;
		   Address
		   Done!
		   ```
		   用户根本没有输入地址的机会.因为在读取年份时,回车键产生的换行符留在了输入队列中.后面的get.getline()将认为是一个空行.因此在cin >> year；之后加上cin.get()或(cin >> year).get()；
	 3. ### string类简介
	  	* C++添加了string类型的变量,来储存字符串.string类型变量包含在头文件string中.   
	  	```Cpp
	  	#include <iostream>
	  	#include <string>
	 	 int main()
	 	 {
	  	    using namespace std;
	 	    char charr1[20];
	  	    char charr2[20] = "jaugar";
	   	    string str1;
	   	    string str2 = "panther";
	   	    cout << "Enter a kind of feline: ";
	        cin >> charr1;
	   	    cout << "Enter another kind of feline: ";
	        cin >> str1;
	        cout << "Here are some felines:\n";
	        cout << charr1 << " " << charr2 << " " << str1 << " " << str2 << endl;
	        cout << "The third letter in " << charr2 << " is " << charr2[2] << endl;
	        cout << "The third letter in " << str2 << " is " << str2[2] << endl;
	        return 0;
	      }
	      
	        output:
	        Enter a kind of feline: **ocelot**
	        Enter another kind of feline: **tiger**
	        Here are some felines:
	        ocelot jaguar tiger panther
	        The third letter in jaguar is g
	        the third letter in panther is n
	    ```
	 	 可以用C风格字符串来初始化string对象；可以用cin来键盘输入储存到string对象中；可以用cout来显示string对象；可以使用数组表示法来访问存储在string对象中的字符.  
	  主要区别是可以将string对象声明为简单变量而不是数组. 
	  	1. **C++11字符串初始化**  
		   允许使用列表初始化.
		2. **赋值,拼接和附加**  
		   有些操作string类比数组更简单,例不能将一个数组赋给另一个数组,但可以将一个string对象赋给另一个string对象.  
		   同样对于字符串的合并可以使用'+'将两个string对象合并起来,也可以使用'+='将字符串附加到string对象的末尾.
		3. **string类的其他操作**  
		   在C++中可以用size()这个成员函数来计算字符串大小,用法:`int len1 = str1.size()；	// 计算str1的大小`  
		   赋值,合并的用法上一小节讲过,另外在合并过程中string类具有自动调整大小的功能.
		4. **string类 I/O**  
		   读取一行而不是一个单词时,使用的句法不同.
		   ```Cpp
		   #include <iostream>
		   #include <string>
		   #include <cstring>
		   int main()
		   {
		      using namespace std;
		      char charr[20];
		      string str;
		      cout << "Length of string in charr before input: " << strlen(charr) << endl;
		      cout << "Length of string in str before input: " << str.size() << endl;
		      cout << "Enter a line of text:\n"
		      cin.getline(charr,20);
		      cout << "You entered: " << charr <endl;
		      cout << "Enter antohr line of text: \n";
		      getlinr(cin,str);
		      cout << "You entered: " << str << endl;
		      cout << "Length of string in charr after input: " << strlen(charr) << endl;
		      cout << "Length of string instr after input: " << str.size() << endl;
		      return 0;
		   }
		   
		   output:
		   "Length of string in charr before input: 27
		   "Length of string in charr before input: 0
		   Enter a line of text
		   **peanut butter**
		   You entered: peanut butter
		   Enter another line of text:
		   **blueberry jam**
		   You entered: blueberry jam
		   Length of string in charr after input: 13
		   Length of string in str after input:13
		   ```
		   程序说明:再输入前,数组charr中字符串的长度为27,是因为未初始化的数组的内容是随机的,并且strlen计算到空字符为止.而未被初始化string对象长度被自动设置为0.  
		   将一行输入读取到数组中的代码,在这不多说了.而将一行输入读取到string对象中的代码:`getline(cin,str)；`这里没有句点表示法,表明这个getline()不是类方法.它将cin作为参数,指出到哪里去查找输入.另外,因为string对象将按字符串长度自动调整自己的大小,所以没有长度参数.  
		5. **其他形式的字符串字面值**  
		   (暂时省略)
	4. ### 结构简介(即结构体)  
		* 在C++中关键字struct可以省略.
		1. **在程序中使用结构体**
		   ```Cpp
		   #include <iostream>
		   struct inflatable 	// structure declaration
		   {
		      char name[20];
		      float volume;
		      double price;
		   };
		   int main()
		   {
		      using namespace std;
		      inflatable guest =
		      {
		         "Glorious Gloria",
			     1.88,
			     29.99
		      };
		      inflatable pal = 
		      {
		         "Audacious Arthur",
			     3.12,
			     32.99
		      };
		       cout << "Expand your guest list with " << guest.name;
		       cout << " and " << pal.name << "!\n";
		       cout << "Your can have both for $";
		       cout << guest.price + pal.price << "!\n";
		       return 0;
		   }
		   
		   output:
		   Expand your guest list which Glorious Gloria and Audacious Arthur!
		   You can have both for $62.98!
		   ```
		   (因与C类似,暂时省略)
		2. **C++11结构初始化**  
		   支持列表初始化用于结构体.
		3. **结构体可以将string类作为成员**
		4. **其他结构属性**  
		   可以将结构体作为参数传递给函数(结构体相当于一个新的数据类型).另外可以用赋值运算符( = )将结构体赋给另一个同类型的结构体,即使成员是数组.
		5. **结构数组**(与C类似,暂时省略)
		6. **结构体中的位字段**  
		   (与C类似 )
	5. ### 共用体
		   
	  
	 
	

