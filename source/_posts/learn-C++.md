---
title: learn-C++
date: 2020-05-19 13:24:29
tags: C++
categories: language
---



# 							Learn C++

由于事故本人现在重开新博客，这篇也是新博客的第一篇文章，继续来学习C++。主要内容为之前未曾详细提到的面向对象，同时也算是为了应对学校里的考试而进行的复习 （滑稽）。



<!--more-->



## 从C到C++

#### 引用变量 

​		引用变量的主要用途是用作函数的形参。通过将引用变量用作参数函数将使用原始数据，而不是其副本。这样除指针之外，引用也为函数处理大型结构提供了便捷途径。

###### 创建引用变量

​		C++将&用来声明引用，例如要将 rodents作为rats变量的别名，可以这样做：

```C++
int rats;
int & rodents = rats;	//makes rodents an alias for rats
```

​		其中，&不是地址运算符，而是类型标识符的一部分。就像声明中char*指的是指向char的指针一样，int&指的是指向int的引用。

```C++
# include <iostream>
int main()
{
	using namespace std;
	int rats = 101;
	int & rodents = rats;	// reodents is a reference
	cout << "rats = " << rats;
	cout << ", reodents = " << rodents << endl;
    rodents++;
    cout << "rats = " << rats;
	cout << ", reodents = " << rodents << endl;
	
	cout << "rats address = " << &rats;
	cout << ", rodents address = " << &rodents << endl;
	return 0;
}
```



输出：

	 rats = 101, rodents = 101
	 rats = 102, rodents = 102
	 rats address = 0x0065fd48,  rodents address = 0x0065fd48  

从中可知rats和rodents的值和地址都相同。

虽然指针和引用很相似，但它们其实还是有区别的：

+ ``` C++
  int rats = 101;
  int & rodents = rats;
  int * prats = & rats;
  ```

  ​		其中，表达式rodents和*parts 可以同rats互换；&rodents 和 parts 可任意同&rats互换。

+ 必须在声明引用将其初始化，而指针可以先声明再赋值。

###### 将引用用作函数参数

引用经常被用作函数参数，使得函数中的变量名成为调用程序中的变量别名。这种传递参数的方法被称为按引用传递。下面是交换两个值的例子：

```c++
 #include <iostream>
void swapr(int & a, int & b);
void swapp(int * p, int * q);
void swapv(int a, int b);
int main()
{
    using namespace std;
    int wallet1 = 300;
    int wallet2 = 350;
    cout << "wallet1 = $" << wallet1;
    cout << "wallet2 = $" << wallet2 << endl;
    
    cout << "Using references to swap contents:\n";
    swapr(wallet1, wallet2);
    cout << "wallet1 = $" << wallet1;
    cout << "wallet2 = $" << wallet2 << endl;
    
    cout << "Using pointers to swap contents:\n";
    swapp(&wallet1, &wallet2);
    cout << "wallet1 = $" << wallet1;
    cout << "wallet2 = $" << wallet2 << endl;
    
    cout << "Trying to use passing by value:\n";
    swapv(wallet1, wallet2);
    cout << "wallet1 = $" << wallet1;
    cout << "wallet2 = $" << wallet2 << endl;
    return 0;
}

void swapr(int & a, int & b)
{
    int temp;
    temp = a;
    a = b;
    b = temp;
}

void swapp(int * p, int * q)
{
    int temp;
    temp = *p;
    *p = *q;
    *q = temp;
}

void swapv(int a, int b)
{
    int temp;
    temp = a;
    a = b;
    b = temp;
}

```



输出：

```c++
wallet1 = $300wallet2 = $350
Using references to swap contents:
wallet1 = $350wallet2 = $300
Using pointers to swap contents:
wallet1 = $300wallet2 = $350
Trying to use passing by value:
wallet1 = $300wallet2 = $350
```

在swapr()中，变量a 和 b 是wallet1 和wallet2 的别名，所以交换a 和 b 的值相当于交换wallet1和wallet2的值。



###### 引用的属性和特别之处

```c++
# include <iostream>
double cube(double a);
double recube(double &ra);
int main()
{
    using namespace std;
    double x = 3.0;
    
    cout << cube(x);
    cout << " = cube 0f " << x << endl;
    cout << recube(x);
    cout << " = cube of " << x << endl;
    return 0;
}

double cube(double a)
{
    a *= a * a;
    return a;
}

double recube(double &ra)
{
    ra *= ra * ra;
    return ra;
}
```



输出：

```C++
27 = cube of 3
27 = cube of 27
```

recube()函数修改了main()中的x值，而cube()没有。变量a位于cube()中，它被初始化为x的值，但修改a并不会影响x。但由于recube()使用了引用参数，因此修改re实际上等于修改x。

如果意图让函数使用传递给它的信息，而不对这些信息进行修改，同时又想使用引用，则应使用常量引用：`double recube(const double &ra);`

这样做，当编译器发现代码修改了ra的值时，将生成错误信息。

> **注：应尽可能使用const**
>
> + 使用const可以避免无意中修改数据的编程错误
> + 使用const使函数能够处理const和非const实参，否则将只能接受非const数据;
> + 使用const引用使函数能够正确生成并使用临时变量；

###### 将引用用于类对象

将类对象传递给函数时，C++通常的做法是使用引用。下面有一个例子：

```C++
#include <iostream>
#include <string>
 using namespace std;
string version1(const string &s1, const string &s2);
const string & version2(string & s1, const string & s2);	//has side effect
const string & version3(string & s1, const string & s2);	//bad design

int main()
{
    string input;
    string copy;
    string result;
    
    cout << "Enter a string: ";
    getline(cin, input);
    copy = input;
    cout << "Your string as enterd: " << input << endl;
    result = version1(input, "***");
    cout << "You string enhanced: " << result << endl;
    cout << "Your original string: " << input << endl;
    
    result = version2(input, "###");
    cout << "You string enhanced: " << result << endl;
    cout << "Your original string: " << input << endl;
    
    cout << "Resetting original string:\n";
    input = copy;
    result = version3(input, "@@@");
    cout << "You string enhanced: " << result << endl;
    cout << "Your original string: " << input << endl;
    
    return 0;
}

string version1(const string &s1, const string &s2)
{
    string temp;
    
    temp = s2 + s1 + s2;
    return temp;
}
const string & version2(string & s1, const string & s2)
{
    s1 = s2 + s1 + s2;	//safe to return reference passed to function
    return s1;
}
const string & version3(string & s1, const string & s2)
{
    string temp;
    
    temp = s2 + s1 + s2;	//unsafe to return reference to local variable
    return temp;
}
```

