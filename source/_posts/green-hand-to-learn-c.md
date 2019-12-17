---
title: green hand to learn c++
date: 2019-11-13 22:48:37
tags: c++
categories: programming

---




# ~~作者~~菜鸟序

虽然我很菜,但是毕竟也学过了一点c语言,所以和c比较相似的内容就简略了.

<!--more-->

1. ## 开始学习c++

   *    注:(1)c++对大小写敏感,所以在编写程序时要注意区分大小写；(2)     在c++中也可以使用c的输入和输出函数,只需头文件包括<stdio.h>.

           ##### 1.main()函数  
    	(暂时省略)

          #####  2.c++注释

       	以//打头,到行尾结束 ​				

           ##### 3.c++预处理器以及iostream文件

        ​	(暂时省略)    使用cin和cout函数时必须包括头文件iostream.  

           ##### 4.头文件名

          (暂时省略)   包括对c语言风格的改变

           ##### 5.名称空间(此乃c++特性)

        如果使用iostream,而不是iostream.h,则应该在函数体中使用下面的名称空间编译指令来使iostream中的定义对程序有用:`using namespace std;`

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
		 ```Cpp
		 #include <iostream>
		  int main()
		  {
	 		 using namespace std;
	 	 	int carrots;
	    		 arrots = 25;
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
		```

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
	2. ### 其他C++语句
		 ```Cpp
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
		程序运行情况:  
		How many carrots do you have?  
		12  
		Here are two more. Now you have 14 carrots.
		```
		1. **使用cin**  
	   `cin >> carrots;`  
	   C++将输入看作是流入程序的字符流.cin则为一个表示这种流的对象.输入时,cin 用>>运算符从输入流中抽取**字符**(类似cout),通常在右侧提供变量接受抽取的信息.
		2. **使用cout进行拼接**  
	      	 以下三种方式都可行
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
			* 其内部通过ASCII码存储字符,因此char类型是另一种整型,可以用做比short更小的整型.一般定义为char类型时:输入字符,cout将字符转化为数字编码；输出时cin再转化为字符.
			``` Cpp
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
	    	     // using the cout.put() member function to display a char
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
		10. **bool**类型  
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
				}
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
		(与结构体的关系和C中共用体与结构体的关系相似,因此暂时省略)
	6. ### 枚举
		使用枚举(enum)的句法与结构体相似:`enum spectrum {red,orange,yellow,green,blue,violet,indigo,ultraviolet};`  
		在这个语句中,让spectrum成为新的类型名称；同时将red,orange,yellow等作为符号常量,对应整数值0~7(当然也可以自己定义).  
		可以用枚举名称来声明这种类型的变量:`spectrum band;`  
		在不进行强转的情况下,只能将定义枚举时使用的量赋值给枚举变量:`band = 2000;`这是非法的.  
		另外对于枚举,只定义了赋值运算,没有算数运算.但尽管这样如`band = orange + red;`在算数表达式中,枚举会被转为整型,得出结果为1.但此时是整型,不能赋给band.  
		枚举量是整型,可以被提升为int类型,但int类型不能自动转为枚举类型:`int color = blue;`这是可行的；`band = 3;`这是不行的.
		1. **设置枚举量的值**
		2. **枚举的取值范围**  
		   (暂时省略)
	7. ### 指针和自由存储空间  
		(由于指针比较重要,将之后另开一篇,专门写指针)  
		1. **声明和初始化指针**
		2. **指针的危险**
		3. **指针和数字**  
		   不能将一个整数赋给指针,需要进行强转.
		4. **使用new来分配内存**  
			前面我们将指针初始化为变量的地址：变量是在编译时分配的有名称的内存，而指针只是为可以通过名称直接访问的内存提供的一个别名。指针真正的用武之地在于，在运行阶段分配未命名的内存以存储值。在这种情况下只能以指针来访问内存。在C语言中，可以用malloc()来分配内存；在C++中也可以这么做，但C++还有更好的选择--new运算符。  
			`int *pn = new int;`这表示：在运行阶段，为一个int分配分配未命名的内存，并用指针来访问这个值。程序员告诉为int类型分配内存；而new将找到一个长度正确的内存块，并返回地址。接下来将地址赋给pn，pn是被声明为指向int的指针。  
			术语“数据对象”比“变量”更通用，它指的是为数据分配的内存块。因此变量也是数据对象，但pn指向的内存不是变量。为一个数据对象（可以是结构，也可以是基本类型）获得并指定分配内存的通用格式如下：  
			`typeName * pointer_name = new typeName;`  
			```Cpp
			#include <iostream>
			int main()
			{
			    using namespace std;
			    int nights = 1001;
			    int * pt = new int;    // allocate space for an int
			    *pt = 1001;	     // store a value there
			    cout << "nights value = ";
			    cout << nights << ": location " << &nights << endl;
			    cout << "int ";
			    cout << "value = " << *pt << " : location = " << pt << endl;
			    double * pd = new double;
			    *pd = 10000001.0;
			    cout << "double ";
			    cout << "value = " << *pd << " : location = " << pd << endl;
			    cout << "location of pointer pd: " << &pd << endl;
			    cout << "size of pt = " << sizeof(pt);
			    cout << ": size of *pt = " << sizeof(*pt) << endl;
			    cout << "size of pd = " << sizeof(pd);
			    cout << ": size of *pd = " << sizeof(*pd) << endl;
			    return 0;
			}
			
			output:
			nights value = 1001: location 0028F7F8
			int value = 1001: location = 00033A98
			double value = 1e+007: location = 000339B8
			location of pointer pd: 0028F7FC
			size of pt = 4: size of *pt = 4
			size of pd = 4: size of *pd = 8
			```
			当然，内存位置的准确值随系统而异。  
			程序说明：  
			该程序使用new分别为int类型和double类型的数据对象分配内存，这是程序运行时进行的。  
			对于指针，需要另外指出，变量nights和pd的值都存储在栈里，而new从堆例分配内存。  
		5. **使用delete释放内存**
			当new申请的内存使用完后，需要用delete运算符释放内存。使用示例：  
			```Cpp
			int * ps = new int;
			······
			delete ps;
			```
			这将释放ps指向的内存，但不惠删除ps本身，可以将ps重新指向另一个新分配的内存。另外，一定要配对的使用new和delete，否则会发生内存泄漏。另外不能用得了特来释放声明变量（即不是new）所获得的内存
		7. **使用new来创建动态数组**  
		   如果通过声明来创建数组，则在程序 被编译时将为它分配内存空间，不管最终是否使用数组，数组都在那，占用了内存，这种方式叫做静态联编。但使用new，如果在运行阶段需要数组，则创建它；如果不需要，则不创建。还可以在程序运行时选择数组长度，这被称为动态联编.
			1. *使用new创建动态数组*
				创建动态数组，只要将数组的元素类型和元素数目告诉new即可。如果想创建一个包含10个int元素的数组，可以这样做:
				`int * psome = new int [10];`
				new运算符返回第一个元素的地址。在这个例子中，该地址被赋给指针psome.
				当使用完new分配的内存块时，应使用delete释放他们。对于new创建的数组，应使用另一种格式：
				`delete [] psome;`
				方括号告诉程序，应释放整个数组，而不仅仅是指针指向的元素.
				总之，使用new和delete时，应遵循以下规则：
				* 不要使用delete来释放不是new分配的内存。
				* 不要使用delete释放同一个内存两次（特别注意在用两个指针指向同一块内存的情况）。
				* 如果使用new[]为数组分配内存，则应使用delete[]来释放。
				* 如果使用new[]为一个实体分配内存，则应使用delete（没有方括号）来释放。
				* 对空指针应用delet是安全的。
			3. *使用动态数组*  
				方法一：把指针当作数组名使用即可。
				```Cpp
				#include <iostream>
				int main()
				{
				   using namespace std;
				   double * p3 = new double[3];
				   p3[0] = 0.2;
				   p3[1] = 0.5;
				   p3[2] = 0.8;
				   cout << "p3[1] is " << p3[1] << ".\n";
				   p3 = p3 + 1;
				   cout << "Now p3[0] is " << p3[0] << " and ";
				   cout << "p3[1] is " << p3[1] << ".\n";
				   p3 = p3 -1;
				   delete [] p3;
				   return 0;
				}
				
				output:
				p3[1] is 0.5.
				Now p3[0] is 0.5 and p3[1] is 0.8.
				```
				从这可以看数，数组名和指针之间的根本差别：  
				`p3 = p3 + 1；`  
				不能修改数组名的值（因为数组名是地址常量），但指针是变量。p3加1的效果就是将指向该数组的下一个元素。
		
	8. ### 指针、数组和指针算数  
		指针和数组基本等价的原因在于指针算数和C++内部处理数组的方式。首先，看一下算数，将整数变量加1后，其值将增加1；但将指针变量增加1后，增加的量等于它指向的类型的字节数。
		```Cpp
		#include <iostream>
		int main()
		{
		    using namespace std;
		    double wages[3] = {10000.0, 20000.0, 30000.0};
		    short stacks[3] = {3, 2, 1};
		    // Here are two ways to get the adress of an array
		    double * pw = wages;
		    short * ps = &stacks[0];
		    cout << "pw = " << pw << ", *pw = " << *pw << endl;
		    pw = pw + 1;
		    cout << "add 1 to the pw pointer:\n";
		    cout << "pw = " << pw << ", *pw = "<< *pw << "\n\n";
		    cout << "ps = " << ps << ", *ps = " << *ps << endl;
		     ps = ps + 1;
		    cout << "add 1 to the ps pointer:\n";
		    cout << "ps = " << ps << ", *ps = "<< *ps << "\n\n";
		    cout << "access two elements with array notation\n";
		    cout << "stacks[0] = " << stacks[0] << ",stacks[1] = " << stacks[1] << endl;
		    cout << "access two elements with pointer notation\n";
		    cout << "*stacks = " << *stacks << ",*(stacks + 1) = " << *(stacks + 1) << endl;
		    cout << sizeof(wages) << " = size of wages array\n";
		    cout << sizeof(pw) << " = size of pw pointer\n";
		    return 0;
		 }
		 
		 output:
		 pw = 0x28ccf0, *pw = 10000
		 add 1 to the pw pointer:
		 pw = 0x28ccf8, *pw = 20000
		 
		 ps = 0x28ccea, *ps = 3
		 add 1 to the ps pointer:
		 ps = 0x28ccec, *ps = 2
		 
		 acces two elements with array notation
		 stacks[0] = 3,stacks[1] = 2
		 access two elements with pointer notation 
		 *stacks = 3,*(stacks + 1) = 2
		 24 = size of wages array
		 4 = size of pw pointer
		```
		1. **程序说明**  
			数组名相当于第一个元素的地址。
		2. **指针小结**
			1. *声明指针*
			2. *给指针赋值*
			3. *对指针解除引用*
			4. *区分指针和指针所指向的值*
			5. *数组名*
			6. *指针算数*
			7. *数组的动态联编和静态联编*
			8. *数组表示法和指针表示法*
		3. **指针和字符串**
			```Cpp
			#include <iostream>
			#include <cstring>
			int main()
			{
			    using namespace std;
			    char animal[20] = "bear";
			    const char * bird = "wear";
			    char * ps;
			    cout << animal << " and ";
			    cout << bird << "\n";
			    cout << Enter a kind of animal: "
			    cin >> animal;
			    ps = animal;
			    cout << ps << "!\n";
			    cout << "Before using strcpy():\n";
			    cout << "animal << " at " << (int *)animal << endl;
			    cout << ps << "at " << (int *) ps << endl;
			    ps = new char[strlen(animal) + 1];
			    strcpy(ps, animal);
			    cout << "After using strcpy():\n";
			    cout << animal << " at " << (int *) animal << endl;
			    cout << ps << " at " << (int *) ps << endl;
			    delete [] ps;
			    return 0;
			}
			
			output:
			bear and wren
			Enter a kind of animal: **fox**
			fox!
			Before using strcpy():
			fox at 0x0065fd30
			fox at 0x0065fd30
			After using strcpy():
			fox at 0x0065fd30
			fox at 0x004301c8
			```
	   		* 程序说明（暂时省略）
	 	4. **使用new创建动态结构**  
		   	需要在程序运行时为结构分配所需的空间，也可以使用new运算符来完成。通过使用new，可以创建动态结构体。由于类与结构体非常相似，因此有关结构体的技术也适用于类。  
			例如，要创建一个未命名的inflatable类型，并将其地址赋给一个指针，可以这样做：  
			`inflatable * ps = new inflatable;`  
			比较棘手的是访问成员。创建动态结构体时，不能将成员运算符句点用于结构名，因为这种结构体没有名称，只是知道它的地址。此时应用箭头成员运算符（->)。另一种访问结构体成员的方法就是(*ps).price.
			1. *一个使用new和delete的示例*  
			   ```Cpp
			   #include <iostream>
			   #include <cstring>
			   using namespace std;
			   char * getname(void);
			   int main()
			   {
			       char * name;
			       name = getname();
			       cout << name << " at " << (int *) name << "\n";
			       delete [] name;
			       name = getname();
			        cout << name << " at " << (int *) name << "\n";
			       delete [] name;
			       return 0;
			   }
			   char  * getname()
			   {
			       char temp[80];
			       cout << Enter last name: ";
			       cin >> temp;
			       char * pn = new char[strlen(temp) + 1];
			       strcpy(pn,temp);
			       return pn;
			   }
			   
			   output:
			   Enter last name: Fredelddumpkin
			   Fredelddumpkin AT 0x004326b8
			   Enter last name: Pook
			   Pook at 0x004301c8
			   ```
			2. *程序说明*  
			        在getname()函数中,使用cin讲输入的单词放到temp数组中,然后使用new分配新内存,以存储该单词.
		6. **自动存储,静态存储和动态存储**  
			1. *自动存储*
				* (类似C的自动变量,自动变量通常存储在栈中)
			2. *静态存储*
				* 使变量成为静态的方法有两种:一种是在函数外面定义它；另一种是在声明变量时使用关键字static:  
				`static double fee = 56.50;`  
			3. *动态存储*
				* new和delete运算符提供了一种更灵活的方法.它们管理一个内存池,被称为自由存储空间或堆.且数据的生命周期不完全受程序和函数的生存时间控制.
	9. ### 类型组合  
	   	```Cpp
		#include <iostream>
		struct antarctica_years_end
		{
		    int year;
		}
		int main()
		{
		    antarctica_years_end s01, s02, s03;
		    s01.year = 1998;
		    antarctica_years_end * pa = &s02;
		    pa->year = 1999;
		    antarctica_years_end trio[3];
		    trio[0].year = 2003;
		    std::cout << trio->year << std::endl;
		    const antarctica_years_end * arp[3] = {&s01, &s02, &s03};
		    std::cout << arp[1]->year << std::endl;
		    const antarctica_years_end **ppa = arp;
		    auto ppb = arp;
		    std::cout << (*ppa)->year << std::endl;
		    std::cout << (*(pbb+1))->year << std::endl;
		    return 0;
		 }
		 
		 output:
		 2003
		 1999
		 1998
		 1999
		```
		 * 程序说明  
		    可以创建这种类型的变量:
		    `antarctica_years_end s01, s02, s03;`    
		    然后使用成员运算符访问其成员:
		    `s01.year = 1998;`  
		    结构体的指针:
		    `antarctica_years_end * pa = &s02;`  
		    将该指针设置为有效地址后,可以使用间接成员运算符来访问成员:
		    `pa->year = 1999;`  
		    创建结构体数组:
		    `antarctica_years_end trio[3];`  
		    使用成员运算符访问元素的成员:
		    `trio[0].year = 2003;`  
		    其中trio是一个数组,trio[0]是一个结构体,而trio[0].year是该结构体的一个成员.由于数组名是一个指针,因此也可以这样用:
		    `(trio+1)->year = 2003;  // same as trio[1].year = 2003;`  
		    创建指针数组:
		    `const antarctica_years_end * arp[3] = {&s01, &s02, &s03};`   
		    arp是一个指针数组,arp[1]就是一个指针,可以使用间接成员运算符来访问成员:
		    `std::cout << arp[1]->year << std::endl;`    
		    创建指向上述数组的指针:
		    `const antarctica_years_end **ppa = arp;`    
		    arp是一个数组的名称,因此它是第一个元素的地址,并且其第一个元素为指针,因此ppa是一个双重指针--指向一个指向const antarctica_years_end 的指针:
		    `std::cout << (*ppa)->year << std::endl;`    
		    但上面的办法很容易搞错,因此可以使用auto,编译器知道arp的类型,能够正确的推断出ppb的类型:
		    `auto ppb = arp;`  
		    `std::cout << (*(pbb+1))->year << std::endl;` 
	10. ### 数组的替代品
		1. **模板类vector**
			模板类vector类似于string类,也是一种动态数组.可以在运行阶段设置vector对象的长度,可在末尾附加新数据,还可在中间插入新数据.  
			这里只介绍一些基本的实用知识.首先,使用vector对象,必须包含头文件vector；其次,vector包含在名称空间std中.  
			```Cpp
			#include <vector>
			* * *
			using namespace std;
			vector<int> vi;
			int n;
			cin >> n;
			vector<double> vd(n);
			```
			其中,vi是一个vector<int>对象,vd是一个vector<double>对象.由于vector对象在插入或添加值时自动调整长度,因此可以先将长度设置为零,如要调长度需使用vector包中的方法(暂时省略).  
			一般而言,创建一个名为vt的vector对象,可存储出n个类型为typename的元素的示例:
			`vector<typename> vt(n);`  
		2. **模板类array**
			* vector功能强大,但是效率低下.因此新增类模板类array,它的长度固定,使用栈,效率与数组相同,但更方便,更安全.想使用array需要包含头文件array.  
			下面的声明创建一个名为arr的array对象,包含n个类型为typename的元素:`array<typename,n> arr;`  
		4. **比较数组,vector对象和array对象**
			* 数组在编写是有可能产生数组越界如:a[-1].vector和array也可以编写不安全的代码,但是可以使用成员函数at(),用于捕获非法索引.它们还包含begin()和end(),来确定边界,以免无意间越界.(在之后讨论)
