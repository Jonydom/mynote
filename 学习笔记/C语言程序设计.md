# C语言程序设计

[toc]

## 基础知识

### 输入、输出

`scanf()和printf()`

- `scanf()`有返回值且类型为int型，当发生错误时立刻返回EOF；
- `scanf()`函数返回的值为：**正确**按指定格式输入变量的个数，未正确接受的变量不算在内。

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

- **map**和**unordered_map**

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
 
```

