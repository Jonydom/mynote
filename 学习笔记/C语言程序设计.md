# C语言程序设计

[toc]

## 基础知识

### 输入、输出

`scanf()和printf()`

- `scanf()`有返回值且类型为int型，当发生错误时立刻返回EOF；
- `scanf()`函数返回的值为：**正确**按指定格式输入变量的个数，未正确接受的变量不算在内。

**类型标识符：**

| 类型标识符 |    对应类型     |
| :--------: | :-------------: |
|     %d     |   十进制数字    |
|     %s     |                 |
|     %c     |      char       |
|     %f     | float或者double |

### 类型转换

- 隐式转换：

  算术运算式中，低类型转换为高类型
  赋值表达式中，表达式的值转换为左边变量的类型
  函数调用时，实参转换为形参的类型
  函数返回值，return表达式转换为返回值类型

- ```
  double ←── float 高
  ↑
  long
  ↑
  unsigned
  ↑
  int ←── char,short 低
  ```

### 注意点❗❗❗

- `scanf`的输入参数中，变量前面的`&`不要省略；

  `scanf`中双引号内，除了“输入控制符”外什么都不要写；

  “输出控制符”和“输出参数”无论在“**顺序上**”还是在“**个数上**”一定要一一对应；

  “输入控制符”的类型和变量所定义的类型一定要一致；

  使用 `scanf` 之前先用 `printf` 提示输入。

## 编程练习

### 《谭浩强C语言程序设计》例题

#### 1. 判断闰年

**题目**：判定2000-2500年中的每一年是否为闰年，并将结果输出。

解析：闰年判断条件：

1. 能被4整除，但不能被100整除的年份都是闰年；
2. 能被400整除的年份是闰年。

代码：

```c
#include<stdio.h>
int main() {
	for(int year=2000; year<=2500; year++) {
		if ((year%4==0 && year%100!=0) || year%400==0)
		{
			printf("year %d is a run year.", year);
		}
	} 
	return 0;
} 
```

#### 2. 分数相加减