4. ## 循环和关系表达式  
	1. ### for循环  
	   (与C相似部分省略)
		1. **for循环的组成部分**  
		   1. *表达式和语句*  
			   C++每个表达式都有值:28 *20 是值为560的表达式；x = 20 是值为20 的表达式；maids = (cooks = 3) + 4,表达式cooks = 3的值为3,因此maids的值是7；x<y将被判定为bool值true或false.  
				然而在语句中<<运算符优先级高于算数运算符,所以要使用括号.  
				从表达式到语句的转变很容易,只要加分号即可.
			2. *非表达式和语句*  
				虽然表达式加上分号变成语句,但不代表所有语句去掉分号就是表达式.
			3. *修改规则*  
				C++允许在for循环中初始化:`for (int i = 0; i< 5; i++);`这种变量只存在于for语句中.
		2. **回到for语句**  
		3. **修改步长**
		4. **使用for循环访问字符串**
		5. **递增运算符(++)和递减运算符(--)**
		6. **副作用和顺序点**
		7. **前缀格式和后缀格式**
		8. **递增/递减运算符和指针**
		9. **组合赋值运算符**
		10. **复合语句**
		11. **其他语法技巧---逗号运算符**
			C++中逗号表达式的值是右半部分的值.
		12. **关系表达式**
		13. **赋值,比较和可能犯的错误**
		14. **C风格字符串的比较**
		15. **比较string类字符**  
		    对于C风格的字符串只能用strcmp()进行比较,而string可以用关系运算符即可.
	2. ### while循环
		1. **for和while**
		2. **等待一段时间:编写延时循环**
			* 最早期的技术:  
			```Cpp
			long wait = 0;
			while (wait < 10000)
			    wait++;
			```
			但如果计算机处理器的速度过快,必须修改计数限制.  
			在C++库中,有一个函数clock(),返回程序开始执行后所用的系统时间.但是返回的时间单位不一定是秒,其次返回的数据类型不确定.  
			在头文件ctime中定义了一个符号常量---CLOCKS_PER_SEC,等于每秒包含的系统时间的单位,其次ctime将clock_t作为clock()返回类型的别名,意味着可以缉拿个变量声明为clock_t类型.
			```Cpp
			#include <iostream>
			#include <ctime>
			int main()
			{
			    using namespace std;
			    cout << "Enter the delay time,in second: ";
			    float secs;
			    cin >> secs;
			    clock_t delay = secs * CLOCKS_PER_SEC;
			    cout << "starting\a\n";
			    clock_t start = clock();
			    while (clock() - start < delay);
			    cout << "done\a\n";
			    return 0;
			}
			```
	3. ### do while循环
	4. ### 基于范围的for循环(C++11)
		这简化了一种常见的循环任务:对数组的每个循环执行相同的操作:
		```Cpp
		double prices[5] = {4.99, 10.99, 6.87, 7.99, 8.48};
		for(double x : prices)
		    cout << x << std::endl;
		```
		其中x最初表示数组prices的第一个元素.显示完后,不断执行循环,而x依次表示数组的其他元素.  
		要修改数组的元素,则需要使用不同的循环变量语法:
		```Cpp
		for(double &x : prices)
		    x = x * 0.80;
		```
		符号&表明x是一个引用变量.
	5. ### 循环和文本输入
		(暂时省略)
		1. **使用原始的cin**
		2. **使用cin.get(char)**
		3. **使用哪一个cin.get()**
		4. **文件尾条件**
		5. **另一个cin.get()**
	6. ### 嵌套循环和二维数组
		1. **初始化二维数组**
		2. **使用二维数组**
