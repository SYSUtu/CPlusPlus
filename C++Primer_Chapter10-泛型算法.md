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

### 介绍back_inserter
一种保证算法有足够元素空间来容纳输出数据的方法是使用插入迭代器。通常情况，当我们通过一个迭代器向容器元素赋值的时候，值被赋予迭代器指向的元素。而当我们通过一个插入迭代器赋值时，一个与赋值号右侧相等的元素被添加到容器当中。back_inserter接受一个指向容器的引用，返回一个与该容器绑定的插入迭代器。当我们通过此迭代器赋值时，赋值运算符会调用push_back将一个具有给定值的元素添加到容器中：

`vector<int>vec;`
`auto it=back_inserter(vec);`
`*it=42;`

##重排容器元素的算法
某些算法会重排容器中元素的顺序。一个明显的例子是sort。还可以配合unique使得元素不重复。由于算法不能执行容器操作，我们将使用vector的erase成员来完成删除。
`void elimDups(vector<string> &words){`
`sort(words.begin(),words.end());`
`auto end_unque=unique(words.begin(),words.end());//最后一个不重复元素的后一个位置`
`word.erase(end_unique,words.end());}`

使用unique之后，words大小并未改变，它仍然有10个元素，只是覆盖了相邻的重复元素。

