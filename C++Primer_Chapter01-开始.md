## 1.1
	int main(){
	return 0;
	}
函数包括：返回类型，函数名，形参列表，函数体。
## 1.2
标准库定义了4个IO对象。分别为：cin，cout，cerr，clog。    
endl：操纵符。写入的效果是结束当前行，并将与设备关联的缓冲区中的内容刷到设备中。
## 1.3
注释：单行注释，界定符对注释（不能嵌套）
## 1.4
### 如何判断哪个if...else...是一对
当一个程序中出现多个if……else……的时候，也可能会引来一些麻烦的事情。因为每个if都具有和else配对的功能。那么我们在阅读一段程序的时候，怎么才能够知道哪个if和哪个else是在一起的呢？具体的规则是，else向上寻找最近的一个和它处于相同缩进位置的if配对，我们把这种规则理解为“门当户对”。
### if...else if...else
	if(boolean_expression 1)
	{
   	// 当布尔表达式 1 为真时执行
	}
	else if( boolean_expression 2)
	{
   	// 当布尔表达式 2 为真时执行
	}
	else if( boolean_expression 3)
	{
   	// 当布尔表达式 3 为真时执行
	}
	else 
	{
   	// 当上面条件都不为真时执行
	}
# 1.5类简介
在c++中，我们通过定义一个类来定义自己的数据结构。区别类和struct

## 字符串，向量和数组
### 定义和初始化
		string s1;
		string s2=s1;
		string s3="hiya";
		string s4(10,'c');

* 有时我们希望能在最终得到的字符串中保留输入的空白符，这时应该用getline函数代替原来的>>运算符。函数从给定的输入流中读入内容，直到遇到换行符为止（换行符也被读进去了）。然后把所读的内容存入到那个string对象中去（注意不存换行符）。getline只要一遇到换行符就结束读取。
* string的empy和size操作
* size（）函数返回的是一个string::size_type类型的值
* 字面值可以和string对象相加
* 处理string对象中的字符：基于范围FOR语句，可以使用islower,ispunct,isspace,isupper,tolower,toupper
### 标准库类型vector
#### 初始化
		vetor<T> v1;
		vetor<T> v2(v1);拷贝初始化
		vetor<T> v2=v1;同上一种；直接初始化
		vetor<T> v3(n,val);
		vetor<T> v4(n);
		vetor<T> v5{a,b,c...};
		vetor<T> v5={a,b,c...};
* c++语言提供了几种不同的初始化方式。在大多数情况下这些初始化方式可以互相等价地使用，不过也并非一直如此。目前以及介绍过的两种例外是：1.使用拷贝初始化时，只能提供一个初始值；其二，如果提供的是一个类内初始值则只能使用拷贝初始化或使用花括号的形式初始化。3.如果提供的是初始元素值得列表，则只能把初始值都放在花括号里进行列表初始化，而不能放在园括号里。
* 在某些情况下，初始化的真实含义依赖于传递初始值时用的是圆括号还是花括号。例如，

		vector<int> v1(10);
		vector<int> v2{10};
		vector<int> v3(10,1);
		vector<int> v3{10,1};
* 迭代器
		vector<int>:;interator
* 但凡用了迭代器的循环，都不要向迭代器所属的容器添加元素。
* 理解复杂的数组申明：

		int(*p)[10]=&arr;指向一个含有10个整数的数组
* 数组的下标类型为size_t
# 语句
## try语句块和异常处理
* 当程序的某部分检测到一个它无法处理的问题时，需要用到异常处理。此时，**检测问题的部分应该发出某种信号以表明程序遇到故障，无法继续下去了，而且信号的发出方无需知道故障将在何处得到解决。**一旦发出异常信号，检测出问题的部分也就完成了任务。
* **如果程序中含有可能引发异常的代码，那么通常也会有专门的代码处理问题。**例如，如果程序的问题是输入无效，则异常处理部分可能会要求用户重新输入正确的数据；如果丢失了数据库连接，会发出报警信息。
* 异常处理机制为程序中异常检测和异常处理这两部分的协作提供支持。在c++语言中，异常处理包括：
* throw表达式，**异常检测**部分使用throw表达式来表示它遇到了无法处理的问题。我们说throw引发了异常。
* try语句块，**异常处理**部分使用try语句块处理异常。try语句块以关键字try开始，并以一个或多个catch子句结束。try语句块中代码抛出的异常通常会被某个catch子句处理。因为catch子句处理异常，所以它们也被称作异常处理代码。
* try语句块的通用语法形式
 
		try {
			program-statements
		} catch (exception-declaration){
			handler-statements
		}
		catch (exception-declaration){
			handler-statements
		}

