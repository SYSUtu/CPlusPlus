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
## 类型转换与继承

		
    
