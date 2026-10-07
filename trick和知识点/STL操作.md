# 删除set中的指定元素
### 删除末尾元素
```cpp
if(!st.empty())
	st.erase(prev(st.end()));
```
不能 `st.erase(st.rbegin())` 
`prev(it)` 返回迭代器it的上一个迭代器，如果it是反向迭代器，那么就是想容器末尾移动
对应的，`next(it)` 返回迭代器it的下一个迭代器
### 删除指定值的元素
如果是普通set
```cpp
st.erase(x);
```
如果x不存在，不会出错
`st.erase(key)` 返回被删除元素的个数
`st.erase(pos)` 返回被删除元素的下一个元素的迭代器
如果是multiset
```cpp
st.erase(x);
```
会删除所有的x
```cpp
auto it = st.find(x);
if(it != st.end())
	st.erase(it);
```
可以只删除一个x
# 初始化vector为指定数组
```cpp
vector<int> b(a + 1, a + 1 + n);
```
定义一个vector b，元素为数组a中1到n的元素
# unique
unique函数去重时，相等的元素只保留**第一个**
所以如果要对自定义结构体进行排序和去重，要注意比较函数的写法