# 函数
* 函数调用完成两个工作：一，用实参初始化函数对应的形参，二是将控制权转移给被调用函数。此时，主调函数的执行被暂时中断，被调函数开始执行
## 数组形参

	void print(int*);
	void print(int[]);
	void print(int[10]);//这里表示期望含有多少元素，实际不一定
* 数组引用形参

		void print(int (&arr)[10])
		//同样int *arr[4]；
		是一个一维数组，数组的每一项都是一个指向int的指针
		int (*arr)[4]；
		是一个二位数组的首地址，相当于int arr[n][4]中的arr
## 函数指针
* 函数指针指向的是函数而非对象，和其他指针一样，函数指针指向某种特定类型。函数的类型由它的返回类型和形参类型共同决定，与函数名无关。例如：

		bool lengthCompare(strint&,string&);
		=>
		bool (*ptr)(strint&,string&);
* 当我们把函数名作为一个值使用时候，该函数自动地转换成指针。此外我们也可以直接使用指向函数的指针调用函数，无需提前解引用

# 类

类的基本思想是**数据抽象和封装**。   
`struct Sales_data{`   
`std::string isbn()const{return bookNo;}`   
`Sales_data& combine(const Sales_data&);`   
`double avg_price()const;`   
`std::string bookNo;`   
`unisigned units_sold=0;`   
`double revenue=0.0;`   
`}`
`//非成员接口函数`
`Sales_data add(const Sales_data&,const Sales_data&);`
`std::ostream &print(std::ostream&,const Sales_data&);`
`std::istream &read(std::istream&,Sales_data&);`

## 定义成员函数

定义在类内部的函数是隐式的inline函数。尽管所有的成员都必须在类的内部声明，但是成员函数体可以定义在类内也可以定义在类外。**成员函数通过一个名为this的额外隐式参数来访问调用它的那个对象。当我们调用一个成员函数时，用请求该函数的对象地址初始化this**   
例如，如果调用`total.isbn()`则编译器负责把total的地址传递给isbn的隐式形参this类似`isbn(&total)`。对于我们来说，this形参是隐式定义的。任何自定义名为this的参数或者变量行为都是非法的。我们可以在成员函数内部使用this，但这样是没有必要的。

## const成员函数

isbn函数的另一个关键之处是紧随形参列表之后的const关键字，const的作用是修改隐式this指针de类型。默认情况下，this是指向类类型非常量版本的常量指针，即`Sales_data* const this;`
于是紧跟在参数列表后的const表示this是一个指向常量的指针。像这样使用const的成员函数被称为**常量成员函数**。          
**PS**:如果const位于星号的左侧，则const就是用来修饰指针所指向的变量，即指针指向为常量；如果const位于星号的右侧，const就是修饰指针本身，即指针本身是常量。   
**io类无法被拷贝，可以通过引用来传递**

## 构造函数

构造函数无法被声明为const。类通过一个特殊的构造函数来控制默认初始化的过程，这个函数叫做**默认构造函数**。无需任何实参。  
`struct Sales_data{`   
`std::string isbn()const{return bookNo;}`   
`Sales_data& combine(const Sales_data&);`   
`double avg_price()const;`   
`std::string bookNo;`   
`unisigned units_sold=0;`   
`double revenue=0.0;`   
`}//修改前` 
  
`struct Sales_data{`   
`//新增的构造函数`  
`Sales_data()=default;`   
`Sales_data(const std::string&s):bookNo(s){};`  
`Sales_data(const std::string&s,unsigned n,double p):bookNo(s),units_sold(n),revenue(p*n){};`
`Sales_data(std::istream&);`  
`//之前的原有成员`   
`std::string isbn()const{return bookNo;}`   
`Sales_data& combine(const Sales_data&);`   
`double avg_price()const;`   
`std::string bookNo;`   
`unisigned units_sold=0;`   
`double revenue=0.0;`   
`}修改后`