输出：

```c++
Enter a string: It's not my fault./
Your string as entered: It's not my fault.
Your string enhanced: ***It's not my fault.***
Your original string: It's not my fault.
Your string enhanced: ###It's not my fault.###
Your original strnig: ###It's not my fault.###
Resetting original string.
此时，该程序崩溃
```

+ 在version1中，temp是一个新的string对象，只在函数version1()中有效，该函数执行完毕后，它将不再存在。因此，返回指向temp的引用不可行，因此，该函数的返回类型为string，这意味着temp的内容将被复制到一个临时存储单元中，然后在main()中，该存储单元的内容被复制到result中；
+ 在version3中，返回一个指向version3()中声明的变量的引用。导致在`result = version3(input, "@@@");`执行该语句时，程序试图引用已经释放的内存。



#### 默认参数

默认参数指的是当函数调用中省略了实参是自动使用的一个值。例如，如果将void wow(int n)设置成n有默认值为1,则函数调用wow()相当于wow(1)。

应当通过函数原型来设置默认参数。如上，若省略参数n，则它的值将为1；否则，传递的值将覆盖1.

对于带参数列表的函数，必须从右向左添加默认值。也就是说为某个参数设置默认值，则必须为它右边的所有参数提供默认值。

#### 函数重载

函数重载的关键是函数的参数列表-------也成为函数特征标。若两个函数的参数数目和类型相同，同时参数的排列顺序也相同，则它们的特征标相同，而变量名是无关紧要的。C++允许定义名称相同的函数，条件是它们的特征标不同。

使用同名函数时，编译器将根据采取的用法使用有相应特征标的原型。

类型引用和类型本身为同一个特征标。



## 类和对象的基础



#### 抽象和类



##### C++中的类（定义类）

类是一种将抽象转换为用户定义类型的C++工具，它将数据表示和操纵数据的方法组合成一个整洁的包。下面举一个表示股票的类：

+ 首先考虑如何表示股票。可以将某人当前持有的股票作为一个基本单元，数据表示中包含他持有的股票数量。因此，其对数据的可执行操作为：
  + 获得股票
  + 增持
  + 卖出股票
  + ……
+ 根据以上可定义stock类的公有接口。为支持这些接口，需要存储一些信息。我们将存储下面的信息：
  + 公司名称
  + 所持股票的数量
  + 每股的价格
  + ……
+ 接下来，定义类。一般来说，类规范由两个部分组成：
  + 类声明：以数据成员的方式描述数据部分，以成员函数的方式描述公有接口。
  + 类成员函数定义：描述如何实现类成员函数。

下面是类定义的工作方式：

```C++
#include <string>
class Stock		// class declaration
{
private:
    std::string company;
    long shares;
    double share_val;
    double total_val;
    void set_tot()
    {
        total_val = shares * share_val;
    }
public:
    void acquire(const std::string & co, long n, double pr);
    void buy(long num, double price);
    void sell(long num, double price);
    void update(double price);
    void show();
};
```

首先，C++关键字class指出这些代码定义了一个类设计。这指出Stock是这个新类的类型名，该声明让我们能够声明Stock类型的变量------成为对象或实例。例如，下面声明创建两个Stock对象，分别名为sally和solly：`Stock sally;` `Stock solly;`sally对象可以表示Sally持有的股票。

接下来，要存储的数据以类数据成员的形式出现。例如sally的company成员存储了公司名称，share成员存储了Sally持有的股票数量……

同样，要执行的操作以类函数成员（如，sell()和update())的形式出现。成员函数可以就地定义（如set_tot())，也可以用原型表示（如其他成员函数）。



###### 访问控制

关键字public和private描述了对类成员的访问控制。使用类对象的程序都可以直接访问公有部分，但只能通过公有成员函数来访问对象的私有成员。例如，要修改Stock类的shares成员，只能通过Stock的成员函数。因此公有成员函数是程序和对象的私有成员之间的桥梁。防止程序直接访问数据被成为数据隐藏。

类设计尽可能将公有接口与实现细节分开。公有接口表示设计的抽象组件。将实现细节放在一起，并将它们与抽象分开成为封装。数据隐藏是一种封装，将实现细节隐藏在私有部分中，就像Stock类对set_tot（）所作的那样，也是一种封装。



###### 控制对成员的访问：公有还是私有

由于隐藏数据是OOP主要的目标之一，因此数据通常放在私有部分，组成接口的成员函数放在公有部分；否则，就无法从成员成员中调用这些函数。但是如set_tot()，不能直接从程序中哦该调用这种函数，但公有方法却可以使用它们。

另外，若没有声明为什么，则默认为private。



##### 实现类成员函数

还需要创建类描述的第二部分：为那些由类声明中的原型表示的成员函数提供代码。成员函数定义与常规函数定义非常相似，它们有函数头和函数体，也可以有返回类型和参数。但是它们还有两个特殊的特征：

+ 定义成员函数时，使用作用域解析运算符(::)来标识函数所属的类;
+ 类方法可以访问类的private组件。

首先，成员函数的函数头使用作用域解析运算符(::)来指出函数所属的类。例如，update()成员函数的函数头如下：

`void Stock::update(double price);`

这意味着update()函数是Stock类的成员。这不仅将update()标识为成员函数，还意味着我们可以将另一个类的成员函数也命名为update()。

Stock类的其他成员函数不必使用作用域解析运算符，就可以使用update()，是因为它们属于同一个类。然而，在类声明和成员函数定义之外使用update()时，需要采取特殊的措施。

其次，成员函数可以访问类的私有成员。例如，show()方法可以使用这样的代码：

```C++
std::cout << "Company" << company
		  << " Shares: " << shares << endl;
```

其中，company、shares等都是Stock类的私有数据成员。如果试图使用非成员函数访问这些数据成员，编译器禁止这样做（友元函数例外）。

接下来，开始实现类方法了：

