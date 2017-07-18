## 第三章 字符串，向量和数组
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
