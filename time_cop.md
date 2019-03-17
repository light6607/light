# 时间复杂度
算法界的基本道理之一， 时间复杂度就是衡量算法好坏的一个重要标准，也是理性化思考的第一步！
本章主要讲了如何入门时间复杂度。

python data structure:http://interactivepython.org/runestone/static/pythonds/index.html

## 为何需要分析时间复杂度
- 不同机器上的代码执行效率不同，需要时间复杂度从宏观上来判断一段代码的执行效率


## 初体验 （小例子入门）
```
设想每一句代码执行时间为一个unit_time
1. int cal(int n) {
   int sum = 0; # 1 次
   int i = 1; # 1 次
   for (; i <= n; ++i) { # n次
     sum = sum + i; # n次
    }
   return sum;
    
 时间复杂度为:  (2n+2)*unit_time     ==  n
   
2. int cal(int n) {
   int sum = 0;  # 1
   int i = 1; # 1
   int j = 1; # 1
   for (; i <= n; ++i) { # n 
     j = 1; # n
     for (; j <= n; ++j) { # n^2
       sum = sum +  i * j; # n^2
     }
   }
 }
 
     2n^2 + 2n +3     == n^2

3. O(n) 表示法
T(n) = O(2n+2)
T(n) = O(2n2+2n+3)

当n很大的时候，公式之中的常量、低阶、系数三部分都无足轻重
所以我们只记录最大的量级即可。
T(n) = O(n)
T(n) = O(n^2)


```

## 分析时间复杂度技巧

1. 关注循环执行次数最多的一段代码

```
设想每一句代码执行时间为一个unit_time
 int cal(int n) {
   int sum = 0; 
   int i = 1; 
   for (; i <= n; ++i) { # n次
     sum = sum + i; # n次
    }
   return sum;
 }
 
 此处关注循坏的部分

```
2. 加法原则：总复杂度等于量级最大的那段代码复杂度
- 即可能存在多段不相关的代码，各自的复杂度为O(n) O(n^2)， 我们只需量级最大的部分即可


3. 乘法原则： 所谓的嵌套循环
```
int cal(int n) {
   int ret = 0; 
   int i = 1;
   for (; i < n; ++i) {
     ret = ret + f(i);
   } 
 } 
 
 int f(int n) {
  int sum = 0;
  int i = 1;
  for (; i < n; ++i) {
    sum = sum + i;
  } 
  return sum;
 }
 
 f(n)是一个复杂度为T(n)=O(n)的代码嵌套则为 O(n^2)

```
## 常见的时间复杂度

![image](https://static001.geekbang.org/resource/image/37/0a/3723793cc5c810e9d5b06bc95325bf0a.jpg)

- 需要注意的几个：
1. O(logn)、O(nlogn)

```
 i=1;
 while (i <= n)  {
   i = i * 2;
 }

T(n) = O(log2n)


 i=1;
 while (i <= n)  {
   i = i * 3;
 }
 
 T(n) = O(log3n)
 
对数都称之为O(logn)
因为 log3n 就等于 log32 * log2n， 忽略系数，就相当于 log2n 

```

2. O(m+n)、O(m*n)

- 两个数据集的规模些许不同
```
int cal(int m, int n) {
  int sum_1 = 0;
  int i = 1;
  for (; i < m; ++i) {
    sum_1 = sum_1 + i;
  }

  int sum_2 = 0;
  int j = 1;
  for (; j < n; ++j) {
    sum_2 = sum_2 + j;
  }

  return sum_1 + sum_2;
}

```

其实所有时间复杂度都逃不过下图四种！

![image](https://static001.geekbang.org/resource/image/49/04/497a3f120b7debee07dc0d03984faf04.jpg)