```c++
#include <iostream>
#include <string>

class Stock		// class declaration
{
private:
    std::string company;
    long shares;
    double share_val;
    double total_val;
    void set_tot()
    {
        total_val = shares * share_val;
    }
public:
    void acquire(const std::string & co, long n, double pr);
    void buy(long num, double price);
    void sell(long num, double price);
    void update(double price);
    void show();
};
void Stock::acquire(const std::string &co, long n, double pr)
{
    company = co;
    if (n < 0)
    {
        std::cout << "Number of share can't be negtive;"
            	  << company << " shares set to 0.\n";
        shares = 0;
    }
    else
        shares = n;
    share_val = pr;
    set_tot();
}
```

1. 成员函数声明
2. 内联方法
   + 其定义位于类声明中的函数都将自动成为内联函数。
   + 如果愿意，也可以在类声明之外定义成员函数，并使其成为内联函数。为此，只需在类实现部分中定义函数是=时使用inline限定符即可。
3. 方法使用那个对象
   + 首先看如何创建对象：`Stock kate，joe；`
   + 接下来，看如何使用对象的成员函数：`kate.show();` `joe.show();`
   + 所创建的每个新对象都有自己的存储空间，用于存储其内部变量和类成员；但同一个类的所有对象共享同一组类方法。

##### 使用类

略

##### 修改实现

略

#### 类的构造函数和析构函数

到现在为止，还不能向初始化int或结构那样来初始化Stock对象。也就是说，常规的初始化语法不适用于类型Stock：

```C++
int year = 2001;	// valid initialization
struct thing
{
	char * pn;
	int m;
}
thing amabob = {"wodget", -23};		// valid initialization
Stock hot = {"Sukie's Autos, Inc.", 200, 50.25};	//NO! compile error

```

不能像上面初始化Stock对象的原因在于，数据部分的访问状态是私有的，这意味着程序不能直接访问数据成员。

+ 为了在创建对象时，自动对它进行初始化，C++提供了一个特殊的成员函数------类构造函数，专门用于构造新对象、将值赋给它们的数据成员。
+ 构造函数的名称与类名相同。
+ 构造函数的原型和函数头没有返回值（包括void），没有声明类型。
+ 若定义时没写构造函数，则编译器自动生成一个默认的无参数的构造函数，其不做任何操作。

###### 声明和定义构造函数

现在需要创建Stock的构造函数。由于需要为Stock对象提供3个值，因此应为构造函数提供3个参数。函数原型：`Stock(const string & co, long n = 0, double pr = 0.0);`

注意没有返回类型，原型位于类声明的公有部分。

下面是构造函数的一种可能定义：

```C++
Stock::Stock(const string & co, long n, double pr)
{
company = co;
	if (n < 0)
	{
		std::cerr << "Number of shares can't be negative;"
				  << company << " shares set to 0.\n";
		shares = 0;
	}
	eles
		shares = n;
	share_val = pr;
	set_tot();
}
```

上述代码和前面的acquire()相同。区别在于，程序声明对象中，将自动调用构造函数。

###### 使用构造函数

C++提供了两种使用构造函数来初始画对象的方式：

1. 显示的调用构造函数：`Stock food = Stock("World Cabbage", 250, 1.25);`
2. 隐式地调用构造函数：`Stock garment("Furry Mason", 50, 2.5);`
3. 每次创建类对象（甚至使用new动态内存分配）时，C++都使用类构造函数。下面是将构造函数与new一起使用的方法：`Stock *pstock = new Stock("Electroshock Games", 18, 18.0);`
4. 构造函数的使用方式不同于其他类方法。一般来说，使用对象来调用方法：`stock1.show();` 但无法使用对象来调用构造函数，因为在构造函数构造出对象之前，对象是不存在的。
5. 因此构造函数被用来创建对象，而不能通过对象来调用（对象一旦生成，就再也不能在其上执行构造函数）

###### 默认构造函数

基本概念：

+ 默认构造函数是在为提供显示初始值是，用来创建对象的构造函数。即用于下面这种声明的构造函数：`Stock fluffy_the_cat;	// use the default constructor` 

+ 如果没有提供任何构造函数，则C++将自动提供默认构造函数。

+ 对于Stock类来说，默认构造函数可能如下：`Stock::Stock(){}` 因此将创建fluffy_the_cat对象，但不初始化其成员，这和下面的语句创建x，但没有提供值给它一样：`int x;`

+ 默认构造函数没有参数，因为声明中不包含值。

  

定义默认构造函数的方式有两种：

1. 给已有构造函数的所有参数提供默认值：`Stock(const string & co = "Error", int n = 0, double pr = 0.0);`

2. 另一种方法是通过函数重载来定义另一个构造函数------一个没有参数的构造函数：`Stock();`

3. 例如，下面是为Stock类定义的一个默认构造函数：

   ```C++
   Stock::Stock()
   {
       company = "no name";
       shares = 0;
       share_val = 0.0;
       total_val = 0.0;
   }
   ```

使用上述任何一种方式创建了默认构造函数后，便可以声明对象变量，而不对它们进行显式初始化：

```C++
Stock first;
Stock first = Stock();
Stock *prelief = new Stock;
```

然而不要被非默认构造函数的隐式形式所误导：

```C++
Stock first("Concrete Conlomerate");	//call constructor
Stock second();		// declare a function
Stock third;	// call default constructor
```

第一个声明调用非默认构造函数；第二个声明指出，second()是一个返回Stock对象的函数。隐式的调用默认构造函数时，不要使用圆括号。

#### 析构函数

基本概念：

+ 用构造函数创建对象后，程序负责跟踪该对象，直到其过期为止。对象过期时，程序将自动调用一个特殊的成员函数——析构函数。
+ 析构函数可以来完成清理工作，比如在构造函数使用new来分配内存，则析构函数可使用delete来释放这些内存。
+ 但若像Stock类一样没有使用new，这时，只需让编译器自动生成一个什么都不做的隐式析构函数。
+ 析构函数的名称，在类名前加上～。没有返回值和声明类型。与构造函数不同，析构函数没有参数。
+ 一个类最多只有一个析构函数。

什么时候应该调用析构函数？

+ 如果创建的是静态存储类对象，则其析构函数将在程序结束时自动被调用。
+ 若创建的是自动存储类对象，则其析构函数将在程序执行完代码块时自动被调用。
+ 若对象是通过new创建的，则它将驻留在栈内存或自由存储区中，当使用delete时，自动被调用
+ 程序可以创建临时对象来完成特定的操作，在这种情况下，程序将在结束对该对象的使用时自动调用其析构函数。

