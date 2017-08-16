1.类的一个特征就是封装，public和private作用就是实现这一目的。所以：用户代码（类外）可以访问public成员而不能访问private成员；private成员只能由类成员（类内）和友元访问。   
2.类的另一个特征就是继承，protected的作用就是实现这一目的。所以：
protected成员可以被派生类对象访问，不能被用户代码（类外）访问。

	class A{
	public:
 		int a;
  	A(){
    	a1 = 1;
    	a2 = 2;
    	a3 = 3;
    	a = 4;
 	 }
	void fun(){
   	 	cout << a << endl;    //正确
    	cout << a1 << endl;   //正确
    	cout << a2 << endl;   //正确，类内访问
    	cout << a3 << endl;   //正确，类内访问
  	}
	public:
  		int a1;
	protected:
  		int a2;
	private:
  		int a3;
	};
	int main(){
  		A itema;
  		itema.a = 10;    //正确
  		itema.a1 = 20;    //正确
  		itema.a2 = 30;    //错误，类外不能访问protected成员
  		itema.a3 = 40;    //错误，类外不能访问private成员
  		system("pause");
  		return 0;
	}
## 继承中的特点
有public, protected, private三种继承方式，它们相应地改变了基类成员的访问属性。

* public继承：基类public成员，protected成员，private成员的访问属性在派生类中分别变成：public, protected, private
* protected继承：基类public成员，protected成员，private成员的访问属性在派生类中分别变成：protected, protected, private
* private继承：基类public成员，protected成员，private成员的访问属性在派生类中分别变成：private, private, private

但无论哪种继承方式，上面两点都没有改变：

* private成员只能被本类成员（类内）和友元访问，不能被派生类访问；
* protected成员可以被派生类访问。

	
### private继承

	class A{
	public:
 	 int a;
 	 A(){
  	  a1 = 1;
  	  a2 = 2;
  	  a3 = 3;
  	  a = 4;
 	 }
 	 void fun(){
 	   cout << a << endl;    //正确
 	   cout << a1 << endl;   //正确
  	  cout << a2 << endl;   //正确
  	  cout << a3 << endl;   //正确
 	 }
	public:
  	int a1;
	protected:
  	int a2;
	private:
  	int a3;
	};
	class B : private A{
	public:
  	int a;
  	B(int i){
   	 A();
   	 a = i;
	  }
  	void fun(){
    	cout << a << endl;       //正确，public成员。
    	cout << a1 << endl;       //正确，基类public成员,在派生类中变成了private,可以被派生类访问。
    	cout << a2 << endl;       //正确，基类的protected成员，在派生类中变成了private,可以被派生类访问。
   	 cout << a3 << endl;       //错误，基类的private成员不能被派生类访问。
 	 }
	};
	int main(){
  	B b(10);
 	 cout << b.a << endl;       //正确。public成员
  	cout << b.a1 << endl;      //错误，private成员不能在类外访问。
  	cout << b.a2 << endl;      //错误, private成员不能在类外访问。
  	cout << b.a3 << endl;      //错误，private成员不能在类外访问。
  	system("pause");
  	return 0;
	}



整理自：http://www.jb51.net/article/54224.htm