**题目**：![image-20220119134017274](https://raw.githubusercontent.com/Jonydom/myPic/main/img/202201191544755.png)

解析：用`sign`代表正负号

代码：

```c
#include<stdio.h>
int main() {
	double sign = 1, sum = 0;
	for (int i = 1; i <= 3; i++) {
		if (i%2 == 0) {
			sign = -1;
		}
		else {
			sign = 1;
		}
		sum += sign * (1/double(i)); 
	}
	printf("结果是%f", sum);
	return 0;
} 
```



### 《leetcode》题目

#### STL注意点❗❗❗

- **vector**

  ![image-20220119135851234](https://raw.githubusercontent.com/Jonydom/myPic/main/img/202201191544539.png)

- **map**和**unordered_map**（映射）

  map和unordered_map都是c++中可以充当字典（key-value）来用的数据类型

  1️⃣  **map**：

  底层原理是红黑树（一种非严格意义上的平衡二叉树），因此map内部的数据是**有序**的，map的查询、插入、删除操作的时间复杂度都是**O(logn)**。此外，map的key需要定义operator <。

  **基本操作**：

  ```
  
  ```

  2️⃣  **unordered_map**：

  与map类似，存储的也是key-value，但是unordered_map不跟据key的大小进行排序，存储时是根据key的**hash值**判断元素是否相同，所以内部元素是**无序**的。unordered_map的底层是一个**防冗余的哈希表**（开链法避免地址冲突）。unordered_map的key需要定义hash_value函数并且重载operator ==。

  **基本操作：**

  ```
  
  ```

  [简述C++中map和unordered_map的用法](https://blog.csdn.net/jingyi130705008/article/details/82633778)

- **set和unordered_set**（集合）

- **string类**

  **基本操作：**

  ```
  append()--在字符串的末尾添加字符
  find()--在字符串中查找字符串
  insert()--插入字符
  length()--返回字符串的长度
  replace()--替换字符串
  substr()--返回某个子字符串
  ```

  

#### 1. 219 存在重复元素II

**题目：**给你一个整数数组 nums 和一个整数 k ，判断数组中是否存在两个 不同的索引 i 和 j ，满足 nums[i] == nums[j] 且 abs(i - j) <= k 。如果存在，返回 true ；否则，返回 false 。

**题意：**是否在小于k的连续数据中，存在相同元素。

**思路：** **哈希表**。遍历数组，如果哈希表中没有这个元素，就加入表中；如果哈希表中有这个元素了，就判断当前元素下标和哈希表中存储的值相减，看其是否小于等于k；若大于k，则更新表中那个元素的值，然后继续向后遍历。

**代码：**

```c
bool containsNearbyDuplicate(vector<int>& nums, int k) {
        unordered_map<int, int> dict;
        int length = nums.size();
        for (int i = 0; i < length; i++) {
            int num = nums[i];
            if (dict.count(num) && i - dict[num] <= k)
            {
                return true;
            }
            dict[num] = i;
        }
        return false;
    }
```

#### 2. 3 无重复字符的最长子串

**题目：**给定一个字符串 `s` ，请你找出其中不含有重复字符的 **最长子串** 的长度。

**思路：** **滑动窗口**

**代码：**

```c
int lengthOfLongestSubstring(string s) {
	if(s.length() == 0) return 0;
	unordered_set<char> dict;
	int maxStr = 0;
	int left = 0;
	for (int i = 0; i < s.length(); i++) {
		//如果出现重复字符，则将左指针left设置为set中重复字符的下一个
		while (dict.find(s[i]) != dict.end()) {
			//把set中最左边元素剔除出去
			dict.erase(s[left]); 
			left++;
		}
		//如果不是重复字符
		maxStr = max(maxStr, i - left + 1);
		dict.insert(s[i]);
	}
	return maxStr;
    }
};
```

[参考链接](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/solution/wu-zhong-fu-zi-fu-de-zui-chang-zi-chuan-by-leetc-2/)

#### 3. 9 回文数

**题目：**给你一个整数 `x` ，如果 `x` 是一个回文整数，返回 `true` ；否则，返回 `false` 。

**思路：** 思路一：将数字转为字符串，然后检查字符串是否为回文串；

​				思路二：将数字本身反转，因为反转后可能存在整数溢出的问题，所以只反转一半数字，然后两个数字作比较。

**代码：**

```c
//思路一：
//思路二：
bool isPalindrome(int x) {
	//考虑边界情况：
    //负数，末尾为0且不是0的数字，都返回false
    if (x < 0 || (x % 10 == 0) && x != 0 ) {
        return false;
    }
    int reverseNumber = 0;
    while (x > reverseNumber) {
        reverseNumber = reverseNumber * 10 + (x % 10);
        x /= 10;
    }
    //若是奇数，则reverseNumber大于x，返回（x == reverseNumber/10）
    //若是偶数，则reverseNumber等于x，返回（x == reverseNumber）
	return x == reverseNumber || x == reverseNumber/10;
}
```

#### 4. 1332 删除回文子序列

## 注意点❗❗❗

### C++中内置函数

- accumulate()

  **所属文件：**#include<numeric>

  **函数作用：**

  1. 累加求和

  ```c++
  int sum = accumulate(vec.begin() , vec.end() , 42);
  //accumulate带有三个形参：头两个形参指定要累加的元素范围，第三个形参则是累加的初值。
  
  //可以使用accumulate把string型的vector容器中的元素连接起来：
  string sum = accumulate(v.begin() , v.end() , string(" "));
  //这个函数调用的效果是：从空字符串开始，把vec里的每个元素连接成一个字符串。
  ```

  2. 自定义数据类型的处理

### vector

**初始化：**

```c++
vector<int> list1; 
//默认初始化，vector为空， size为0，而且 capacity 也返回 0，意味着还没有分配内存空间
vector<int> list2(list1);
//list2初始化为list1
vector<int> list3 = {1,2,3,4,5,6};
vector<int> list4(7);
//list4中将包含7个元素，每个元素进行缺省的值初始化，对于int，也就是被赋值为0，因此ilist4被初始化为包含7个0
vector<int> list5(7,3);
//指定值初始化，初始化为包含7个值为3的int
vector<int> list6(list3.begin()+2, list3.end()-1);
//初始化为两个迭代器指定范围中元素的拷贝
```