`Sales_data()=default;` 表示默认构造函数
`Sales_data(const std::string&s):bookNo(s),units_sold(0),revenue(0){};` 
## 访问控制与封装
public：定义在说明符后面的成员在整个程序中可以被访问，public成员定义接口。    
private：说明符后面的成员可以被类的成员函数访问，不能被使用该类的代码访问。   
当我们希望定义的类的所有成员是public时，使用struct；反之使用class。
## 友元函数
类可以允许其他类或者函数访问它的非公有成员，方法是令其他类或者函数称为它的**友元**。

# 顺序容器
* 顺序容器为程序员提供了控制元素和访问顺序的能力。这种顺序不依赖于元素的值，而是与元素加入容器时的位置相对应。与之相对应，有序和无序关联容器，则根据关键字的值来存储元素。
* 所有顺序容器都提供了快速顺序访问元素的能力。
* vector：支持快速随机访问，在尾部之外的位置插入或删除元素可能很慢。
* deque：双端队列。支持快速随机访问，在头尾插入删除很快
* list：双向链表，支持双向顺序访问。在任何位置插入删除都很快
* forward_list：单向链表
* array：固定大小数组
* string：与vector相似。专门保存字符
## 容器操作
* iterator
* const_interator

**构造函数**

* C c
* C c(c1)
* C c(b,e);迭代器b和e指定的内容

**赋值与swap**

* c1=c2
* c1={a,b,c}
* a.swap(b);
* swap(a,b)

**大小**

* c.size()
* c.max_size()
* c.empty();

**反向容器**

* c.rbegin()
* c.rend();

## array
* 当定义一个array时，除了指定元素类型，还要指定容器大小：

		array<int,12>
* **值得注意的是，虽然我们不能对内置数组类型进行拷贝或对象赋值操作，但array无限制**

		array<int,3>v1={1,2,3}
		array<int,3>copy=v1;
* list,forward_list,deque还支持push_front

# 泛型算法
大多数算法都定义在头文件**algorithm**中。标准库还在头文件**numeric**中定义了一组数值泛型算法。它不会改变容器大小，不会直接添加或删除元素。

`int val=42;`                     
`auto resualt = find (vec.cbegin(),vec.cend(),val);`
`cout<<"The value"<<val`
`<<(resualt==vec.cend()?"is not present":"is present")<<endl;`

概念上，find应执行如下步骤：

* 1访问序列的首元素。
* 2比较此元素与我们要查找的值。
* 3如果此元素和我们要查找的值匹配，find返回标识此元素的值。
* 4.否则，find前进到下一个元素，重复执行步骤2与3.
* 5.如果到达序列尾，find应停止。
* 6.如果find到达序列尾，它应该返回一个指出元素未找到的值。此值和步骤三返回的值必须具有相同类型。
## 只读函数
一些算法只会读取其输入范围的元素，而不改变元素，除了find，count还有accumulate。

`int sum=accumulate(vec.cbegin(),vec.cend,0);`

另一个只读算法是equal，用于确定两个序列是否保存相同的值。

`equal(roster1.cbegin(),roster1.cend(),roster2.cbegin());`

## 写容器元素的算法
一些算法会向输入范围写入元素。

`fill(vec.begin(),vec.end(),0);`

repalce算法读入一个序列，并将其中所有等于给定值的元素都改为另一个值。

`repalce(ilst.begin(),ilst.end(),0,42);//将所有值为0的元素改为42`

replace_copy可以保留原序列不变。

`replace_copy(ilst.cbegin(),ilst.cend(),back_inserter(ivec),0,42);`
`//此调用后，ilst并未改变，ivec包含ilst的拷贝，不过原来在ilst中值为0的元素在ivec中变为42。`

## 介绍back_inserter
一种保证算法有足够元素空间来容纳输出数据的方法是使用插入迭代器。通常情况，当我们通过一个迭代器向容器元素赋值的时候，值被赋予迭代器指向的元素。而当我们通过一个插入迭代器赋值时，一个与赋值号右侧相等的元素被添加到容器当中。back_inserter接受一个指向容器的引用，返回一个与该容器绑定的插入迭代器。当我们通过此迭代器赋值时，赋值运算符会调用push_back将一个具有给定值的元素添加到容器中：