如果程序员没有提供析构函数，编译器将隐式地声明一个默认析构函数。



#### 改进Stock类

```C++
#include <string>
#include <iostream>

class Stock
{
    std::string company;
    long shares;
    double share_val;
    double total_val;
    void set_tot() {total_val = shares * share_val;}
public:
    Stock();	// default constructor
    Stock(const std::string & co, long n = 0, double pr = 0.0);
    ~Stock();	// noisy destuctor
    void buy(long num, double price);
    void sell(long num, double price);
    void update(double price);
    void show();
};

Stock::Stock()
{
    std::cout << "Default constructor called\n";
    company = "no name";
    shares = 0;
    share_val = 0.0;
    total_val = 0.0;
}
Stock::Stock(const std::string & co, long n, double pr)
{
    std::cout << "Constructor using " << co << " calles\n";
    company = co;
    
    if (n < 0)
    {
        std::cout << "Number of shares can't be negtive; "
            	  << company << " shares set to 0.\n";
        shares = 0;
    }
    else
        shares = n;
    share_val = pr;
    set_tot();
}
Stock::~Stock()
{
    std::cout << "Bye, " << company << "!\n";
}

void Stock::buy(long num, double price)
{
    if (num < 0)
    {
        std::cout << "Number of shares purchased can't be negtive." << "Transaction is aborted.\n";
    }
    else
    {
        shares += num;
        share_val = price;
        set_tot();
    }
}
void Stock::sell(long num, double price)
{
    using std::cout;
    if (num < 0)
    {
        cout << "Number of shares sold can't be negtive." 
             << "Transaction is aborted.\n";
    }
    else if (num > shares)
    {
        cout << "You can't sell more than you have!"
             << "Transaction is aborted.\n";
    }
    else
    {
        shares = num;
        share_val = price;
        aet_tot();
    }
}
void Stock::update(double price)
{
    share_val = price;
    set_tot();
}
void Stock::show()
{
    using std::cout;
    using std::ios_base;
    ios_base::fmtflags orig = 
        cout.setf(ios_base::fixed, ios_base::floated);
    std::streamsize prec = cout.precision(3);
    cout << "Company: " << company
        	  << " Shares: " << shares << '\n';
    cout << " Share Price: $" << share_val;
    cout.precision(2);
    cout << " Total Worth: $" << total_val << '\n';
    
    cout.setf(orig, ios_base::floatfield);
    cout.precision(prec);
}

int main()
{
    {
        using std::cout;
        cout << "Using constructors to creat new poject\n";
        Stock stock1("NanoSmart", 12, 2.0);
        stock1.show();
        Stock stock2 = Stock("Boffo Obejects", 2, 2.0);
        stock2.show();
        
        cout << "Assigning stock1 to stock2:\n";
        stock2 = stock1;
        cout << "Listing stock1 and stock2:\n";
        stock1.show();
        stock2.show();
        
        cout << "Using a constructor to reset an object\n";
        stock1 = Stock("Nifty Foods", 10, 50.0);
        cout << "Revised stock1:\n";
        stock1.show();
        cout << "Done\n";
    }
    return 0;
}
```

输出：

```
Using constructor to creat new projects
Constructor using NanoSmart called
Company:NanoSmart Shares: 12
  Share Price: $20.00 Total Worth: $240.00
Constructor using Boffo Obejects called
(Bye, Boffo Obejects!)	// may exist 
Company: Boffo Objects  Shares: 2
  SHare Price: $2.00  Total Worth: $4.00
Assigning stock1 to stock2:
Listing stock1 to stock2:
Company:NanoSmart Shares: 12
  Share Price: $20.00 Total Worth: $240.00
Company:NanoSmart Shares: 12
  Share Price: $20.00 Total Worth: $240.00
Using a constructor to reset an object
Constructor using Nifty Foods called
Bye, Nifty Foods!
Revised stock1:
Company: Nifty Foods Shares: 10
  Share Price: $50.00 Total Worth: $500.00
Done
Bye, NanoSmart!
Bye,Nifty Foods!
```

程序说明：

+ `Stock stock1("NanoSmart", 12, 20.0);`创建一个名为stock1的Stock对象，并将其数据成员初始化为指定的值；
+ `Stock stock2 = Stock ("Boffo Obejects", 2, 2.0);`使用另一种语法创建并初始化一个名为stock2的对象；
+ C++编译器允许使用来嗯中方式来执行第二种语法。
  1. 使其行为和第一种语法完全相同；
  2. 允许调用构造函数来创建一个临时对象，然后在将该临时对象复制到stock2中，并丢弃它。此时会调用析构函数，因此生成括号内的输出。
+ `stock2 = stock1；` 可以将一个对象赋给同类型的另一个对象；
+ `stock1 = Stock("Nifty Foods", 10, 50.0);`stock1对象已存在，因此这条语句不是对其初始化，而是将新值赋给它。通过让构造函数创建一个新的、临时的对象，然后将其内容复制给stock1来实现。随后调用析构函数，以删除该临时对象。
+ 函数main()结束时，其局部变量将消失。由于存放与栈中，因此后创建的对象将先被删除。

C++11列表初始化

+ 只要提供与某个构造函数的参数列表匹配的内容，并用大括号将它们括起。

const成员函数

+ `const Stock land = Stock("Kludgehorn Properties");` `land.show();`
+ 对于C++来说，编译器将拒绝第二行。因为show()代码无法确保调用对象不被修改——调用对象和const一样不应该被修改。
+ 我们以前通过将函数参数声明为const引用或指向const的指针来解决这些问题。但这里，show()没有参数。
+ 相反，它所使用的对象是由方法调用隐式地提供的。C++的解决办法是将const放在函数的括号后面：`void show() const;` `void stock::choW() const;`



## 类和对象的提高



#### this指针

到目前为止，每个类成员函数只涉及到一个对象，即调用它的对象。但有时候成员函数可能涉及到两个对象，在这种情况下需要使用this指针。



在之前Stock类的例子中，可以添加如下代码

```c++
class Stock()
{
    private:
    ***
        double total_val;
    ***
    public:
    	double total() const { return total_
val;}
    ***
};
```

