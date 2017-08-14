# c++动态数组
##　动态分配一维数组

		#include<iostream>
		#include<iomanip>
		using namespace std;

		int main()
		{
			int* p = new int[5];//将动态数组起始地址赋给指针p
			int i;
			for (i = 0;i<5;i++)
			{
				p[i] = i;
				cout<<setw(4)<<p[i];
			}
			cout<<endl;
			delete[] p;
			return 0;

		}

×　动态分配内存解决了运行时确定数组大小的问题，但是这样的数组是没有名字的，只能通过地址来访问。本例中，将new操作得到的动态数组起始地址赋给指针p，这样*p,*(p+1).......*(p+i)就依次是数组中下标为0、1……i的元素。其实数组名就是数组的起始地址，那我们现在得到了数组的起始地址，可否将p当做数组名用呢？当然可以。因此访问元素我们还可以用p[0]、p[1]……p[i]的形式


		#include<iostream>
		#include<iomanip>
		using namespace std;

		int main()
		{
			int (*p)[3];//后面的[3]是必需的
			p = new int[2][3];
			int i,j;
			for (i=0;i<2;i++)
			{
				for (j=0;j<3;j++)
				{
					p[i][j] = i*j;
					cout<<setw(4)<<p[i][j];
				}
				cout<<endl;
			}
			return 0;

		}
* 本例创建了一个2\*3的二维数组，它实际上是由两个一维数组构成的，每个一维数组有3个元素，因此需要声明一个指向一维Int数组的指针p。指针p接收了二维数组的首地址后，既可以作为数组名来使用（如p[i][j]），也可以以指针运算的方式访问数组元素（如\*(\*(p+i)+j)）。C++标准规定，一个n维数组的数组名，如果出现在表达式中，就会立刻被转换成指向n-1维数组的指针，如果对这个指针执行*运算，其结果就是一个n-1维数组，并且也被转换成指针（指向n-2维数组的）。
