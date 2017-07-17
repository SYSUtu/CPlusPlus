# Typedef
* typedef 行为有点像 #define 宏，用其实际类型替代同义字。
* 不同点：typedef 在编译时被解释，因此让编译器来应付超越预处理器能力的文本替换。
##

		typedef int (*MYFUN)(int, int); 
* 这种用法一般用在给函数定义别名的时候,上面的例子定义MYFUN 是一个函数指针, 函数类型是带两个int 参数, 返回一个int.在分析这种形式的定义的时候可以用下面的方法: 先去掉typedef 和别名, 剩下的就是原变量的类型. 去掉typedef和MYFUN以后就剩: 

		int (*)(int, int)
## 
* typedef给变量类型定义一个别名.

		typedef struct{ 
		int a; 
		int b; 
		}MY_TYPE; 

* 这里把一个未命名结构直接取了一个叫MY\_TYPE的别名, 这样如果你想定义结构的实例的时候就可以这样:
 
		MY_TYPE tmp;