6. ## 分支语句和逻辑运算符
	1. ### if语句
		1. **if else语句**
		2. **格式化if else语句**
		3. if else if else语句**
	2. ### 逻辑表达式
		1. **逻辑OR运算符:||**
		2. **逻辑AND运算符:&&**
		3. **用&&来设置取值范围**
		4. **逻辑NOT运算符:!**
		5. **逻辑运算符细节**
	3. ### 字符函数库cctype
	4. ### ?:运算符
	5. ### switch语句
	6. ### break和continue语句
	7. ### 读取数字的循环
		假设要编写一个读取数字的程序,而用户输入了一个单词情况将如何?出现这种类型不匹配的情况时,将发生4种情况:
		* n的值保持不变
		* 不匹配的输入将被留在输入队列中
		* cin对象中的一个错误标记被设置
		* 对cin方法的调用将返回false(如果被转换为bool类型)

		方法返回false意味着可以用非数字输入来接数读取数字的循环.非数字输入设置错误标记意味着必须充值该标记,程序才能继续读取输入,可以用clear()来重置标记.
		```Cpp
		#include <iostream>
		const int MAX = 5;
		int main()
		{
		    using namespace std;
		    int golf[MAX];
		    cout << "Please enter your golf scores.\n";
		    cout << "You must enter " << MAX << " rounds.\n";
		    int i;
		    for(i = 0; i < MAX; i++)
		    {
		        cout << "round #" << i+1 << ": ";
			while (!(cin >> golf[i])
			{
			    cin.clear();
			    while (cin.get() !='\n')
			        continue;
			    cout << "Please enter a number: ";
			}
		    }
		    double total = 0.0;
		    for (i = o;i < MAX; i++)
		        total += golf[i];
		    cout << total / MAX << " = average score " << Max << " rounds\n";
		    return 0;
		}
		
		output:
		Please enter your golf scores.
		You must enter 5 rounds.
		round #1: **88**
		round #2: **87**
		round #3: **must i?**
		Please enter a number: **103**
		round #4: **94**
		round #5: **86**
		91.6 = average score 5 rounds
		```
	8. ### 简单文件输入/输出
