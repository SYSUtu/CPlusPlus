# memset的用法
* memset 函数是内存赋值函数，用来给某一块内存空间进行赋值的。 其原型是：

void\* memset(void \*\_Dst, int  \_Val, size_t \_Size)


\_Dst是目标起始地址，\_Val是要赋的值，\_Size是要赋值的字节数。
 
		char str[9];//我们用memset给str初始化为“00000000”

        memset(str,0,8); //注意，memset是逐字节 拷贝的。

		int num[8];我们用memset给str初始化为{1,1,1,1,1,1,1,1}，

       	memset(num,1,8);//这样是不对的
		
		一个int是4个字节的，8个int是32个字节，所以首先要赋值的长度就不应该为8而是32。因为memset是 逐字节 拷贝，以num为首地址的8字节空间都被赋值为1，即一个int变为0X00000001 00000001 00000001 00000001，显然，把这个数化为十进制不会等于1的。