让成员函数返回一个值，让我们知道价格最高的一只。

然而，可以采用另一种方法——通过this指针。定义一个成员函数，它查看两个Stock对象，并返回股价较高的那个对象的引用。此时会出现一些问题：

1. 如何将两个要比较的对象提供给成员函数？将该成员函数命名为topval()，则stock1.topval()将访问stock1对象的数据，而stock2.topval()将访问stock2对象的数据。因此必须将第二个对象作为参数传递给它。

2. 如何将结果传回给调用的程序？让成员函数返回一个引用，该引用指向较高的对象。

   `const Stock & topval(const Stock & s) const;`

   该程式隐式地访问一个对象，而显式的访问另一个对象，并返回其中一个对象的引用。括号中的const表示，该函数不会修改被显示地访问的对象；而括号后面的const表明，该函数不会修改被隐示地访问的对象。

将设要对stock1和stokc2进行比较，则可如下使用：`top = stock1.topval(stock2);` 或`top = stock2.topval(stock1);`

topval()的实现可以如下表示：

```c++
const Stock & Stock::topval(const Stock & s) const
{
    if (s.total_val > total_val)
        return s;
    else
        return *this;
}
```

> 每个成员函数都有一个this指针。this指针指向调用对象。若成员函数要引用整个调用对象，则可以使用表达式*this。在函数的括号后面使用const限定符将this限定为const。
>
> 然而要返回的并不是this，因为this是对象的地址。



#### 对象数组

当创建同一个类的多个对象时可以创建独立对象变量，但创建对象数组更合适。

声明对象数组的方法与声明标准类型数组相同：`Stock mystuff[4];`

可以用构造函数来初始化数组元素：

```C++
Stock stocks[4] = {
    Stock("N", 12.5, 20),
    Stock("B", 12.5, 20),
    Stock("M", 12.5, 20),
    Stock("F", 12.5, 20)
};
```

如果类包含多个构造函数，则可以对不同的元素使用不同的构造函数：

```C++
Stock stocks[10] = {
    Stock("N", 12.5, 20),
    Stock(),
    Stock("F", 12.5, 20)
};
```



由于该数组只初始化了数组的部分元素，因此余下的7个元素将使用默认构造函数。

初始化对象数组的方案是，首先使用默认构造函数创建数组元素，然后画括号中的构造函数将创建*临时对象*，然后将临时对象的内容复制到相应的元素中。因此，要创建类对象数组，则必须有默认构造函数。

```c++
#include <iostream>
#include "stock2.h"

const int STKS =4;
int main()
{
    Stock stocks[4] = {
    	Stock("N", 12.5, 20),
    	Stock("B", 12.5, 20),
    	Stock("M", 12.5, 20),
    	Stock("F", 12.5, 20)
    	};
    std::cout << "Stock holdings:\n";
    int st;
    for (st = 0; st < STKS; st++)
        stocks[st].show();
    const Stock * top = &stocks[0];
    for (st = 1; st < STKS; st++)
        top = &top->topval(stocks[st]);		// select the toppest
    std::cout << "\n Most valuable holding:\n";
    top->show();
    return 0;
}
```

#### 类作用域

略



## 运算符重载



#### 简介

运算符重载是一种形式的C++多态。C++会根据操作数的数目和类型来决定采用那种操作。但也允许运算符重载扩展到用户定义的类型。

要重载运算符，需要使用被称为运算符函数的特殊函数形式：

`operator op (argument-list)`

例如，operator+()重载+运算符，operator*() 重载 *运算符。op必须为有效的C++运算符。

#### 计算时间：一个运算符重载实例

例如，今早在Priggs的帐户上花费了2小时35分钟，下午又花费了2小时40分钟，则共花了多少时间？这与加法概念很吻合，但相加单位与内置类型不匹配。

先看一种普通示例：

```C++
class Time
{
    private:
    int hours;
    int minutes;
    public:
    Time();
    Time(int h, int m = 0);
    void AddMIng(int m);
    void AddHr(int h);
    void Reset(int h = 0, int m = 0);
    Time Sum(const Time & t) const;
    void Show() const;
};

Time::Time()
{
    hours = minutes = 0;
}
Time::Time(int h, int m)
{
    hours = h;
    minutes = m;
}
void Time::AddMin(int m)
{
    minutes += m;
    hours += minutes / 60;
    minutes %= 60;
}
void Time::AddHr(int h)
{
    hours += h;
}
void Time::Reset(int h, int m)
{
    hours = h;
    minutes = m;
}
Time Time::Sum(const Time & t)
{
    Time sum;
    sum.minutes = minutes + t.minutes;
    sum.hours = hours + t.hours + sum.minutes / 60;
    sum.minutes %= 60;
    return sum;
}
void Time::Show() const
{
    std::cout << hours << "hours, " << minutes << " minutes";
}

int main()
{
    using namespace std;
    Time planning;
    Time coding(2, 40);
    Time fixing(5, 55);
    Time total;
    
    cout << "planning time = ";
    planning.Show();
    cout << endl;
    
    cout << "coding time = ";
    coding.Show();
    cout << endl;
    
    cout << "fixing time = ";
    fixing.Show();
    cout << endl;
    
    total = conding.Sum(fixing);
    cout << "coding.Sum(fixing) = ";
    total.Show();
    cout << endl;
    
    return 0;
}
```

sum()函数代码中，参数是引用，用来提高效率；返回值不是引用，因为返回的是新建的一个局部函数sum。

###### 添加加法运算符

以上方式很普通，但略微不直观。因此将Time类转换为重载的加法运算符。

