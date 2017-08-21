#关联容器
关联容器支持高效的关键字查找和访问。两个主要的**关联容器**类型是map和set。map中的元素是一些关键字-值对：关键字起到索引的作用，值则表示与索引相关联的数据。set中每个元素只包含一个关键字；     
map和multimap定义在头文件map中；set和multiset在set里面；无序容器在头文件`unordered_map`和`unordered_set`中。     
**按关键字有序保存元素:**      

* map
* set
* multimap
* multiset

**无序集合:** 

* unordered_map
* unordered_set
* unordered_multimap
* unordered_multiset  

##使用关联容器
一个经典的使用关联数组的例子：

`map<string,size_t>word_count;`        
`string word;`     
`while(cin>>word)`    
`++word_count[word];`    
`for(const auto &w:word_count)`      
`cout<<w.first<<"occurs"<<w.second<<((w.second>1)?"times":"time")<<endl;`

关联容器不支持顺序容器的位置相关操作，例如push_back。原因是关联容器中元素是根据关键字存储的，这些操作对关联容器没有意义。而且，关联容器也不支持构造函数或插入操作这些操作这些接受一个元素值和一个数量值的操作。
##定义关联容器
当定义一个map时，必须既指明关键字类型又指明值类型；而定义一个set时候，只需指明关键字类型，因为set中没有值。每个关联容器都定义一个默认构造函数，它创建一个类型制定的空容器。    
`map<string,size_t>word_count;//空容器`   
`set<string>exclude={"the","but"};`   
`map<string,string>authors={{"joyce","james"},{"auston","jane"}};`
#pair类型
定义在头文件utility中，一个pair保存两个数据成员。类似容器，pair是一个用来生成特定类型的模板。当创建一个pair时候，我们必须提供两个类型名：
`pair<string,string>anon;//保存两个string`
`pair<string,size_t>word_count;//保存一个string和一个size_t`
我们也可以为每个成员提供初始化器：    
`pair<string,string>author{"james",""joyce};`
`pair<string,string>author("james",""joyce);`
`pair<string,string>author={"james",""joyce};`
`make_pair("james",""joyce);//返回一个pair，类型从v1，v2看出`
#pair类型操作
对于set类型，`key_type`和`value_type`是一样的；set中保存的值就是关键字。在一个map中，元素是关键字-值对。即，每个元素是一个pair对象，包含一个关键字和一个关联的值。
`map<>string,int>::value_type v3;//v3是一个pair<const string ,int>`
`map<>string,int>::key_type v4;//v4为一个string`
`map<>string,int>::mapped_type v5;//v5为int`    
当解引用一个关联容器迭代器时，我们会得到一个类型为容器`value_type`的值得引用。对map而言，`value_type`是一个pair类型，其first成员保存const的关键字，second成员保存值。**迭代器指向的关键字值都是const的，我们通常不对关联容器使用泛型算法。关键字是const的特性意味着不能将关联容器传递给修改或重排容器元素的算法，如果我们真要对一个关联容器使用算法，要么是将它当做一个源序列，要么当做一个目的位置**
#向map添加元素
对一个map进行insert操作时候，必须记住元素类型是pair。通常，对于想要插入的数据，并没有一个现成的pair对象。可以在insert的参数列表中创建一个pair：
`word_count.insert({word,1});`   
`word_count.insert(make_pair(word,1));`
`word_count.insert(pair<string,size_t>(word,1));`
`word_count.insert(map<string,size_t>::value_type(word,1));`