7. ## 函数---C++的编程模块
	1. ### 复习函数的基本知识
		1. **定义函数**
		2. **函数原型和函数调用**
	3. ### 函数参数和按值传递
		1. **多个参数**
		2. **另外一个接受两个参数的函数**
	3. ### 函数和数组
		1. **使用数组区间的函数**
			```Cpp
			#include <iostream>
			const int ArSize = 8;
			int sum_arr(const int * begin, const int * end);
			int main()
			{
			    using namespace std;
			    int cookies[ArSize] = {1,2,4,8,16,32,64,128};
			    int sum = sum_arr(cookies, cookies + ArSize);
			    cout << "Total cookies eaten: " << sum << << " cookies.\n";
			    sum = sum_arr(cookies, sookies + 3);
			    cout << "First thre eaters ate " << sum << " cookies.\n);
			    sum = sum_arr(cookies + 4,cookies + 8);
			    cout << "Last four eaters ate " << sum << " cookies.\n";
			    return 0;
			}
			    int sum_arr(const int * begin, const int * end)
			    {
				const int * pt;
				int total;
				for(pt = begin; pt != end; pt++)
				     total =total + *pt;
			        return total;
		       	    }
				
			output:
			Total cookies eaten: 255
			First thre  eaters ate 7 cookies.
			Last four eaters ate 240 cookies.
			```
			2. **指针和const**   
				将const用于指针有一些很微妙的地方.可以有两种不同的方式将const关键字用于指针.第一种是让指针指向一个常量对象,这样可以防止使用该指针来修改所指向的值；第二种是将指针本身声明为常量,这样可以防止改变指针指向的值.  
				* 首先,声明一个指向常量的指针pt:  
				
					`int age = 39；`  
					`const int * pt = &age;`  
					该声明指出,pt指向一个const int,因此不能用pt来修改这个值,即*pt为常量不能被修改(以下代码是不成立的):  
					`*pt += 1;`  
					`cin >> *pt;`  
					但是有一个很微妙的问题.pt的声明并不意味这它指向的值实际上就是一个常量,而只是对于pt而言是常量.例如上面的情况下,可以直接通过age变量来修改age的值(前提是age本身不是常量).(另外C++进制将const地址赋给非const指针)  
					再回到之前的声明:  
					`int age = 39;`  
					`const int * pt = &age;`  
					第二个声明只能防止修改pt指向的值,而不能防止修改pt的值,也就是说,可以将一个新地址赋给pt,但仍然不能用pt来修改其值.  
				* 第二种:使用const的方法时的无法修改指针的值:
					* `int sloth = 3;`
					* `const int * ps = &sloth;`
					* `int * const finger = &sloth;`
					* 最后一个声明使得finger只能指向sloth,但允许用finger来修改sloth的值.
	4. ### 函数和二维数组
	5. ### 函数和C-风格字符串
		1. **将C-风格字符串作为参数的函数**  
			假设要将字符串作为参数传递给函数,则表示字符串的方法有三种:
			* char数组
			* 用引号括起的字符串常量
			* 被设置为字符串地址的char指针
		
			可以说将字符串作为参数来传递,但实际传递的是字符串的第一个字符的地址.  
			C-风格字符串与常规char数组之间的一个重要区别就是,字符串由内置的结束字符.
		2. **返回C-风格字符串的函数**  
		 	函数无法返回一个字符串,但是可以返回字符串的地址.
			```Cpp
			#include <iostream>
			char * buildstr(char r, int n);
			int main()
			{
			    using namespace std;
			    int times;
			    char ch;
			    cout << "Enter a character: ";
			    cin >> ch;
			    cout << "Enter an integer: ";
			    cin >> times;
			    char *ps = buildstr(ch, times);
			    cout << ps << endl;
			    delete [] ps;
			    ps = buildstr('+',4);
			    cout << ps << "-DONE-" << ps << endl;
			    delete [] ps;
			    return 0;
			}
			char * buildstr(char c, int n)
			{
			     char * pstr = new char[n+1];
			     pstr[n] = '\0';
			     while ( n-- > 0)
			         pstr[n] = c;
			     return pstr;
			}
			
			output:
			Enter a charcater: **V**
			Enter an integer: **14**
			vvvvvvvvvvvvvv
			vvvv-DONE-vvvv
			```
	6. ### 函数和结构体
		1. **传递和返回结构体**
		2. **另一个处理结构体的函数示例**
		3. **传递结构体的地址**
	7. ### 函数和string对象
	8. ### 函数与array对象
	9. ### 递归
		1. **包含一个递归调用的递归**
		2. **包含多个递归调用的递归**
	10. ### 函数指针
		与数据相似,函数也有地址.函数的地址是存储其机器代码的内存开始的地址.
		1. **函数指针的基础知识**
			1. *获取函数的地址*  
			   函数的地址就是其函数名(后面不跟参数).
			2. *声明函数指针*  
			   声明指向某种数据类型的指针时,必须指定指针指向的类型.  
			   假如编写了一个函数:  
			   `double pam(int);`  
			   则正确的指针类型声明如下:  
			   `double (*pf)(int);`  
			   (*pf)是函数,pf是函数指针.
			3. *使用指针来调用函数*
				```Cpp
			   	double pam(int);
			   	double (*pf)(int);
			   	pf = pam;
			   	double x = pam(4);
			   	double y = (*pf)(5);
			   ```
				最后一句也可以这么写`double y = pf(int);`  
		2. **函数指针示例**
		3. **深入探讨函数指针**
		4. **使用typedef进行简化**