```C++
class TIme
{
    private:
    int hours;
    int minutes;
    public:
    Time();
    Time(int h, int m = 0);
    void AddMIng(int m);
    void AddHr(int h);
    void Reset(int h = 0, int m = 0);
    Time operator+(const Time & t) const;	// 重载运算符+
    void Show() const;
};

Time::Time()
{
    hours = minutes = 0;
}
Time::Time(int h, int m)
{
    hours = h;
    minutes = m;
}
void Time::AddMin(int m)
{
    minutes += m;
    hours += minutes / 60;
    minutes %= 60;
}
void Time::AddHr(int h)
{
    hours += h;
}
void Time::Reset(int h, int m)
{
    hours = h;
    minutes = m;
}
Time Time::operator+(const Time & t)
{
    Time sum;
    sum.minutes = minutes + t.minutes;
    sum.hours = hours + t.hours + sum.minutes / 60;
    sum.minutes %= 60;
    return sum;
}
void Time::Show() const
{
    std::cout << hours << "hours, " << minutes << " minutes";
}

int main()
{
    using namespace std;
    Time planning;
    Time coding(2, 40);
    Time fixing(5, 55);
    Time total;
    
    cout << "planning time = ";
    planning.Show();
    cout << endl;
    
    cout << "coding time = ";
    coding.Show();
    cout << endl;
    
    cout << "fixing time = ";
    fixing.Show();
    cout << endl;
    
    total = coding + fixing;	// <===> total = coding.operator+(fixing);
    cout << "coding + fixing = ";
    total.Show();
    cout << endl;
    
    return 0;
}
```

当两个以上的对象进行运算是，从右往左。



###### 重载限制

多数C++运算符都可以用这样的方式进行重载。重载的运算符不必是成员函数，但必须至少有一个操作数是用户定义的数据类型。下面为一些限制：

1. 重载后的运算符必须至少有一个操作数是用户定义的类型，这将防止用户为标准运算符重载。
2. 使用运算符时不能违反运算符原来的语句规则。
3. 不能创建新运算符。
4. 不能重载下面的运算符：
   1. sizeof
   2.  .
   3. .*
   4. ::
   5. ?:
   6. typeid
   7. const_cast :强制类型转换运算符
   8. dynamic_cast :强制类型转换运算符
   9. reinterpret_cast :强制类型转换运算符
   10. static_cast :强制类型转换运算符
5. 下面的运算符只能通过成员函数进行重载：
   1. =
   2. （）函数调用运算符
   3. [] 下标运算符
   4. ->

###### 其他重载运算符

略



#### 重载运算符：作为成员函数还是非成员函数

略

## 友元



C++控制了对类对象私有部分的访问。通常，公有类方法提供惟一的访问途径，

但有时会造成不便，因此提供了另一种形式的访问权限：友元。包括：

+ 友元函数
+ 友元类
+ 友元成员函数

通过让函数成为类的友元，可以赋予该函数与类的成员函数相同的访问权限。

为何需要友元？

+ 在运算符重载时，如上，将一个Time值与一个double值结合在一起时，会出现限制：
  + `A = B + 2.75;` 将被转换为`A = B.operator+(2.75);`
  + 但是对该语句`A = 2.75 + B；`编译器将报错
+ 解决这个问题可以靠非成员函数。非成员函数不是由对象调用的，它使用的所有值（包括对像）都是显式参数。如此：
  + `A = 2.75 + B；` 可与`A = operator+(2.75, B);`匹配
  + 该函数的原型：`Time operator*(double m, const Time & t);`
+ 使用非成员函数需访问私有数据，因此需要友元函数

#### 友元



###### 创建友元

创建友元函数的第一步是将其原型放在类声明中，并在原型前加上关键字friend：

`friend Time operator*(double m, const Time & t);`

这原型意味着：

+ 虽然operator*()函数实在类声明中声明的，但并不是成员函数，因此不能使用成员运算符来调用；
+ 虽然operator*()函数不是成员函数，但与成员函数的访问权限相同。

接下来编写定义函数。因不是成员函数，不用Tame::限定符。另外再定义中不使用friend：

```C++
Time operator*(double m, const Time & t)
{
    Time result;
    long totalminutes = t.hours * mult * 60 + t.minutes * mult;
    result.hours = totalminuyes / 60;
    result.minutes = totalminutes % 60;
    return result;
}
```

###### 常见的友元：重载<<运算符

假设trip是一个Time对象。为显示Time的值，可以使用Show()，但是使用cout << trip;更直观。

1. 第一个重载版本

   + 如果使用一个Time成员函数来重载<<，Time对象将是第一个操作数。这意味着必须这样使用：`trip << cout;`

   + 因此需要通过友元函数,完成像下面这样的重载运算符：

     ```C++
     void operator<<(ostream & os, const Time & t)
     {
         os << t.hours << " hours, " << t.minutes << " minutes";
     }
     ```

2. 第二种重载版本

   + 前面那种实现不允许如下使用：`cout << "Trip time: " << trip << " (Tuesday)\n";`

   + 因为<<运算符要求左边是一个ostream对象。

   + 因此如下操作：

     ```C++
     ostream & operator<<(ostream & os, const Time & t)
     {
     	os << t.hours << " hours, " << t.minutes << " minutes";
     	return os;
     }
     ```



###### 友元类

假设需要编写一个模拟电视机和遥控器的简单程序，需定义一个Tv类和Remote类。这两个类之间存在某种关系，但不是继承关系。事实上遥控器可以改变电视机的状态，因此Remote类作为Tv类的一个友元。

友元声明可以位于公有，私有或保护成员：

```c++
class Tv
{
public:
    friend class Remote;
    enum {Off, On};
    enum {MinVal,MaxVal = 20};
    enum {Antenna, Cable};
    enum {TV, DVD};
    
    Tv(int s = Off, int mc = 125) : state(s), volume(5),
    	maxchannel(mc),channel(2),mode(Cable), input(TV){}
    void onoff() 
    {
        state = (state == On)? Off : On;
    }
    bool ison() const 
    {
        return state == On;
    }
    bool volup();
    bool voldown();
    void chanup();
    void chandown();
    void set_mode()
    {
        mode = (mode == Antenna)? Cable : Antenna;
    }
    void set_input()
    {
        input = (input == TV)? DVD : TV;
    }
    void setting() const;
private:
    int state;
    int volume;
    int manchannel;
    int channel;
    int mode;
    int input;
};
class Remote
{
private:
    int mode;
public:
    Remote(int m = Tv::TV) : mode(m) {} 
    bool volup(Tv & t)
    {
        return t.volup();
    }
    bool voldown(Tv & t)
    {
        return t.voldown();
    }
    void onoff(Tv & t)
    {
        t.onoff();
    }
    void chanupp(Tv & t)
    {
        t.chanup();
    }
    void chandown(Tv & t)
    {
        t.chandown();
    }
    void set_chan(Tv & t, int c)
    {
        t.channel = c;
    }
    void set_mode(Tv & t)
    {
        t.set_mode();
        
    }
    void set_input(Tv & t)
    {
        t.set_input();
    }
};

bool Tv::volup()
{
    if (volume < MaxVal)
    {
        volume++;
        return true
    }
    else
        return false;
}
bool Tv::voludown()
{
    if (volume > MinVal)
    {
        volume--;
        return true
    }
    else
        return false;
}
bool Tv::chanup()
{
    if (channel < maxchannel)
        channel++;
    else
        channe = 1;
}
bool Tv::chandown()
{
    if (channel > 1)
        channel--;
    else
        channe = maxchannel;
}
void Tv::setting() const
{
    using namespave std;
    cout << "TV is " << (state == Off ? "Off" : "On") << endl;
    if (state == On)
    {
        ……
    }
}

int main()
{
    using namespace std;
    Tv s42;
    cout << "Initial settings for 42\" TV:\n";
    s42.settings();
    s42.onoff();
    s42.chanup();
    cout << "\nAdiusted settings for 42\" TV:\n";
    s42.chanup();
    
    Remote grey;
    grey.setchan(s42, 10);
    ******
}
```

