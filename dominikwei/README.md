# LeetCodeDaily

### C++ 语言基础:

## 1. vector

```c++
// initialize
vector<int> res; vector<int> res(n); vector<int> res{1,2,3};vector<vector<int> >dp; 

/**
*	member function
*/

bool is empty()
// the length of vector
size_type size();

// return the last element;
reference back();

// return the first element;
reference front();

// add element at the end
void push_back(const value_type& val);
// c++11. 
void emplace_back (Args&&... args);

// delete last element
void pop_back(const value_type& val);

void insert (iterator position, const value_type& val);

iterator erase (const_iterator position);
iterator erase (const_iterator first, const_iterator last);

// clear content
void clear() noexcept;

// swap content. like vector1 <-> vector2
void swap (vector& x); 

排序一个vector: nums = [[1,1,2], [2,3,5]]
sort(nums.begin(), nums.end(), [&](auto& a, auto& b) {
  return a[0] < b[1] // 从小到大
});

void iota( ForwardIterator first,ForwardIterator last, T value );
// 用顺序递增的值赋值指定范围内的元素
std::iota(foo.begin(), foo.end(), 0);// 将从 0 开始的 n 次递增值赋值给 foo
// out: 0 1 2 3 .... 15
```

## 2. string

```c++
1. size()
2. empty()
3. push_back() // 尾部插入一个元素
4. pop_back() // 删除尾部元素
5. substr(pos, len) // 从索引pos开始, 长度为len的子字符串
6. reserve(s.begin() //s.end()) 字符串翻转
7. split 分割实现:
       //C++ split
        /**
          string str = "dog cat cat dog";
          words = ["dog", "cat", "cat", "dog"];
        */
        istringstream strs(str);
        vector<string> words;
        string word;
        while(strs>>word){
            words.push_back(word);
        }
```

## 3. 哈希表,unordered_map

{ key: value }, 一般使用int 或者 string 作为key;

```c++
1. count(key) // 返回哈希表中key出现的次数,但哈希表中不会出现重复的键,可以用于判断key是否存在
2. erase(key) // 通过key清除哈希表的键值对
unordered_map<int, int> counter;  
//  遍历:
for (auto& it : counter) {
  int key = it.first;
  int val - it.second;
  cout << key << " " << val << endl;
}
初始化
unordered_map<int, char> map = {
    {1000, 'M'},
    {500, 'D'},
    {100, 'C'},
    {50, 'L'},
    {10, 'X'},
    {5, 'V'},
    {1, 'I'}
};
```

#### 4.哈希集合,unordered_set

```c++
1. insert(val)
2. erase(key)
```



#### 判断数字和文字以及大小写转换

<cctype>头文件.

1. isalpha(), 判断是否为字母, 

```c++
cout<<isalpha('a'); //返回非零
cout<<isalpha('2'); //返回0
```

2. isalnum, 判断是否为字母或者数字

```c++
cout<<isalnum('a'); //输出非零
cout<<isalnum('2'); // 非零
cout<<isalnum('.'); // 零
```

3. islower(), 判断是否小写 issupper(). 判断是否大写
4. tolower, toupper


# Const 常量
1. `INT_MAX` 和 `INT_MIN`
2. 