`vector<int>vec;`
`auto it=back_inserter(vec);`
`*it=42;`

## 重排容器元素的算法
某些算法会重排容器中元素的顺序。一个明显的例子是sort。还可以配合unique使得元素不重复。由于算法不能执行容器操作，我们将使用vector的erase成员来完成删除。
`void elimDups(vector<string> &words){`
`sort(words.begin(),words.end());`
`auto end_unque=unique(words.begin(),words.end());//最后一个不重复元素的后一个位置`
`word.erase(end_unique,words.end());}`

使用unique之后，words大小并未改变，它仍然有10个元素，只是覆盖了相邻的重复元素。

## OOP：概述
**面向对象程序设计**的核心思想是数据抽象，继承和动态绑定。通过使用数据抽象，我们可以将类的接口与实现分离；使用继承，可以定义相似的类型并对其相似关系建模；使用动态绑定，可以在一定程度上忽略相似类型的区别，而以统一的方式使用它们的对象。
### 继承
通过继承联系在一起的类构成一种层次关系。  
对于某些函数，**基类希望它的派生各自定义适合自身的版本，此时基类就将这些函数声明成虚函数。** 
 
          class Bulk_quote : public Quote{
          public:
                 double net_price(std::size_t) const override;
          };

派生类必须在其内部对所有重新定义的虚函数进行声明。派生类可以在这样的函数之前加上virtual关键字，但不是必须的。c++11新标准允许派生类显式地注明它将使用哪个成员函数改写其基类虚函数，在形参列表后面加override。 
### 动态绑定

 	double print_total(ostream &os,const Quote &item,size_t){
     ...
	}
函数print_total的item形参是基类Quote 的引用，我们既能使用基类的对象调用该函数，也能使用派生类的对象调用；又因为print_total是引用类型调用net_price函数，实际传入print_total的对象类型将决定到底执行哪一个net_price版本。
## 定义基类和派生类
### 定义基类
	class Quote{
	public:
		Quote()=default;
		Quote(const std::string &book,double sales_price):
						bookNo(book),price(sales_price){}
		std::string isbn() const {return bookNo;}
    
    	virtual double net_price(std::size_t n) const
			{return n*price;}
		virtual ~Quote()=defualt;
		private:
			std::string bookNo;
		protected:
			double price=0.0;
	};
**作为继承关系中的根节点的类通常会定义一个析构函数**

派生类需要对虚函数提供自己的新定义以覆盖（override）从基类继承而来的旧定义。在c++中，基类必须将他两类成员函数区别开来：一种是基类希望其派生类进行覆盖的函数；另一种是基类希望派生类直接继承而不需要改变的函数。**当我们使用指针或引用调用虚函数时，该调用将动态绑定。根据引用或指针所绑定的对象类型不同，该调用可能执行基类版本，也可能是派生类。
###定义派生类
	class Bulk_quote : public Quote{
	public:
		Bulk_quote()=default;
		Bulk_quote(const std::string ,double,std::size_t,double);
		std::string isbn() const {return bookNo;}
    
    	double net_price(std::size_t) const override;
		
		private:
			std::size_t min_qty=0;
			double discount=0.0;
	};
我们的Quote类希望它的派生类定义各自的net_price函数，因此派生类需要访问Quote的price成员。与之相反，派生类访问bookNo的方式与其他用户一样,只能通过调用isbn函数。                                     

一个派生类会包含多个对象：含有派生类自己定义的对象，以及从基类继承的子对象，如果有多个基类，那么这样的子对象也有多个。**因为在派生类的对象中包含与其基类对应的组成部分，所以我们能把派生类的对象当成基类来使用，而且我们也能将基类的指针或引用绑定到派生类对象中的基类部分上**

	Quote item;
	Bulk_quote bulk;
	Quote *p=&item;
	p=&bulk;//p指向bulk的Quote部分
	Quote&r=bulk;//r绑定到bulk的Quote部分

派生类必须使用基类的构造函数来初始化这些成员。

	Bulk_quote(const std::string &book,double p,std::size_t qty,double disc):Quote(book,p),min_qty(qty),discount(disc){}