###### 友元成员函数

在上一个例子中，大多数Remote成员函数都是用Tv类的公有接口实现的。

事实上，唯一直接访问Tv成员的只有Remote::set_chan()，这时可以选择仅让特定的类成员成为另一个类的友元。

其方法是：

```C++
class Tv
{
    ***
        friend void Remote::set_chan(Tv & t, int c);
    ***
};
```

然而，为此必须要知道Remote的定义。这意味着应将Remote的定义放到Tv前面。

Remote的成员函数提到了Tv对象，意味着Tv定义应当位于Remote定义前。

为此，使用前向声明。需在Remote定义前插入下面语句：`class Tv；`

但是，在Remote类的声明中包含了内敛代码，其中调用了Tv的一个成员函数。所以，在Remote声明中只包含方法声明，将实际定义放在Tv类后面。

###### 其他友元关系

互为友元，此时应注意要让编译器有足够的信息来编译。

###### 共同的友元

略



## 类继承



#### 一个简单的基类

从一个类派生出另一个类时，原始类成为基类，继承类成为派生类。

假设Webtown俱乐部决定跟踪乒乓球会会员，为此需设计一个TabelTennisPlayer类。

```c++
class TabelTennisPlayer
{
private:
    string firstname;
    string lastname;
    bool hasTable;
public:
    TabelTennisPlayer {const string & fn = "none",
                      const string & ln = "none", 
                       bool ht = false};
    void Name() const;
    bool HasTable() const {return hastable;}
    void ResetTabel(bool v)
    {
        hasTAbel = v;
    }
    
     TabelTennisPlayer {const string & fn = "none",
                      const string & ln = "none", 
                       bool ht = false} : firstname(fn),
    lastname(ln),hasTable(ht) {}
    
    void TabelTennisPlayer::Name() const
    {
        std::cout << lastname << ", " << firstname;
    }
}
```

###### 派生一个类

Webtown俱乐部需要一个类能包括成员在比赛中的比分。可以在TabelTennisPlayer类派生一个类。

首先声明RatedPlayer类：

```C++
class RatedPlayer : public TabelTennisPlayer
{
    ***
};
```

Ratedplayer对象将具有一下特征：

+ 派生类对象存储了基类的数据成员
+ 派生类对象可以使用基类的方法。

需要在继承特性中添加什么？

+ 派生类需要自己的构造函数
+ 派生类可以根据需要添加额外的素据成员和数据函数。

###### 构造函数：访问权限的考虑

派生类不能直接访问基类的私有成员，而必须通过基类方法进行访问。即，RatedPlayer构造函数不能直接设置继承的成员（firstname、lastname等）具体地说，派生类构造函数必须使用基类构造函数。

例如下面是第一个RatedPlayer构造函数的代码：

```c++
RatedPlayer::RatedPlayer(unsigned int r, const string & fn,
                        const string & ln, bool ht) : TabelTennisPlayer(fn, ln, ht)
{
    rating = r;
}
```

其中：TabelTennisPlayer(fn, ln, ht)是成员初始化列表。调用TabelTennisPlayer的构造函数。

如果省略成员初始化列表，如果不调用基类构造函数，则使用默认的基类构造函数。

对于一下代码：

```C++
RatedPlayer::RatedPlayer(unsigned int r, const TabelTennisPlayer & tp) : TabelTennisPlayer(tp)
{
    rating = r;
}
```

这里也将TabelTennisPlayer的信息传递给了TabelTennisPlayer构造函数，因为tp的类型为TabelTennisPlayer&，因此将调用基类的复制构造函数。



有关构造函数的要点如下：

+ 首先创建基类对象
+ 派生类构造函数应通过成员初始化列表将信息传递给基类构造函数
+ 派生类构造函数应初始化派生类新增的数据成员。

> 创建派生类对象时，程序首先调用基类构造函数，然后再调用派生类构造函数。基类构造函数负责初始化继承的数据成员；派生类构造函数主要用于初始化新增的数据成员。派生类构造函数总是调用一个基类构造函数。可以使用初始化器列表语法指明要使用的基类构造函数，否则将使用默认的基类构造函数。
>
> 派生类对象过期时，程序先调用派生类析构函数，再调用基类析构函数。

###### 使用派生类

一个例子：