8. ## 深入探索函数
	1. ### C++内联函数
		该特性可以让程序减少跳跃到函数所在地址的时间,但是相应的将会占用更多的内存.  
		使用该特性,必须采取下述措施之一:
		* 在函数声明前加上关键字inline
		* 在函数定义前加上关键字inline
		
		需要注意的是内联函数不能递归.
	2. ### 引用变量
		1. **创建引用变量**
			* 例如,要将rodents作为rats变量的别名,可以这样做:  
			`int rats;`  
			`int & rodents = rats;`
			
			其中,&不是地址运算符,而是类型标识符的一部分.上述引用表明允许rats和rodents互换.
		2. **将引用用作函数参数**
			
			* 具体用法类似指针
		3. **引用的属性和特别之处**
		4. **将引用用于结构体**
		5. **将引用用于类对象**
		6. **对象,继承和引用**
		7. **何时使用引用参数**
	3. ### 默认参数
	4. ### 函数重载
	5. ### 函数模板
	(以上暂时省略)
9. ## 内存模型和名称空间
10. ## 对象和类
11. ## 使用类
12. ## 类和动态内存分配
13. ## 类继承
14. ## C++中的代码重用
15. ## 友元,异常和其他
16. ## string类和标准模板库
	1. ### string类
		1. **构造字符串**
			* 构造函数:
				* string(吃哦那是他char * s):将string对象初始化为s指向的NBTS.
				* string(size_type n,char c):创建一个包含n个元素的string对象,其中每个元素都被初始化为字符c.
				* string(const string & str):将一个string对象初始化为stringduixiangstr(复制构造函数).
				* string():创建一个默认的string对象,长度为0.
				* string(constr * char s,size_type n):将string对象初始化为s指向的NBTS的前n个字符.
				* template<class Iter\> string(Iter begin, Iter end):将string对象初始化为区间[begin,end)内的字符.
				* string(const string & str,string size_type pos = 0,size_type n = npos):将一个string对象初始化为对象str中从位置pos开始到结尾的字符,或从位置pos开始的n个字符.
			```Cpp
			#include <iostream>
			#include <string>
			int main()
			{
			    using namespace std;
			    string one("Lottery Winner!";
			    cout << one << endl;
			    string two(20, '$');
			    cout << two << endl;
			    string three(one);
			    cout << three << endl;
			    one += "Oops";
			    cout << one << endl;
			    two = "Sorry! That was ";
			    three[0] = 'P';
			    string four;
			    four = two + three;
			    cout << four << endl;
			    char alls[] = "All's well that ends ends well";
			    string five(alls,20);
			    cout << five << "!\n";
			    string six(alls + 6, alls + 10);
			    cout << six << ", ";
			    string seven(&five[6], &five[10]);
			    cout << seven << "...\n";
			    string eight(four, 7, 16);
			    cout << eight << " in motion!" << endl;
			    return 0;
			}
			
			output:
			Lottery Winner!
			$$$$$$$$$$$$$$$$$$$$$
			Lottery Winner!
			Lottery Winner! Oops!
			Sorry! That was Pottery Winner!
			All's well that ends!
			well, well...
			That was Pottery in motion!
			```
		2. **string**类输入
			* C-风格字符串的输入方式:
				* `char info[100];`
				* `cin >> info;`
				* `cin.getline(info, 100);`
				* `cin.get(info, 100);`
			* string对象的输入方式:
				* `string stuff;`
				* `cin >> stuff;`
				* `getline(cin. stuff)`
			* 两个版本的getline()都有一个可选参数,用于指定使用哪个字符来确定输入的边界:
				* `cin.getline(info,100,':');`
				* `getline(stuff, ':');`
			在功能上,其最主要的区别在于string版本的getline()将自动调整目标string对象的大小.
		3. **使用字符串**
		4. **string还提供了那些功能**
		5. **字符串种类**
	2. ### 智能指针模板类
		* 智能指针是行为类似于指针的对象,但这种对象还有其他功能.这里将介绍三种模板指针(auto_ptr,unique_ptr和shared_ptr).
		1. **使用智能指针**
			* 这三个模板指针,都定义了类似指针的对象,可以将new获得的地址赋给这种对象.当智能指针过期时,其析函数将自动使用delete来释放内存.
			```Cpp
			void demo1()
			{
			    double * pd = new double;	// 为pd和一个double值分配存储空间,保存地址.
			    *pd = 25.5;	     // 将值复制到动态内存中.
			    return;     // 删除pd,值被保留在动态内存中.
			}
			
			void demo2()
			{
			     auto_ptr<double> ap(new double);	   // 为ap和一个double值分配存储空间,保存地址.
			     *ap = 25.5;	// 将值复制到动态内存中.
			     return;	// 删除ap,ap的析构函数释放动态内存.
			}
			```
			要创建智能指针对象,必须包含头文件memory.
		2. **有关智能指针的注意事项**
	3. ### 标准模板库
		* STL提供了一组表示容器,迭代器,函数对象和算法的模板.容器是一个与数组类似的单元,可以存储若干值.STL存储的值的类型相同；算法是完成特定任务(如对数组进行排序或在链表中查找特定值)的处方；迭代器能够用来遍历容器的对象,与能够遍历数组的指针类似,是广义指针；函数对象是类似于函数的对象,可以是类对象或函数指针.
		* STL不是面向对象编程,而是一种不同的编程模式---泛型编程.所以STL在功能和方法方面都很有趣.
		1. **模板类<vector\>**
			> 在前面曾简单的介绍过vector类,接下来更详细的介绍它.计算中,矢量(vector)对应数组,而不是数学矢量.
			* 计算矢量存储了一组可随机访问的值,即可以使用索引来直接访问矢量的第十个元素.而不必首先访问前面的9个元素,即可以使用[]运算符来访问vector元素.
			```Cpp
			#include <iostream>
			#include <string>
			#include <vector>
			const int NUM = 5;
			int main()
			{
			    using namespace std;
			    vector<int> ratings(NUMS);
			    vector<double> titles(NUM);
			    cout << "You will do exactly as told. You will enter\n"
			         << NUM << " book titles and your ratings (0 - 10).\n";
			    int i;
			    for (i = 0; i < NUM; i++)
			    {
			        cout << "Enter title #" << i + 1 << ": ";
				getline(cin,titles[i]);
				cout << "Enter your ratings (0-10): ";
				cin >> rating[i];
				cin.get();
			    }
			    cout << "Thank you. You entered the following:\n"
			         << "Rating\tBook\n";
			    for(i = 0; i < NUM; i++)
			    {
			        cout << ratings[i] << "\t" << titles[i] << endl;
			    }
			    return 0;
			}
			
			output:
			You will do exactly as told. You will enter
			5 book titles and your ratings ( 0 -10 ).
			......
			```
			
		2. **可对矢量执行的操作**
			* 除分配存储空间外,vector模板还可以完成:size()---返回容器中元素数目,swap()---交换两个容器的内容,begin()---返回一个指向容器的第一个元素的迭代器,end()---返回一个表示超过容器尾的迭代器.
			* 迭代器是一个广义指针.事实上它可以是指针,也可以是一个可对其执行类似指针的操作---如解除引用(如operate*())和递增(如operate++())---的对象.
			* 每个容器类都定义了一个合适的迭代器,vector迭代器的类型是一个名为iterator的typedef,其作用域是整个类.例如,要为vector的double类型规范声明一个迭代器:  
			
				`vector<double>::iterator pd;`  
				假设scores是一个vector<double>对象:  
				`vector<double> scores;`  
				则可以使用迭代器pd执行这样的操作:  
				`pd = scores.begin();`  
				`*pd = 22.3;`  
				`++pd;`
			* 还有一个C++11自动类型推断很有用的地方.例如,可以不这样做:
			
				`vector<double>::iterator pd = score.begin();`  
			而这样做:  
			`auto pd = scores.begin();`
			* 回到前面,超过结尾是一种迭代器,指向容器最后一个元素后面的元素.这个与C-风格字符串最后一个字符后面的空字符类似,只是空字符是一个值,而"超过结尾"是一个指向元素的指针.因此,可以使用以下代码来遍历整个容器的内容:
				* `for (pd = scores.begin(); pd != scores.end(); pd++)`  
				`cout << *pd << endl;`
			* 所有容器都包含刚才讨论的方法.vector模板类也包含了一些只有某些STL容器才有的方法.如push_back(),它将元素添加到矢量末尾:
			
				```Cpp
				vector<double> scores;
				double temp;
				while (cin >> temp &&temp >= 0)
				 	scores.push_back(temp);
				cout << "You entered " << scores.size() << " scores.\n";
				```
			* erase()方法删除矢量中给定区间的元素.它接受两个迭代器的参数,这些参数定义了要删除的区间(包括第一个,不包括第二个):  
			`scores.erase(scores.begin(), scores.begin() + 2);`
			* insert()方法的功能与erase()相反.它接受三个迭代器参数,第一个参数指定了新元素的插入位置,第二个和第三个迭代器参数定义了被插入区间,该区间通常是另一个容器对象的一部分.例如,下面将矢量new_v中的元素插入到old_v矢量的第一个元素前面:  
			`vector<int> old_v;`  
			`vector<int> new_v;`  
			`...`  
			`old_v.insert(old_v.begin(),new_v.begin() + 1,new_v.end());`
			```Cpp
			#include <iostream>
			#include <string>
			#include <vector>
			
			struct Review
			{
			    std::string title;
			    int rating;
			};
			bool FillReview(Review & rr);
			void ShowReview(const Review & rr);
			
			int main()
			{
			    using namespace std;
			    vector<Review> books;
			    Review temp;
			    while (FillReview(temp))
			        books.push_back(temp);
			    int num = books.size();
			    if (num > 0)
			    {
			        cout << "TYhank you.You entered the following:\n"
				     << "Rating\tBook\n";
				for (int i = 0; i < num; i++)
				     ShowReview(books[i]);
				cout << "Reprising:\n"
				     << "Rating\t Book\n";
				vector<review>::iterator pr;
				for (pr = books.begin(); pr != books.end(); pr++)
				     ShowReview(*pr);
				vector <Review> oldlist(books);	    // copy construct used
				if (num > 3)
				{
				   books.erase(books.begin() + 1, books.begin() + 3);
				   cout << "After erasure:\n";
				   for (pr = books.begin(), pr != books.end(); pr++)
				       ShowReview(*pr);
				   books.insert(books.begin(), oldlist.begin() + 1, oldlist.begin + 2);
				   cout << "After insertion:\n";
				   for (pr = books.begin(); pr != books.end(); pr++)
				       ShowReview(*pr);
				}
				books.swap(oldlist);
				cout << "Swapping oldlist with books:\n";
				for (pr = books.begin(); pr != books.end(); pr++)
				    ShowReview(*pr);
			    }
			    else
			        cout << "Nothing entered, nothing gained.\n";
			    return 0;
			}
			
			bool FillReview(Review & rr)
			{
			    using namespace std;
			    cout << "Enter book title (quit to quit): ";
			    getline(cin,rr.title);
			    if (rr.title == "quit")
			        return flase;
			    cout << "Enter book rating: ";
			    cin >> rr.rating;
			    if (!cin)
			        return false;
			    while (cin.get() != '\n')
			        continue;
			    erturn true;
			}
			
			void ShowReview(const Review & rr)
			{
			    std::cout << rr.rating << "\t" << rr.title << std::endl;
			}
			```
			
		3. **对矢量可执行的其他操作**
			* 对于有些常见的操作的方法,STL并没有为每个容器定义成员函数,而是定义了一个适用于所有容器类的非成员函数.下面来看3个具有代表性的STL函数: for_esch(), random_shuffle, sort().
			* for_each()函数可用于很多容器,它接受三个参数.前两个是定义容器中间区间的迭代器,最后一个是指向函数的指针.for_each()函数将被指向的函数应用于容器区间中的各个元素.被指向的函数不能修改容器元素的值.可以用for_each()来代替for循环:
			
				```Cpp
				vector<Review>::iterator
				pr;
				for (pr = books.begin();
				pr != books.end(); pr++)
				ShowReview(*pr);
				```
				可替换为:
				`for_each(books.begin(), books.end(), ShowReview);`
			* Random_shuffle()函数接受两个指定区间的迭代器参数,并随即排列该区间中的元素:  
			
				`random_shuffle(books.begin(), books.end());`  
				与可用于任何容器的for_each()函数不同,该函数要求容器允许随机访问.
			* sort()函数也要求容器支持随机访问.该函数有两个版本:第一个版本接受两个定义区间的迭代器参数,并使用为存储在容器中的类型元素定义的<运算符,对区间中的元素进行操作.例如下面的语句按升序对coolstuff进行排序:
				```Cpp
				vector<int> coolstuff;
				...
				sort(coolstuff.begin(), coolstuff.end());
				```
			* 如果容器元素是用户定义的对象,则要使用sort(),必须定义能够处理该类型对象的operate<()函数.例如,为对结构体Review进行排序:
				```Cpp
				bool operate<(const Review & r1, const Review & r2)
				{
				    if (r1.title < r2.title)
				        return true;
				    else if (r1.title == r2.title && r1.rating < r2.rating)
				        return true;
				    else return false;
				}
				```
				有了这样的函数后,就可以对包含Review对象(如books)的矢量进行排序:
				`sort(books.begin(), books.end());`  
				如果想按降序或是rating排序,则可以使用另一种格式的sort().它接受三个参数,前面两个参数也是指定区间的迭代器,最后一个参数是指向要使用的函数的指针,而不是用于比较的operate<():
				```Cpp
				bool Worsethan(const Review & r1, const Review & r2)
				{
				    if (r1.rating < r2.rating)
				        return true;
				    else
				        return false;
				}
				```
				之后就可以用下面的语句将包含Review对象的books矢量按rating升序排列:
				`sort(books.begin(), books.end(), Worsethan);`  
			
		4. **基于范围的for循环(C++11)**
			* 按照第五章的内容可以将以下语句:  
			`for_each(books.begin(), books,end(), ShowReview);`  
			替换为:  
			`for (auto x : books) ShowReview(x);`
			* 不同于for_each(),基于范围的for循环可修改容器的内容,诀窍是指定一个引用参数:
				```Cpp
				void InflatReview(Review &r)
				    {r.rating++;}
				for (auto & x : books)
				    InflatReview(x);
				```
	4. ### 泛型编程
		1. **为何使用迭代器**
			* 模板使得算法独立于存储的数据类型,而迭代器使得算法独立于使用的容器类型.
			* 举个例子,来看看如何为两种不同数据表示实现find函数,然后来看如何推广这种方法.首先来看,在一个double数组中搜索特定值得函数:
				```Cpp
				double * find_ar(double * ar, int n, const double & val)
				{
				    for (int i = 0, i < n; i++)
				        if (ar[i] == val)
					    return &ar[i];
				    return 0;
				}
				```
				可以用模板将这种算法推广到包含==运算符的,任意类型的数组.尽管如此,这种算法仍与一种特定的数据结构(数组)关联在一起.
			* 下面来看另一种数据结构---链表的情况:
				```Cpp
				Node * find_ll(Node * head, const double & val)
				{
				    Node * start;
				    for (start = head; start != 0; start = start->p_next)
				        if (start->item == val)
					    return start;
				    return 0;
				}
				```
				同样也可以用模板将这种算法推广到支持==运算符的任何数据类型的链表.然而这也是,与特定的数据结构---链表关联在一起.
			* *泛型编程旨在使用同一个find函数来处理数组,链表或其他任何容器类型.即函数不仅独立于容器中存储的数据类型,而且独立于容器本身的数据结构.模板提供了存储在容器中的数据类型的通用表达式,因此还需要遍历容器中的值的通用表示,迭代器正式这样的通用表示*.
			* 要实现find函数迭代器应具备以下特征:
				* 应能够对迭代器执行解除引用的操作,以便能够访问它引用的值.即如果p是一个迭代器,则应对*p进行定义.
				* 应能够将一个迭代器赋给另一个.即如果p和q都是迭代器,则应对表达式p=q进行定义.
				* 应能够将一个迭代器与另一个迭代器进行比较,看它们是否相等.即如果p和q都是迭代器,则应对p==q和p!=q进行定义.
				* 应能够使用迭代器遍历容器中的所有元素,这可以通过为迭代器p定义++p和p++来实现.
			* 因此,可以重新编写find_arr()函数:
				```Cpp
				typedef double * iterator;
				iterator find_ar(iterator ar, int n, const double & val)
				{
				    for (int i = 0; i < n; i++, ar++)
				        if (*ar == val)
					    return ar;
				    return 0;
				}
				```
				然后可以修改参数函数,使之接受两个指示区间的指针参数,其中一个指向数组的起始位置,另一个指向数组的超尾.下面的代码完成了这些修改:
				```Cpp
				typedef double * iterator;
				iterator find_ar(iterator begin, iterator end, consr double & val)
				{
				    iterator ar;
				    for (ar = begin; ar != end; ar++)
				        if (*ar == val)
					    retyrn ar;
				    return end;
				}
				```
			* 对于find_ll函数,可以定义一个迭代器类,其中定义了运算符*和++:
				```Cpp
				struct Node
				{
				    double item;
				    Node * p_next;
				};
				
				class iterator
				{
				    Node * pt;
				public:
				    iterator() : pt(0) {}
				    iterator (Node * pn) : pt(pn) {}
				    double operate*() { return pt->item;}
				    iterator& operate++()	// for ++it
				    {
				        pt = pt->p_next;
					return * this;
				    }
				    iterator operate++(int)	// for it++
				    {
				        iterator tmp = *this;
					pt = pt->p_next;
					return tmp;
				    }
				};
				```
				有了这样的类后,第二个find函数就可以这样编写:
				```Cpp
				iterator find_ll(iterator head, const double & val)
				{
				    iterator start;
				    for (start = head; start != 0; ++start)
				        if (*start == val)
					    return start;
				    return 0;
				}
				```
				这样这两个函数的差别只在于达到最后一个值.find_ar()函数使用超尾迭代器,find_ll()函数使用存储在最后一个节点中的空值.,这时可以要求表的最后一个元素后面还有一个额外元素,即让数组和链表都有超尾元素.
			* STL遵循上面介绍的方法.首先,每个容器类定义了相应的迭代器类型；每个容器类都有一个超尾标记...
		2. **迭代器类型**
			* 不同的算法对迭代器的要求也不同.例如,查找算法需要定义++运算符,以便迭代器能够遍历整个容器；而排序运算符要求能够随机访问.
			* STL定义了5种迭代器,并根据所需的迭代器类型对算法进行了描述.这5种迭代器分别是输入迭代器,输出迭代器,正向迭代器,双向迭代器和随机访问迭代器.下面来看迭代器的其他特征:
				1. 输入迭代器
				2. 输出迭代器
				3. 正向迭代器
				4. 双向迭代器
				5. 随机访问迭代器(暂时省略)
		3. **迭代器层次结构**
		4. **概念,改进和模型**
			1. *将指针用作迭代器*
			2. *其他有用的迭代器*
		5. **容器种类**
			* STL具有容器概念和容器类型.概念是具有名称(如容器,序列容器,关联容器等)的通用类别；容器类型是可用于创建具体容器对象的模板.因为概念对类型进行了分类,所以下面讨论容器概念:
			1. *容器概念*
				* 没有与容器概念对应的类型,但概念描述了容器类都同用的元素.
				* 容器是存储其他对象的对象.被存储的对象必须是同一种类型的.当容器过期时,存储在容器中的数据也将过期(如果数据是指针的话,则它指向的数据并不一定过期).
				* 所有的容器都提供某些特征和操作:![image](/home/leolanger/blog/source/_posts/images/Screenshot_20191217_112021.png)
			2. *C++11新增的容器要求*
				![image1](/home/leolanger/blog/source/_posts/images/Screenshot_20191217_115409.png)
			3. *序列*
				* 可以通过添加要求来改进基本的容器概念.序列概念增加了迭代器至少是正向迭代器这样的要求,这保证了元素将按特定顺序排列,不会发生两次迭代之间发生变化.
				* 序列的要求:![image3](/home/leolanger/blog/source/_posts/images/Screenshot_20191217_115855.png)
				* 下面详细介绍7中序列容器类型:
					1. vector
					2. deque
					3. list
					4. list工具箱
					5. forward_list (C++11)
					6. queue
					7. priority_queue
					8. stack
					9. array(C++11)
			4. **关联容器**
				1. set示例
				2. multimap示例
			5. **无序关联容器**
	5. ### 函数对象
17. ## 输入输出和文件
18. ## 探讨C++新标准 
