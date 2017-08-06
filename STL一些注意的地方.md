# STL一些主意的地方
* 插入删除等改变容器容量的操作，会改变容器中数据的位置。用迭代器时候，需要注意

		for(vector<int>::iterator it=arr.begin(); it!=arr.end(); it ++) {
            	if(* it == 0) {
                	arr.erase(it); //在erase后，it失效，并不是指向vector的下一个元素，it成了一个“野指针”。

            	}
		}
		调用erase（）函数后，vector后面的元素会向前移位，形成新的容器，这样原来指向删除元素的迭代器就失效了。
* 可以简单的理解为如下：map可以当做一个容器（装载具有一定格式的数据）；pair可以理解为元素（放入到容器的的一个个个体），发现pair并没有单独行动的典型用法，正常都是配合map来使用（即把pair这个元素插入到map这个容器里面）
*    插入数据
 
  		(1)   my_Map["a"]   =   1; 
  		(2)   my_Map.insert(map<string,   int>::value_type("b",2)); 
  		(3)   my_Map.insert(pair<string,int>("c",3)); 
  		(4)   my_Map.insert(make_pair<string,int>("d",4)); 
* 