```c++
#include <string>
#include <iostream>
using namespace std;
class TableTennisPlayer
{
private:
    string firstname;
    string lastname;
    bool hasTable;
private:
    TabelTennisPlayer (const string & fn = "none",
                      const string & ln = "none", 
                       bool ht = false);
    void Name() const;
    bool HasTable() const {return hastable;}
    void ResetTabel(bool v)
    {
        hasTAbel = v;
    }    
};

class RatedPlayer : public TableTennisPlayer
{
private:
    unsigned int rating;
public:
    RatedPlayer (unsigned int r = 0, const string & fn = "none", const string &ln = "none", bool ht = false);
    RatedPlayer(unsigned int r, const TableTennisPlayer & tp);
    unsigned int Rating() const {return rating;}
    void ResetRating (unsigned int r) {rating = r;}
};

TableTennisPlayer::TableTennisPlayer (const string & fn,
                   const string & ln, bool ht) : firstname(fn), lastname(ln), hasTable(ht) {}

void TableTennisPlayer::Name() const
{
    std::cout << lastname << ", " << firstname;
}

RatedPlayer::RatedPlayer(unsigned int r, const string & fn,
                        const string & ln, bool ht) :TableTennisPlayer(fn, ln, ht)
{
    rating = r;
}
RatedPlayer::RatedPlayer(unsigned int r, const TableTennisPlayer & tp) :TableTennisPlayer(tp), rating(r)
{
    
}


int main()
{
    TableTennisPlayer player1("Tara", "Boomdea", false);
    RatedPlayer rplayer1(1140, "Mallory", "Duck", true);
    rplayer.Name();
    if (rplayer1.HasTable())
        cout << ": has a table";
    else
        cout << ": hasn't a table.\n";
    cout << "Name: ";
    rplayer1.Name();
    cout << ";Rating: " << rplayer1.Rating() << endl;
    RatedPlayer rplayer2(1212, player1);
    cout << "Name: ";
    rplayer2.Name();
    cout << ";Rating: " << rplayer2.Rating() << endl;
    return 0;
}
```

输出：

```
Duck, Mallory: has a table.
Boomdea, Tata: hasn't a table.
Name: Duck, Mallory; Rating: 1140
Name: Boomedea, Tara; Rating: 1212
```

###### 派生类和基类之间的特殊关系

1. 派生类对象可以使用基类的方法，条件是方法不是私有的;

2. 基类指针可以再不进行显示类型转换的情况向指向派生类对象

3. 基类引用可以再不进行显示类型转换的情况向引用派生类对象：

   ```C++
   Ratedplayer rplayer1(1140, "Mallore", "Duck", true);
   TableTennisPlayer &rt = rplayer1;
   rt.Name();
   ```

然而基类指针，只能用于调用基类方法，不能调用派生类方法。

#### 继承：is-a关系

C++有三种继承关系：公有继承、保护继承和私有继承。

公有继承最常用，它建立一种is-a关系。更准确的为is-akind-of（是一种）。

#### 访问控制：protected

关键字protected与private相似，在类外只能用公有类成员函数来访问protected中的类成员。区别是：派生类成员可以直接访问基类的保护成员，但不能直接访问基类的私有成员。

#### 继承和动态内存分配

###### 略

#### 私有继承





## 多态

事实上运算符重载，函数重载也是多态。

#### 多态公有继承

如果希望同一个方法在派生类和基类中的行为是不同的，即方法的行为取决于调用对象。这种较复杂的行为称为多态——具有多种形态。

有两种重要的机制可以实现多态公有继承：

+ 在派生类中重新定义基类方法
+ 使用虚函数。

举一个实际的例子：

需要开发两个类BrassAccount和BrassPLus。

其中第一个类的信息包括：

1. 数据成员：
   1. 客户姓名
   2. 帐号
   3. 结余
2. 可执行操作：
   1. 创建账户
   2. 存款
   3. 取款
   4. 显示信息

对第二个类希望包含以上类，并且加上：

1. 数据成员
   1. 透支上限
   2. 透支贷款利率
   3. 当前透支额
2. 对以下两种操作，实现不同：
   1. 取款考虑透支保护
   2. 显示操作必须显示BrassPLus账户的其他信息

###### 开发Brass类和BrassPlus类

```C++
class Brass
{
private:
    std::string fullName;
    long acctNum;
    double balance;
public:
    Brass(const std::string & s = "Nullbody", long an = -1,
         double bal = 0.0);
    void Deposit(double amt);
    virtual void Withdraw(double amt);
    double Balance() const;
    virtual void ViewAcct() const;
    VIRTUAL ~Brass() {}
};

class BrassPlus : pubilc Brass
{
private:
    double maxLoan;
    double rate;
    double owesBank;
public:
    BrassPlus(const std::string & s = "Nullbody", long an = -1, double bal = 0.0, double ml = 500,double r = 0.11125);
    BrassPlus(const Brass  ba, double ml = 500, double r = 0.11125);
    virtual void ViewAcct() const;
    virtual void Withdraw(double amt);
    void ResetMax(double m) { maxLoan = m; }
    void ResetRate(double r) { rate = r; }
    void ResetOwes() {owesBank = 0; }
};
```

> 如果方法是通过指针或引用调用，对于实函数，程序将根据引用类型或指针类型选择方法；对于虚函数，将非根据引用对象或指针对象的类型进行选择。

1. 类实现

   ```C++
   using namespace std;
   Brass::Brass (const string & s, long an, double bal)
   {
       fullName = s;
       acctNum = an;
       balance = bal;
   }
   void Brass::Deposit(double amt)
   {
       if (amt < 0)
           cout << "Negetive deposit is not allowed;"
           	 << "deposit is cannclled.\n";
       else
           ballance += amt;
   }
   void Brass::Withdraw(double amt)
   {
    	if (amt < 0)
           cout << "Withdrawal amount must be positve;";
       else if (amt <= balance)
           balance -= amt;
       else
           cout << "Withdrawal amount if &" << amt;
       restore(initialState, prec);
   }
   
   double Brass::Balance() const
   {
       return balance;
   }
   void Brass::ViewAcct() const
   {
       ***
   }
   BrassPlus::BrassPlus(const string & a, long an, double bal, double ml, double r) : Brass(s, an, bal)
   {
       ***
   }
   BrassPlus::BrassPlus(const Brass & ba, double ml, double r) : Brass(ba)
   {
       ***
   }
   void BrassPlus::ViewAcct() const
   {
       Brass::ViewAcct();
       ***
   }
   void BrassPlus::WIthdraw(double amt)
   {
       if
           Brass::Withdras(amt);
       else
           ***;
   }
   ```

2. 使用Brass和BrassPlus类

   ```c++
   int main()
   {
       using namespace std;
       Brass Piggy("Porcelot Pigg", 381299, 400.0);
       BrassPlus Hoggy(***);
       ***
   }
   ```

3. 演示虚方法的行为

4. 为何需要虚析构函数

   + 如果析构函数不是虚的，则将只调用对应于指针类型的析构函数
   + 如果析构函数是需的，将调用相应对象类型的析构函数。
   + 因此，使用虚析构函数可以确保正确的析构函数序列被调用。

#### 抽象基类

略



## 类的自动转换和强制类型转换

 暂略