该函数将他的前两个参数传递给了Quote的构造函数，由Quote的构造函数负责初始化Bulk_quote的基类部分。
### 静态成员
如果基类定义了一个静态成员，则在整个继承体系中只存在该成员的唯一定义。不论从基类中派生出来多少个派生类，对于每个静态成员来说都只存在唯一的实例
### 派生类声明
派生类的声明中包含类名，不包含派生列表。
### 被用作基类的类
如果我们想将某个类用作基类，则该类必须已经定义而非声明。在类名后跟一个final，这个类就不能作为基类来使用。
### 类型转换与继承
之所以存在派生类向基类的类型转换是因为每个派生类对象都包含一个基类部分，而基类的引用或指针可以绑定到该基类部分上。因为一个基类对象可能是派生类对象的一部分，也可能不输，所以不存在从基类向派生类的自动类型转换。
## 虚函数
当我们使用基类的引用或指针调用一个虚成员函数时会执行动态绑定，直到运行时才能知道到底调用了那个版本虚函数，所以所有虚函数都必须定义。一个派生类的函数如果覆盖了某个继承而来的虚函数，则它的形参类型必须与被它覆盖的基类函数完全一致。同样返回类型也要一致。
		
    
# 操作符重载
operator是C++的关键字，它和运算符一起使用，表示一个运算符函数，理解时应将operator=整体上视为一个函数名。   
这是C++扩展运算符功能的方法，虽然样子古怪，但也可以理解：一方面要使运算符的使用方法与其原来一致，另一方面扩展其功能只能通过函数的方式（c++中，“功能”都是由函数实现的)。
## 一、为什么使用操作符重载？
对于系统的所有操作符，一般情况下，只支持基本数据类型和标准库中提供的class，对于用户自己定义的class，如果想支持基本操作，比如比较大小，判断是否相等，等等，则需要用户自己来定义关于这个操作符的具体实现。比如，判断两个人是否一样大，我们默认的规则是按照其年龄来比较，所以，在设计person 这个class的时候，我们需要考虑操作符==，而且，根据刚才的分析，比较的依据应该是age。那么为什么叫重载呢？这是因为，在编译器实现的时候，已经为我们提供了这个操作符的基本数据类型实现版本，但是现在他的操作数变成了用户定义的数据类型class，所以，需要用户自己来提供该参数版本的实现。
## 二、如何声明一个重载的操作符？
A:操作符重载实现为类成员函数    
重载的操作符在类体中被声明，声明方式如同普通成员函数一样，只不过他的名字包含关键字operator，以及紧跟其后的一个c++预定义的操作符。
可以用如下的方式来声明一个预定义的==操作符:

    class person{
    private:
        int age;
    public:
    person(int a){
       this->age=a;
    }
    inline bool operator == (const person &ps) const;
    };
实现方式如下：

    inline bool person::operator==(const person &ps) const
    {

     if (this->age==ps.age)
        return true;
     return false;
    }
调用方式如下：

    #include
    using namespace std;
    int main()
	{
  		person p1(10);
  		person p2(20);
  		if(p1==p2) cout<<”the age is equal!”< return 0;
	}

B:操作符重载实现为非类成员函数(全局函数)      
对于全局重载操作符，代表左操作数的参数必须被显式指定。例如： 
 
	#include
	#include
	using namespace std;
	class person
	{
	public:
	int age;
	};

	bool operator==(person const &p1 ,person const & p2)

	//满足要求，做操作数的类型被显示指定
	{
	if(p1.age==p2.age)
	return true;
	return false;
	}

	int main()
	{
	person rose;
	person jack;
	rose.age=18;
	jack.age=23;
	if(rose==jack)
	cout<<"ok"< return 0;
	}  
C:如何决定把一个操作符重载为类成员函数还是全局名字空间的成员呢？  
①如果一个重载操作符是类成员，那么只有当与他一起使用的左操作数是该类的对象时，该操作符才会被调用。如果该操作符的左操作数必须是其他的类型，则操作符必须被重载为全局名字空间的成员。
②C++要求赋值=，下标[]，调用()， 和成员指向-> 操作符必须被定义为类成员操作符。任何把这些操作符定义为名字空间成员的定义都会被标记为编译时刻错误。
③如果有一个操作数是类类型如string类的情形那么对于对称操作符比如等于操作符最好定义为全局名字空间成员。                                                                  

