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